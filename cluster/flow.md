PORTAL
      ↓
BACKSTAGE
      ↓
CLUSTER / ENVIRONMENT PROVISIONING
      │
      ├── VPC
      │     ├── CIDR
      │     ├── Availability Zones
      │     ├── Public Subnets
      │     ├── Private Subnets
      │     ├── Route Tables
      │     ├── Internet Gateway
      │     ├── NAT Gateway
      │     ├── Elastic IP
      │     ├── Security Groups
      │     └── VPC Endpoints
      │
      ├── IAM
      │     ├── EKS Cluster Role
      │     ├── Node Role
      │     ├── IAM Policies
      │     └── Pod / Service IAM Roles
      │
      ├── SECURITY / ENCRYPTION
      │     ├── KMS Key
      │     └── Encryption Configuration
      │
      └── EKS CLUSTER
            ├── EKS Control Plane
            ├── Cluster Security Group
            ├── Managed Node Groups
            │     └── EC2 Worker Nodes
            ├── Auto Scaling
            └── EKS Add-ons
                  ├── VPC CNI
                  ├── CoreDNS
                  ├── kube-proxy
                  ├── EBS CSI Driver
                  └── Load Balancer Controller
      ↓
EKS CLUSTER READY
