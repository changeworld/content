# How to create a simple Node.js application and deploy it to a web app in Azure App Service by using Visual Studio Online

This tutorial shows how to create a simple [Node.js](http://nodejs.org) application and deploy it to a [web app](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-web-overview/) in [Azure App Service](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-value-prop-what-is/) by using [Visual Studio Online](https://www.visualstudio.com/). The instructions in this tutorial can be followed on any operating system that is capable of running Node.js.

You'll learn:

* How to create a web app in Azure App Service by using the Azure preview portal.
* How to deploy a Node.js application to the web app using Visual Studio Online.

The completed application writes a short "hello world" string to the browser.

![A browser displaying the 'Hello World' message.](https://lh4.googleusercontent.com/-DGNFXXFbkaA/ViTJC8lNWSI/AAAAAAAABuA/xxEDVobJMLw/w2048-h350-no/image151018-21.png)

The overall picture will look like the following diagram.

![The overall picture.](https://lh5.googleusercontent.com/-g81UGpL3vrk/ViTJC1g4PyI/AAAAAAAABt8/fG3m-9Odfzg/w1400-h646-no/image151018-01.png)

## Web Appsの作成とGitでのデプロイの有効化

Azure App ServiceにWeb Appsを作成し、Gitでのデプロイの有効化をするために以下を行います。

1. [Azure preview portal](https://portal.azure.com)にサインインします。
2. ポータルの左上にある**+ New**アイコンをクリックします。
3. **Web + Mobile**をクリックし、**Web App**をクリックします。
4. **Web app**にWebサイトの名前(URL)を入力します。
5. **Subscription**を選択します。
6. **Resource Group**を選択するか、新しく作成します。
7. **App Service plan/Location**を選択するか、新しく作成します。新しいプランを作成する場合は、価格レベル、および場所などのオプションを選択します。
8. **Create**をクリックします。作成が終わるまでしばらく待ちます。  
![Create a web app](https://lh6.googleusercontent.com/-Xpiene9r-WA/ViTJCywRCTI/AAAAAAAABuA/MQT2ClJihzk/w2030-h1422-no/image151018-02.png)  
9. **Web Apps > {your new web app}**をクリックします。  
![Enable Git publishing 1](https://lh3.googleusercontent.com/-jZy_TwAKBeU/ViTJC2VXiqI/AAAAAAAABt8/XZChBYssHA8/w2048-h1138-no/image151018-03.png)
10. **Continuous Deployment**をクリックし、**Choose Source**をクリックします。
11. **Local Git Repository**をクリックし、**OK**をクリックします。  
![Enable Git publishing 2](https://lh6.googleusercontent.com/-YQKxYgpGktc/ViTJC3q4M4I/AAAAAAAABt8/5uvQspD4wxU/w2048-h1276-no/image151018-04.png)
12. **Deployment credentials**をクリックします。
13. [FTP/デプロイ ユーザー名]、[パスワード]、[パスワードの確認]に値を入力後、**Save**をクリックします。  
![Enable Git publishing 3](https://lh4.googleusercontent.com/-aIUJi0gfGgc/ViTJC6pUD0I/AAAAAAAABt8/o18KA3cTiJo/w2048-h1322-no/image151018-05.png)
14. **Web Apps > {your new web app}**をクリックします。  
[Git クローン URL]の欄にGitでデプロイするURLが表示されますので、コピーします。  
![Enable Git publishing 4](https://lh3.googleusercontent.com/-B1pZOVUChXg/ViTJCwMoBiI/AAAAAAAABt8/TEolMFSFgZU/w1382-h1422-no/image151018-06.png)
15. **URL**をクリックします。
現在のWeb Appsの状態を確認するために、[URL]の欄のURLをクリックします。
![Enable Git publishing 5](https://lh4.googleusercontent.com/-1qbpll_dUuk/ViTJCxLpIaI/AAAAAAAABt8/iZRuhbCWISw/w1794-h1422-no/image151018-07.png)

## シンプルなNode.jsアプリケーションの作成

今回は説明のためにシンプルなNode.jsアプリケーションの作成します。
[nodejs.org](https://nodejs.org/en/)にある’Hello World’を出力する[server.js](https://nodejs.org/en/about/)を使用します。
nodejs.orgの例からAzure Web Appsで実行する際のリッスンするポートとして**process.env.PORT**を追加しています。

1. *helloworld*という名のディレクトリを作成します。
2. テキスト エディターを使い、*helloworld*ディレクトリに*server.js*を作成します。
3. *server.js*に以下のコードをコピー後、保存します。
    var http = require('http');
    var port = process.env.PORT || 1337;
    http.createServer(function (req, res) {
      res.writeHead(200, {'Content-Type': 'text/plain'});
      res.end('Hello World\n');
    }).listen(port);
4. コマンド ラインから以下のコマンドを実行し、ローカルでNode.jsアプリケーションを起動させます。
    $ node server.js
5. Web ブラウザーを開き、 http://localhost:1337 にアクセスし、以下のスクリーンショットのようになっていることを確認します。  
![Create a simple Node.js application](https://lh3.googleusercontent.com/-BUKMgxa2Fbk/ViTJC9w0EQI/AAAAAAAABuA/E7ZL5YbdSpg/w2048-h308-no/image151018-08.png)

## Create a team project on Visual Studio Online and create a Build Definition

1. Sign in to [Visual Studio Online](https://www.visualstudio.com/).
2. Click **New**.
3. Enter a name for the project in the **Project name** box.  
Select a **Process template**.  
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
15. Enter a name for the build definition in the **Name** box, and then click **OK**.  
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

## アプリへの変更を発行する

1. *server.js*を開き、'Hello World\n' を 'Hello Azure\n'に変更します。
2. ファイルを保存します。
3. **helloworld**フォルダで、以下のコマンドをコマンドラインから実行します。
    $ git add .
    $ git commit -m "Modify Hello World -> Hello Azure"
    $ git push azure master
4. Wevアプリのページのウィンドウを更新すると、'Hello Azure'というメッセージが表示されます。