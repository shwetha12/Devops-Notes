# ============================================================
# Lambda Function
# Sample values:
#   Function name = my-app-lambda
#   Runtime       = Python 3.12
#   Handler       = lambda_function.lambda_handler
#   Package       = lambda.zip
# ============================================================

resource "aws_lambda_function" "app" {

  function_name = "my-app-lambda"
  # Name of the Lambda function.

  runtime = "python3.12"
  # Python runtime used by Lambda.

  handler = "lambda_function.lambda_handler"
  # Lambda looks for lambda_handler inside lambda_function.py.

  filename = "lambda.zip"
  # ZIP file containing the Lambda application code.

  source_code_hash = filebase64sha256("lambda.zip")
  # Calculates a hash of the ZIP file.
  # Terraform can detect when the code package changes.

  role = "arn:aws:iam::123456789012:role/my-app-lambda-role"
  # IAM role that gives Lambda permission to access AWS resources.
}





----------------------------------------------------------------------------------------------------------
CF 

# ============================================================
# Lambda Function
# Sample values:
#   Function name = my-app-lambda
#   Runtime       = Python 3.12
#   Code location = S3
# ============================================================

Resources:

  AppLambda:
    Type: AWS::Lambda::Function
    # Creates a Lambda function.

    Properties:

      FunctionName: my-app-lambda
      # Name of the Lambda function.

      Runtime: python3.12
      # Python runtime.

      Handler: lambda_function.lambda_handler
      # Python file and function Lambda should execute.

      Role: arn:aws:iam::123456789012:role/my-app-lambda-role
      # IAM role used by Lambda.

      Code:
        S3Bucket: my-app-deployment-bucket
        # S3 bucket containing the Lambda deployment package.

        S3Key: lambda.zip
        # ZIP file containing the Lambda code.




