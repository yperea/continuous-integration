# AWS CodeDeploy Setup Guideline

## Installation Steps

  1. Log into AWS.

  2. Search for the CodeDeploy service and select it.

![CodeDeploy Setup 1](screenshots/CD01.png)

  3. In the Applications pane, click on **Create application**.

![CodeDeploy Setup 2](screenshots/CD02.png)

  4. On the Create application pane, enter the name for your application and select **EC2/On-premises** option as *Compute platform* and then click on **Create application**.

![CodeDeploy Setup 3](screenshots/CD03.png)

  5. You should see a confirmation message and the configuration entered in **Application details** section. Now a deployment group need to be created, click on **Create deployment group** button.

![CodeDeploy Setup 4](screenshots/CD04.png)

  6. Create deployment group. Enter a name for the Deployment Group and choose the service role with CodeDeploy permissions created previously. If not, create one following the instructions in the link [Creating a Service Role for AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/getting-started-create-service-role.html#getting-started-create-service-role-console). After that you can continue creating the deployment group.

![CodeDeploy Setup 4](screenshots/CD05.png)

   - [ ] Since we are going to work on the same instance we need to choose **In-place** as Deployment type. Select **Amazon EC2 instances** for your **Environment configuration** *you need to have your EC2 instance tagged*.

![CodeDeploy Setup 4](screenshots/CD06.png)

   - [ ] In **Deployment settings** choose **CodeDeployDefault.AllAtOnce** as you *Deployment configuration*. Uncheck *Enable load balancing* option in **Load balancer** pane as we are not using any load balancing configuration. Leave **Advanced** options As-Is, then click **Create deployment group**.

![CodeDeploy Setup 4](screenshots/CD07.png)

   - [ ] You should see a confirmation message and the details for the Deployment group just created. Click **Create deployment**.

![CodeDeploy Setup 4](screenshots/CD08.png)

  7. **Create a Deployment**. Now that we have the application and a group configured we are ready to create our deployment. Verify you have the correct Deployment group selected then choose **My application is stored in GitHub** option as *Revision type*. Then you need to enter the GitHub account where is the application you are going to deploy. *To connect to a GitHub account for the first time, type an alias for the account, and then choose Connect to GitHub.*

    Go to your GitHub account and get the **Full Path name** and **Commit ID** you want to deploy.

  - [ ] Repository Full name.

![CodeDeploy Setup 4](screenshots/CD09-01.png)

   - [ ] Click on **"commits"**.

![CodeDeploy Setup 4](screenshots/CD09-02.png)

   - [ ] Copy the *Commit ID* by clicking on the icon on the left of the Id.

![CodeDeploy Setup 4](screenshots/CD09-03.png)

   - [ ] At the en your screen on AWS Deployment settings should look like this.

![CodeDeploy Setup 4](screenshots/CD09.png)

   - [ ] Check option *"Don't fail the deployment to an instance if this lifecycle event on the instance fails"*, and choose *"Overwrite the content"* option.

![CodeDeploy Setup 4](screenshots/CD10.png)

   - [ ] Leave *"Disable rollback"* option unchecked.

  8. Finally, click **Create deployment** and you will see a confirmation message.

![CodeDeploy Setup 4](screenshots/CD11-1.png)

   - [ ] If process run successfully you should see a page like this.

![CodeDeploy Setup 4](screenshots/CD11-2.png)

   - [ ] Now you can navigate to your instance url and verify that your application was deployed correctly.

![CodeDeploy Setup 4](screenshots/CD12.png)

## Troubleshooting

During Deployment things could go wrong, fortunately AWS gives pretty good hints about the possible error causes.

  1. After a failed Deployment you can check the events by clicking on *View events* link on **Deployment lifecycle events** section.

![CodeDeploy Setup 4](screenshots/CD13-1.png)

  2. Event list will show you the source of the error. For this particular example we can see that an error occurred during the package Installation. The next step is click on the UnknownError link to view the detail of this error.

![CodeDeploy Setup 4](screenshots/CD13-2.png)

  3. **Event Details Message** describes the cause of the error.

![CodeDeploy Setup 4](screenshots/CD13-3.png)

The most common causes of error during a Deployment process are:

 - Troubles finding the built artifact or war file to deploy. Mostly because in our GitHub repositories we don't push targets directories with war files.
 - Missing Permissions on AWS Service Roles, remember that at least a CodeDeploy Service Role needs to be configured.
