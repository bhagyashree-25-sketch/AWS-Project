# Auto scaling and Load balancer

# AWS Services used
auto scaling group
template
load balancer

# Key Features
**High Availability**: Resources are deployed across multiple Availability Zones to ensure fault tolerance.
**Dynamic Scaling**: Automatically adjusts the number of EC2 instances based on traffic load (e.g., CPU utilization).
**Load Distribution**: Evenly distributes traffic across all healthy instances using an ALB.
**Health Checks**: Automatically detects and replaces unhealthy instances to ensure end-users are never routed to a failing server.
**Cost Optimization**: Scales down during off-peak hours, ensuring you only pay for the compute resources you actually need.

 # Deployment Steps
**Create a Launch Template**: Select an Amazon Machine Image (AMI) (e.g., Amazon Linux 2023). Choose an instance type (e.g., t2.micro for Free Tier). Add a User Data script to install and start your web server (e.g., Nginx or Apache).
Attach a Security Group allowing HTTP (port 80) from the Load Balancer and SSH (port 22) from your IP.
**Create the Application Load Balancer**: Select "Application Load Balancer" and make it internet-facing. Configure a target group on port 80.
**Create the Auto Scaling Group**: Attach the Launch Template created in Step 1. Select the same VPC and public subnets. Attach the ALB created in Step 2 to the ASG.
Set the Group Size: Minimum (e.g., 2), Maximum (e.g., 6), and Desired (e.g., 2).
**Configure Scaling Policies**: Go to the ASG "Automatic Scaling" tab.Create a Target Tracking Scaling Policy. Select ASG Average CPU Utilization and set the target value (e.g., 50%).
