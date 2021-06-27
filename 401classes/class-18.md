# Review, Research, and Discussion

1. Describe the similarities between AWS API Gateway + Lambda functions and an ExpressJS Server

- Express Gateway is an API Gateway that can sit at the heart of any microservices architecture, regardless of what language or platform you’re using. Express Gateway secures your microservices and exposes them through APIs using Node.js, ExpressJS and Express middleware.

- Amazon’s API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. With a few clicks you can create an API that acts as a “front door” for applications to access data, business logic, or functionality from your back-end services, such as workloads running on Amazon Elastic Compute Cloud (Amazon EC2), code running on AWS Lambda, or any Web application. Amazon API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls, including traffic management, authorization and access control, monitoring, and API version management.

2. List the AWS Database offerings and talk about the pros and cons of each

- Relational Database. Relational databases store data with predefined schemas and relationships between them. ...
- Amazon Aurora. ...
- Amazon Relational Database Service (RDS) ...
- Amazon Redshift. ...
- Key-value Database. ...
- Amazon DynamoDB. ...
- In-memory Database. ...
- Amazon ElastiCache for Memcached.

3. What’s the difference between a FIFO and a standard queue?
Standard queues guarantee that a message is delivered at least once and duplicates can be introduced into the queue. FIFO queues ensure a message is delivered exactly once and remains available until a consumer processes and deletes it; duplicates are not introduced into the queue.

4. How can the server be assured a message was properly received?
The client (usually a browser) opens a connection to the server and sends a request. The server processes the request, generates a response, and closes the connection if it finds a Connection: Close header. ... Headers may provide various information about the request or the client body data.

## Document the following Vocabulary Terms

- Serverless API: Serverless is a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers. A serverless application runs in stateless compute containers that are event-triggered, ephemeral (may last for one invocation), and fully managed by the cloud provider.

- Triggers: Triggers are stored programs, which are automatically executed or fired when some events occur. Triggers are, in fact, written to be executed in response to any of the following events − A database manipulation (DML) statement (DELETE, INSERT, or UPDATE) A database definition (DDL) statement (CREATE, ALTER, or DROP).

- Dynamo vs Mongo: DynamoDB is a fully managed AWS service, MongoDB can be self installed or fully managed with MongoDB Atlas. ... DynamoDB uses tables, items and attributes, MongoDB uses JSON-like documents. DynamoDB supports limited data types and smaller item sizes; MongoDB supports more data types and has fewer size restrictions.

- Dynamoose vs Mongoose:
Dynamoose is a modeling tool for Amazon's DynamoDB. Dynamoose is heavily inspired by Mongoose, which means if you are coming from Mongoose the syntax will be very familar.

Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node. js. It manages relationships between data, provides schema validation, and is used to translate between objects in code and the representation of those objects in MongoDB.

## AWS SQS vs SNS

Comparisons: SQS vs SNS in AWS — Simple Notification Service and Simple Queue Service.

![Image](https://miro.medium.com/max/1446/1*DRrTtdyah9NHwR0VCm6MWA.png)

### TL;DR

SQS and SNS are important components for scalable, large scale, distributed, cloud-based applications:

SNS is a distributed publish-subscribe service.

SQS is distributed queuing service.

### SNS (Simple Notification Service)

![image](https://miro.medium.com/max/1004/1*mdUPKzrfJFuXa4d43KhKUQ.png)

Amazon SNS is a fast, flexible, fully managed push notification service that lets you send individual messages or to bulk messages to large numbers of recipients. Amazon SNS makes it simple and cost effective to send push notifications to mobile device users, email recipients or even send messages to other distributed services.

A distributed publish-subscribe system. Messages are pushed to subscribers as and when they are sent by publishers to SNS ,SNS supports several end points such as email, sms, http end point and SQS. If you want unknown number and type of subscribers to receive messages, you need SNS.

With Amazon SNS, you can send push notifications to Apple, Google, Fire OS, and Windows devices , as well as to Android devices in China with Baidu Cloud Push. You can use SNS to send SMS messages to mobile device users in the US or to email recipients worldwide.

SNS is a distributed publish-subscribe system. Messages are pushed to subscribers as and when they are sent by publishers to SNS.

### SNS Javascript SDK

Constructs a service interface object. Each API operation is exposed as a function on service.
Service Description

Amazon Simple Notification Service (Amazon SNS) is a web service that enables you to build distributed web-enabled applications. Applications can use Amazon SNS to easily push real-time notification messages to interested subscribers over multiple delivery protocols. For more information about this product see the Amazon SNS product page. For detailed information about Amazon SNS features and their associated API calls, see the Amazon SNS Developer Guide.

For information on the permissions you need to use this API, see Identity and access management in Amazon SNS in the Amazon SNS Developer Guide.

We also provide SDKs that enable you to access Amazon SNS from your preferred programming language. The SDKs contain functionality that automatically takes care of tasks such as: cryptographically signing your service requests, retrying requests, and handling error responses. For a list of available SDKs, go to Tools for Amazon Web Services.

### Sending a Request Using SNS

        var sns = new AWS.SNS();
        sns.addPermission(params, function (err, data) {
        if (err) console.log(err, err.stack); // an error occurred
        else     console.log(data);           // successful response
        });

### Locking the API Version

In order to ensure that the SNS object uses this specific API, you can construct the object by passing the apiVersion option to the constructor:

        var sns = new AWS.SNS({apiVersion: '2010-03-31'});

You can also set the API version globally in AWS.config.apiVersions using the sns service identifier:

        AWS.config.apiVersions = {
        sns: '2010-03-31',
        // other service API versions
        };

        var sns = new AWS.SNS();

### SQS Javascript SDK

#### Overview

Constructs a service interface object. Each API operation is exposed as a function on service.
Service Description

Welcome to the Amazon Simple Queue Service API Reference.

Amazon Simple Queue Service (Amazon SQS) is a reliable, highly-scalable hosted queue for storing messages as they travel between applications or microservices. Amazon SQS moves data between distributed application components and helps you decouple these components.

For information on the permissions you need to use this API, see Identity and access management in the Amazon Simple Queue Service Developer Guide.

You can use AWS SDKs to access Amazon SQS using your favorite programming language. The SDKs perform tasks such as the following automatically:

- Cryptographically sign your service requests

- Retry requests

- Handle error responses

#### Sending a Request Using SQS

        var sqs = new AWS.SQS();
        sqs.addPermission(params, function (err, data) {
        if (err) console.log(err, err.stack); // an error occurred
        else     console.log(data);           // successful response
        });

#### Locking the API Version

In order to ensure that the SQS object uses this specific API, you can construct the object by passing the apiVersion option to the constructor:

        var sqs = new AWS.SQS({apiVersion: '2012-11-05'});

You can also set the API version globally in AWS.config.apiVersions using the sqs service identifier:

        AWS.config.apiVersions = {
        sqs: '2012-11-05',
        // other service API versions
        };

        var sqs = new AWS.SQS();

#### References

- SQS and SNS Basics [Check it out](https://www.youtube.com/watch?v=UesxWuZMZqI)

- AWS SQS vs SNS[Read full article](https://medium.com/awesome-cloud/aws-difference-between-sqs-and-sns-61a397bf76c5)

- SNS Javascript SDK [Read full article](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/SNS.html)

- SQS Javascript SDK [Read full article](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/SQS.html)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
