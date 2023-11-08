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

    


