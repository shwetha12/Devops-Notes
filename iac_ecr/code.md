# ============================================================
# ECR Repository
# Sample values:
#   Repository name = my-app
#   Tag behavior    = MUTABLE
#   Image scanning  = Enabled
# ============================================================

resource "aws_ecr_repository" "app" {

  name = "my-app"
  # Creates an ECR repository named "my-app".
  # Docker images for the application are stored here.

  image_tag_mutability = "MUTABLE"
  # Allows an existing image tag to be reused.
  # Example: my-app:latest can point to a newer image.

  image_scanning_configuration {
    scan_on_push = true
    # Automatically scans a Docker image for vulnerabilities
    # whenever the image is pushed to ECR.
  }
}


====================================================================
# ============================================================
# ECR Repository
# Sample values:
#   Repository name = my-app
#   Tag behavior    = MUTABLE
#   Image scanning  = Enabled
# ============================================================

Resources:

  AppRepository:
    Type: AWS::ECR::Repository
    # Creates an Amazon ECR repository.

    Properties:

      RepositoryName: my-app
      # Name of the ECR repository.

      ImageTagMutability: MUTABLE
      # Allows an existing image tag to be reused or updated.

      ImageScanningConfiguration:
        ScanOnPush: true
        # Scans Docker images automatically when they are pushed.
