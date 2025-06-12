# -ALI-KACI-Blocking-web-traffic-with-WAF-in-AWS
## Purpose of the Hands on
Implement AWS WAF to control inbound/outbound traffic to web servers via an application Load Balancer(ALB)

### Step-by-Step Implementation

# Launch two EC2 instances (WebServerA & WebServerB)

1. Create <b>Security Groupe</b> for the <b>Load Balancer</b>
2. Launch two EC2 Instances <b>(WebServerA)</b>-<b>(webServerB)</b>
   - instance-type t2.micro
   - Keypair.pem
   - auto-assign public IPV4 address
   - Security groupe web: <b>webserver-SG</b>
   - inbound rule: SSH, HTTP source Loadbalancer
   - user-data file://apache_install.sh
4. Create a Target groupe.
5. Create <b>Application Load Balancer</b>
6. Test the Load Balancer by copy the <b>DNS</b> name and past it to the browser, the Load is shared between the two web servers via the application Load Balancer
   - Response coming from server A
   - Response coming from server B
7. In <b>WAF & Shield</b> service Create <b>IP Sets</b> with IP 119.13.69.68/32
8. Create <b>Web ACL</b>
   - Attach the load balancer
   - block the IP sets created and added to the rule.
9. Test
    - By copy the DNS from Load balancer we receive <b>403 Forbidden error</b>
    - Means that WAF blocked the connectivity from Load balancer
10. Resolve the Problem
    - Delete the IP sets
    - Finally we will got again the response from the two web servers

 
    

> *Lab originally from: [Whizlabs - Blocking web traffic with WAF in AWS](https://www.whizlabs.com/labs/blocking-web-traffic-with-waf-in-aws/)*



