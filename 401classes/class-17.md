# Review, Research, and Discussion

1. What are serverless functions?
Serverless computing is a cloud computing execution model in which the cloud provider allocates machine resources on demand, taking care of the servers on behalf of their customers.
A serverless function is a programmatic function written by a software developer for a single purpose. It's then hosted and maintained on infrastructure by cloud computing companies. These companies take care of code maintenance and execution so that developers can deploy new code faster and easier.

2. If you were to create a system that emulated Lambda functions, how would you do it?

- Open the Functions page on the Lambda console.
- Choose Create function.
- Under Basic information, do the following: For Function name, enter my-function . For Runtime, - - confirm that Node. js 14. x is selected. Note that Lambda provides runtimes for . ...
-Choose Create function.

3. Describe how a CDN works
A CDN (Content Delivery Network) is a highly-distributed platform of servers that helps minimize delays in loading web page content by reducing the physical distance between the server and the user. ... Without a CDN, content origin servers must respond to every single end user request.

## Document the following Vocabulary Terms

- Serverless Functions: A serverless function is a programmatic function written by a software developer for a single purpose. It's then hosted and maintained on infrastructure by cloud computing companies. These companies take care of code maintenance and execution so that developers can deploy new code faster and easier.

- Cloud Storage: Cloud storage is a model of computer data storage in which the digital data is stored in logical pools, said to be on "the cloud". The physical storage spans multiple servers (sometimes in multiple locations), and the physical environment is typically owned and managed by a hosting company.

- CDN: A content delivery network, or content distribution network, is a geographically distributed network of proxy servers and their data centers. The goal is to provide high availability and performance by distributing the service spatially relative to end users.

## AWS API Gateway Overview

### What is Amazon API Gateway?

Amazon API Gateway is a managed service that allows developers to define the HTTP endpoints of a REST API or a WebSocket API and connect those endpoints with the corresponding backend business logic. It also handles authentication, access control, monitoring, and tracing of API requests.

Many Serverless applications use Amazon API Gateway, which conveniently replaces the API servers with a managed serverless solution.

### How does API Gateway work?

API Gateway sits between the backend services of your API and your API’s users, handling the HTTP requests to your API endpoints and routing them to the correct backends. It provides a set of tools that help you manage your API definitions and the mappings between endpoints and their respective backend services. It can also generate API references from your definitions and make them available to your users as API documentation.

API Gateway integrates with many other AWS services like AWS Lambda, AWS SNS, AWS IAM, and Cognito Identity Pools. These integrations allow for fully managed authentication and authorization layers, as well as detailed metrics and tracing for API requests.

![Image](https://s3-us-west-2.amazonaws.com/assets.site.serverless.com/guides/amazon-api-gateway/amazon-api-gateway-guide-1.png)

The Amazon API Gateway graphical user interface.

The service’s graphical user interface allows you to sketch out the API structure and view the API flows in graphical form after they’ve been created.

While the user interface is a good way to try out API Gateway, we recommend creating your API structure in code, for example, using the Serverless Framework’s built-in API Gateway event.

### Why is API Gateway an essential part of the Serverless ecosystem?

Within the Serverless ecosystem, API Gateway is the piece that ties together Serverless functions and API definitions. Being able to trigger the execution of a Serverless function directly in response to an HTTP request is the key reason why API Gateway is so valuable in Serverless setups: it enables a truly serverless architecture for web applications. When using API Gateway together with other AWS services, it’s possible to build a fully functional customer-facing web application without maintaining a single server yourself.

This brings the advantages of the serverless model—scalability, low maintenance, and low cost due to low overhead—to mainstream web applications.

## AWS API Gateway

Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. APIs act as the "front door" for applications to access data, business logic, or functionality from your backend services. Using API Gateway, you can create RESTful APIs and WebSocket APIs that enable real-time two-way communication applications. API Gateway supports containerized and serverless workloads, as well as web applications.

API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including traffic management, CORS support, authorization and access control, throttling, monitoring, and API version management. API Gateway has no minimum fees or startup costs. You pay for the API calls you receive and the amount of data transferred out and, with the API Gateway tiered pricing model, you can reduce your cost as your API usage scales.

### API Types

#### RESTful APIs

Build RESTful APIs optimized for serverless workloads and HTTP backends using HTTP APIs. HTTP APIs are the best choice for building APIs that only require API proxy functionality. If your APIs require API proxy functionality and API management features in a single solution, API Gateway also offers REST APIs.

#### WEBSOCKET APIs

Build real-time two-way communication applications, such as chat apps and streaming dashboards, with WebSocket APIs. API Gateway maintains a persistent connection to handle message transfer between your backend service and your clients.

![image](https://d1.awsstatic.com/serverless/New-API-GW-Diagram.c9fc9835d2a9aa00ef90d0ddc4c6402a2536de0d.png)

## AWS DynamoDB Guide

### What is DynamoDB?

DynamoDB is a hosted NoSQL database offered by Amazon Web Services (AWS). It offers:

1. reliable performance even as it scales;
2. a managed experience, so you won't be SSH-ing into servers to upgrade the crypto libraries;
3. a small, simple API allowing for simple key-value access as well as more advanced query patterns.

### DynamoDB is a particularly good fit for the following use cases

Applications with large amounts of data and strict latency requirements. As your amount of data scales, JOINs and advanced SQL operations can slow down your queries. With DynamoDB, your queries have predictable latency up to any size, including over 100 TBs!

Serverless applications using AWS Lambda. AWS Lambda provides auto-scaling, stateless, ephemeral compute in response to event triggers. DynamoDB is accessible via an HTTP API and performs authentication & authorization via IAM roles, making it a perfect fit for building Serverless applications.

Data sets with simple, known access patterns. If you're generating recommendations and serving them to users, DynamoDB's simple key-value access patterns make it a fast, reliable choice.

### Key Concepts

In this section, we'll cover the key concepts you need to know about DynamoDB. At the end of this section, you will understand:

1. tables, items, and attributes.
2. primary key.
3. secondary indexes.
4. read and write capacity.

### Tables, Items, and Attributes

Tables, items, and attributes are the core building blocks of DynamoDB.

A table is a grouping of data records. For example, you might have a Users table to store data about your users, and an Orders table to store data about your users' orders. This concept is similar to a table in a relational database or a collection in MongoDB.

An item is a single data record in a table. Each item in a table is uniquely identified by the stated primary key of the table. In your Users table, an item would be a particular User. An item is similar to a row in a relational database or a document in MongoDB.

Attributes are pieces of data attached to a single item. This could be a simple Age attribute that stores the age of a user. An attribute is comparable to a column in a relational database or a field in MongoDB. DynamoDB does not require attributes on items except for attributes that make up your primary key.
Primary Key

Each item in a table is uniquely identified by a primary key. The primary key definition must be defined at the creation of the table, and the primary key must be provided when inserting a new item.

There are two types of primary key: a simple primary key made up of just a partition key, and a composite primary key made up of a partition key and a sort key.

Using a simple primary key is similar to standard key-value stores like Memcached or accessing rows in a SQL table by a primary key. One example would be a Users table with a Username primary key.

The composite primary key is more complex. With a composite primary key, you specify both a partition key and a sort key. The sort key is used to (wait for it) sort items with the same partition. One example could be an Orders tables for recording customer orders on an e-commerce site. The partition key would be the CustomerId, and the sort key would be the OrderId.

Remember: each item in a table is uniquely identified by a primary key, even with the composite key. When using a table with a composite primary key, you may have multiple items with the same partition key but different sort keys. You can only have one item with a particular combination of partition key and sort key.

The composite primary key enables sophisticated query patterns, including grabbing all items with the given partition key or using the sort key to narrow the relevant items for a particular query.

For more on interacting with items, start with the lesson on the anatomy of an item.
Secondary Indexes

The primary key uniquely identifies an item in a table, and you may make queries against the table using the primary key. However, sometimes you have additional access patterns that would be inefficient with your primary key. DynamoDB has the notion of secondary indexes to enable these additional access patterns.

The first kind of secondary index is a local secondary index. A local secondary index uses the same partition key as the underlying table but a different sort key. To take our Order table example from the previous section, imagine you wanted to quickly access a customer's orders in descending order of the amount they spent on the order. You could add a local secondary index with a partition key of CustomerId and a sort key of Amount, allowing for efficient queries on a customer's orders by amount.

The second kind of secondary index is a global secondary index. A global secondary index can define an entirely different primary key for a table. This could mean setting an index with just a partition key for a table with a composite primary key. It could also mean using completely different attributes to populate a partition key and sort key. With the Order example above, we could have a global secondary index with a partition key of OrderId so we could retrieve a particular order without knowing the CustomerId that placed the order.

Secondary indexes are a complex topic but are extremely useful in getting the most out of DynamoDB. Check out the section on secondary indexes for a deeper dive.
Read and Write Capacity

When you use a database like MySQL, Postgres, or MongoDB, you provision a particular server to run your database. You'll need to choose your instance size -- how many CPUs do you need, how much RAM, how many GBs of storage, etc.

Not so with DynamoDB. Instead, you provision read and write capacity units. These units allow a given number of operations per second. This is a fundamentally different pricing paradigm than the instance-based world -- pricing can more closely reflect actual usage.

DynamoDB also has autoscaling of your read and write capacity units. This makes it much easier to scale your application up during peak times while saving money by scaling down when your users are asleep.

## AWS DynamoDB

Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale. It's a fully managed, multi-region, multi-active, durable database with built-in security, backup and restore, and in-memory caching for internet-scale applications. DynamoDB can handle more than 10 trillion requests per day and can support peaks of more than 20 million requests per second.

Many of the world's fastest growing businesses such as Lyft, Airbnb, and Redfin as well as enterprises such as Samsung, Toyota, and Capital One depend on the scale and performance of DynamoDB to support their mission-critical workloads.

Hundreds of thousands of AWS customers have chosen DynamoDB as their key-value and document database for mobile, web, gaming, ad tech, IoT, and other applications that need low-latency data access at any scale. Create a new table for your application and let DynamoDB handle the rest.

### Benefits

#### Performance at scale

DynamoDB supports some of the world’s largest scale applications by providing consistent, single-digit millisecond response times at any scale. You can build applications with virtually unlimited throughput and storage. DynamoDB global tables replicate your data across multiple AWS Regions to give you fast, local access to data for your globally distributed applications. For use cases that require even faster access with microsecond latency, DynamoDB Accelerator (DAX) provides a fully managed in-memory cache.

#### No servers to manage

DynamoDB is serverless with no servers to provision, patch, or manage and no software to install, maintain, or operate. DynamoDB automatically scales tables up and down to adjust for capacity and maintain performance. Availability and fault tolerance are built in, eliminating the need to architect your applications for these capabilities. DynamoDB provides both provisioned and on-demand capacity modes so that you can optimize costs by specifying capacity per workload, or paying for only the resources you consume.

#### Enterprise ready

DynamoDB supports ACID transactions to enable you to build business-critical applications at scale. DynamoDB encrypts all data by default and provides fine-grained identity and access control on all your tables. You can create full backups of hundreds of terabytes of data instantly with no performance impact to your tables, and recover to any point in time in the preceding 35 days with no downtime. You also can export your DynamoDB table data to your data lake in Amazon S3 to perform analytics at any scale. DynamoDB is also backed by a service level agreement for guaranteed availability.

### Applications

#### Serverless Web Apps

Build powerful web applications that automatically scale up and down. You don't need to maintain servers, and your applications have automated high availability.

#### Mobile Backends

Use DynamoDB and AWS AppSync to build interactive mobile and web apps with real-time updates, offline data access, and data sync with built-in conflict resolution.

#### Microservices

Build flexible and reusable microservices using DynamoDB as a serverless data store for consistent and fast performance.

#### References

- AWS API Gateway Overview [Read full article](https://www.serverless.com/amazon-api-gateway)

- AWS API Gateway [Read full article](https://aws.amazon.com/api-gateway/)

- AWS DynamoDB Guide [Read full article](https://www.dynamodbguide.com/what-is-dynamo-db/)

- AWS DynamoDB [Read full article](https://aws.amazon.com/dynamodb/)

- Dynamoose [Read full article](https://dynamoosejs.com/getting_started/Introduction/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
