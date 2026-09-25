# ============================================================
# Security Group
# Sample values:
#   Name = my-app-sg
#   Port = 8080
#   Source = 10.0.0.0/16
# ============================================================

resource "aws_security_group" "app" {

  name = "my-app-sg"
  # Name of the security group.

  description = "Security group for my-app"
  # Describes the purpose of the security group.

  vpc_id = aws_vpc.app.id
  # Associates the security group with my-app-vpc.

  ingress {
    from_port = 8080
    # Starting port allowed.

    to_port = 8080
    # Ending port allowed.

    protocol = "tcp"
    # Allows TCP traffic.

    cidr_blocks = ["10.0.0.0/16"]
    # Allows traffic from this VPC IP range.
  }

  egress {
    from_port = 0
    # Starting outbound port.

    to_port = 0
    # Ending outbound port.

    protocol = "-1"
    # -1 means all protocols.

    cidr_blocks = ["0.0.0.0/0"]
    # Allows outbound traffic to any IPv4 address.
  }
}




-----------------------
cloud formation



# ============================================================
# Security Group
# Sample values:
#   Name = my-app-sg
#   Port = 8080
#   Source = 10.0.0.0/16
# ============================================================

Resources:

  AppSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    # Creates a security group.

    Properties:

      GroupName: my-app-sg
      # Name of the security group.

      GroupDescription: Security group for my-app
      # Description of the security group.

      VpcId: !Ref AppVPC
      # Associates the security group with the VPC.

      SecurityGroupIngress:
        - IpProtocol: tcp
          # Allows TCP traffic.

          FromPort: 8080
          # Starting port.

          ToPort: 8080
          # Ending port.

          CidrIp: 10.0.0.0/16
          # Allows traffic from this IP range.

      SecurityGroupEgress:
        - IpProtocol: -1
          # Allows all outbound protocols.

          FromPort: 0
          # Starting port.

          ToPort: 0
          # Ending port.

          CidrIp: 0.0.0.0/0
          # Allows outbound traffic to any IPv4 address.


