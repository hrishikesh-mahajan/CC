# 3. Deploy Web application on AWS Cloud (or any cloud)

| Name        | Hrishikesh Mahajan   |
| ----------- | -------------------- |
| PRN         | 22110292             |
| Roll Number | 321041               |
| Department  | Computer Engineering |
| Class       | Third Year           |
| Division    | A                    |
| Batch       | A2                   |

- [3. Deploy Web application on AWS Cloud (or any cloud)](#3-deploy-web-application-on-aws-cloud-or-any-cloud)
  - [1. Cloud Computing Definition](#1-cloud-computing-definition)
  - [2. Cloud Service models and Deployment models](#2-cloud-service-models-and-deployment-models)
    - [2.1. Cloud Service Models](#21-cloud-service-models)
      - [2.1.1. Infrastructure as a Service (IaaS)](#211-infrastructure-as-a-service-iaas)
      - [2.1.2. Platform as a Service (PaaS)](#212-platform-as-a-service-paas)
      - [2.1.3. Software as a Service (SaaS)](#213-software-as-a-service-saas)
    - [2.2. Cloud Deployment Models](#22-cloud-deployment-models)
      - [2.2.1. Public Cloud](#221-public-cloud)
      - [2.2.2. Private Cloud](#222-private-cloud)
      - [2.2.3. Hybrid Cloud](#223-hybrid-cloud)
      - [2.2.4. Community Cloud](#224-community-cloud)
      - [2.2.5. Multi-Cloud](#225-multi-cloud)
  - [3. Step-by-step screenshot to upload web application on the cloud](#3-step-by-step-screenshot-to-upload-web-application-on-the-cloud)
    - [3.1. Creating an Instance](#31-creating-an-instance)
    - [3.2. LAMP installation](#32-lamp-installation)
    - [3.3. MySQL](#33-mysql)
    - [3.4. PHP](#34-php)
  - [4. Conclusion](#4-conclusion)

## 1. Cloud Computing Definition

> Cloud computing is the on-demand availability of computer system resources, especially data storage (cloud storage) and computing power, without direct active management by the user. Large clouds often have functions distributed over multiple locations, each of which is a data center. Cloud computing relies on sharing of resources to achieve coherence and typically uses a pay-as-you-go model, which can help in reducing capital expenses but may also lead to unexpected operating expenses for users.
\- Wikipedia

## 2. Cloud Service models and Deployment models

Understanding cloud service and deployment models is essential for making informed decisions when deploying web applications and designing cloud-based architectures. Each model has its advantages, challenges, and use cases, and selecting the appropriate combination can significantly impact the success of a deployment.

### 2.1. Cloud Service Models

IaaS, PaaS, and SaaS are the three most popular types of **cloud service** offerings. They are sometimes referred to as cloud service models or cloud computing service models.

#### 2.1.1. Infrastructure as a Service (IaaS)

- Provides virtualized computing resources over the internet.
- Users can rent virtual machines, storage, and networking infrastructure.
- Offers flexibility and control, allowing users to manage operating systems, applications, and data.
- Examples include Amazon Web Services (AWS) EC2, Microsoft Azure Virtual Machines, and Google Compute Engine.

#### 2.1.2. Platform as a Service (PaaS)

- Provides a platform for building, deploying, and managing applications without the complexity of managing underlying infrastructure.
- Offers development tools, runtime environments, and middleware services.
- Allows developers to focus on application development and deployment.
- Examples include AWS Elastic Beanstalk, Heroku, and Google App Engine.

#### 2.1.3. Software as a Service (SaaS)

- Delivers software applications over the internet on a subscription basis.
- Users access applications through web browsers without needing to install or maintain software locally.
- Offers scalability, accessibility, and automatic updates.
- Examples include Salesforce, Google Workspace, and Microsoft Office 365.

### 2.2. Cloud Deployment Models

The **cloud deployment** model identifies the specific type of cloud environment
based on ownership, scale, and access, as well as the cloud’s nature and purpose.

#### 2.2.1. Public Cloud

- Services are provided over the public internet by cloud service providers.
- Infrastructure is shared among multiple users and organizations.
- Offers scalability, accessibility, and pay-as-you-go pricing.
- Examples include AWS, Azure, Google Cloud Platform (GCP), and IBM Cloud.

#### 2.2.2. Private Cloud

- Infrastructure is dedicated to a single organization and is hosted either on-premises or by a third-party provider.
- Offers greater control, security, and customization compared to the public cloud.
- Suitable for organizations with specific security and compliance requirements.
- Examples include VMware vSphere, OpenStack, and Microsoft Azure Stack.

#### 2.2.3. Hybrid Cloud

- Combines public and private cloud environments, allowing workloads to move between them as needed.
- Offers flexibility, scalability, and the ability to leverage the benefits of both deployment models.
- Suitable for organizations with fluctuating workloads, data sovereignty concerns, or specific regulatory requirements.
- Examples include AWS Outposts, Azure Arc, and Google Anthos.

#### 2.2.4. Community Cloud

- It allows systems and services to be accessible by a group of organizations.
- It is a distributed system that is created by integrating the services of different clouds to address the specific needs of a community, industry, or business.

#### 2.2.5. Multi-Cloud

- We’re talking about employing multiple cloud providers at the same time under this paradigm, as the name implies.
- It’s similar to the hybrid cloud deployment approach, which combines public and private cloud resources.

## 3. Step-by-step screenshot to upload web application on the cloud

### 3.1. Creating an Instance

To deploy your web application on the AWS cloud, follow these steps:

**Step 1:** Login to the [AWS console](https://aws.amazon.com/console/).

**Step 2:** Go to the EC2 service and click on "Launch Instance".

**Step 3:** Configure the instance settings:

- Give your instance a name and tags if required.
- Choose the operating system for your AWS server. For example, select "Ubuntu 22.04.4 LTS".
- Select the CPU type. For example, choose "t3.micro".

  ![AWS Configuration](https://github.com/hrishikesh-mahajan/CC/assets/140654204/46980e03-d974-4730-9dce-db5db38bd254)

**Step 4:** Create a key pair:

- Create a new key pair or use an existing one to securely connect to your instance.

**Step 5:** Configure network security groups and storage:

- Configure the network security groups to allow inbound traffic on the desired ports.
- Configure the storage options for your instance.

  ![AWS Configuration](https://github.com/hrishikesh-mahajan/CC/assets/140654204/fb505a5d-9297-475c-88a6-a4b01e7281ec)

**Step 6:** Launch the instance:

- Review your instance configuration and click on "Launch" to start the instance.
- Once launched, you can see the instance running in the instances tab.

  ![Instances](https://github.com/hrishikesh-mahajan/CC/assets/140654204/f79b177e-e677-4f10-b13e-749fd0047074)

**Step 7:** SSH into your AWS instance:

- Change the permissions of your key.pem file to 400 to ensure only the current user can access it in read-only mode.
- Use the following command to connect to your server via SSH, replacing the `key.pem` with the path to your key file and "aws_server_dns.compute.amazonaws.com" with the DNS of your AWS server:

    ```bash
    chmod 400 key.pem
    ssh -i "key.pem" ubuntu@aws_server_dns.compute.amazonaws.com
    ```

- This will take you to the AWS server's shell prompt.

  ![Connected to Server via SSH](https://github.com/hrishikesh-mahajan/CC/assets/140654204/4f9482ee-6886-4c66-b59a-6c368a3eb147)

**Step 8:** Edit network security group permissions:

- Navigate to the EC2 console and locate the security group associated with your instance.
- Edit the network security group associated with your instance to allow inbound traffic on the HTTP protocol's port (usually port 80).

  ![Add Rule to Security Group](https://github.com/hrishikesh-mahajan/CC/assets/140654204/fdbb7700-2628-4385-bd6c-6d5e45e567f5)

You have now successfully created an instance on the AWS cloud and connected to it via SSH. Next, you can proceed with the remaining steps to deploy your web application.

### 3.2. LAMP installation

LAMP stands for

1. L - Linux for Operating System
2. A - Apache HTTP Server
3. M - MySQL for Relational DataBase Management System
4. P - PHP, Perl, or Python as the programming language

We installed L in our Linux server, let's install the other three on this server too.

**Step 1:** Install the rest of the packages for the LAMP stack.

```bash
sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php php-mysql
```

**Step 2:** Change permissions of /var/www/html/ folder

```bash
sudo chmod 777 -R /var/www/html
```

### 3.3. MySQL

**Step 3:** Create a user in MySQL and give that user all database privileges

![MySQL user creation](https://github.com/hrishikesh-mahajan/CC/assets/140654204/5d92c572-41cf-4cdc-b5d7-a691c9c34228)

**Step 4:** Use the username and password of the user to open MySQL shell. Create a database and create a table in that database.

![Creating MySQL table](https://github.com/hrishikesh-mahajan/CC/assets/140654204/60e85cc0-0787-4fd1-9b1f-c49546e1bbdd)

### 3.4. PHP

Now we need to copy our files from our local machine to the server's /var/www/html directory. For this, we use the `scp` command. It allows users to share files via ssh protocol.

**Step 5:** Secure copy our files (index.php) from our local machine to the server's /var/www/html directory.

```bash
scp -i key.pem local_file.php ubuntu@aws_server_dns.com:/var/www/html/
```

![SCP command](https://github.com/hrishikesh-mahajan/CC/assets/140654204/e3f031cf-c2eb-40bc-9591-f2bd38e50123)

## 4. Conclusion

In conclusion, deploying a web application on the AWS cloud (or any cloud) involves several steps and considerations. By following the step-by-step process outlined in this guide, we have successfully deployed our web application on the AWS cloud.

Key takeaways from this assignment include:

1. Understanding cloud service models (IaaS, PaaS, SaaS) and deployment models (public, private, hybrid, community, multi-cloud) is crucial for making informed decisions when deploying web applications.

2. Cloud computing offers on-demand availability of computer system resources, such as data storage and computing power, without direct active management by the user.

3. AWS is a popular cloud service provider that offers a wide range of services for deploying and managing web applications.

4. The LAMP stack (Linux, Apache, MySQL, PHP) is a common technology stack used for web application development and deployment.

5. Proper configuration of network security groups, storage options, and key pair management is essential for securing and accessing cloud instances.

6. The use of SSH (Secure Shell) allows for secure remote access to cloud instances.

7. The SCP (Secure Copy) command can be used to transfer files between local machines and cloud instances.

By following best practices and leveraging the capabilities of cloud computing, organizations can benefit from scalability, accessibility, and cost-efficiency in deploying web applications.
