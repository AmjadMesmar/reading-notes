
# Review, Research, and Discussion

1. Describe the Web-Request-Response-Cycle.
Web request-response happens by the 3-ways handshake:
1- The client send a request to the server.
2- The server open a port to the client and sends an acknowledgement response to the client.
3- The client then acknowledge the server's response and start sending data.

2. Explain what a “server” is, as it relates to the WRRC.
In computing, a server is a piece of computer hardware or software that provides functionality for other programs or devices, called "clients". This architecture is called the client–server model.

3. What does it mean to “deploy” an application?
Software deployment is all of the activities that make a software system available for use. The general deployment process consists of several interrelated activities with possible transitions between them. These activities can occur at the producer side or at the consumer side or both.

## Amazon EC2

### What is Amazon EC2?

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers. Amazon EC2’s simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment.

Amazon EC2 offers the broadest and deepest compute platform with choice of processor, storage, networking, operating system, and purchase model. We offer the fastest processors in the cloud and we are the only cloud with 400 Gbps ethernet networking. We have the most powerful GPU instances for machine learning training and graphics workloads, as well as the lowest cost-per-inference instances in the cloud. More SAP, HPC, Machine Learning, and Windows workloads run on AWS than any other cloud. Click here to learn What's New with Amazon EC2.

### Reliable, scalable, infrastructure on demand

1. Increase or decrease capacity within minutes, not hours or days.

2. SLA commitment of 99.99% availability for each Amazon EC2 region. Each region consists of at least 3 availability zones.

3. The AWS Region/AZ model has been recognized by Gartner as the recommended approach for running enterprise applications that require high availability.

### Features of Amazon EC2

Amazon EC2 provides the following features:

1. Virtual computing environments, known as instances

2. Preconfigured templates for your instances, known as Amazon Machine Images (AMIs), that package the bits you need for your server (including the operating system and additional software)

3. Various configurations of CPU, memory, storage, and networking capacity for your instances, known as instance types

4. Secure login information for your instances using key pairs (AWS stores the public key, and you store the private key in a secure place)

5. Storage volumes for temporary data that's deleted when you stop, hibernate, or terminate your instance, known as instance store volumes

6. Persistent storage volumes for your data using Amazon Elastic Block Store (Amazon EBS), known as Amazon EBS volumes

7. Multiple physical locations for your resources, such as instances and Amazon EBS volumes, known as Regions and Availability Zones

8. A firewall that enables you to specify the protocols, ports, and source IP ranges that can reach your instances using security groups

9. Static IPv4 addresses for dynamic cloud computing, known as Elastic IP addresses

10. Metadata, known as tags, that you can create and assign to your Amazon EC2 resources

11. Virtual networks you can create that are logically isolated from the rest of the AWS Cloud, and that you can optionally connect to your own network, known as virtual private clouds (VPCs)

### Access Amazon EC2

- Amazon EC2 provides a web-based user interface, the Amazon EC2 console. If you've signed up for an AWS account, you can access the Amazon EC2 console by signing into the AWS Management Console and selecting EC2 from the console home page.

If you prefer to use a command line interface, you have the following options:

***AWS Command Line Interface (CLI)***

Provides commands for a broad set of AWS products, and is supported on Windows, Mac, and Linux. To get started, see AWS Command Line Interface User Guide. For more information about the commands for Amazon EC2, see ec2 in the AWS CLI Command Reference.

***AWS Tools for Windows PowerShell***

Provides commands for a broad set of AWS products for those who script in the PowerShell environment. To get started, see the AWS Tools for Windows PowerShell User Guide. For more information about the cmdlets for Amazon EC2, see the AWS Tools for PowerShell Cmdlet Reference.

Amazon EC2 supports creating resources using AWS CloudFormation. You create a template, in JSON or YAML, that describes your AWS resources, and AWS CloudFormation provisions and configures those resources for you. You can reuse your CloudFormation templates to provision the same resources multiple times, whether in the same Region and account or in multiple Regions and accounts. For more information about the resource types and properties for Amazon EC2, see EC2 resource type reference in the AWS CloudFormation User Guide.

Amazon EC2 provides a Query API. These requests are HTTP or HTTPS requests that use the HTTP verbs GET or POST and a Query parameter named Action. For more information about the API actions for Amazon EC2, see Actions in the Amazon EC2 API Reference.

If you prefer to build applications using language-specific APIs instead of submitting a request over HTTP or HTTPS, AWS provides libraries, sample code, tutorials, and other resources for software developers. These libraries provide basic functions that automate tasks such as cryptographically signing your requests, retrying requests, and handling error responses, making it is easier for you to get started. For more information, see Tools to Build on AWS.

#### References

- Virtual Machines [Check it out](https://www.youtube.com/watch?v=yIVXjl4SwVo)

- VMS and the Cloud [Check it out](https://www.youtube.com/watch?v=l0DfHUWMjsU)

- AWS EC2 [Read the full article here](https://aws.amazon.com/ec2/?ec2-whats-new.sort-by=item.additionalFields.postDateTime&ec2-whats-new.sort-order=desc)

- EC2 For Humans[Check it out](https://www.youtube.com/watch?v=lZMkgOMYYIg)

- Elastic Beanstalk [Check it out](https://www.youtube.com/watch?v=SrwxAScdyT0)

## [Main page](https://amjadmesmar.github.io/reading-notes/)
