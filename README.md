# Virtual Private Cloud (VPC)
## Terms
- **VPC** == on-demand configurable pool of shared resources allocated within a **public cloud environment**
- **public cloud environment** == provides a certain level of isolation between the different organisations (i.e. **users**)

## How does VPC work?
- VPC provides the ability to define and control **isolated virtual networks** and then deploy **cloud resources** into those networks
- essentially creates a private network, that's completely virtual, e.g. connecting a single company's offices across the globe
- within this network, a set of IPs is created
- the VPC can be accessed via a VPN

### How is a network deployed in a standard public cloud
- an administrator is going to define a **backbone** that is going to carry all the traffic in that cloud
- there's going to be some **segmentation** on that backbone to create separation between **clients** or **applications** within the same client
- we need a network function to communicate between the different segments == **router**
- Example:
    - maybe we don't want traffic to flow between two segments, e.g. customer A and customer B
    - now, we have a **firewall function** that provides **filtering capabilities**
- can access the wider internet via **NAT function**

### Segmentation and subnets
- as mentioned, can divide a network into **subnets**
- two types of subnets: *private* and *public*
    - **public subnet** == can access the wider internet via a **route** going into the *internet gateway*
    - **private subnet** == doesn't connect to wider internet; extra level of security
- actual resources live within the subnets

### Regions
- **region** = usually refers to a geographical location - e.g. US-WEST1
- within a region, there are **availability zones**
- **availability zone** == corresponds to a *data* *center* in a given region, e.g. US-WEST1A, US-WEST1B
- *a single VPC corresponds to one region*; these VPCs are subdivided into subnets

### Classless Inter-Domain Routing (CIDR)
- **CIDR** == notation for describing blocks of IP addresses
- **CIDER range** == how many IPs there are within a single VPC
- need to make sure that we have enough IP addresses for all machines, database instances, etc.
- 172.31.0.0/16 => tells you how many IP addresses available there are
    - use [https://cidr.xyz](https://cidr.xyz) to get the *first usable IP*, *last usable IP*, and *number of available IPs*
    - in this example, they are 172.31.0.1, 172.31.255.254, 65 536, respectively

### Acessing the wider internet from a Private subnet
- normally cannot do that; but sometimes we want to access the wider internet without allowing the wider internet to access our databases and applications stored in a private subnet
- a private subnet can access the wider internet via a **NAT gateway**
- **NAT** == Network Address Translation
    - the NAT gateway resides **within the public subnet**
    - from private subnet, access the NAT gateway in the public subnet, and thus the internet

### Network ACLs and Security Groups
- **ACL** == access network list
- ACLs and Security groups are quite similar, they both protect your VPC resources, but the key differences are:
    - ACL:
        - firewall that controls traffic in/out of a subnet
        - rules for **allow** and **deny** that are exclusively used with IP addresses
    - Security Groups:
        - firewall that controls traffic in/out of an **EC2 instance**
        - rules for **allow** only
        - rules include IP addresses **AND** other security groups

## Implementations of VPCs
1. [Amazon Web Services (AWS)](https://en.wikipedia.org/wiki/Amazon_Web_Services)
2. [IBM Cloud](https://en.wikipedia.org/wiki/IBM_Cloud)
3. [Google Cloud Platform](https://en.wikipedia.org/wiki/Google_Cloud_Platform)
4. [Microsoft Azure](https://en.wikipedia.org/wiki/Microsoft_Azure)


