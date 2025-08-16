# DevOps Interview Preparation Guide

## AWS Questions

### Q: What is AMI?
**A:** AMI is an Amazon Machine Image that mainly contains operating system and configuration files which is mainly used to deploy multiple virtual machines, regardless of any AWS region.

### Q: What is EC2 instance, and what are the types?
**A:** EC2 is a virtual machine that represents your physical machine for you to deploy an application. Types include:
- General purpose
- Compute optimized
- Memory optimized
- Accelerated compute instance
- Storage optimization instance

### Q: What are the different types of storage?
**A:** 
**Block Storage:**
- Elastic Block Storage (EBS)
- Instance storage

**File Storage:**
- Elastic File System (EFS) - mainly used for Linux operating system
- AWS FSx - mainly useful for Windows operating system

**Object Storage:**
- S3
- Glacier

**Challenges with Instance Storage:**
- It's temporary storage; data will be lost if you stop and start the instance
- Fixed size and type
- Only available with selected instance types
- Cannot detach and attach to other virtual machines

**Advantages of EBS:**
- Permanent or persistent storage
- Can be increased to 16 TB
- Available in different types (SSD and HDD)
- Available to all servers
- Can be detached and attached to others

### Q: What are the different types of load balancers?
**A:** 
- **Application Load Balancer (ALB):** Works on HTTP and HTTPS protocol, and also TCP protocol, but doesn't support UDP
- **Network Load Balancer (NLB):** Works on TCP and UDP protocol. UDP is very efficient for streaming applications or online meetings

**Major disadvantage with NLB:** HTTP to HTTPS redirection is not possible and Web Application Firewall (WAF) is not supported.

### Q: What are the different types of auto scaling groups?
**A:** 
- **Vertical Scaling:** Increasing resources of existing servers (e.g., T2.micro to T2.large). Needs to stop and start. Best suited for DB servers, file servers, app servers
- **Horizontal Scaling:** Automatically creates servers when load is increasing

### Q: What are the different types of Route 53 routing policies?
**A:** 
- **Latency:** Takes the nearest data center to avoid latency
- **Failover:** If one server goes down, the secondary server will take over
- **Weighted:** Load balancing based on weights (e.g., handling large scale users in India)
- **Geolocation:** Strictly follows location-based rules (Indian users go to India, US users go to US)
- **Multivalue:** Can give multiple server IPs; specifically takes any one of the IPs

### Q: What is CDN?
**A:** CDN (Content Delivery Network) delivers a large portion of internet content. It stores cached versions of content in multiple geographical locations (called points of presence) to reduce latency for users accessing content from different regions.

### Q: How do you clear cache memory in CloudFront?
**A:** Go to CloudFront → Distributions → Invalidations → Enter `/*` and then clear.

### Q: What are the different types of databases?
**A:** 
**Structured Database (RDBMS):**
- MySQL, Oracle, MSSQL, PostgreSQL, MariaDB, Aurora

**NoSQL Database:**
- AWS DynamoDB, AWS DocumentDB

**In-Memory Database:**
- ElastiCache, AWS Redshift

### Q: What is Systems Manager?
**A:** Systems Manager is mainly used to centrally manage global configuration settings by using Parameter Store.

### Q: What is the difference between AWS CloudTrail and AWS Config?
**A:** 
- **CloudTrail:** Monitors all API activities such as logging in from console, CLI, or third-party applications like Packer and Terraform. All events are recorded
- **Config:** Tracks detailed changes happening on your resources. Shows consolidated overview of changes performed on resources

### Q: What is Elastic Beanstalk?
**A:** Elastic Beanstalk is a service for deploying and scaling web applications and services. Upload your code and Elastic Beanstalk automatically handles deployment, load balancing, and health monitoring.

### Q: What is Blue-Green Deployment?
**A:** A deployment strategy where you have an application currently running. All traffic hits the load balancer and is directed to the existing application. After testing the new version, traffic is routed to the newly deployed application.

---

## DevOps Questions

### Q: What types of branching strategies do you follow?
**A:** We follow feature branching strategies with main and integration as long-lived branches:
- **Main:** Always points to production commits
- **Integration:** Contains total code
- Process: Create branch from integration → Develop → Test pipeline → Raise PR → Merge to integration → Test with QA/pre-prod/production → Tag version (e.g., v1.0)

---

## Git Questions

### Q: What is Git and why is it used?
**A:** Git is a tool for tracking changes in code. It helps developers work together and keep track of every change.

### Q: Explain the difference between Git and GitHub
**A:** Git is the tool that tracks changes in code. GitHub is a website where you can store and share your code using Git.

### Q: What is a repository in Git?
**A:** A repository is like a folder for your project. It contains all your project files and the history of changes made to those files.

### Q: What does the `git init` command do?
**A:** `git init` creates a new Git repository. It sets up all the necessary files for Git to start tracking changes.

### Q: What is a commit in Git?
**A:** A commit is a snapshot of your project. It records what the project looks like at a certain point in time.

### Q: How do you check the status of your repository?
**A:** Use the `git status` command. It shows you the changes that have been made and not yet committed.

### Q: What does `git add` do?
**A:** `git add` stages changes. It tells Git to include the changes in the next commit.

### Q: What is the purpose of `git clone`?
**A:** `git clone` copies a repository from a remote server to your local machine.

### Q: What does `git pull` do?
**A:** `git pull` updates your local repository with changes from a remote repository.

### Q: What is a branch in Git?
**A:** A branch is like a separate line of development. It lets you work on new features without changing the main codebase.

---

## Terraform Questions

### Q: What is Terraform and what are the advantages?
**A:** Terraform is an infrastructure automation tool mainly used to deploy/provision cloud infrastructure. Main advantages include:
- Automation
- Dry run checks
- Validation of code
- State file management for infrastructure tracking

### Q: How to change a configuration file which is already created using Terraform?
**A:** Use `terraform import` to import existing resources into Terraform state.

### Q: What is the use case of Terraform state file and where do you save it?
**A:** Terraform maintains a state file that maps the current state of your infrastructure with the configuration file. State files can be stored:
- Locally on machine (for backups)
- Remote location (S3 with DynamoDB table for locking)

### Q: What if you have lost your Terraform state file?
**A:** State file contains critical information. If lost, Terraform doesn't know about existing environment, leading to potential overlapping and cross-pollution. Best option is to use `terraform import` to rebuild the state.

### Q: What are the main features in Terraform?
**A:** 
- Can manage infrastructure across multiple cloud platforms
- Uses HashiCorp Configuration Language (HCL) which is human-readable

### Q: What are the different types of Terraform modules?
**A:** 
- **Root Modules:** Contains all resources defined in TF files in the main working directory (main.tf, variables.tf, etc.)
- **Published Modules:** Reusable modules published to registries

### Q: What is remote backend?
**A:** Remote backend is a place where we store all TF state files which can be shared with other developers of infrastructure.

### Q: What are Terraform workspaces?
**A:** Terraform workspaces allow us to manage separate state files for each workspace.

---

## Jenkins Questions

### Q: How do you store Jenkins secrets?
**A:** Jenkins credentials can be stored using:
- Jenkins built-in credential store
- Third-party tools: AWS Secrets Manager, Google Cloud Key Management, Azure Key Vault, HashiCorp Vault

### Q: What are shared libraries in Jenkins?
**A:** Shared libraries in Jenkins refer to a collection of reusable resources that can be shared across multiple Jenkins jobs.

### Q: Can you use Jenkins to build applications with multiple programming languages using different agents in different stages?
**A:** Yes, Jenkins can build applications with multiple programming languages by using different build agents in different stages of the build process.

### Q: What is the difference between Freestyle project and Pipeline project?
**A:** 
- **Freestyle Project:** Traditional approach using manual configuration through web interface
- **Pipeline Project:** Code-based approach using Jenkinsfile integrated with Git to automate software delivery process

### Q: What are Jenkins plugins?
**A:** Jenkins plugins are additional software components that extend Jenkins functionality. Examples include:
- Git plugin
- Docker plugin
- Pipeline plugin
- AWS plugin
- SonarQube plugin
- Maven plugin

### Q: What is a build node?
**A:** Jenkins build node is a machine that Jenkins uses to execute build jobs. It can be physical/virtual machine, on-premises or in cloud.

### Q: What are the different types of Jenkins jobs?
**A:** 
- Freestyle
- Pipeline
- Maven
- Multi-branch pipeline
- GitHub organization
- Parameterized job

### Q: How can you test and debug Jenkins pipeline?
**A:** 
- Use Jenkins Blue Ocean for visual pipeline validation
- Validate Jenkinsfile syntax and structure
- Break down pipeline stages and test independently
- Review logs and errors to identify issues

### Q: How can you manage build artifacts in Jenkins?
**A:** 
- Use "Archive artifacts" post-build action
- Use Copy Artifact plugin to copy build artifacts between jobs
- Configure artifact retention policies

---

## Ansible Questions

### Q: What is Ansible and what is it used for?
**A:** Ansible is an open-source automation tool used for configuration management, application deployment, task automation, and orchestration. It simplifies IT operations by automating repetitive tasks.

### Q: Explain the difference between Ansible and other configuration management tools like Chef or Puppet
**A:** Ansible uses an agentless architecture, relying on SSH and Python to execute tasks on remote servers. Chef and Puppet use an agent-based approach where agents need to be installed on managed nodes.

### Q: What are Ansible playbooks?
**A:** Ansible playbooks are YAML files that define a set of tasks to be executed. They automate configurations, deployments, and orchestration of tasks across managed nodes.

### Q: How do you run an Ansible playbook?
**A:** Use the `ansible-playbook` command followed by the playbook filename. Example: `ansible-playbook site.yml`

### Q: What is an Ansible role?
**A:** An Ansible role is a way to organize playbooks and other files in a reusable structure. It encapsulates tasks, variables, templates, and files into a directory structure.

### Q: How do you install Ansible on your local machine?
**A:** Ansible can be installed using package managers:
- Ubuntu: `sudo apt-get install ansible`
- CentOS/RHEL: `sudo yum install ansible`
- macOS: `brew install ansible`

### Q: What is an inventory file in Ansible?
**A:** An inventory file lists the IP addresses or hostnames of managed nodes (servers) that Ansible will work with. It defines the targets for Ansible playbooks and ad-hoc commands.

### Q: Explain the difference between Ansible ad-hoc commands and playbooks
**A:** 
- **Ad-hoc commands:** Run from command-line for quick tasks on remote nodes
- **Playbooks:** YAML files providing structured and reusable way to automate tasks

### Q: How does Ansible handle idempotency?
**A:** Ansible ensures idempotency by only applying changes when necessary. If a task has already been completed successfully, Ansible will not reapply it unless changes are made.

### Q: What is the Ansible Galaxy?
**A:** Ansible Galaxy is a website and command-line tool for finding, reusing, and sharing Ansible roles. It provides a repository of community-contributed roles.

---

## Docker Questions

### Q: What is Docker and why is it used?
**A:** Docker is a platform that allows you to package, distribute, and run applications in containers. It's used for creating consistent environments across development, testing, and production.

### Q: What is a container?
**A:** A container is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including code, runtime, libraries, and dependencies.

### Q: Explain the difference between a Docker image and a Docker container
**A:** 
- **Docker Image:** Read-only template that contains the application and its dependencies
- **Docker Container:** Runnable instance of a Docker image

### Q: How do you create a Docker container?
**A:** Use the `docker run` command with an image. Example: `docker run -d -p 8080:80 nginx`

### Q: What is Docker Hub?
**A:** Docker Hub is a cloud-based registry service that allows you to store and share Docker images publicly or privately.

### Q: How do you list running Docker containers?
**A:** 
- `docker ps` - lists running containers
- `docker ps -a` - lists all containers (including stopped ones)

### Q: What is the purpose of a Dockerfile?
**A:** A Dockerfile is a text document containing commands to assemble a Docker image automatically.

### Q: How do you stop and remove a Docker container?
**A:** 
- Stop: `docker stop <container_id_or_name>`
- Remove: `docker rm <container_id_or_name>`

### Q: Explain the concept of Docker volumes
**A:** Docker volumes provide a way to persist data generated by and used by Docker containers. They are stored outside the Union File System and can be shared among containers.

### Q: What are Docker networks and why are they used?
**A:** Docker networks allow containers to communicate with each other and with other non-containerized devices. They facilitate communication and isolation between containers.

---

## Kubernetes Questions

### Q: What is Kubernetes and why is it used?
**A:** Kubernetes is an open-source platform for automating deployment, scaling, and management of containerized applications. It helps manage containerized applications across multiple hosts.

### Q: What is a container?
**A:** A container is a lightweight, executable package of software that includes everything needed to run an application, including code, runtime, libraries, and dependencies.

### Q: Explain the difference between Kubernetes and Docker
**A:** 
- **Docker:** Platform for building and running containers
- **Kubernetes:** Container orchestration platform that manages deployment and scaling of containers

### Q: What are Pods in Kubernetes?
**A:** Pods are the smallest Kubernetes objects. They represent a single instance of a running process in the cluster, consisting of one or more containers that share storage and network resources.

### Q: How do you create a Pod in Kubernetes?
**A:** Create a Pod manifest file in YAML format and apply it using `kubectl apply -f pod.yaml`.

### Q: What is a Deployment in Kubernetes?
**A:** A Deployment manages a set of identical Pods, ensuring the desired number of Pods is running and handling updates and rollbacks.

### Q: How do you create a Deployment in Kubernetes?
**A:** Create a Deployment manifest file in YAML format and apply it using `kubectl apply -f deployment.yaml`.

### Q: What is a Service in Kubernetes?
**A:** A Service is an abstraction that defines a logical set of Pods and a policy to access them. It provides a stable endpoint for connecting to Pods.

### Q: How do you expose a Deployment as a Service in Kubernetes?
**A:** Create a Service manifest file specifying the service type (ClusterIP, NodePort, LoadBalancer) and apply it using `kubectl apply -f service.yaml`.

### Q: What is the role of kubectl in Kubernetes?
**A:** kubectl is the command-line tool used to interact with Kubernetes clusters. It allows you to deploy and manage applications, inspect cluster resources, and view logs.

### Q: What is a Namespace in Kubernetes?
**A:** A Namespace provides a way to divide cluster resources among multiple users or projects. It helps organize and isolate resources within a cluster.

### Q: How do you scale a Deployment in Kubernetes?
**A:** Update the replicas field in the Deployment manifest or use: `kubectl scale deployment/myapp-deployment --replicas=3`

### Q: What is a ConfigMap in Kubernetes?
**A:** A ConfigMap is an API object used to store non-sensitive configuration data in key-value pairs. It decouples configuration from Pods and containers.

### Q: How do you manage application logs in Kubernetes?
**A:** Use `kubectl logs <pod_name>` to access application logs. For specific containers: `kubectl logs <pod_name> -c <container_name>`

### Q: What is a Node in Kubernetes?
**A:** A Node is a worker machine in the cluster (physical or virtual machine) that runs Pods managed by the Kubernetes control plane.

### Q: What are Labels and Selectors in Kubernetes?
**A:** 
- **Labels:** Key-value pairs attached to Kubernetes objects for identification and grouping
- **Selectors:** Used to filter and select objects based on labels

### Q: How does Kubernetes handle container restarts?
**A:** Kubernetes automatically restarts containers that fail or exit, based on the Pod's restartPolicy (default is Always), ensuring the desired state is maintained.

### Q: What is a Persistent Volume (PV) in Kubernetes?
**A:** A Persistent Volume is storage in the cluster provisioned by an administrator or dynamically using StorageClasses. It provides storage resources for Pods.

### Q: How do you upgrade Kubernetes cluster components?
**A:** Kubernetes cluster components can be upgraded by updating the Kubernetes version in a controlled manner, following the upgrade instructions in the Kubernetes documentation.

### Q: What is the difference between a StatefulSet and a Deployment in Kubernetes?
**A:** 
- **StatefulSet:** Used for stateful applications requiring stable, unique network identifiers and persistent storage. Manages non-interchangeable Pods
- **Deployment:** Used for stateless applications and manages interchangeable Pods
