# Day 2: AWS Global Infrastructure

## 1. Introduction

AWS operates a global infrastructure that allows organizations to deploy applications and services across different geographical locations.

This infrastructure is designed to support:
- High availability
- Fault tolerance
- Low network latency
- Scalability
- Disaster recovery
- Global application delivery

To understand how AWS organizes its infrastructure, we need to understand three important components:

1. AWS Regions
2. Availability Zones (AZs)
3. Edge Locations

## 2. AWS Regions

### What is an AWS Region?

An AWS Region is a separate geographical area where AWS operates its cloud infrastructure.

Each Region contains multiple isolated Availability Zones.

When deploying an AWS resource, we generally select the Region where that resource should be created.

### Why do AWS Regions matter?

Choosing the right Region is important because it affects:

- **Latency:** Deploying resources closer to users can reduce network latency.
- **Compliance:** Some applications must store data within specific geographical boundaries.
- **Service Availability:** Not every AWS service or feature is available in every Region.
- **Cost:** Pricing for AWS services can vary between Regions.
- **Disaster Recovery:** Applications can use multiple Regions as part of a disaster recovery strategy.

### Examples of AWS Regions

| Region Name | Region Code |
|---|---|
| US East (N. Virginia) | us-east-1 |
| US West (Oregon) | us-west-2 |
| Asia Pacific (Mumbai) | ap-south-1 |
| Asia Pacific (Hyderabad) | ap-south-2 |
| Asia Pacific (Singapore) | ap-southeast-1 |
| Europe (Ireland) | eu-west-1 |

### Example

Suppose a company has most of its customers in India.

It may choose the Mumbai Region (`ap-south-1`) to host its application because it can provide lower network latency for its Indian users compared with hosting everything in a distant Region.

However, the final decision should also consider service availability, compliance, cost and architecture requirements.

### Important Points

- Each Region is designed to be independent of other Regions.
- Resources created in one Region are not automatically replicated to another Region.
- Some AWS services are available only in selected Regions.
- Some Regions require explicit activation in an AWS account before they can be used.

## 3. Availability Zones (AZs)

### What is an Availability Zone?

An Availability Zone is an isolated location within an AWS Region.

An AZ consists of one or more discrete data centers with independent power, cooling and networking infrastructure.

Multiple AZs within a Region are connected through highly redundant, low-latency networking.

### Why do we need Availability Zones?

Imagine an application running on a single EC2 instance in one Availability Zone.

If that Availability Zone experiences a failure, the application may become unavailable.

To reduce this risk, organizations can distribute application resources across multiple Availability Zones.

### Example

Consider an application deployed in the Mumbai Region.

```text
             AWS Region
           ap-south-1
                 |
       +---------+---------+
       |                   |
   AZ - A                AZ - B
       |                   |
   EC2 Instance        EC2 Instance
       |                   |
       +---------+---------+
                 |
           Application
```

If one Availability Zone experiences a failure, the application may continue operating through resources in another Availability Zone, provided the architecture has appropriate redundancy and failover mechanisms.

### Availability Zone Naming

Availability Zones have identifiers associated with their Region.

For example:

- ap-south-1a
- ap-south-1b
- ap-south-1c

**Important:** The AZ name assigned to an account may map to a different physical AZ than the same letter used in another AWS account. AZ IDs provide a consistent way to identify physical Availability Zones across accounts.

### Key Benefits

- Fault isolation
- High availability
- Better application resilience
- Reduced impact of individual infrastructure failures
- Support for multi-AZ architectures

## 4. Edge Locations

### What is an Edge Location?

An Edge Location is a location in the AWS edge network used to deliver content and services closer to end users.

Edge Locations are primarily used by services such as Amazon CloudFront.

They help reduce latency by allowing users to retrieve cached content from a nearby location instead of repeatedly requesting it from the origin server.

### How do Edge Locations work?

Consider a website hosted on an EC2 instance in the Mumbai Region.

A user located in another country requests an image from the website.

Without a caching layer, the request may need to travel to the origin server.

With Amazon CloudFront:

1. The user requests content.
2. CloudFront directs the request to an appropriate edge location.
3. If the content is cached, CloudFront serves it from the edge location.
4. If the content is not cached, CloudFront retrieves it from the origin.
5. The content can then be cached according to the configured caching policy.

### Benefits

- Reduced content delivery latency
- Faster loading of cached content
- Reduced repeated requests to the origin
- Improved user experience for globally distributed users

**Example:** A company uses CloudFront to distribute images, videos, CSS and JavaScript files to users across different countries.

## 5. Regions vs Availability Zones vs Edge Locations

These three components serve different purposes.

| Feature | Region | Availability Zone | Edge Location |
|---|---|---|---|
| Meaning | Geographical AWS area | Isolated location within a Region | Location in AWS's edge network |
| Main purpose | Deploy regional infrastructure | Improve availability and fault isolation | Deliver content closer to users |
| Relationship | Contains multiple AZs | Belongs to a Region | Part of the global edge network |
| Example | ap-south-1 | ap-south-1a | CloudFront point of presence |

### Easy way to remember

- **Region:** Where your AWS infrastructure is deployed.
- **Availability Zone:** Where you distribute infrastructure for resilience within a Region.
- **Edge Location:** Where content can be delivered closer to users.

## 6. Regional Services vs Global Services

AWS services can have different scopes.

### Regional Services

Regional services are operated within a particular AWS Region.

Resources created in one Region are generally managed within that Region.

Examples:
- Amazon EC2
- Amazon RDS
- Amazon VPC
- Amazon DynamoDB

### Global Services

Some AWS services have a global scope rather than being limited to one individual Region.

Examples:
- AWS IAM
- Amazon Route 53
- Amazon CloudFront

**Important:** Global scope does not mean every resource or configuration is automatically replicated everywhere. Each service has its own resource and configuration behavior.

### Why does this distinction matter?

When working with AWS resources, understanding service scope helps avoid confusion when switching Regions.

For example, an EC2 instance launched in Mumbai will not automatically appear when viewing EC2 resources in another Region.

However, IAM users and policies are managed through the global IAM service.

## 7. How AWS Global Infrastructure Supports Application Architecture

Consider a company hosting an application for users across multiple countries.

A possible architecture could look like this:

```text
                 Global Users
                      |
                      v
               CloudFront
              (Edge Network)
                      |
                      v
             AWS Region
              ap-south-1
                      |
             +--------+--------+
             |                 |
          AZ - A             AZ - B
             |                 |
         EC2 Instance      EC2 Instance
             |                 |
             +--------+--------+
                      |
                Application
```

In this architecture:

- CloudFront helps deliver cached content closer to users.
- The Mumbai Region hosts the application's infrastructure.
- Multiple Availability Zones provide infrastructure redundancy.
- Application resources can be configured to handle failures and distribute traffic.

This design helps improve availability and user experience.

## 8. Practical Activity

Today, we'll explore AWS infrastructure without creating any billable resources.

### Task 1: Explore AWS Global Infrastructure

1. Visit the AWS Global Infrastructure website.
2. Explore the interactive infrastructure map.
3. Identify Regions across different geographical areas.
4. Find the Mumbai and Hyderabad Regions.
5. Observe the Availability Zones and Edge Locations.

Resource:

https://aws.amazon.com/about-aws/global-infrastructure/

### Task 2: Explore Regions in AWS Console

1. Sign in to the AWS Management Console.
2. Locate the Region selector in the navigation bar.
3. Explore available Regions.
4. Identify:
   - Asia Pacific (Mumbai)
   - Asia Pacific (Hyderabad)
   - US East (N. Virginia)
5. Observe how the selected Region changes when navigating between services.

### Task 3: Explore Availability Zones

1. Open the Amazon EC2 console.
2. Select the Mumbai Region (`ap-south-1`).
3. Navigate to the Availability Zones section.
4. Observe the available AZ names and their states.
5. Repeat for another Region.

No EC2 instance needs to be launched for this exercise.

### Task 4: Understand CloudFront

1. Open the Amazon CloudFront service page.
2. Understand what a Content Delivery Network (CDN) does.
3. Explore how CloudFront uses Edge Locations.
4. Understand the difference between an origin server and an edge location.

## 9. Optional: Explore Availability Zones Using AWS CLI

If AWS CLI is configured and you have the required permissions, run:

```bash
aws ec2 describe-availability-zones \
  --region ap-south-1
```

This command retrieves information about Availability Zones available to your account in the Mumbai Region.

To display only their names and states:

```bash
aws ec2 describe-availability-zones \
  --region ap-south-1 \
  --query "AvailabilityZones[*].[ZoneName,State]" \
  --output table
```

Example output format:

```text
--------------------------------
| DescribeAvailabilityZones    |
+----------------+-------------+
| ap-south-1a    | available   |
| ap-south-1b    | available   |
| ap-south-1c    | available   |
+----------------+-------------+
```

The actual results depend on account access and the current Region configuration.

## 10. Interview Questions

Try answering these questions without referring to the notes.

1. What is an AWS Region?
2. What is an Availability Zone?
3. What is the difference between a Region and an Availability Zone?
4. Why does AWS maintain multiple Availability Zones within a Region?
5. What happens if an application runs in only one Availability Zone and that AZ becomes unavailable?
6. What is an Edge Location?
7. How does Amazon CloudFront use Edge Locations?
8. What is the difference between a Region and an Edge Location?
9. What factors should be considered when selecting an AWS Region?
10. What is the difference between regional and global AWS services?
11. Are resources automatically replicated across AWS Regions?
12. How can deploying an application across multiple AZs improve availability?

## 11. Official Learning Resources

1. AWS Global Infrastructure:
   https://aws.amazon.com/about-aws/global-infrastructure/

2. AWS Regions and Availability Zones:
   https://docs.aws.amazon.com/global-infrastructure/latest/regions/aws-regions-availability-zones.html

3. Amazon EC2 Regions and Zones:
   https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html

4. Amazon CloudFront:
   https://aws.amazon.com/cloudfront/

---

**Day 2 Complete: AWS Global Infrastructure**

Next: **Day 3 – AWS Shared Responsibility Model**

We'll understand which security responsibilities belong to AWS and which responsibilities belong to the customer.