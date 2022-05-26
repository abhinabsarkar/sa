# Data architecture
* [ACID principle](https://database.guide/what-is-acid-in-databases) - Atomic, Consistent, Isolated Durable
* [Normalization](https://www.guru99.com/database-normalization.html) - Normalization divides larger tables into smaller tables and links them using relationships. 
* Concurrency
* [Sharding vs Partitioning](https://hazelcast.com/glossary/sharding/) - Sharding and partitioning are both about breaking up a large data set into smaller subsets. The difference is that sharding implies the data is spread across multiple computers while partitioning does not. Partitioning is about grouping subsets of data within a single database instance. In many cases, the terms sharding and partitioning are even used synonymously, especially when preceded by the terms “horizontal” and “vertical.”
* [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem) - The CAP theorem implies that a distributed system, in the presence of a network partition, must make trade-offs between availability and consistency.
> Often, you can achieve higher availability by adopting an eventual consistency model.