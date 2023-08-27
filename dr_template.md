# Infrastructure

## AWS Zones
Identify your zones here

## Servers and Clusters

### Table 1.1 Summary
| Asset      | Purpose           | Size     | Qty   | DR                                   |
|------------|-------------------|----------|-------|--------------------------------------|
| EC2        | Server Instance   | t3.micro | 6     | 2 region and 3 instances per region           |
| EC2 Keypair| EC2 ssh key for server| -    | 2     | 2 region and 1 keypair per region            |
| VPC        | Virtual private network   | - | 2     | 2 region and 1 VPC per region          |
| ALB         | Load balance    | - | 2     | 2 region for HA/DR            |
| EKS        | Kubenates cluster   | t3.medium | 4  | 2 region and 2 cluster nodes per region           |
| S3         | S3 bucket for terraform   | - | 2     | 2 region and 1 S3 bucket per region            |
| RDS (master)         | Database   | - | t3.micro     | 1 cluster 2 nodes on primary region            |
| RDS (replica)         | Database   | - | t3.micro     | 1 cluster 2 replica nodes on secondary region            |


### Descriptions
More detailed descriptions of each asset identified above.
EC2: Enviroment to run application
EC2 Keypair: Use this key for ssh to EC2 instance
VPC: Provide network for infrastructure
ALB: Provide load balance for application 
EKS: Kubernate cluster for deploy and monitoring application and server
S3: Store terraform information
RDS: Provide Relationship Database to application store data


## DR Plan
### Pre-Steps:
List steps you would perform to setup the infrastructure in the other region. It doesn't have to be super detailed, but high-level should suffice.
- Deploy the Terraform code for zone 1 and zone 2

## Steps:
You won't actually perform these steps, but write out what you would do to "fail-over" your application and database cluster to the other region. Think about all the pieces that were setup and how you would use those in the other region
- RDS: can promote replica database to master database
- ALB: can router traffic to HA zone