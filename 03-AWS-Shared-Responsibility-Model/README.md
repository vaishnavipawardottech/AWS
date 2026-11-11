
# Day 03: AWS Shared Responsibility Model

## 1. Introduction

When using AWS, security is not handled entirely by AWS or entirely by the customer.

AWS and its customers share security and compliance responsibilities. This division is known as the **AWS Shared Responsibility Model**.

It helps us understand:
- What AWS is responsible for securing.
- What customers must secure themselves.
- How responsibilities change depending on the AWS services being used.

The model is commonly explained using two concepts:

1. Security OF the Cloud
2. Security IN the Cloud

---

## 2. Security OF the Cloud

**AWS is responsible for security OF the Cloud.**

This means AWS protects the underlying infrastructure that runs its cloud services.

AWS responsibilities include:

- Physical security of data centers.
- Physical servers and hardware.
- Storage infrastructure.
- Underlying networking infrastructure.
- Virtualization infrastructure.
- Global infrastructure, including Regions and Availability Zones.

### Example

Suppose an organization launches an EC2 instance.

AWS is responsible for:
- Maintaining the physical server.
- Securing the data center.
- Managing the underlying hardware.
- Maintaining the underlying virtualization infrastructure.

Customers do not need to manage the physical AWS data center or replace failed physical servers.

---

## 3. Security IN the Cloud

**Customers are responsible for security IN the Cloud.**

This means customers must secure the AWS resources, applications, data, and configurations they use.

Customer responsibilities generally include:

- Managing customer data.
- Configuring IAM users, roles, and permissions.
- Securing applications.
- Configuring network access.
- Managing encryption settings.
- Configuring AWS services securely.
- Patching and maintaining guest operating systems where applicable.

### Example

Suppose an organization launches an EC2 instance and installs an application on it.

The customer is responsible for:
- Installing and updating the operating system.
- Applying security patches to the guest OS.
- Securing the application.
- Configuring security groups.
- Managing user access and permissions.

AWS provides the infrastructure, but the customer must securely configure and manage the workload.

---

## 4. AWS vs Customer Responsibilities

| Responsibility | AWS | Customer |
|---|---|---|
| Physical data center security | Yes | No |
| Physical hardware | Yes | No |
| Underlying networking | Yes | No |
| Virtualization infrastructure | Yes | No |
| Customer data | No | Yes |
| IAM permissions | No | Yes |
| Application security | No | Yes |
| EC2 guest OS patching | No | Yes |
| Security group configuration | No | Yes |

**Note:** This is a simplified overview. Exact responsibilities depend on the service and its configuration.

---

## 5. How Responsibilities Change With AWS Services

The responsibility boundary is not identical for every AWS service.

Let's understand this using three examples.

### A. Amazon EC2

EC2 is an Infrastructure as a Service (IaaS) offering.

AWS manages:
- Physical infrastructure.
- Physical servers.
- Networking infrastructure.
- Underlying virtualization.

Customer manages:
- Guest operating system.
- OS updates and security patches.
- Installed applications.
- Security group configuration.
- Data and access permissions.

**Key point:** EC2 gives customers more control over the operating system and therefore more responsibility for managing it.

### B. Amazon S3

S3 is a managed object storage service.

AWS manages:
- Physical infrastructure.
- Storage infrastructure.
- Underlying operating systems and platform.

Customer manages:
- Data stored in buckets.
- Bucket policies and access permissions.
- IAM permissions.
- Encryption choices and data protection settings.
- Data classification.

**Key point:** Customers do not manage the underlying operating system or storage hardware, but they must configure access to their data securely.

### C. Amazon RDS

RDS is a managed relational database service.

AWS manages:
- Physical infrastructure.
- Underlying operating system and database service infrastructure.
- Much of the database maintenance and infrastructure management.

Customer manages:
- Database configuration and usage.
- Database users and permissions.
- Data stored in the database.
- Network access configuration.
- Encryption choices and application-level security.

Some maintenance and patching responsibilities depend on the RDS configuration and maintenance options selected by the customer.

**Key point:** RDS reduces infrastructure administration, but customers are still responsible for protecting their data and configuring the database securely.

---

## 6. Shared Controls

Some security responsibilities involve both AWS and the customer.

These are known as shared controls.

### A. Patch Management

- AWS patches and maintains its underlying infrastructure.
- Customers patch their guest operating systems and applications where they manage them.

### B. Configuration Management

- AWS maintains the configuration of its infrastructure.
- Customers configure their own AWS resources, operating systems, databases, and applications.

### C. Awareness and Training

- AWS trains its employees on their responsibilities.
- Customers train their employees to follow their organization's security practices.

---

## 7. Practical Scenarios

Let's understand the model through real-world situations.

| Scenario | Responsible Party |
|---|---|
| Physical data center security | AWS |
| Replacing a failed physical server | AWS |
| Updating the Linux OS on an EC2 instance | Customer |
| Configuring EC2 security groups | Customer |
| Managing IAM permissions | Customer |
| Securing the underlying S3 infrastructure | AWS |
| Configuring S3 bucket access policies | Customer |
| Protecting data stored in S3 | Customer |
| Maintaining the underlying RDS infrastructure | AWS |
| Managing database users and permissions | Customer |

### Important Scenario

Imagine an organization accidentally configures an S3 bucket to allow public access.

Who is responsible?

**Answer: The customer.**

AWS provides the security controls, but customers must configure them correctly.

This is why understanding the Shared Responsibility Model is important when designing secure cloud applications.

---

## 8. Practical Exploration

For this topic, we can understand the responsibility boundaries without creating any AWS resources.

### Activity 1: Explore the AWS documentation

1. Open the official AWS Shared Responsibility Model documentation.
2. Review the AWS responsibilities.
3. Review the customer responsibilities.
4. Compare the EC2 and S3 examples.

### Activity 2: Analyze a scenario

Consider an application running on an EC2 instance.

Identify who is responsible for:

- Physical server security.
- Linux OS updates.
- Application security.
- Security group rules.
- IAM permissions.
- Customer data protection.

Try answering before checking the previous sections.

### Activity 3: Compare AWS services

Compare EC2, S3, and RDS.

Observe how AWS manages more of the underlying infrastructure when we use managed services, while customers retain responsibility for their data, access, and configurations.

---

## 9. Common Mistakes to Avoid

1. Assuming AWS handles all security because the application is hosted on AWS.
2. Assuming AWS automatically secures customer data and access permissions.
3. Forgetting to patch the guest OS on EC2 instances.
4. Configuring S3 bucket permissions incorrectly.
5. Assuming that using managed services removes all customer security responsibilities.

**Remember:** Using AWS does not automatically make an application secure. Customers must configure and operate their workloads securely.

---

## 10. Interview Questions

### Q1. What is the AWS Shared Responsibility Model?

It is a security model that defines how security and compliance responsibilities are divided between AWS and its customers.

### Q2. What is the difference between Security OF the Cloud and Security IN the Cloud?

- Security OF the Cloud refers to AWS securing the underlying infrastructure.
- Security IN the Cloud refers to customers securing their data, applications, identities, and configurations.

### Q3. Who is responsible for patching the operating system on an EC2 instance?

The customer is responsible for patching and maintaining the guest operating system.

### Q4. Who is responsible for physical data center security?

AWS is responsible for physical data center security.

### Q5. If an S3 bucket is accidentally made public, who is responsible?

The customer is responsible for configuring bucket access permissions securely.

### Q6. Does AWS manage everything when we use Amazon RDS?

No. AWS manages much of the underlying infrastructure, but customers remain responsible for their data, database access, configurations, and other workload-specific security tasks.

### Q7. Does using managed AWS services eliminate customer security responsibilities?

No. Customers remain responsible for areas such as data protection, identity management, permissions, and service configuration.

---

## 11. Key Takeaways

- AWS and customers share security responsibilities.
- Security OF the Cloud is AWS's responsibility.
- Security IN the Cloud is the customer's responsibility.
- Customer responsibilities vary depending on the AWS service.
- Managed services reduce infrastructure management but do not eliminate customer security responsibilities.
- Secure configuration and access management are essential.

---

## 12. References

1. [AWS Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)
2. [AWS Well-Architected Framework - Shared Responsibility](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/shared-responsibility.html)
3. [AWS Security Best Practices](https://docs.aws.amazon.com/security/)

---

**Next: Day 04 - AWS Account Setup, Management Console and AWS CLI**
