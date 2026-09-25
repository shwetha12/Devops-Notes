# ============================================================
# AWS Batch Compute Environment
# Sample values:
#   Environment = my-app-batch
#   Type        = Managed
#   Compute     = Fargate
#   Max vCPU    = 16
# ============================================================

resource "aws_batch_compute_environment" "app" {

  compute_environment_name = "my-app-batch"
  # Name of the Batch compute environment.

  type = "MANAGED"
  # AWS manages the compute resources.

  compute_resources {

    type = "FARGATE"
    # Batch jobs run using Fargate containers.

    max_vcpus = 16
    # Maximum number of vCPUs available for jobs.

    subnets = [
      "subnet-0123456789abcdef0",
      "subnet-0123456789abcdef1"
    ]
    # Subnets where Batch jobs run.

    security_group_ids = [
      "sg-0123456789abcdef0"
    ]
    # Security group controlling network access.
  }
}







-------------------------------------------------
# ============================================================
# AWS Batch Job Queue
# Sample value:
#   Queue name = my-app-queue
# ============================================================

resource "aws_batch_job_queue" "app" {

  name = "my-app-queue"
  # Name of the queue where jobs wait to run.

  state = "ENABLED"
  # Enables the queue.

  priority = 1
  # Priority used when deciding which jobs to process.

  compute_environment_order {
    order = 1
    # First compute environment used by this queue.

    compute_environment = aws_batch_compute_environment.app.arn
    # Connects the queue to the Batch compute environment.
  }
}





--------------------------------------------
CF:

# ============================================================
# AWS Batch
# Sample values:
#   Environment = my-app-batch
#   Queue       = my-app-queue
#   Compute     = Fargate
# ============================================================

Resources:

  AppBatchEnvironment:
    Type: AWS::Batch::ComputeEnvironment
    # Creates the compute environment used to run Batch jobs.

    Properties:

      Type: MANAGED
      # AWS manages the compute resources.

      ComputeResources:
        Type: FARGATE
        # Runs Batch jobs using Fargate.

        MaxvCpus: 16
        # Maximum number of vCPUs.

        Subnets:
          - subnet-0123456789abcdef0
          - subnet-0123456789abcdef1
          # Subnets where jobs run.

        SecurityGroupIds:
          - sg-0123456789abcdef0
          # Security group for the jobs.


  AppBatchQueue:
    Type: AWS::Batch::JobQueue
    # Creates a queue where Batch jobs wait.

    Properties:

      JobQueueName: my-app-queue
      # Name of the queue.

      State: ENABLED
      # Enables the queue.

      Priority: 1
      # Queue priority.



      -----------------------------------------------

      Job submitted
      ↓
Batch Job Queue
      ↓
Compute Environment
      ↓
Container runs







