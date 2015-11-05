# How to create a simple Node.js application and deploy it to a web app in Azure App Service by using Visual Studio Online

This tutorial shows how to create a simple [Node.js](http://nodejs.org) application and deploy it to a [web app](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-web-overview/) in [Azure App Service](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-value-prop-what-is/) by using [Visual Studio Online](https://www.visualstudio.com/). The instructions in this tutorial can be followed on any operating system that is capable of running Node.js.

You'll learn:

* How to create a web app in Azure App Service by using the Azure preview portal.
* How to deploy a Node.js application to the web app by using to the Visual Studio Online.

The completed application writes a short "hello world" string to the browser.

![A browser displaying the 'Hello World' message.](https://lh4.googleusercontent.com/-DGNFXXFbkaA/ViTJC8lNWSI/AAAAAAAABuA/xxEDVobJMLw/w2048-h350-no/image151018-21.png)

The overall picture would look like the following screenshot.

![The overall picture.](https://lh5.googleusercontent.com/-g81UGpL3vrk/ViTJC1g4PyI/AAAAAAAABt8/fG3m-9Odfzg/w1400-h646-no/image151018-01.png)

## Create a web app and enable Git publishing

Follow these steps to create a web app in Azure App Service and enable Git publishing.

1. Sign in to the [Azure preview portal](https://portal.azure.com).
2. Click **+ 新規** icon on the top left of the portal.
3. Click **Web + モバイル**, and then click **Web Apps**.
4. Enter a name for the web app in the **Web アプリ** box.  
This name must be unique in the azurewebsites.net domain because the URL of the web app will be {name}.azurewebsites.net. If the name you enter isn't unique, a red exclamation mark appears in the text box.
5. Select a **サブスクリプション**.
6. Select a **リソース グループ** or create a new one.  
For more information about resource groups, see [Using the Azure Preview Portal to manage your Azure resources](https://azure.microsoft.com/en-us/documentation/articles/resource-group-portal/).
7. Select an **App Service プラン/場所** or create a new one.  
For more information about App Service plans, see [Azure App Service plans in-depth overview](https://azure.microsoft.com/en-us/documentation/articles/azure-web-sites-web-hosting-plans-in-depth-overview/)
8. Click **作成**.  
![Create a web app](https://lh6.googleusercontent.com/-Xpiene9r-WA/ViTJCywRCTI/AAAAAAAABuA/MQT2ClJihzk/w2030-h1422-no/image151018-02.png)  
In a short time, typically less than a minute, Azure finishes creating the new web app.
9. Click **Web Apps > {your new web app}**.  
![Enable Git publishing 1](https://lh3.googleusercontent.com/-jZy_TwAKBeU/ViTJC2VXiqI/AAAAAAAABt8/XZChBYssHA8/w2048-h1138-no/image151018-03.png)
10. Click **継続的なデプロイ**, and then click **ソースの選択**.
11. Click **ローカル Git リポジトリ**, and then click **OK**.  
![Enable Git publishing 2](https://lh6.googleusercontent.com/-YQKxYgpGktc/ViTJC3q4M4I/AAAAAAAABt8/5uvQspD4wxU/w2048-h1276-no/image151018-04.png)
12. Click **デプロイ資格情報**.
13. Set up deployment credentials if you haven't already done so.  
Create a user name and password, and then click **保存**.  
![Enable Git publishing 3](https://lh4.googleusercontent.com/-aIUJi0gfGgc/ViTJC6pUD0I/AAAAAAAABt8/o18KA3cTiJo/w2048-h1322-no/image151018-05.png)
14. Click **Web Apps > {your new web app}**.  
To publish, you'll push to a remote Git repository. The URL for the repository is listed under **Git クローン URL**. You'll use this URL later in the tutorial.  
![Enable Git publishing 4](https://lh3.googleusercontent.com/-B1pZOVUChXg/ViTJCwMoBiI/AAAAAAAABt8/TEolMFSFgZU/w1382-h1422-no/image151018-06.png)
15. Click **URL**.  
A webpage that displays "This web app has been successfully created" appears, as shown in the following screenshot.  
![Enable Git publishing 5](https://lh4.googleusercontent.com/-1qbpll_dUuk/ViTJCxLpIaI/AAAAAAAABt8/iZRuhbCWISw/w1794-h1422-no/image151018-07.png)

## Create a simple Node.js application

In this section, you'll create a [server.js](https://nodejs.org/en/about/) file that contains a slightly modified version of the 'Hello World' example from [nodejs.org](https://nodejs.org/en/). The code adds **process.env.PORT** as the port to listen on when running in an Azure App Service.

1. Create a directory named **helloworld**.
2. Use a text editor to create a new file named **server.js** in the **helloworld** directory.
3. Copy the following code into the **server.js** file, and then save the file:  
    var http = require('http');
    var port = process.env.PORT || 1337;
    http.createServer(function (req, res) {
      res.writeHead(200, {'Content-Type': 'text/plain'});
      res.end('Hello World\n');
    }).listen(port);
4. Open the command line, and use the following command to start the web app locally.  
    $ node server.js
5. Open your web browser and navigate to http://localhost:1337.  
A webpage that displays "Hello World" appears, as shown in the following screenshot.  
![Create a simple Node.js application](https://lh3.googleusercontent.com/-BUKMgxa2Fbk/ViTJC9w0EQI/AAAAAAAABuA/E7ZL5YbdSpg/w2048-h308-no/image151018-08.png)

## Create a team project on Visual Studio Online and create a Build Definition

1. Sign in to the [Visual Studio Online](https://www.visualstudio.com/).
2. Click **New**.
3. Enter a name for the project in the **Project name** box.  
Select an **Process template**.  
Select **Git** from the **Version control** drop-down menu, and then Click **Create project**.  
![Create a team project on Visual Studio Online 1](https://lh4.googleusercontent.com/-7w5nPtL8G60/ViTJC4aKpnI/AAAAAAAABuA/Qo5sWVQPTf8/w2048-h1344-no/image151018-09.png)  
In a short time, typically less than a minute, Visual Studio Online finishes creating the new team project.
4. Click **Navigate to project**.  
![Create a team project on Visual Studio Online 2](https://lh4.googleusercontent.com/-7cCyTP9bkew/ViTJC9hGXCI/AAAAAAAABuA/1ryWFKviATc/w1400-h1240-no/image151018-10.png)
5. Click **BUILD**.  
![Create a Build Definition 1](https://lh4.googleusercontent.com/-fLAjAC3vH7g/ViTJC5_mdQI/AAAAAAAABuA/gRmZle-J-Zw/w1800-h1288-no/image151018-11.png)
6. Click **+**, and then click **Empty** to start with an empty definition, click **OK**.  
![Create a Build Definition 2](https://lh3.googleusercontent.com/-6Mk0Sndae-A/ViTJC6hXcoI/AAAAAAAABuA/2EaieFtnrsM/w1856-h1422-no/image151018-12.png)
7. Click **+ Add build step…**, and then click **Utility**.
8. Click **Command Line's** **Add** twice, and then click **Close**.  
![Create a Build Definition 3](https://lh5.googleusercontent.com/-lVmcgGTSoOA/ViTJC6NHf8I/AAAAAAAABuA/hwA8DwiHBao/w2048-h1352-no/image151018-13.png)
9. Click 1st **Command Line**.
10. Enter **git** in the **Tool** box.  
Enter **remote add azure https://{user name}:{password}@{your new web app}.scm.azurewebsites.net:443/{your new web app}.git** in the **Arguments** box.  
![Create a Build Definition 4](https://lh3.googleusercontent.com/-RnMiTePopIY/ViTJC6SindI/AAAAAAAABuA/OD7yoXXeAdQ/w2048-h900-no/image151018-14.png)
11. Click 2nd **Command Line**.
12. Enter **git** in the **Tool** box.  
Enter **push azure master** in the **Arguments** box.
13. Click **Triggers**.  
![Create a Build Definition 5](https://lh3.googleusercontent.com/-am3txWmBKgY/ViTJCy0pbII/AAAAAAAABuA/5X2KFgy3Jas/w2048-h902-no/image151018-15.png)
14. Check the **Continuous integration (CI)**, and then click **Save**.  
![Create a Build Definition 6](https://lh5.googleusercontent.com/-sdKZknViZYw/ViTJCwC7U7I/AAAAAAAABuA/BIntiP7VDS8/w2048-h924-no/image151018-16.png)
15. Enter a name for the build eefinition in the **Name** box, and then click **OK**.  
![Create a Build Definition 7](https://lh5.googleusercontent.com/-AtuY3U8g7IM/ViTJCzm28sI/AAAAAAAABuA/JLU4Uj9Q12I/w2048-h980-no/image151018-17.png)

## Publish your application

1. Install **Git** if you haven't already done so.  
For installation instructions for your platform, see the [Git download page](http://git-scm.com/download).
2. From the command line, change directories to the **helloworld** directory and enter the following command to initialize a local Git repository.
    $ git init
3. Use the following commands to add files to the repository:
    $ git add .
    $ git commit -m "Initial commit"
4. Add a Git remote for pushing updates to the Visual Studio Online that you created previously, by using the following command:
    $ git remote add azure https://{your_account}.visualstudio.com/DefaultCollection/_git/{your_team_project}
5. Push your changes to Azure by using the following command:
    $ git push azure master
6. Open your team project in your web browser.
7. Click **BUILD**.  
![Publish your application 1](https://lh3.googleusercontent.com/-wC0DL-cmz64/ViTJCxWB_jI/AAAAAAAABuA/qlDBAqJv5RY/w2048-h944-no/image151018-18.png)
8. Click **Queued**.  
![Publish your application 2](https://lh6.googleusercontent.com/-DEPlbTU4EBU/ViTJC-2FpdI/AAAAAAAABuA/OGxF7Wp5cXg/w2048-h688-no/image151018-19.png)
9. After a successful build, click **Completed**.
![Publish your application 3](https://lh3.googleusercontent.com/-tK-nzdGowZE/ViTJC_2IYsI/AAAAAAAABuA/t7oOqBk5HV8/w2048-h696-no/image151018-20.png)
10. Check your site: http://{your new web app}.azurewebsites.net
![Publish your application 4](https://lh4.googleusercontent.com/-DGNFXXFbkaA/ViTJC8lNWSI/AAAAAAAABuA/xxEDVobJMLw/w2048-h350-no/image151018-21.png)

## Publish changes to your application

1. Open the **server.js** file in a text editor, and change 'Hello World\n' to 'Hello Azure\n'.
2. Save the file.
3. From the command line, change directories to the **helloworld** directory and run the following commands:
    $ git add .
    $ git commit -m "Modify Hello World -> Hello Azure"
    $ git push azure master
4. Refresh the browser window that you navigated to the web app's URL. A browser displaying the 'Hello Azure' message.
