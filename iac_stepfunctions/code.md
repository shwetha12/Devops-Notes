# ============================================================
# Step Functions State Machine
# Sample values:
#   State machine = my-app-workflow
#   First step    = Lambda
# ============================================================

resource "aws_sfn_state_machine" "app" {

  name = "my-app-workflow"
  # Name of the Step Functions workflow.

  role_arn = "arn:aws:iam::123456789012:role/my-app-stepfunctions-role"
  # IAM role that allows Step Functions to call AWS services.

  definition = jsonencode({

    StartAt = "RunLambda"
    # Defines the first state to execute.

    States = {

      RunLambda = {

        Type = "Task"
        # A Task state performs work.

        Resource = "arn:aws:lambda:us-east-1:123456789012:function:my-app-lambda"
        # Lambda function that Step Functions calls.

        End = true
        # Workflow ends after Lambda completes.
      }
    }
  })
}





---------------------------------------------------------
# ============================================================
# Step Functions
# Sample values:
#   State machine = my-app-workflow
#   Task          = Lambda
# ============================================================

Resources:

  AppWorkflow:
    Type: AWS::StepFunctions::StateMachine
    # Creates a Step Functions state machine.

    Properties:

      StateMachineName: my-app-workflow
      # Name of the workflow.

      RoleArn: arn:aws:iam::123456789012:role/my-app-stepfunctions-role
      # IAM role used by Step Functions.

      Definition:
        StartAt: RunLambda
        # First step in the workflow.

        States:

          RunLambda:
            Type: Task
            # Task performs an operation.

            Resource: arn:aws:lambda:us-east-1:123456789012:function:my-app-lambda
            # Lambda function called by the workflow.

            End: true
            # Ends the workflow after Lambda finishes.



            ------------
            Step Functions = workflow/orchestration between AWS services.


