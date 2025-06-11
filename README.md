# Access-S3-from-private-EC2-instance-using-VPC-endpoint-
## Purpose of the Hands on
Access to the S3 backet from Private instance in VPC through Gateway endpoint without using external network.

### Methods

1. Create <b>Security Groupe</b> for the <b>Load Balancer</b>
2. Create two Instances (WebServerA)-(webServerB)
   - Keypair.pem
   - auto-assign public IPV4 address
   - name of Security groupe web: webserver-SG
   - inbound rule: SSH, HTTP source Loadbalancer
   - Copy an HTML script by an Apache HTTPD web server in user data section
4. Create a Target groupe.
5. Create Application Load Balancer
6. Test the Load Balancer by copy the DNS name and past it to the browser, the Load is shared between the two web servers via the application Load Balancer
   - Response coming from server A
   - Response coming from server B
   8. Create Route tables:
   - Public:  Route to Internet gateway
   - Private: Default route
9. Create security groups:
   - Bastion: Allow SSH,HTTP,HTTPs
   - private: Allow SSH from Bastion 
10. Create VPC Endpoint to access in S3 backet 
11. SSH into private instance through Bastion host
   ```bash
     # Connect to Bastion
        aws ec2-instance-connect ssh --instance-id i-bastion...
   
     # Transfer key
       vi WhizKey.pem
       chmod 400 WhizKey.pem
   
     # SSH to Private
       ssh -i "WhizKey.pem" ec2-user@192.168.0.60
    
     # Configure AWS CLI
       aws configure
     # Enter AWS credentials and region

     # Test S3 access
       aws s3 ls
    

> *Lab originally from: [Whizlabs - Access S3 from Private EC2 using VPC Endpoint](https://www.whizlabs.com/learn/course/aws-solutions-architect-associate/153/lab)*

# -ALI-KACI-Blocking-web-traffic-with-WAF-in-AWS
