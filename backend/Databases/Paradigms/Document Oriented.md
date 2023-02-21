source: https://www.influxdata.com/document-database/

### What is it?

A document database or document-oriented database is a new type of [noSQL database](https://www.influxdata.com/from-sql-to-nosql/) structure. Along with other types of noSQL database designs, a document database represents the use of a type of object-oriented engineering in database technologies, or some similar innovation that improves how data is used. The data is typically stored in a JavaScript Object Notation or “JSON” format.

Experts have [described this JSON format as a “readable”](https://jsonformatter.curiousconcept.com/) way to store key-value pairs and create the noSQL design that leads to certain data storage and retrieval benefits.

Compared to relational databases, noSQL databases, like document databases, have abundant use cases in enterprise and administrative data governance strategies. While methodologies vary a bit, the document database aims to accomplish the objective of using the same data model that developers use in their application code.

### Examples

- [AWS DynamoDb]
- [MongoDB]
- [Couchbase]

### Use cases

Many businesses use a document database to keep structured or semi-structured data in an easy-to-retrieve environment. As we’ll talk about later, they may also use these formats to make it easier to input raw data into a more structured format. Queries that use the noSQL design allow users to get specific results based on the agile nature of the document database storage setup.

For example, companies may use a document database to store customer identifiers and other customer data. They may retrieve that customer data for predictive analytics, as part of the sales funnel operation, or to use in standalone customer relationship management software systems or other business purposes. In any case, the document database is the central holder of information for this and other types of business intelligence.

Document databases can also be used for inventory management. The key-value pairs and data structures would be linked to physical products in a warehouse, and a company would retrieve this information to move product or otherwise handle inventory. If the document database is open source they can be used for [edge computing](https://www.influxdata.com/glossary/edge-computing/) workloads like collecting sensor data from [IoT devices](https://www.influxdata.com/glossary/iot-devices/) and then sending data from the [edge back to a cloud](https://www.influxdata.com/products/influxdb-edge-data-replication/) instance for analysis.

As a third example, a document database could be used for product development, in which key-value pairs and a data storage system identify product characteristics and attributes, helping teams bring products to market.

Because of their flexible data model, document databases can also be extended with different types of indexes to support features like full text search that is normally done by dedicated [search engine databases](https://www.influxdata.com/search-engine-database/).

### Why use

As mentioned above with use cases, companies often use document databases because of the agile nature of their data handling capabilities. However, there’s another major benefit to using document databases or other noSQL designs. It has to do with the use of raw or unstructured data. Many companies face challenges with raw or unstructured data and funneling it into a database design. For instance, suppose a company gets letters it wants to mine for data, and they’re stored in digital format. The letters themselves don’t have those static relational database tables built in. Instead, they have a narrative where the identifiers are hidden in the text. Therefore, to get that important data and use it, the company must have some consistent, universal way to mine it from a letter and get it into a context where it can be queried. Typically, you can’t query something out of a letter format.

Over time, the ability to take raw, unstructured data and add structure to it became a valuable part of what database engineers do. So when experts say a noSQL design “facilitates rich data structures,” they mean, in part, that it puts data in a situation or environment where people can conduct richer queries. On the other hand, you could describe it as a system in which the JSON format is simply what makes the data more structured than it otherwise would be.

A new document database design in a JSON format or similar object format helps facilitate the mining of raw information, aggregating it, and generally governing it according to business principles. Another way to think about this is that having a database in a new JSON format may make it easier for companies to upgrade over time.

One of the biggest challenges in working with data systems is the chore of manual data entry or other manual data work. If data is in a static traditional database table, there are only certain use cases that work and ways to retrieve that data. Migrating the data from a legacy system to a new one might take a lot of labor-intensive manual data entry work.

By contrast, when the data is in a new noSQL format, there will be different ways to retrieve it or migrate it without manual data entry.

### Advantages

Experts have identified various benefits to using a [new document database or noSQL design](https://www.influxdata.com/solutions/). First of all, these databases often provide faster development cycles. Another benefit of document databases or noSQL databases is better querying. As mentioned above, these systems make data retrieval more efficient in various ways.

Document databases can also accommodate rich data structures. To understand this, it’s helpful to get a good understanding of JSON format and what that entails.

Beyond these, one of the other key benefits of NoSQL document databases in terms of querying is that some of these noSQL types of designs can scale horizontally.

In general, “horizontal scaling” refers to creating more independent modules to tackle parts of a complex data task. For instance, horizontal scaling in hardware means adding more machines, but vertical scaling simply means adding more power to one machine. In database management, horizontal scaling involves splitting data sets into multiple tables, objects, or modules, so that querying can be done better or more efficiently. There are various tradeoffs in database performance when it comes to sharding which are described in [CAP theorem](https://www.influxdata.com/glossary/cap-theorem/).

Another benefit of noSQL databases involves more accessible development. An intuitive way to understand this is that developers feel most comfortable with technologies that are transparent to them and ones that they understand. Since many developers are trained on new NoSQL database designs, they are accustomed to working through these structures.
