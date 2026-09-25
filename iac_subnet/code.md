# ============================================================
# Subnet
# Sample values:
#   Subnet name = my-app-subnet
#   CIDR        = 10.0.1.0/24
#   VPC         = my-app-vpc
# ============================================================

resource "aws_subnet" "app" {

  vpc_id = aws_vpc.app.id
  # Places this subnet inside the VPC created above.

  cidr_block = "10.0.1.0/24"
  # IP address range for this subnet.

  availability_zone = "us-east-1a"
  # Places the subnet in Availability Zone us-east-1a.

  tags = {
    Name = "my-app-subnet"
    # Name of the subnet.
  }
}



----------------------------------------------

# ============================================================
# Subnet
# Sample values:
#   Subnet name = my-app-subnet
#   CIDR        = 10.0.1.0/24
#   AZ          = us-east-1a
# ============================================================

Resources:

  AppSubnet:
    Type: AWS::EC2::Subnet
    # Creates a subnet.

    Properties:

      VpcId: !Ref AppVPC
      # Places the subnet inside the VPC.

      CidrBlock: 10.0.1.0/24
      # IP address range for the subnet.

      AvailabilityZone: us-east-1a
      # Availability Zone where the subnet is created.

      Tags:
        - Key: Name
          Value: my-app-subnet
          # Name of the subnet.
