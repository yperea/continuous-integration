# EC2 Role for AWS CodePipeline and AWS CodeDeploy Setup

## Steps

1. Log into AWS.

2. Search for the **IAM** service and select it.

3. In option Roles click **Create Role**:

![CodeDeploy TS 1](screenshots/CD-TS4.png)

4. Select **AWS service** as type of trusted entity and **EC2** for the service that will use the role, then click **Next: Permissions**.

![CodeDeploy TS 1](screenshots/CD-TS5.png)

5. Select and attach to the role the predefined polices **AmazonEC2RoleforAWSCodeDeploy** and **AWSCodePipelineCustomActionAccess**, then click **Next: Review**.

![CodeDeploy TS 1](screenshots/CD-TS6-1.png)

![CodeDeploy TS 1](screenshots/CD-TS6-2.png)

6. Review that both polices were attached and assign a name for the role, then click **Create role**.

![CodeDeploy TS 1](screenshots/CD-TS7.png)

7. Verify on Roles pane the creation of the new Role.

![CodeDeploy TS 1](screenshots/CD-TS8.png)

8. Return to EC2 Dashboard and select **Actions** > **Instance settings** > **Attach/Replace IAM Role** option.

![CodeDeploy TS 1](screenshots/CD-TS2.png)

9. Finally select the Role just created and click **Apply**.

![CodeDeploy TS 1](screenshots/CD-TS9.png)

![CodeDeploy TS 1](screenshots/CD-TS10.png)

This role enable AWS CodePipeline to deploy artifacts on the EC2 Instance selected.




