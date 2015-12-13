# Developers receive Benefits by using the Visual Studio Team Services

Visual Studio Team Services is a cloud-based ALM solutions.
Visual Studio Team Services offers the solutions required for all of the steps of software development.
If you use the Visual Studio Team Services, you can get for free the following benefits. Moreover, you can access from anywhere in the world.

* Planning and tracking of project, tracking of issues
    * Capture, prioritize, and track work with backlogs and customizable Kanban boards.
    * Work items link directly to code to ensure transparency.
* Management of source code
    * Store and collaborate on code with unlimited private repositories.
    * Use Git for distributed version control to maximize collaboration.
* Automated build, automated testing, automated deployment
    * Catch quality issues early with continuous integration (CI) builds that compile and test your application automatically after any code change.
    * Use continuous deployment to automatically deploy applications that pass tests.
* You can collaborate with team members
* Cloud-based load testing

Let me show you how to get started.

## Create a team project on Visual Studio Team Services

1. Sign in to [Visual Studio Team Services](https://www.visualstudio.com/).
2. Click **New**.  
![Create a team project on Visual Studio Team Services 1](../images/developers-receive-benefits-by-using-vsts/image001.png)
3. Enter a name for the project in the **Project name** box.  
Select a **Process template**.  
Select **Git** from the **Version control** drop-down menu, and then click **Create project**.  
In a short time, typically less than a minute, Visual Studio Team Services finishes creating the new team project.  
![Create a team project on Visual Studio Team Services 2](../images/developers-receive-benefits-by-using-vsts/image002.png)
4. Click **Navigate to project**.

## Create work items

1. Click **WORK**.  
![Create work items 1](../images/developers-receive-benefits-by-using-vsts/image003.png)
2. Click **+ New item**, then click **Product Backlog Item**.  
![Create work items 2](../images/developers-receive-benefits-by-using-vsts/image004.png)
3. Enter *As a deeveloper, I want to get Visual Studio Team Services's benefits*.
4. Click **…**, then click **+ Add task**.  
![Create work items 3](../images/developers-receive-benefits-by-using-vsts/image005.png)  
![Create work items 4](../images/developers-receive-benefits-by-using-vsts/image006.png)
5. Enter *Create a build definition*, then enter *Management of source code*.
6. Click **Create a build definition**, then note the task number.

Tip: "As a deeveloper, …" is NOT a User Story. Here I use this description as a sample.

## Create a build definition

1. Click **BUILD**.
2. Click **+**, and then click **Empty** to start with an empty definition, click **Next**.  
![Create a build definition 1](../images/developers-receive-benefits-by-using-vsts/image007.png)  
![Create a build definition 2](../images/developers-receive-benefits-by-using-vsts/image008.png)
3. Check the **Continuous integration : build each check-in**, and then click **Create**.  
![Create a build definition 3](../images/developers-receive-benefits-by-using-vsts/image009.png)
4. Click **+ Add build step…**.  
![Create a build definition 4](../images/developers-receive-benefits-by-using-vsts/image010.png)
5. Click **Package**, then click **npm's** **Add**.  
![Create a build definition 5](../images/developers-receive-benefits-by-using-vsts/image011.png)
6. Click **Build**, then click **gulp's** **Add**.  
![Create a build definition 6](../images/developers-receive-benefits-by-using-vsts/image012.png)
7. Click **Test**, then click **Publish Test Results's** **Add**.  
![Create a build definition 7](../images/developers-receive-benefits-by-using-vsts/image013.png)
8. Click **Deploy**, then click **Azure Web App Deployment's** **Add**, and then click **Close**.  
![Create a build definition 8](../images/developers-receive-benefits-by-using-vsts/image014.png)
9. Click **Publish Test Results**.
10. Enter *test-results.xml* in the **Test Results Files** box.  
![Create a build definition 9](../images/developers-receive-benefits-by-using-vsts/image015.png)
11. Click **Azure Web App Deployment**.
12. Select **Azure Subscription**.  
Make sure the subscription you want to use is selected. If a subscription is not available, then add a service endpoint:
  1. Click **Manage**.  
  ![Create a build definition 10](../images/developers-receive-benefits-by-using-vsts/image016.png)
  2. Click **New Service Endpoint**, and then click **Azure**.  
  ![Create a build definition 11](../images/developers-receive-benefits-by-using-vsts/image017.png)
  3. On the Add New Azure Connection dialog box:
      1. Select **Certificate Base**.
      2. Enter the name in the **Connection Name** box.
      3. Click this [link](https://go.microsoft.com/fwlink/?LinkId=254432) to download your publishsettings xml file and then open the file.
      4. Copy the ID and Name, ManagementCertificate from the file and paste them into the Add New Azure Connection dialog.  
      ![Create a build definition 12](../images/developers-receive-benefits-by-using-vsts/image018.png)
      5. Click **OK**.
13. Enter the name in the **Web App Name** box.  
Tip: The name you enter must be unique or the name of an Azure Web App you have already created. Azure will create the Web App for you and add it to your subscription if it does not already exist.
14. Enter *_package/package.zip* in the **Web Deploy Packagee**.
15. Click **Save**.  
![Create a build definition 13](../images/developers-receive-benefits-by-using-vsts/image019.png)
16. Enter a name for the build definition in the **Name** box, and then click **OK**.

## Upload your application

1. Install **Git** if you haven't already done so.  
For installation instructions for your platform, see the [Git download page](http://git-scm.com/download).
2. Run the following command. Download my simple Node.js application:
    $ git clone https://github.com/changeworld/hello-world-nodejs-express.git
3. Add a Git remote for pushing updates to the Visual Studio Team Services that you cloned previously, by using the following command:
    $ cd hello-world-nodejs-express
    $ git remote add azure https://{your_account}.visualstudio.com/DefaultCollection/_git/{your_team_project}
4. Open the *hello-world-nodejs-express/server.js* file in a text editor, and add empty line.
5. Use the following commands to add files to the repository:
    $ git add .
    $ git commit -m "Management of source code #task2"
6. Push to Azure by using the following command:
    $ git push azure master
7. Open your team project in your web browser.
8. Click **BUILD**.
9. After a successful build, click build number and check your site: http://{your web app name}.azurewebsites.net  
![Upload your application 2](../images/developers-receive-benefits-by-using-vsts/image021.png)  
![Upload your application 3](../images/developers-receive-benefits-by-using-vsts/image022.png)  

## Publish changes to your application

1. Open the *hello-world-nodejs-express/routes/index.js* file in a text editor, and change 'Hello, world!' to 'Hello, Azure!'.
2. Save the file.
3. Publish to Azure by using the following command:
    $ git add .
    $ git commit -m "Modify Hello World -> Hello Azure"
    $ git push azure master
4. Open your team project in your web browser.
5. Click **BUILD**.
6. After a successful build, refresh the browser window that you navigated to the web app's URL. A browser displaying the 'Hello, Azure!' message.  
![Upload your application 1](../images/developers-receive-benefits-by-using-vsts/image023.png)  
![Upload your application 2](../images/developers-receive-benefits-by-using-vsts/image024.png)

Enjoy your development, have fun ;-)
