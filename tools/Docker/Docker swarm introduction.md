
Issues you will have to deal with when using docker in productions:

-   Automated scheduling and scaling
-   Service discovery
-   Zero downtime deployments
-   High availability and fault tolerance
-   A/B deployments

What is container orchestration
![[Pasted image 20230210151147.png]]

-   Cluster management
-   Scheduling
-   Service discovery
-   Replication
-   Health management
-   Declare desired state
	- Active reconciliation

Container ecosystem layers
![[Pasted image 20230210151220.png]]
Container orchestration solutions

(open source)
![[Pasted image 20230210151237.png]]

-   Hosted solutions
	-   IBM cloud container service
	-   Amazon ECS
	-   Azure containers
	-   Google containers engine

operational model used by Docker Swarm for managing a cluster is declarative

You can think of Docker Swarm as a special mode that is activated by the command: docker swarm init. The --advertise-addr option specifies the address in which the other nodes will use to join the swarm.

This docker swarm init command generates a join token. The token makes sure that no malicious nodes join the swarm. You need to use this token to join the other nodes to the swarm. For convenience, the output includes the full command docker swarm join, which you can just copy/paste to the other nodes.

Back on node1, run docker node ls to verify your three-node cluster:

$ docker node ls

ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS

7x9s8baa79l29zdsx95i1tfjp     node3               Ready               Active

x223z25t7y7o4np3uq45d49br     node2               Ready               Active

zdqbsoxa6x1bubg3jyjdmrnrn *   node1               Ready               Active              Leader

This command outputs the three nodes in your swarm. The asterisk (*) next to the ID of the node represents the node that handled that specific command (docker node ls in this case).

Your node consists of one manager node and two workers nodes. Managers handle commands and manage the state of the swarm. Workers cannot handle commands and are simply used to run containers at scale. By default, managers are also used to run containers.

Although you control the swarm directly from the node in which its running, you can control a Docker swarm remotely by connecting to the Docker Engine of the manager by using the remote API or by activating a remote host from your local Docker installation (using the $DOCKER_HOST and $DOCKER_CERT_PATH environment variables). This will become useful when you want to remotely control production applications, instead of using SSH to directly control production servers.

To run containers on a Docker Swarm, you need to create a service. A service is an abstraction that represents multiple containers of the same image deployed across a distributed cluster.

docker service create --detach=true --name nginx1 --publish 80:80  --mount source=/etc/hostname,target=/usr/share/nginx/html/index.html,type=bind,ro nginx:1.12

This command statement is declarative, and Docker Swarm will try to maintain the state declared in this command unless explicitly changed by another docker service command. This behavior is useful when nodes go down, for example, and containers are automatically rescheduled on other nodes.

The --mount flag is useful to have NGINX print out the hostname of the node it's running on. You will use this later in this lab when you start load balancing between multiple containers of NGINX that are distributed across different nodes in the cluster and you want to see which node in the swarm is serving the request.

The --publish command uses the swarm's built-in routing mesh. In this case, port 80 is exposed on every node in the swarm. The routing mesh will route a request coming in on port 80 to one of the nodes running the container.

To take a deeper look at the running tasks, use the command docker service ps. A task is another abstraction in Docker Swarm that represents the running instances of a service. In this case, there is a 1-1 mapping between a task and a container.

Run the docker service update command:

$ docker service update --image nginx:1.13 --detach=true nginx1

This triggers a rolling update of the swarm. Quickly enter the command docker service ps nginx1 over and over to see the updates in real time.

You can fine-tune the rolling update by using these options:

--update-parallelism: specifies the number of containers to update immediately (defaults to 1).

--update-delay: specifies the delay between finishing updating a set of containers before moving on to the next set.

The inspect-and-then-adapt model of Docker Swarm enables it to perform reconciliation when something goes wrong. For example, when a node in the swarm goes down, it might take down running containers with it. The swarm will recognize this loss of containers and will attempt to reschedule containers on available nodes to achieve the desired state for that service.

n this lab, your Docker Swarm cluster consists of one master and two worker nodes. This configuration is not highly available. The manager node contains the necessary information to manage the cluster, but if this node goes down, the cluster will cease to function. For a production application, you should provision a cluster with multiple manager nodes to allow for manager node failures.

You should have at least three manager nodes but typically no more than seven. Manager nodes implement the raft consensus algorithm, which requires that more than 50% of the nodes agree on the state that is being stored for the cluster. If you don't achieve more than 50% agreement, the swarm will cease to operate correctly. For this reason, note the following guidance for node failure tolerance:

-   Three manager nodes tolerate one node failure.
-   Five manager nodes tolerate two node failures.
-   Seven manager nodes tolerate three node failures.

It is possible to have an even number of manager nodes, but it adds no value in terms of the number of node failures. For example, four manager nodes will tolerate only one node failure, which is the same tolerance as a three-manager node cluster. However, the more manager nodes you have, the harder it is to achieve a consensus on the state of a cluster.

While you typically want to limit the number of manager nodes to no more than seven, you can scale the number of worker nodes much higher than that. Worker nodes can scale up into the thousands of nodes. Worker nodes communicate by using the gossip protocol, which is optimized to be perform well under a lot of traffic and a large number of nodes.