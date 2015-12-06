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
## Create a Work Items
## Create a Build Definition
## Upload your application

1. Install **Git** if you haven't already done so.  
For installation instructions for your platform, see the [Git download page](http://git-scm.com/download).
2. Use the following command. Download my simple Node.js application:
    $ git clone {git url}
3. Add a Git remote for pushing updates to the Visual Studio Team Services that you cloned previously, by using the following command:
    $ git remote add azure https://{your_account}.visualstudio.com/DefaultCollection/_git/{your_team_project}
4. Push to Azure by using the following command:
    $ git push azure master
5. Open your team project in your web browser.
6. Click **BUILD**.  
![Upload your application]()
7. After a successful build, check your site: http://{your new web app}.azurewebsites.net

## Publish changes to your application
## Next Step
