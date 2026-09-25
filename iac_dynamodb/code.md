# ============================================================
# DynamoDB Table
# Sample values:
#   Table name = my-app-table
#   Primary key = id
#   Billing     = PAY_PER_REQUEST
# ============================================================

resource "aws_dynamodb_table" "app" {

  name = "my-app-table"
  # Name of the DynamoDB table.

  billing_mode = "PAY_PER_REQUEST"
  # DynamoDB automatically handles capacity.
  # You pay based on actual requests instead of defining capacity.

  hash_key = "id"
  # Defines "id" as the partition/primary key.

  attribute {
    name = "id"
    # Name of the key attribute.

    type = "S"
    # S means String.
  }
}





-----------------------------------------------------
cloud frmation

# ============================================================
# DynamoDB Table
# Sample values:
#   Table name = my-app-table
#   Primary key = id
#   Billing     = PAY_PER_REQUEST
# ============================================================

Resources:

  AppTable:
    Type: AWS::DynamoDB::Table
    # Creates a DynamoDB table.

    Properties:

      TableName: my-app-table
      # Name of the table.

      BillingMode: PAY_PER_REQUEST
      # Uses on-demand capacity.

      AttributeDefinitions:
        - AttributeName: id
          AttributeType: S
          # Defines "id" as a String attribute.

      KeySchema:
        - AttributeName: id
          KeyType: HASH
          # Makes "id" the partition key.



          -------------

          DynamoDB = NoSQL database.



