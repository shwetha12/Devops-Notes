# ============================================================
# VPC
# Sample values:
#   VPC name = my-app-vpc
#   CIDR     = 10.0.0.0/16
# ============================================================

resource "aws_vpc" "app" {

  cidr_block = "10.0.0.0/16"
  # Defines the private IP address range for the VPC.

  tags = {
    Name = "my-app-vpc"
    # Gives the VPC a recognizable name.
  }
}


-----------------
# ============================================================
# VPC
# Sample values:
#   VPC name = my-app-vpc
#   CIDR     = 10.0.0.0/16
# ============================================================

Resources:

  AppVPC:
    Type: AWS::EC2::VPC
    # Creates an AWS VPC.

    Properties:

      CidrBlock: 10.0.0.0/16
      # Defines the IP address range for the VPC.

      Tags:
        - Key: Name
          Value: my-app-vpc
          # Gives the VPC a recognizable name.



          
