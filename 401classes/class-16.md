# Review, Research, and Discussion

1. Describe “The Cloud”
The definition for the cloud can seem murky, but essentially, it's a term used to describe a global network of servers, each with a unique function. The cloud is not a physical entity, but instead is a vast network of remote servers around the globe which are hooked together and meant to operate as a single ecosystem.

2. What is a container (as it relates to computers and servers)?
A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. ... Available for both Linux and Windows-based applications, containerized software will always run the same, regardless of the infrastructure.

3. What is auto-scaling?
Autoscaling, also spelled auto scaling or auto-scaling, and sometimes also called automatic scaling, is a method used in cloud computing that dynamically adjusts the amount of computational resources in a server farm - typically measured by the number of active servers - automatically based on the load on the farm.

4. What is bandwidth?
In computing, bandwidth is the maximum rate of data transfer across a given path. Bandwidth may be characterized as network bandwidth, data bandwidth, or digital bandwidth.

5. How do cloud providers compute service costs?
When setting price, cloud providers determine the expense to maintaining the network. They start by calculating costs for network hardware, network infrastructure maintenance, and labor. These expenses are added together and then divided by the number of rack units a business will need for its IaaS cloud.

## Document the following Vocabulary Terms

- Server Instances: A server instance is a collection of SQL Server databases which are run by a solitary SQL Server service or instance. The details of each server instance can be viewed on the service console which can be web-based or command-line based.

- Containers: A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. ... Available for both Linux and Windows-based applications, containerized software will always run the same, regardless of the infrastructure.

- Cloud Services: What is Cloud Computing? Cloud Computing is defined as storing and accessing of data and computing services over the internet. It doesn't store any data on your personal computer. It is the on-demand availability of computer services like servers, data storage, networking, databases, etc.

- Cloud Architecture: A Cloud computing architecture consists of several components like a front-end platform, a back-end platform or servers, a network or internet service, and a cloud based delivery service. ... It comprise of interfaces and applications that are required to access the Cloud Computing or Cloud Programming platform.

- AWS: Amazon Web Services (AWS) is the leading Infrastructure-as-a-Service (IaaS) cloud provider. ... Students interested in a software development approach can use programming languages such as Java, Objective-C, C#, or Ruby-on-Rails to develop and deploy an application that uses AWS Cloud services or resides in the AWS Cloud.

- EC2/Beanstalk vs Heroku: Heroku is best suitable for Startups, Medium Businesses whereas AWS is mainly focused on Medium Businesses and Large Enterprises. Heroku can meet low computational demands whereas AWS can meet high/very high computational demands. Heroku doesn't needs infrastructure maintenance whereas AWS needs a dedicated DevOps guy.

## AWS S3

Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as data lakes, websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides easy-to-use management features so you can organize your data and configure finely-tuned access controls to meet your specific business, organizational, and compliance requirements. Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data for millions of applications for companies all around the world.

### Use cases

#### Backup and restore

Build scalable, durable, and secure backup and restore solutions with Amazon S3 and other AWS services, such as S3 Glacier, Amazon EFS, and Amazon EBS, to augment or replace existing on-premises capabilities. AWS and APN partners can help you meet Recovery Time Objectives (RTO), Recovery Point Objectives (RPO), and compliance requirements. With AWS, you can back up data already in the AWS Cloud or use AWS Storage Gateway, a hybrid storage service, to send backups of on-premises data to AWS.

#### Disaster recovery (DR)

Protect critical data, applications, and IT systems that are running in the AWS Cloud or in your on-premises environment without incurring the expense of a second physical site. With Amazon S3 storage, S3 Cross-Region Replication, and other AWS compute, networking, and database services, you can create DR architectures in order to quickly and easily recover from outages caused by natural disasters, system failures, and human errors.

#### Archive

Retire physical infrastructure, and archive data with S3 Glacier and S3 Glacier Deep Archive. These S3 Storage Classes retain objects long-term at the lowest rates. Simply create an S3 Lifecycle policy to archive objects throughout their lifecycles, or upload objects directly to the archival storage classes. With S3 Object Lock, you can apply retention dates to objects to protect them from deletions, and meet compliance requirements. Unlike tape libraries, S3 Glacier lets you restore archived objects in as little as one minute for expedited retrievals and 3-5 hours for standard retrievals. Bulk data restores from S3 Glacier and all restores from S3 Glacier Deep Archive are completed within 12 hours.

#### Data lakes and big data analytics

Accelerate innovation by building a data lake on Amazon S3, and extract valuable insights using query-in-place, analytics, and machine learning tools. As your data lake grows, use S3 Access Points to easily configure access to your data, with specific permissions for each application or sets of applications. You can also use AWS Lake Formation to quickly create a data lake, and centrally define and enforce security, governance, and auditing policies. The service collects data across your databases and S3 resources, moves it into a new data lake in Amazon S3, and cleans and classifies it using machine learning algorithms. All AWS resources can be scaled up to accommodate your expanding data stores — without upfront investments.

#### Hybrid cloud storage

Set up private connectivity between Amazon S3 and on-premises with AWS PrivateLink. You can provision private endpoints in a VPC to allow direct access to S3 from on-premises using private IPs from your VPC. AWS Storage Gateway lets you seamlessly connect and extend your on-premises applications to AWS Storage all while caching data locally for low-latency access. You can also automate data transfers between on-premises storage, including from S3 on Outposts, and Amazon S3 by using AWS DataSync, which can transfer data at speeds up to 10 times faster than open-source tools. You can also transfer files directly into and out of Amazon S3 with the AWS Transfer Family — a fully managed, simple, and seamless service that enables secure file exchanges with third parties using SFTP, FTPS, and FTP. Another way to enable a hybrid cloud storage environment is to work with a gateway provider from the APN.

#### Cloud-native applications

Build fast, cost-effective mobile and internet-based applications by using AWS services and Amazon S3 to store development and production data shared by the microservices that make up cloud-native applications. With Amazon S3, you can upload any amount of data and access it anywhere in order to deploy applications faster and reach more end users. Storing data in Amazon S3 means you have access to the latest AWS developer tools, S3 API, and services for machine learning and analytics to innovate and optimize your cloud-native applications.

## AWS Lambda - The Ultimate Guide

Are you looking to use AWS Lambda for the first time? Or are you evaluating its use for a production environment? We’ve created this article to help you in both of these cases.

AWS Lambda is one of the most popular serverless computing services out there. It is also the most popular provider used with the Serverless Framework.

In this article we’ll cover everything we know about AWS Lambda, its upsides and downsides, and we’ll provide a list of resources so you can learn more and get hands-on experience in using AWS Lambda.

### What is AWS Lambda?

AWS Lambda is a serverless computing service provided by Amazon Web Services (AWS). Users of AWS Lambda create functions, self-contained applications written in one of the supported languages and runtimes, and upload them to AWS Lambda, which executes those functions in an efficient and flexible manner.

The Lambda functions can perform any kind of computing task, from serving web pages and processing streams of data to calling APIs and integrating with other AWS services.

The concept of “serverless” computing refers to not needing to maintain your own servers to run these functions. AWS Lambda is a fully managed service that takes care of all the infrastructure for you. And so “serverless” doesn’t mean that there are no servers involved: it just means that the servers, the operating systems, the network layer and the rest of the infrastructure have already been taken care of, so that you can focus on writing application code.

### Why is AWS Lambda an essential part of the Serverless architecture?

When building Serverless applications, AWS Lambda is one of the main candidates for running the application code. Typically, to complete a Serverless stack you’ll need:

1. a computing service.
2. a database service; and
3. an HTTP gateway service.

Lambda fills the primary role of the compute service on AWS. It also integrates with many other AWS services and, together with API Gateway, DynamoDB and RDS, forms the basis for Serverless solutions for those using AWS. Lambda supports many of the most popular languages and runtimes, so it’s a good fit for a wide range of Serverless developers.

### What are the most common use cases for AWS Lambda?

Due to Lambda’s architecture, it can deliver great benefits over traditional cloud computing setups for applications where:

1. individual tasks run for a short time;
2. each task is generally self-contained;
3. there is a large difference between the lowest and highest levels in the workload of the application.

Some of the most common use cases for AWS Lambda that fit these criteria are:

Scalable APIs. When building APIs using AWS Lambda, one execution of a Lambda function can serve a single HTTP request. Different parts of the API can be routed to different Lambda functions via Amazon API Gateway. AWS Lambda automatically scales individual functions according to the demand for them, so different parts of your API can scale differently according to current usage levels. This allows for cost-effective and flexible API setups.

Data processing. Lambda functions are optimized for event-based data processing. It is easy to integrate AWS Lambda with datasources like Amazon DynamoDB and trigger a Lambda function for specific kinds of data events. For example, you could employ Lambda to do some work every time an item in DynamoDB is created or updated, thus making it a good fit for things like notifications, counters and analytics.

Task automation. With its event-driven model and flexibility, AWS Lambda is a great fit for automating various business tasks that don’t require an entire server at all times. This might include running scheduled jobs that perform cleanup in your infrastructure, processing data from forms submitted on your website, or moving data around between different datastores on demand.

## AWS Lambda Functions

AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers, creating workload-aware cluster scaling logic, maintaining event integrations, or managing runtimes. With Lambda, you can run code for virtually any type of application or backend service - all with zero administration. Just upload your code as a ZIP file or container image, and Lambda automatically and precisely allocates compute execution power and runs your code based on the incoming request or event, for any scale of traffic. You can set up your code to automatically trigger from over 200 AWS services and SaaS applications or call it directly from any web or mobile app. You can write Lambda functions in your favorite language (Node.js, Python, Go, Java, and more) and use both serverless and container tools, such as AWS SAM or Docker CLI, to build, test, and deploy your functions.

### Benefits

#### No servers to manage

AWS Lambda automatically runs your code without requiring you to provision or manage infrastructure. Just write the code and upload it to Lambda either as a ZIP file or container image.

#### Continuous scaling

AWS Lambda automatically scales your application by running code in response to each event. Your code runs in parallel and processes each trigger individually, scaling precisely with the size of the workload, from a few requests per day, to hundreds of thousands per second.

#### Cost optimized with millisecond metering

With AWS Lambda, you only pay for the compute time you consume, so you’re never paying for over-provisioned infrastructure. You are charged for every millisecond your code executes and the number of times your code is triggered. With Compute Savings Plan, you can additionally save up to 17%.

#### Consistent performance at any scale

With AWS Lambda, you can optimize your code execution time by choosing the right memory size for your function. You can also keep your functions initialized and hyper-ready to respond within double digit milliseconds by enabling Provisioned Concurrency.

### Content Delivery Network (CDN)

A Content Delivery Network (CDN) is a geographically distributed group of servers that work together to provide fast delivery of Internet content. A CDN allows for the fast transfer of data needed for loading Internet content including HTML pages, javascript files, stylesheets, images, and videos.

CDNs work through servers nearest to the website visitor respond to the request. The content delivery network copies the pages of a website to a network of servers that are spread out at geographically different locations, caching the contents of the page. When a user requests a webpage that is part of a content delivery network, the CDN will redirect the request from the originating site’s server to a server in the CDN that is closest to the user and deliver the cached content. CDNs will also communicate with the originating server to deliver any content that has not been previously cached. In turn, the speed is improved by distributing content closer to the website visitors by using a nearby CDN server, causing visitors to experience faster page loading times. In simpler terms, for example, instead of a user in London trying to access a server in LA, which can cause slower Internet speeds, the user would be redirected through a CDN that is geographically closest to them (London, Paris, Stockholm, etc). As of today, the majority of web traffic goes through through CDNs, including traffic from major sites like Facebook, Netflix, and Amazon.

Employing a CDN doesn’t only speed up the delivery of Internet content, it helps protect your website against certain forms of cyber attacks, such as Denial of Service attacks. It protects against these threats because CDNs allow for the handling of more traffic and withstanding hardware failure better than many origin servers.

Source: CloudFlare, Webopedia

Additional Reading: Pantheon’s Advanced Global CDN to Further Enterprise Open Source Adoption

Related Terms: Denial of Service (DoS), Distributed Denial of Service (DDoS)

### What does this mean for an SMB?

CDNs are something that larger companies are more likely to implement. The main reasons why company want to use CDNs are to improve Internet website load speeds, content delivery speeds, and to reduce the likelihood of falling victim to and improve defenses against Distributed Denial of Service attacks (DDoS).

A smaller company probably doesn’t need to improve website load speeds with a CDN as they typically don’t have an overwhelming amount of traffic. A Distributed Denial of Service attack may pose a potential threat against gambling companies or other mid-to-large enterprises such as banks or defense contractors. DDoS attacks are rarely used against SMB’s unless they upset a hacker group. CyberHoot is not saying a denial of service attack won’t happen, but the cost of protection is too much for most SMBs to afford.

CyberHoot’s best advice to an SMB is to know what a CDN is, and at most, establish a relationship with a CDN protection vendor without paying for protection. DDoS protection vendors include: Arbor Networks, AT&T, Verizon, and Akamai.

Mid-to-Large enterprises should have contracts in place to protect themselves in seconds when hit with a DDOS attack. SMB’s should not. Although, if you are looking to employ a CDN; Akamai, Cloudflare and Arbor Networks all operate CDN’s in addition to DDOS solutions.

**References:**

- AWS S3 [Read full article](https://aws.amazon.com/s3/)

- AWS Lambda Basics [Read full article](https://www.serverless.com/aws-lambda)

- AWS Lambda Functions [Read full article](https://aws.amazon.com/lambda/)

- CDN [Read full article](https://cyberhoot.com/cybrary/content-delivery-network-cdn/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
