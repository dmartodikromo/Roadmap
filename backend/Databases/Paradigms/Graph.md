source: https://www.influxdata.com/graph-database/

### What is it?

A graph database is a specialized [NoSQL](https://www.influxdata.com/from-sql-to-nosql/) database designed for storing and querying data that is connected via defined relationships. Data points in a graph database are called nodes and these nodes are connected to related data via edges. The data attached to each node are known as properties. Graph databases aren’t restricted by predefined schema like relational databases, and this flexibility allows for data to be connected naturally through the life of an application.

Because of their simplicity and ease of use, graph databases are quickly becoming one of the fastest-growing categories in data management.

![[Pasted image 20230216112251.png]]

### Examples

- [Neo4J](https://neo4j.com/)
- [TigerGraph](https://www.tigergraph.com/)
- [AWS Neptune](https://aws.amazon.com/neptune/)

### Use cases

Developers and analysts use graph databases for a range of use-case scenarios. As you use relationships to process the transactions in your graph databases, you can detect scenarios where a single purchase relates to other data related to a customer, products, regional data, and other data.

#### Fraud detection

With a graph database, you can process purchase and financial transactions in (almost) real-time, which means you can prevent fraud. With a graph database, you can easily detect if a certain email address and credit card are related to other fraudulent charges.

With fraud detection, you can also differentiate accounts where a single email address is being used for multiple people. You can find scenarios where various people are associated with a single IP address, even though they have multiple physical addresses in different accounts.

#### Master data management (MDM)

Master data management (MDM) is a record of everything that’s essential about your company’s operations. It could include everything about accounts, business units, customers, locations, partners, products, and users. With a graph database, you can connect all that master data to solve pressing business questions. With its immediate business value, you can gain a competitive advantage as you’re able to manage your connected data better and understand your networks.

#### Network and IT operations

You can easily connect your monitoring tools across your network and IT operations with a graph database. Not only can you gain valuable performance insights, but you can better gauge vulnerabilities, troubleshoot solutions, conduct capacity planning, and better prepare your organization with impact analysis based on user guides.

#### Identity and access management (IAM)

You can identify and manage changing authorizations, groups, roles, and products with a graph database. As these interrelationships become ever-more complex, you can track all the data and better control access for your native graph with real-time results. With the interconnected nature of a graph database, you can support an intuitive access management relationship. You can be faster and more accurate while ensuring a greater level of efficiency across your organization.

#### Recommendation engines

You can easily store a customer’s friends, interests, and purchase history with a graph database. Based on your analysis of what you can see about the relationships between these variables, you can offer a recommendation engine that will offer ideas of what the user will like and prefer. For example, you can extrapolate with a high degree of accuracy that a customer might like products like those another user bought if/when they have the same purchasing history and behavior.

### Why use

A graph database allows you to quickly and easily store data and analyze the relationships among data, so you can better understand the myriad of possible outcomes.

#### Graphs are everywhere

The most obvious example of a graph database is a social network, but you can see them in business transactions, recommendations based on connections, routing, and the logistics involved in optimal paths related to things like supply chain management.

#### Support simple modeling

With a graph database, you model based on understanding the problem, so it’s much cleaner and more simplified. It’s an easy-to-understand model which you can use to represent and store complex data.

#### Use structured or unstructured data

With a graph database, you can support a range of data demands with structured, non structured, and even a hybrid solution to meet your needs.

#### Simple querying

While almost any graph query could be performed on a relational database using SQL, the query would be extremely complex. Most graph databases have query languages built around the idea of working with edges and nodes and traversing a graph structure. The result is simpler queries that are faster to write and easier to understand.

Here’s an example showing the difference in query complexity between standard SQL versus the Cypher query language used with the Neo4J graph database. The query is grabbing a territory description by using the name of a sales rep employed by the company.

```sql
SELECT e.LastName, et.Description
FROM Employee AS e
JOIN EmployeeTerritory AS et ON (et.EmployeeID = e.EmployeeID)
JOIN Territory AS t ON (et.TerritoryID = t.TerritoryID);
```
```cypher
MATCH (t:Territory)<-[:IN_TERRITORY]-(e:Employee)
RETURN t.description, collect(e.lastName);
```
The query using Cypher is only 2 lines compared to 4 lines to SQL. This difference in number of lines and complexity only gets larger when you want to grab information from more relationships.

Joins are also very expensive in terms of performance, trying to join values between many tables will result in very slow queries for large data sets. In comparison, these types of queries using a graph database will still be fast even at large scale.

#### Queries directly from relations

With a graph database, you can query directly from one relation. So, instead of creating three queries, you can more quickly arrive at your answer without the hassle of multiple steps.

#### Achieve better performance

Graph databases use a simple index, so you see improved efficiency with query performance. Since the queries are broken into sub-queries, they run concurrently to achieve high throughput and low latency. And because graph databases are designed for running graph traversals, they are more efficient in terms of required hardware resources.

#### Get a visualization

With a graph database, it’s important to visualize the data to understand it better and draw conclusions. You can see parts of the stored relations and entities along with associated properties. Most graph databases will provide a variety of tools or integrations to make visualizing your data easy.

#### Qualified relations

You can quickly and easily add properties to the relations with graph databases. While there are other database models that you could select, graph databases continue to offer the high-quality solution you need to deliver on time and on budget. They’re also a great way to avoid the monumental headache of figuring out how to achieve the same results with other methods.

### Workings

Graphs and graph databases work on relationship principles. You can follow those connections through the data lifecycle since your connected data is equally or more important than any single data point. You start with the idea, move to design, and then implement and operate with your query language. Since you’re not inferring data connections, your data is more expressive and simpler than other relational database structures.

#### Components of a graph database

There are 3 main components of a graph database. The first are nodes, which represent an entity like a product, user, event, or place. The second component of a graph database are properties, which can be added to these nodes to give more context, for example a user node might have properties like username, email address, interests, and many other potential properties. The third component are the edges or relationships that connect nodes in the graph. These edges can be directed or undirected. For example it might make sense to have a directed edge if you are connecting a manager and their direct report. Edges can also have values attached, for something like a map where the edge represents a road between cities the edge could represent the number of miles between the two cities.

#### Graph database architecture and design

From a design perspective graph databases provide better performance due to a variety of optimizations compared to more general purpose databases. The most obvious is how data is mapped in-memory compared to stored on disk.

A native graph database uses what is called index-free adjacency. What this means is that on disk each node actually stores pointers to connected nodes. The result is that for great performance the database doesn’t need to store a large index in RAM, because it’s already available via the node itself. This also means that performance stays the same regardless of how large your graph is. It only depends on how many nodes you are traversing

In comparison if you were using a relational database you would have to join tables together at query time and this would get slower as the tables get larger. The alternative would be to have a massive index in memory, but this is also costly.

### Advantages

#### Performance

When you’re dealing with data that is highly relational in nature, a graph database offers greater performance, with a consistency that’s essential as your data continues to grow. A graph database is a great solution when you have real-time queries involving big data analysis, even as your data continues to expand.

#### Better problem-solving

With a graph database, you’re better able to solve problems in ways that are just not practical with relational databases. Consider hypothetical situations that will offer your interconnected data the most practical situation for a graph database before you lock it in.

#### AI and machine learning friendly

Graph databases are a natural fit for use with machine learning and artificial intelligence. By using a graph database you can find valuable business insights by finding patterns and connections between your data that might otherwise be missed. By using a graph database you have a scalable data store that can quickly be used to train models and create predictions on your data.

Some examples of problems that can be solved by combining a graph database with machine learning would be finding valuable steps in customer acquisition journeys, personalizing services and platforms, finding users across multiple platforms, fraud prevention by finding non-obvious but connected behavior, and much more.

#### Object-oriented thinking

With a graph database, there are no hidden assumptions. The semantics are clear and explicit. With object-oriented thinking, you have the fine control to keep the data in place without hidden assumptions.

#### Flexibility

With a graph database, you have a flexible platform to discover connections. You can analyze your data based on quality or strength compared to other data in your database. You also have the ability to simply add more properties or types of nodes as your application grows, without having to worry about schema changes.

#### Accessible recursive path queries

You can find direct and indirect connections between data with real-life queries with a graph database. That level of accessibility is important as you bundle the queries together and look for patterns related to your product and how it interconnects with your audience data.

#### Multiple dimensions

You can manage big data with a graph database by combining and hierarchizing multiple dimensions. So, you could segment a group based on different dimensions: time, demographics, geo dimensions, and more.

#### Aggregate queries

With a graph database, you can easily aggregate and group relevant data in a way that would be impractical with relational databases. So, business analysts and data scientists can conduct virtually any analytical query on a graph database.

### Disadvantages

There’s always tradeoffs with any technology. It’s not perfect, and you should understand the disadvantages and limitations of using graph databases. Here are a few reasons why you might not want to use a graph database.

#### No standard query language

With graph databases, there is no standardized query language. The language depends on the platform used, which could be an advantage or disadvantage depending on your situation. This generally means developers will need to learn a new query language which increases time to adopt a graph database and will increase onboarding time for new hires.

This situation may change in the near future, in 2019 a proposal was made for a standard language called [GQL](https://en.wikipedia.org/wiki/Graph_Query_Language) (Graph Query language) and approved by an ISO/IEC committee. GQL is intended to be a declarative language similar to SQL but borrow features from current graph query implementations like Cypher and GSQL.

#### No transactions

Graphs are not the right choice for apps that require transactions. They’re just not efficient when processing high volumes of transactional data. They also struggle to process queries that span the entire database.

#### Smaller community

Graph databases have a relatively small user base compared to relational databases, so it may be difficult to find the support you need to optimize further, maintain, or grow your graph database as your company continues to develop.