# ============================================================
# CloudWatch Log Group
# Sample value:
#   Log group = /aws/my-app
#   Retention = 30 days
# ============================================================

resource "aws_cloudwatch_log_group" "app" {

  name = "/aws/my-app"
  # Name of the CloudWatch log group.

  retention_in_days = 30
  # CloudWatch keeps the logs for 30 days.
}


-----------------------------------------------------------------

# ============================================================
# CloudWatch Alarm
# Sample values:
#   Alarm name = my-app-high-cpu
#   CPU limit  = 80%
# ============================================================

resource "aws_cloudwatch_metric_alarm" "cpu" {

  alarm_name = "my-app-high-cpu"
  # Name of the CloudWatch alarm.

  comparison_operator = "GreaterThanThreshold"
  # Alarm triggers when the metric is greater than the threshold.

  threshold = 80
  # CPU percentage that triggers the alarm.

  evaluation_periods = 2
  # Condition must occur for 2 evaluation periods.

  metric_name = "CPUUtilization"
  # AWS metric being monitored.

  namespace = "AWS/ECS"
  # AWS service that owns the metric.

  statistic = "Average"
  # Calculates the average CPU utilization.

  period = 300
  # Checks the metric every 300 seconds (5 minutes).
}





-----------------------------------------------

CF:

# ============================================================
# CloudWatch
# Sample values:
#   Log group = /aws/my-app
#   Retention = 30 days
# ============================================================

Resources:

  AppLogGroup:
    Type: AWS::Logs::LogGroup
    # Creates a CloudWatch log group.

    Properties:

      LogGroupName: /aws/my-app
      # Name of the log group.

      RetentionInDays: 30
      # Keeps logs for 30 days.





