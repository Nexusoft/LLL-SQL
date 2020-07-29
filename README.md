# LLL-SQL
LLL: Lower Level Library - SQL: Structure Query Language for high performance database systems

# Performance 

This repository will contain a high performance database system that operates using SQL, built as a means to be a drop-in replacement to MySQL servers, that improves performance substantially. The LLD is O(1), so tables and queries will always execute in constant time no matter how large the database becomes. 

## The LLD benchmarks currently stand at:

- 180k Random Reads per Second
- 120k Random Writes per Second
- 600k Random Keychain Checks per Second (to determine if a key is in the dataset)
- 1200k Sequential Reads per Second

## The LLP benchmarks currently stand at:

- 450k Requests per Second
- Max Concurrent Connections consistent with ulimit rather than available threads

# Development 

This development tree will implement a SQL parser on top of an LLP for MySQL and Postgres protocols, to act as a drop-in replacement for current databases powering the internet. MySQL maxes out at 2k queries per second, this project will be updated with benchamrks of the complete LLL-SQL performance once completed, but we anticipate 50-100k queries per second, being that most SELECT queries can use Sequential Reads that operate at 1.2M rows per second. Performance could very well be over 100k queries per second, and a maximum of 120k inserts or updates per second.

# Integrations 

Using the MySQL protocol as a drop-in replacement, we will begin with some basic integrations such as using the LLL-SQL backend to power WordPress sites among many others. 100k requests per second is a MASSIVE website, so based on projections a single server should be able to do with the LLL-SQL what would take 50 servers clustered using MySQL with the same level of performance. This should overall reduce overhead associated with large websites, and reduce the load balancing required to manage such a large server cluster.

# Graphing Database Semantics 

The Datachain in the LLD can contain mappings to other keys associated with a JOIN operation, significantly improving the performance of JOIN queries. This will enable foreign keys and relational models to be joined while retaining Sequential Read Performance. JOIN is a wonderful operation for SQL, but very resource intensive. We intend this architecure to make JOIN queries fast and efficient, potentially reaching 50-100k JOIN operations per second.
