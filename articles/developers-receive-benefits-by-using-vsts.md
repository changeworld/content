# Developers receive Benefits by using the Visual Studio Team Services

Visual Studio Team Services is a cloud-based ALM solutions.
Visual Studio Team Services offers the solutions required for all of the steps of software development.
If you use the Visual Studio Team Services, you can get for free the following benefits. Moreover, you can access from anywhere in the world.

* Planning and tracking of project, tracking of issues
  * Capture, prioritize, and track work with backlogs and
customizable Kanban boards.
  * Work items link directly to code to ensure transparency.
* Management of source code
  * Store and collaborate on code with unlimited private repositories.
  * Use Git for distributed version control to maximize collaboration.
* Automated build, automated testing, automatic deployment
  * Catch quality issues early with continuous integration (CI)
builds that compile and test your application automatically after any
code change.
  * Use continuous deployment to automatically deploy applications
that pass tests.
* You can collaborate with team members
* Cloud-based load test

let me show you how to get started.

## Create a team project on Visual Studio Team Services

1. Sign in to [Visual Studio Online](https://www.visualstudio.com/).
2. Click **New**.
3. Enter a name for the project in the **Project name** box.  
Select a **Process template**.  
Select **Git** from the **Version control** drop-down menu, and then Click **Create project**.  
In a short time, typically less than a minute, Visual Studio Team Services finishes creating the new team project.
4. Click **Navigate to project**.

## Create a Work Items
## Create a Build Definition

1. Click **BUILD**.
2. Click **+**, and then click **Empty** to start with an empty definition, click **Next**.
3. Check the **Continuous integration : build each check-in**, and then click **Create**.
4. Click **+ Add build step…**, and then click **Package**.
5. Click **npm's** **Add**, and then click **Build**.
6. Click **gulp's** **Add**, and then click **Test**.
7. Click **Publish Test Results's** **Add**, and then click **Deploy**.
8. Click **Azure Web App Deployment's** **Add**, and then click **Close**.
9. Click **Publish Test Results**.
10. Enter *test-results.xml* in the **Test Results Files** box.
11. Click **Azure Web App Deployment**.
12. Select **Azure Subscription**.  
Make sure the subscription you want to use is selected. If a subscription is not available, then add a service endpoint:
  1. Click **Manage**.
  2. Click **New Service Endpoint**, and then click **Azure**.
  3. On the Add New Azure Connection dialog box:
      1. Select **Certificate Base**.
      2. Enter the name in the **Connection Name** box.
      3. Click this [link](https://go.microsoft.com/fwlink/?LinkId=254432) to download your publishsettings xml file and then open the file.
      4. Copy the ID and Name, ManagementCertificate from the file and paste them into the Add New Azure Connection dialog.
13. Enter the name in the **Web App Name** box.  
Tip: The name you enter must be unique or the name of an Azure Web App you have already created. Azure will create the Web App for you and add it to your subscription if it does not already exist.
14. Enter *$(Build.StagingDirectory)/package.zip* in the **Web Deploy Packagee**
15. Click **Save**.
16. Enter a name for the build definition in the **Name** box, and then click **OK**.

## Upload your application

1. Install **Git** if you haven't already done so.  
For installation instructions for your platform, see the [Git download page](http://git-scm.com/download).
2. Use the following command. Download my simple Node.js application:
    $ git clone https://github.com/changeworld/hello-world-nodejs-express.git
3. Add a Git remote for pushing updates to the Visual Studio Team Services that you cloned previously, by using the following command:
    $ git remote add azure https://{your_account}.visualstudio.com/DefaultCollection/_git/{your_team_project}
4. Push to Azure by using the following command:
    $ git push azure master
5. Open your team project in your web browser.
6. Click **BUILD**.
7. After a successful build, check your site: http://{your new web app}.azurewebsites.net

## Publish changes to your application
## Next Step
