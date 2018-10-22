# AWS CodePipeline Setup Guideline

## Installation Steps

  1. Log into AWS.

  2. Search for the CodePipeline service and select it.

![CodePipeline Setup 1](screenshots/CP01.png)

  3. In the Pipelines pane, click on **Create pipeline**.

![CodePipeline Setup 1](screenshots/CP02.png)

  4. **Step 1 - Choose pipeline settings**. Enter the *Pipeline name*. Choose **New service role** option to create a new service role in your account, then select **Default location** as Artifact store and click **Next** to continue.

![CodePipeline Setup 1](screenshots/CP03.png)

  5. **Step 2 - Add source stage**. Select **GitHub** as Source provider then click on **Connect to GitHub** and provide your credentials in case they are required.

![CodePipeline Setup 1](screenshots/CP04.png)

  Once you have been authenticated choose the Repository and Branch that will be the source for the process. Leave GitHub webhooks option checked.

![CodePipeline Setup 1](screenshots/CP05.png)

  6. **Step 3 - Add build stage**. Select **AWS CodeBuild** as your Build provider. Click on **Create project**, this will send you to the CodeBuild process.


  - [ ] Enter a name for you Build Project.

![CodePipeline Setup 1](screenshots/CB001.png)

  - [ ] In the Environment pane choose **Managed image** option and select *Ubuntu* as Operating system, *Java* as Runtime, *java:openjdk-8* for Runtime version and *Always use the latest image for this runtime version*. Then choose to create a new service role.

![CodePipeline Setup 1](screenshots/CB002.png)

  - [ ] For Build specifications, choose *Use a buildspec file*, which will be the buildspec.yaml file in our project. Click **Continue to CodePipeline** to return to the pipeline setup process.

![CodePipeline Setup 1](screenshots/CB003.png)

  - [ ] Once you are in the **Add build stage** screen, click **Next**.

![CodePipeline Setup 1](screenshots/CP07.png)

   7. **Step 4 - Add deploy stage**. Select AWS CodeDeploy as your Deploy provider and select the rest of parameters according to your CodeDeploy Application. If there is not any CodeDeploy Application follow the steps described in the [CodeDeploy Setup Guideline](CodeDeploySetup.md).

![CodePipeline Setup 1](screenshots/CP08.png)

   8. **Step 5 - Review**. Click Next and check that the information entered is correct.

  - [ ] Check Pipeline Settings.

![CodePipeline Setup 1](screenshots/CP09-1.png)

  - [ ] Check Source Code Settings.

![CodePipeline Setup 1](screenshots/CP09-2.png)

  - [ ] Check Build and Deploy Settings.

![CodePipeline Setup 1](screenshots/CP09-1.png)

   9. Finally, click **Create Pipeline**.






