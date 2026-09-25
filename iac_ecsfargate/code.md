: Cluster → Task Definition → Service.

Terraform — ECS Cluster
# ============================================================
# ECS Cluster
# Sample value:
#   Cluster name = my-app-cluster
# ============================================================

resource "aws_ecs_cluster" "app" {

  name = "my-app-cluster"
  # Creates an ECS cluster.
  # The cluster provides a logical place for ECS services and tasks to run.
}

-------------------------------------------------------------------
Terraform — Fargate Task Definition
# ============================================================
# ECS Fargate Task Definition
# Sample values:
#   Application    = my-app
#   CPU            = 256
#   Memory         = 512 MB
#   Container port = 8080
# ============================================================

resource "aws_ecs_task_definition" "app" {

  family = "my-app"
  # Logical name for this task definition.

  network_mode = "awsvpc"
  # Gives the task its own network interface/IP address.
  # This is commonly used with Fargate.

  requires_compatibilities = ["FARGATE"]
  # Says this task definition is intended to run on Fargate.

  cpu = "256"
  # CPU allocation for the task.

  memory = "512"
  # Memory allocation for the task.

  execution_role_arn = "arn:aws:iam::123456789012:role/my-app-ecs-role"
  # IAM role ECS uses to perform actions such as
  # pulling the container image from ECR.

  container_definitions = jsonencode([
    {
      name = "my-app"
      # Name of the container.

      image = "123456789012.dkr.ecr.us-east-1.amazonaws.com/my-app:latest"
      # Docker image that ECS will run.
      # This image is stored in ECR.

      essential = true
      # If this container stops, ECS considers the task stopped.

      portMappings = [
        {
          containerPort = 8080
          # Application listens on port 8080 inside the container.

          protocol = "tcp"
          # Network protocol used by the application.
        }
      ]
    }
  ])
}



------------------------------------------------------------------------------------

Terraform — ECS Service
# ============================================================
# ECS Fargate Service
# Sample values:
#   Service name  = my-app-service
#   Desired tasks = 2
#   Launch type   = Fargate
# ============================================================

resource "aws_ecs_service" "app" {

  name = "my-app-service"
  # Name of the ECS service.

  cluster = aws_ecs_cluster.app.id
  # Tells ECS which cluster to use.
  # "aws_ecs_cluster.app.id" references the cluster created above.

  task_definition = aws_ecs_task_definition.app.arn
  # Tells ECS which task definition to run.

  desired_count = 2
  # Keeps 2 application tasks running.

  launch_type = "FARGATE"
  # Runs the containers using AWS Fargate.
  # AWS manages the underlying servers.

  network_configuration {

    subnets = [
      "subnet-0123456789abcdef0",
      "subnet-0123456789abcdef1"
    ]
    # Subnets where the Fargate tasks will run.

    security_groups = [
      "sg-0123456789abcdef0"
    ]
    # Security group controlling network access to the tasks.

    assign_public_ip = false
    # Tasks do not receive public IP addresses.
}




-------------------------------------------------------------------------

CLOUDFORMATION:
# ============================================================
# ECS / Fargate
# Sample values:
#   Cluster       = my-app-cluster
#   Application   = my-app
#   CPU           = 256
#   Memory        = 512
#   Port          = 8080
#   Desired tasks = 2
# ============================================================

Resources:

  AppCluster:
    Type: AWS::ECS::Cluster
    # Creates the ECS cluster.

    Properties:
      ClusterName: my-app-cluster
      # Name of the ECS cluster.


  AppTaskDefinition:
    Type: AWS::ECS::TaskDefinition
    # Defines how the container should run.

    Properties:

      Family: my-app
      # Logical name of the task definition.

      NetworkMode: awsvpc
      # Gives the Fargate task its own network interface.

      RequiresCompatibilities:
        - FARGATE
        # Specifies that this task runs on Fargate.

      Cpu: "256"
      # CPU allocated to the task.

      Memory: "512"
      # Memory allocated to the task.

      ExecutionRoleArn: arn:aws:iam::123456789012:role/my-app-ecs-role
      # IAM role used by ECS to pull images and perform
      # required execution actions.

      ContainerDefinitions:
        - Name: my-app
          # Name of the container.

          Image: 123456789012.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
          # Docker image stored in ECR.

          Essential: true
          # If this container stops, the task is considered stopped.

          PortMappings:
            - ContainerPort: 8080
              # Application port inside the container.

              Protocol: tcp
              # Network protocol.


  AppService:
    Type: AWS::ECS::Service
    # Maintains the desired number of running containers.

    Properties:

      ServiceName: my-app-service
      # Name of the ECS service.

      Cluster: !Ref AppCluster
      # Connects the service to the ECS cluster above.

      TaskDefinition: !Ref AppTaskDefinition
      # Tells the service which task definition to run.

      DesiredCount: 2
      # Keeps 2 tasks running.

      LaunchType: FARGATE
      # Uses AWS Fargate to run the containers.

      NetworkConfiguration:
        AwsvpcConfiguration:

          Subnets:
            - subnet-0123456789abcdef0
            - subnet-0123456789abcdef1
            # Subnets where the tasks will run.

          SecurityGroups:
            - sg-0123456789abcdef0
            # Security group controlling network access.

          AssignPublicIp: DISABLED
          # Does not assign public IP addresses.
---------------------------------------------------------------

 ECR
 ↓
Docker Image
 ↓
ECS Task Definition
 ↓
ECS Service
 ↓
Fargate














