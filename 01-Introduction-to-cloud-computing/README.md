# Day 1: Introduction to Cloud Computing

## 1. What is Cloud Computing?

Cloud computing is the delivery of computing resources such as servers, storage, databases, networking, software and other IT services over the internet.

Instead of purchasing and maintaining physical infrastructure, organizations can access computing resources from cloud providers whenever required.

For example, suppose a company wants to host a web application.

**Traditional approach:**
- Purchase physical servers.
- Set up networking and storage.
- Install and configure the required software.
- Maintain hardware and handle upgrades.
- Pay for infrastructure even when it is underutilized.

**Cloud computing approach:**
- Rent computing resources from a cloud provider.
- Configure the required infrastructure.
- Deploy the application.
- Scale resources according to demand.
- Pay based on resource usage and pricing models.

Cloud computing reduces the need to own and maintain physical infrastructure.

## 2. Traditional IT Infrastructure vs Cloud Computing

### Traditional IT Infrastructure (On-Premises)

On-premises infrastructure means an organization owns and manages its computing hardware within its own data center or facility.

The organization is responsible for:
- Purchasing physical servers.
- Managing storage and networking equipment.
- Maintaining hardware and replacing faulty components.
- Managing power, cooling and physical security.
- Planning infrastructure capacity.

### Cloud Computing

In cloud computing, infrastructure is provided by a cloud service provider over the internet.

The organization can:
- Provision resources when needed.
- Increase or decrease computing capacity.
- Access managed services.
- Avoid purchasing physical hardware.
- Pay according to the applicable pricing model.

### Key Differences

| Factor | On-Premises | Cloud Computing |
|---|---|---|
| Infrastructure | Owned by organization | Provided by cloud provider |
| Initial investment | Usually high | Usually lower upfront |
| Maintenance | Managed by organization | Shared according to service model |
| Scalability | Requires hardware planning and procurement | Resources can be provisioned on demand |
| Accessibility | Depends on network configuration | Accessible through supported network connections |
| Cost model | Hardware and operational expenses | Usage-based or other provider pricing models |

## 3. Characteristics of Cloud Computing

Cloud computing offers several important characteristics.

### 3.1 On-Demand Self-Service

Users can provision computing resources whenever they need them without requiring manual intervention from the service provider.

**Example:** Launching an EC2 instance through the AWS Management Console.

### 3.2 Broad Network Access

Cloud services are accessible over networks using standard devices and interfaces.

**Example:** Accessing an AWS-hosted application through a web browser.

### 3.3 Resource Pooling

Cloud providers pool computing resources to serve multiple customers.

Resources are dynamically allocated based on demand.

**Example:** Multiple organizations use resources hosted within the same cloud provider's infrastructure while maintaining logical isolation.

### 3.4 Rapid Elasticity

Computing resources can be provisioned and released quickly according to workload requirements.

**Example:** Increasing application capacity during a sudden increase in traffic and reducing it when demand decreases.

### 3.5 Measured Service

Cloud providers monitor resource usage and provide billing based on applicable usage and pricing models.

**Example:** Paying for EC2 instance usage based on its pricing configuration.

## 4. Cloud Service Models

Cloud computing is commonly categorized into three service models:

- Infrastructure as a Service (IaaS)
- Platform as a Service (PaaS)
- Software as a Service (SaaS)

### 4.1 Infrastructure as a Service (IaaS)

IaaS provides fundamental computing infrastructure such as virtual machines, storage and networking.

The cloud provider manages the underlying physical infrastructure, while customers manage the operating system, applications and other configurations according to the service.

**Example:** Amazon EC2.

**Use case:** A company launches a virtual machine, installs its required software and deploys an application.

### 4.2 Platform as a Service (PaaS)

PaaS provides a managed platform for developing, running and deploying applications.

The cloud provider manages more of the underlying infrastructure and platform components, allowing developers to focus on application development.

**Example:** AWS Elastic Beanstalk.

**Use case:** A developer deploys an application without manually managing the underlying server infrastructure.

### 4.3 Software as a Service (SaaS)

SaaS provides ready-to-use software applications over the internet.

Users access the application without managing the underlying infrastructure or application platform.

**Examples:** Gmail, Microsoft 365.

**Use case:** Using an email application through a browser without installing or managing its servers.

### Comparison of Cloud Service Models

| Responsibility | IaaS | PaaS | SaaS |
|---|---|---|---|
| Physical infrastructure | Provider | Provider | Provider |
| Virtualization | Provider | Provider | Provider |
| Operating system | Customer | Provider | Provider |
| Runtime and middleware | Customer | Provider | Provider |
| Application | Customer | Customer | Provider |
| Data | Customer | Customer | Depends on service and usage |

*Note: This is a simplified comparison. Exact responsibilities vary by service and configuration.*

## 5. Cloud Deployment Models

Cloud deployment models describe how cloud infrastructure is deployed and made available.

### 5.1 Public Cloud

Public cloud infrastructure is provided by a third-party cloud provider and made available to multiple customers.

**Examples:** AWS, Microsoft Azure and Google Cloud.

**Use case:** A startup hosts its web application on AWS without building its own data center.

### 5.2 Private Cloud

Private cloud infrastructure is dedicated to a single organization.

It can be hosted within the organization's own data center or by a third-party provider.

**Use case:** An organization uses dedicated cloud infrastructure to meet specific security or compliance requirements.

### 5.3 Hybrid Cloud

Hybrid cloud combines private cloud infrastructure with public cloud services.

Organizations can distribute workloads between these environments according to their requirements.

**Use case:** A company keeps sensitive workloads in its private environment while hosting its public-facing application on AWS.

### 5.4 Multi-Cloud

Multi-cloud means using services from multiple cloud providers.

**Example:** An organization uses AWS for application hosting and Microsoft Azure for other business services.

**Important:** Hybrid cloud and multi-cloud are different. Hybrid cloud combines private and public environments, while multi-cloud uses multiple cloud providers.

## 6. Important Benefits of Cloud Computing

### 6.1 Scalability

Scalability is the ability to increase or decrease computing capacity to handle changing workloads.

**Example:** Increasing the capacity of an application by adding more EC2 instances.

### 6.2 Elasticity

Elasticity is the ability to automatically or dynamically adjust resources according to changing demand.

**Example:** An Auto Scaling Group adds EC2 instances when application demand increases and removes instances when demand decreases.

**Difference:** Scalability refers to the ability to adjust capacity, whereas elasticity emphasizes how resources adjust as demand changes.

### 6.3 High Availability

High availability means designing systems to remain accessible with minimal downtime, even when individual components fail.

**Example:** Deploying application instances across multiple Availability Zones.

### 6.4 Reliability

Reliability refers to the ability of a system to perform its intended functions consistently.

**Example:** Using backups and redundant infrastructure to recover from failures.

### 6.5 Cost Efficiency

Cloud computing can reduce upfront infrastructure investments and provide flexible pricing options.

Organizations pay according to the resources and pricing models they choose.

However, cloud computing does not automatically guarantee lower costs. Poor resource management can result in unnecessary expenses.

### 6.6 Global Reach

Cloud providers operate infrastructure across multiple geographic regions.

Organizations can deploy applications closer to their users to improve accessibility and reduce latency.

## 7. Introduction to Amazon Web Services (AWS)

Amazon Web Services (AWS) is a cloud computing platform provided by Amazon.

It offers a wide range of services for computing, storage, networking, databases, security, analytics, monitoring and application development.

Instead of purchasing and maintaining physical infrastructure, organizations can use AWS services to build and operate applications.

### Major AWS Service Categories

| Category | Purpose | Example AWS Service |
|---|---|---|
| Compute | Run applications and workloads | Amazon EC2 |
| Storage | Store files and data | Amazon S3 |
| Networking | Create and manage cloud networks | Amazon VPC |
| Database | Store and manage application data | Amazon RDS |
| Identity and Security | Manage access and permissions | AWS IAM |
| Monitoring | Monitor resources and applications | Amazon CloudWatch |
| Infrastructure as Code | Define and provision infrastructure | AWS CloudFormation |

### How AWS Services Work Together

Consider a simple web application:

1. An application runs on an EC2 instance.
2. Application files are stored in an S3 bucket.
3. The application connects to an RDS database.
4. A VPC provides network isolation and connectivity.
5. IAM controls access to AWS resources.
6. CloudWatch collects metrics and logs for monitoring.

This demonstrates how multiple AWS services can work together to support an application.

## 8. Why Learn AWS?

AWS knowledge is useful for understanding and building cloud-based infrastructure.

It helps engineers understand:
- How applications run on cloud infrastructure.
- How cloud networks are designed.
- How applications securely access resources.
- How databases and storage services are managed.
- How infrastructure can be automated.
- How applications are monitored and scaled.

For software engineers and DevOps engineers, understanding AWS helps connect application development with deployment and infrastructure management.

## 9. Day 1 Practical Activity

Today, the goal is to explore AWS rather than create infrastructure resources.

### Tasks

- [ ] Visit the [AWS Official Website](https://aws.amazon.com/).
- [ ] Explore the [AWS Management Console](https://console.aws.amazon.com/).
- [ ] Explore different AWS service categories.
- [ ] Understand the basic difference between Regions and Availability Zones.
- [ ] Explore the AWS Free Tier page.
- [ ] Locate the Billing and Cost Management dashboard.
- [ ] Understand how to check service pricing before creating resources.

**Cost awareness:** AWS services and configurations may incur charges. Always check the pricing details before provisioning resources.

## 10. Interview Preparation and Knowledge Check

Try answering these questions without referring to the notes.

1. What is cloud computing?
2. What are the limitations of traditional on-premises infrastructure?
3. What are the five essential characteristics of cloud computing?
4. Explain the difference between IaaS, PaaS and SaaS with examples.
5. What is the difference between public cloud and private cloud?
6. What is the difference between hybrid cloud and multi-cloud?
7. Explain scalability and elasticity with a real-world example.
8. What is the difference between high availability and reliability?
9. What is AWS, and what are its major service categories?
10. How can EC2, S3, RDS, VPC and IAM work together in an application?

## 11. Official Learning Resources

1. [What is Cloud Computing? – AWS](https://aws.amazon.com/what-is-cloud-computing/)
2. [Types of Cloud Computing – AWS](https://aws.amazon.com/types-of-cloud-computing/)
3. [What is AWS?](https://aws.amazon.com/what-is-aws/)
4. [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
5. [AWS Free Tier](https://aws.amazon.com/free/)

---

