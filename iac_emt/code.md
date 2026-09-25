# ============================================================
# EMR Cluster
# Sample values:
#   Cluster name = my-app-emr
#   Release      = emr-7.0.0
#   Applications = Hadoop + Spark
# ============================================================

resource "aws_emr_cluster" "app" {

  name = "my-app-emr"
  # Name of the EMR cluster.

  release_label = "emr-7.0.0"
  # EMR software release version.

  applications = [
    "Hadoop",
    "Spark"
  ]
  # Applications installed on the cluster.

  service_role = "arn:aws:iam::123456789012:role/my-app-emr-service-role"
  # IAM role that allows EMR to interact with AWS services.

  ec2_attributes {
    subnet_id = "subnet-0123456789abcdef0"
    # Subnet where the EMR cluster runs.

    emr_managed_master_security_group = "sg-0123456789abcdef0"
    # Security group for the EMR master node.

    emr_managed_slave_security_group = "sg-0123456789abcdef1"
    # Security group for worker nodes.
  }

  master_instance_group {
    instance_type  = "m5.xlarge"
    instance_count = 1
    # One master node.

    name = "master"
    # Name of the master instance group.
  }

  core_instance_group {
    instance_type  = "m5.xlarge"
    instance_count = 2
    # Two worker/core nodes.

    name = "core"
    # Name of the core instance group.
  }
}




-------------------------------------------------


# ============================================================
# EMR Cluster
# Sample values:
#   Cluster name = my-app-emr
#   Release      = emr-7.0.0
#   Applications = Hadoop + Spark
# ============================================================

Resources:

  AppEMR:
    Type: AWS::EMR::Cluster
    # Creates an EMR cluster.

    Properties:

      Name: my-app-emr
      # Name of the EMR cluster.

      ReleaseLabel: emr-7.0.0
      # EMR software release.

      Applications:
        - Name: Hadoop
        - Name: Spark
        # Applications installed on the cluster.

      ServiceRole: arn:aws:iam::123456789012:role/my-app-emr-service-role
      # IAM role used by EMR.

      Instances:

        Ec2SubnetId: subnet-0123456789abcdef0
        # Subnet where the cluster runs.

        MasterInstanceGroup:
          InstanceCount: 1
          # One master node.

          InstanceType: m5.xlarge
          # Instance type used for the master.

        CoreInstanceGroup:
          InstanceCount: 2
          # Two core/worker nodes.

          InstanceType: m5.xlarge
          # Instance type used for workers.

        TerminationProtected: false
        # Allows the cluster to be terminated.





        -----------------

managed big-data processing platform, commonly Hadoop/Spark.

        managed big-data processing platform, commonly Hadoop/Spark.
