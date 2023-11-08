- All ips for Ec2 have public and private ips
- Ips are dynamic so when EC2 instance restarts the IP changes
- If you want to get the static i.e permant IP use ELASTIC IP  that will remains same
- if you are in network you can use private ip to SSH otherwise always use Public ip to SSH
- ELASTIC IP is static PUBLIC IP we own through AWS and we have to pay for this.
- You can associate Private IP of your choice to ELASTIC IP , this is when you have multiple private IP for same EC2 instance


PLACEMENT GROUPS: 
- CLSUTER placement group    : 
     # Cluster Instances into low latency group in Availabitly ZOens
     # Same Hardware same AZ ::  BETTER Network throughput and low latency HIGH Bandwidth
- SPREAD placement Group     : 
    # Spread Instance acress underlying hardwar ( max 7 instacnes per AZ)
    # Minimize Failure , limted to 7 instance per AZ per PG , Maximize high availablity , Instance failure mus be isolated for security
- Partition placement Group  :  
    # spread instance across different sets of racks withing AZ , scales to 100s of EC2 per instance group (hadoop , Cassandra m Kafka)
    # Each partition == Racks in AWS , SAFE from RACK failures
    # Racks level failure tolerance , Partition Aware in Data or Database 


- ELASTIC NETWORK INTERFACE
    # logical component in VPC 
    # represents network interface card ex ETH0 ETH1
    # This provide EC2 instance with network connectivity and private IP
    # Atrributes : primary private IPv4 and multiple secondary IPv4 
    # One Elastic IPv4 per private IPv4
    # one Public IPv4
    # One or more security Groups
    # A Mac Address
    # On the Fly attach ENI to EC2 instances for failOvers
    # move private IP Between EC2 instance if they have a static IP
    # Bound to Availablity Zones


- EC2 Hibernate
    # Stop Ec2 instance Data on EBS remain intace for next start up
    # In case of ternminate the data on EBS volumes are lost
    # Hiberante state of Ec2 instance the in Memory state is preserved
    # Hibernate the state help boot the Ec2 instace faater
    # The RAM state is written to a file in the root EBS volume
    # The root EBS volume must be encrypted
    # Saving the RAM state , Long time to Iniatalize EC2 instaces , Long running processes.
    # Supprted by EC Famailies C , I , M , R , T
    # Ram Size is less than 150GB
    # Instance Size not supported for BARE metal instance
    # AMI images - Amazn Linux 2, Linux AMI , ubuntu , RHEL  CentOS , Windows
    # Root Volume - Must be EBS , encrypted , not instance store , large
    # On Demand , Reserved and Spot Instances
    # Not To be Hibernated more than 60 days
    


