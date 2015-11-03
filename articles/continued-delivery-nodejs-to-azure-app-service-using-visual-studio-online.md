# How to create a simple Node.js application and deploy it to a web app in Azure App Service by using Visual Studio Online

This tutorial shows how to create a simple [Node.js](http://nodejs.org) application and deploy it to a [web app](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-web-overview/) in [Azure App Service](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-value-prop-what-is/) by using [Visual Studio Online](https://www.visualstudio.com/). The instructions in this tutorial can be followed on any operating system that is capable of running Node.js.

You'll learn:

* How to create a web app in Azure App Service by using the Azure preview portal.
* How to deploy a Node.js application to the web app by using to the Visual Studio Online.

The completed application writes a short "hello world" string to the browser.

![A browser displaying the 'Hello World' message.](https://lh4.googleusercontent.com/-DGNFXXFbkaA/ViTJC8lNWSI/AAAAAAAABuA/xxEDVobJMLw/w2048-h350-no/image151018-21.png)

![A perspective.](https://lh5.googleusercontent.com/-g81UGpL3vrk/ViTJC1g4PyI/AAAAAAAABt8/fG3m-9Odfzg/w1400-h646-no/image151018-01.png)

## Create a web app and enable Git publishing

Follow these steps to create a web app in Azure App Service and enable Git publishing.

1. Sign in to the [Azure preview portal](https://portal.azure.com).
2. Click the **+ 新規** icon on the top left of the portal.
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
To publish, you'll push to a remote Git repository. The URL for the repository is listed under **GIT クローン URL**. You'll use this URL later in the tutorial.  
![Enable Git publishing 4](https://lh3.googleusercontent.com/-B1pZOVUChXg/ViTJCwMoBiI/AAAAAAAABt8/TEolMFSFgZU/w1382-h1422-no/image151018-06.png)
