BACKSTAGE
   ↓
EKS CLUSTER
   ├─ VPC
   ├─ Subnets
   ├─ Routes
   ├─ NAT / IGW
   ├─ Security Groups
   ├─ IAM
   ├─ KMS
   ├─ Node Groups
   ├─ EC2 Nodes
   └─ EKS Add-ons
   ↓
CLUSTER READY
   ↓
RAFAY ENVIRONMENT TEMPLATE
   ├─ Resource Template
   │    └─ S3
   ├─ Resource Template
   │    └─ IAM
   ├─ Resource Template
   │    └─ Vault / Secrets
   ├─ Resource Template
   │    └─ RSA / SSH
   ├─ Resource Template
   │    └─ Namespace / K8s prerequisites
   └─ Other application prerequisites
   ↓
TERRAFORM / OPENTOFU
   ↓
ENVIRONMENT READY
   ↓
HELM
   ├─ Namespace
   ├─ Deployment
   ├─ Pods
   ├─ Container
   ├─ Service
   ├─ ConfigMap
   ├─ Secret
   └─ Routing
   ↓
MICROSERVICE RUNNING
