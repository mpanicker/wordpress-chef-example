# Cloud Formation template(aws-cf-wp-template.json)  will do the following things
1. Create a new Vpc
2. Attach an Internet Gateway to the VPC
3. Create 2 Public and 2 Private Subnets within the VPC
4. Create a Route from the internet into the Public Subnets
5. Create a NAT Gateway
6. Create a route from NAT Gateway to the Internet
7. Create a route from the private subnets to the NAT Gateway
8. Create an Application Load balancer, Target group and Listener
9. Create an AutoScaling group within the Public Subnets
10. Create a RDS MySQL DB in the private subnet
11. Create a Launch Configuration that installs cloud formation init scripts, chef and a Word Press Chef cookbook from https://github.com/mpanicker/wordpress-chef-cookbook
12. Create Security Groups that let in ssh(22) and http(80) traffic into the ALB and EC2 instances
13. Create Security Group that lets in RDP(3306) traffic from the EC2 instances into the RDS MySQL DB

## Known issues
The Wordpress Chef cookbook does not fully work. The database recipe in recipes folder (database.rb) throws a mysql_service error. If we comment the database recipe in app.rb then it throws a apache user id not found error
