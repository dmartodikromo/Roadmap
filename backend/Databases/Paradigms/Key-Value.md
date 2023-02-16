source: https://www.influxdata.com/key-value-database/

### What is it?

A key-value database (also known as a key-value store) is a type of [noSQL](https://www.influxdata.com/from-sql-to-nosql/) database. Unlike prior relational databases that stored data in defined tables and columns, a key-value database instead uses individual or combinations of keys to retrieve associated values. Together they are known as key-value pairs. These values can be anything from simple data types like strings or integers to complex objects with multiple nested values. Each key is a unique identifier that maps to a value or a location of data being stored.

![[Pasted image 20230215224511.png]]

People describing key-value database design sometimes explain that this new type of database is like object-oriented programming applied to database systems. Some of the same ideas about labeling objects in their properties in OOP also apply to the key-value database and the way it is built.

### Examples

- Redis
- Memcached

### Workings

Key-value databases have sets of key-value pairs, where the key is the identifier and the value is the data in question. A key-value pair is very similar to the various different implementations of hash tables in many programming languages, such as dictionaries with Python and objects in Javascript. The major difference with a key-value database is that your data is persisted and managed via the database you are using.

Under the hood, key-value databases work by keeping an in-memory data structure that is mapped to the data stored on disk. RAM is much faster than accessing data from disk so most databases will have some sort of algorithm to keep frequently accessed data in RAM and only fallback to disk if the index isn’t already stored in memory.

Some characterize key-value databases as the ‘simplest’ type of noSQL database. It can be useful for scalable data setups and other enterprise uses that need flexibility. By allowing a freer orientation of data, the key-value database offers a way to store data for more flexible retrieval, in a way that accommodates schema changes that are often needed as application needs change during development.

Key-value databases can differ significantly in their implementation depending on the intended use case. Some differences between databases can include:

-   consistency model
-   whether keys can be sorted
-   replication
-   sharding
-   serialization strategies

### Features

The most basic features that are required for any key-value database are the ability to create, update, retrieve, and delete data using keys. But many of the most popular databases provide features beyond the basics to make developers more productive. Below are some of the most common features provided by popular key-value databases.

#### Data type support

Many key-value databases provide support for defined data types and semi-structured data. This can be things like arrays or nested dictionaries. By giving the database more information about your data, there is room for more optimization in terms of storage and query performance.

#### Sorted keys

The simplest implementations of key-value databases have keys which can be accessed directly. One common feature that is useful is to have keys sorted in some way so that the keys can be efficiently iterated over. Some common use cases for this feature:

-   Grabbing all keys that start with a certain letter
-   Grabbing all keys within a range of numbers
-   Grabbing all keys less than or greater than a certain number
-   Grabbing keys within a certain period of time if the key is a timestamp

#### Secondary key/index support

Some key-value databases allow you to define multiple different keys to access the same information. For example if you are storing user data you might want to be able to find that information by using either the name, email address, or phone number. Secondary key support makes all of these options possible, rather than being forced to choose a single key.

#### Replication and partitioning

Many key-value databases provide support for advanced scaling features out of the box. Replication means you can have multiple nodes with copies of the same data. This not only helps with scalability but also disaster recovery; if one node goes down, you still have your data.

Partitioning is how your data is broken up across nodes. Many databases provide a default way of doing this but also give you the option of defining exactly how you want your data to be partitioned. A simple example of this would be using the first letter of each key as the partition, which would result in 26 partitions, one for each letter in the alphabet.

More advanced key-value databases will have automatic support for distributing your database across multiple data centers. This makes your application more reliable as well as improving performance because you can respond to queries close to users around the world by using local data centers.

#### ACID support

While much of the performance gains possible by NoSQL databases are due to dropping support for things like [[ACID]], many key-value databases will have the option to use ACID transactions when required, at the cost of some performance loss. Simply having the option is a huge benefit for developers because they can use it when they need it but still get great performance for situations where it isn’t necessary.

### Advantages

#### Scalability

The primary selling point of key-value databases and NoSQL databases in general is the scalability they provide compared to relational databases. These DBs became popular after big tech companies like Amazon and Google wrote about the databases they built internally to handle scaling problems.

Databases typically become the primary bottleneck for software and many developers had felt the pain of trying to implement replication, sharding, and other strategies used for scaling out relational databases. Being able to abstract that away and focus on writing code that drove business value appealed to many tech companies and is why usage of key-value databases has grown so fast.

#### Developer productivity

A secondary benefit of key-value databases is developer productivity. A big part of that was mentioned above already — not having to spend so much time trying to scale the database lets developers focus on other things.

Additionally, the schema-less nature of key-value and NoSQL databases made it much easier to iterate while writing code. Making changes to schema with a relational database requires migrations and potential downtime, which doesn’t happen with a key-value database.

There’s also the idea of “impedance mismatch” which relates to the mental model of how your data is manipulated in your code compared to how it is stored in a relational database. Trying to map the objects you are using in your code to a bunch of different tables in your relational database doesn’t feel natural in many cases. Key-value databases mostly eliminate this problem and make it easier for software engineers to work with their data.

#### Performance

Even ignoring the scalability features provided by key-value databases, for various use cases a single node key-value database has performance benefits in terms of reading and writing data compared to a more general-purpose relational database.

### Disadvantages

#### Lack of ACID support

Many key-value databases don’t provide support for ACID to improve their scalability. In the early days of NoSQL adoption, many developers would try to compensate for this by essentially replicating transactions in their application code which led to many problems.

#### Messy schema

While being schema-less can improve developer productivity in the short term, if an engineering team isn’t disciplined enough, their data model can become a mess if they don’t plan properly. Being able to change schema on the fly can cover for poor planning and lead to long-term problems. In some ways, being forced to map out your data model with a relational database can be seen as a benefit.

#### Advanced query support not available

A standard key-value database implementation doesn’t provide any sort of insight into what the actual value contains — when you grab the value using the key you have no guarantee of what you are getting. This means that you will have to filter or process data you don’t need in your application code. This will generally be less efficient in terms of performance compared to doing most of that work in the database.

The lack of query language also means that logic that would normally be kept in the database is now in your application code, which can lead to complexity and make maintaining code more difficult.

Updating values can also be inefficient because the entire chunk of data has to be replaced, even if you just want to update a single field in a nested data structure.

#### Potentially less efficient storage and query optimization

With defined schema types, a relational database is able to optimize storage by using compression in some cases and can also optimize common queries like getting aggregates of column values.

### Use cases

#### Performance-sensitive applications

One common design pattern that works with many apps is to use a key-value database like Redis to improve the read performance of an application. A relational database can act as the source of truth where data is written and that data is then pushed out to a number of geographically distributed key-value database nodes. This results in reduced latency because the data is closer to users and also makes an app more scalable and reliable.

Key-value databases can also be used for storing pre-computed data that is crucial to user experience. An example of this is Twitter generating users’ news feeds ahead of time and caching them so users get a faster homepage load.

#### Storage engine for higher-level databases

Many databases use key-value DBs under the hood as a storage engine due to their raw performance and to save development time by not reinventing the wheel. RocksDB is an open-source embedded key-value database created by Facebook that has been used by or is supported by MySQL, Cassandra, MariaDB, MongoDB, YugabyteDB, and InfluxDB.

#### Internet of Things

Many businesses in many different industries are using sensors and related technology to collect more data about operations. It might be related to manufacturing and product development, or the use of a service model to retrieve data for customers. Companies might be collecting data about supplier and vending contracts, and how those operations work.

A corresponding benefit applies to new communications models like the Internet of Things, where a greater volume of devices are used to move data through a business network. In the [IoT](https://www.influxdata.com/customers/iot-data-platform/), data is “always in transit” – filtered through a greater number of hardware hops, with all of the logistical issues that may entail.

In response, modern engineering has conceived of ways to do [processing closer to the origin of individual data points](https://www.influxdata.com/glossary/edge-computing/). Experts often promote the idea of computing “[close to the edge](https://www.influxdata.com/blog/influxdb-iot-edge-historian/)” with a noSQL database – in the environment that stores data where the devices are collecting information. Key-value databases complement this kind of data operation. Because of their flexibility, they allow for better and more capable handling of this volatile activity as well.

The use of a key-value database in general and an Influx time series model, in particular, can merge with other strategies to build business efficiencies. For example, the better use of time-stamped data can dovetail with data visualization that provides business insights.

Another way to achieve more with these types of noSQL database setups is to tie them to dynamic resources in vendor service models. Serverless function is one prime example of how this works. By utilizing [AWS Lambda](https://www.influxdata.com/blog/build-serverless-lambda-function-influxdb/) or some [serverless function](https://www.influxdata.com/blog/build-serverless-lambda-function-influxdb/) service, the business user can complement the robust database systems around the time-stamped data in a way that doesn’t waste computing power.