# Key Terms

 > Blob Storage 

   Widely used kind of storage in small and large scale systems. They don't really count as database per sec, partially because they only allow the user to store and retrieve data based on the name of the blob. This is sort of like a key-value store but usually blob stores have different guarantees. They might be slower than KV stores but values can be megabytes large (or sometimes gigabytes large). Usually people use this to store things like ***large binaries, database snapshots, or images*** and other static assets that a websites might have.

   Blob storage is rather complicated to have on premise, and only giant companies like Google and Amazon have infrastructure that supports it. So usually in the context of system design interviews you can assume that you will be able to use ***GCS*** or ***S3***. These are blob storage service hosted by Google and Amazon respectively, that cost money depending on how much storage you use and how often you store and retrive blobs from that storage.
---

> Time Series Database 

  A ***TSDB*** is a special kind of database optimized for storing and analyzing time-indexed data: data points that specifically occur at a given moment in time. Examples of ***TSDBx*** are ***InfluxDB***, Prometheus, and  Graphite.

---

> Graph Database 

A **graph database** is a type of database that uses graph structures with nodes, edges, and properties to store and represent data. It’s well-suited for scenarios where relationships between data are as important as the data itself, like social networks, recommendation engines, and network analysis.

---

## Key Concepts of a Graph Database
1. **Nodes**: These are entities or objects, similar to records or rows in a relational database. For example, in a social network, nodes could represent users.
2. **Edges**: These represent the relationships between nodes. For instance, an edge can represent a "friendship" relationship between two users.
3. **Properties**: Both nodes and edges can have properties, which store information about them. For example, a user node might have properties like `name`, `age`, and `location`.
4. **Labels**: Nodes can be labeled to classify them into categories, like `Person` or `Product`.

## Example: Social Network

Consider a simple social network where you want to store information about users and their friendships.

### Graph Model:
- **Nodes**: 
  - `User1` (properties: `name: "Alice"`, `age: 30`)
  - `User2` (properties: `name: "Bob"`, `age: 25`)
  - `User3` (properties: `name: "Charlie"`, `age: 35`)

- **Edges**:
  - `User1` -[**FRIEND**]-> `User2`
  - `User2` -[**FRIEND**]-> `User3`
  - `User1` -[**FRIEND**]-> `User3`

This graph structure means:
- Alice is friends with Bob.
- Bob is friends with Charlie.
- Alice is friends with Charlie.

### How Data Would Look:
In a graph database like **Neo4j**, you might represent the relationships using the **Cypher** query language as follows:

```cypher
// Create Nodes
CREATE (a:Person {name: 'Alice', age: 30})
CREATE (b:Person {name: 'Bob', age: 25})
CREATE (c:Person {name: 'Charlie', age: 35})

// Create Relationships
CREATE (a)-[:FRIEND]->(b)
CREATE (b)-[:FRIEND]->(c)
CREATE (a)-[:FRIEND]->(c)
```
--- 

### Advantages of Graph Databases:

Efficiency with Relationships: They are much faster than relational databases for managing complex relationships between data.
Flexibility: Adding new types of relationships without altering the existing structure is easy.
Intuitive Querying: Queries often mimic the way we think about connected data, making them easy to understand.

### Use Cases:

Social Networks: Storing relationships between users, like friends, followers, and connections.
Recommendation Engines: Finding products or content based on user preferences or behaviors.
Fraud Detection: Identifying unusual patterns in transactional networks.
Network and IT Management: Analyzing networks, dependencies, and relationships between servers and devices.


# Cypher Query Language

Cypher is a query language for Neo4j, a graph database. It is designed to query and manipulate data in a graph format, which consists of nodes, relationships, and properties.

## Key Concepts

- **Node**: Represents an entity, similar to a record in a relational database.
- **Relationship**: Describes how nodes are connected, indicating the relationships between them.
- **Properties**: Key-value pairs that can be used to describe nodes or relationships.

## Basic Syntax

### Creating Nodes

To create a node with a label `Person` and properties like `name` and `age`:

```cypher
CREATE (p:Person {name: "John Doe", age: 30})
``` 

> Creating Relationships
  
  To create a relationship between two existing nodes:

  ```
  MATCH (a:Person {name: "John Doe"}), (b:Person {name: "Jane Doe"})
  
  CREATE (a)-[:FRIENDS_WITH]->(b)

  ```

  > Reading Data
    
    To retrieve nodes and their properties:

    ```
      MATCH (p:Person)
      RETURN p.name, p.age

    ```



> Summary
   
   - Cypher is a powerful language for working with graph data in Neo4j. It allows for intuitive querying and manipulation of nodes, relationships, and their properties. Understanding EXPLAIN and PROFILE can help in optimizing the performance of your queries.


--- 

> Spatial Database

  A type of database optimized for storing and querying spatial database like locations on a map. Spatial database rely on spatial indexes ***like quadtrees*** to quickly perform spatial queries like finding all locations in the vicinity of a region.

> Quadtree 

  
  A quadtree is a data structure that is used to partition a two-dimensional space into smaller regions, allowing efficient querying and storage of spatial data. It's commonly used in computer graphics, image compression, spatial indexing, and geographic information systems (GIS). Here's a breakdown of how a quadtree works:

> Structure of a Quadtree

A quadtree is a tree where each internal node has exactly four children, which correspond to four quadrants of a given space (often labeled as NE, NW, SE, and SW).
The space is recursively divided into four quadrants or regions until each leaf node contains either a single object or none at all (or until a predefined level of granularity is reached).
Key Characteristics

> Recursive Division: The quadtree divides a 2D space into four equal parts at each level. This process continues until a        specified condition is met, such as the maximum number of points per region or a maximum depth.
 Hierarchical Structure: The root node represents the entire space, while each child represents a progressively smaller region of that space.
 
> Leaf Nodes: The leaves of the tree represent the smallest regions, which may contain data points (such as coordinates of objects).

### Types of Quadtrees
There are several variations of quadtrees depending on how the data is stored:

> Point Quadtree: Used for storing points in 2D space. Each point is inserted into a quadrant based on its position relative to the center of the node.
Region Quadtree: Used for storing regions like images or grids. This type divides the space based on whether each region is > > homogeneous (e.g., a uniform color in image compression).
PR (Point-Region) Quadtree: Similar to the region quadtree but stores a list of points in each leaf. It is used to index 2D points efficiently.
Example: Constructing a Quadtree
Start with a space that covers the entire region you want to index.
If the space has more than one data point, divide it into four equal-sized quadrants.
Distribute the points into the corresponding quadrant.
Recursively subdivide each quadrant until each one has a manageable number of points (or none).
Use Cases
Spatial Indexing: Quadtrees are used in spatial databases to store and query points, lines, and polygons.
Image Compression: Quadtree-based algorithms can compress images by breaking them down into homogeneous regions.
Collision Detection: In games and simulations, quadtrees help detect objects that might collide by narrowing down potential intersections.
Visualization
Imagine a large square representing a region on a map. A quadtree divides this square into four smaller squares. If any of these smaller squares contains more than the set limit of objects, they are further divided into smaller squares, continuing until each region is manageable.

> Google Cloud Storage 
  
  > S3

  > InfuxDB

  > InfluxDB

  > Prometheus

  > Neo4j

     