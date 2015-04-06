# Amazon Elastic Load Balancing (ELB)
Elastic Load Balancing automatically distributes incoming application traffic across multiple Amazon EC2 instances in the cloud. It enables you to achieve greater levels of fault tolerance in your applications, seamlessly providing the required amount of load balancing capacity needed to distribute application traffic. [![Intro to Amazon ELB](./intro-to-elb.png)](./Introduction to Elastic Load Balancing.mp4)

# Launching an ELB instance
1. Visit **ELB Dashboard** at https://ap-northeast-1.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-1#LoadBalancers:
2. At the **ELB Dashboard** page, click Create Load Balancer. ![ELB Dashboard](./elb-dashboard.png)
3. At the **Define Load Balancer** page, fill **Load Balancer name**, choose _workshop_ for **Create LB Inside**, and click **Continue**. ![Define Load Balancer](./elb-define-load-balancer.png)
4. At the **Configure Health Check** page, leave as is and click **Continue**. ![Configure Health Check](./elb-configure-health-check.png)
5. At the **Select Subnets** page, choose _public-1a_ and _public-1c_ under **Name**, and click **Continue**. ![Select Subnet](./elb-select-subnet.png)
6. At the **Assign Security Groups** page, choose _Select an existing security group_ for **Assign a security group**, select _public-web_ under **Name**, and click **Continue**. ![Assign Security Groups](./elb-assign-security-group.png)
7. At the **Add EC2 Instances** page, choose EC2 instances that will be registered to this ELB, and click **Continue**. ![Add EC2 Instances](./elb-add-ec2-instances.png)
8. At the **Add Tags** page, fill appropriate tags (under **Key** and **Value**), and click **Continue**. ![Add Tags](./elb-add-tags.png)
9. At the **Review** page, click **Create**. ![ELB Review](./elb-review.png)
10. At the Create Load Balancer page, click Close. ![Create Load Balancer](./elb-launch-status.png)
11. The newly created ELB will be shown at the **ELB Dashboard**. ![ELB Dashboard](./elb-dashboard-2.png)
12. Navigate to **Instances** tab and wait until EC2 instance ready to accept traffic from load balancer (Indicated by _InService_ under **Status**). ![ELB EC2 Instances](./elb-dashboard-3.png)
13. Visit ELB **DNS Name** under **Description** tab using web browser.
