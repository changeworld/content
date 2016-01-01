# シンプルな Node.js アプリケーションを作成し、Visual Studio Online を使用して Azure App Service の Web アプリにデプロイする方法

このチュートリアルでは、シンプルな [Node.js](http://nodejs.org) アプリケーションを作成し、[Visual Studio Online](https://www.visualstudio.com/) を使用して [Azure App Service](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-value-prop-what-is/) の [Web アプリ](https://azure.microsoft.com/ja-jp/documentation/articles/app-service-web-overview/)にデプロイする方法について説明します。このチュートリアルの手順は、Node.js を実行できる任意のオペレーティング システムで使用できます。

学習内容:

* Azure プレビュー ポータルを使用して Azure App Service で Web アプリを作成する方法
* Node.js アプリケーションを Visual Studio Online を使用して Web アプリにデプロイする方法

この手順を最後まで行うと、ブラウザーに "hello world" という短い文字列が出力されます。

![A browser displaying the 'Hello World' message.](https://lh4.googleusercontent.com/-DGNFXXFbkaA/ViTJC8lNWSI/AAAAAAAABuA/xxEDVobJMLw/w2048-h350-no/image151018-21.png)

全体像としては以下のようになります。

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

## Visual Studio Onlineのチームプロジェクトの作成とビルド定義の作成

要求・要件の変更管理やタスクの変更管理、バグのトラッキングといった課題管理システム(ITS)、ソースコードの管理のためのバージョンコントロールシステム(VCS)、継続的インテグレーション(CI)などの機能をすべて持っているVisual Studio Onlineにチームプロジェクトを作成します。
チームプロジェクトを作成後、ビルド定義を作成し、継続的インテグレーションと継続的デプロイを実現する準備をします。

1. [Visual Studio Online](https://www.visualstudio.com/)のページからサインインします。
2. **New**をクリックします。
3. **Project name**にこのプロジェクトの名前を入力し、**Process template**、**Version control**を選択します。**Version control**はGitを選択してください。**Create project**をクリックします。  
![Create a team project on Visual Studio Online 1](https://lh4.googleusercontent.com/-7w5nPtL8G60/ViTJC4aKpnI/AAAAAAAABuA/Qo5sWVQPTf8/w2048-h1344-no/image151018-09.png)  
1分程経つとVisual Studio Onlineがチーム プロジェクトの作成を終え、表示が切り替わります。
4. **Navigate to project**をクリックします。  
![Create a team project on Visual Studio Online 2](https://lh4.googleusercontent.com/-7cCyTP9bkew/ViTJC9hGXCI/AAAAAAAABuA/1ryWFKviATc/w1400-h1240-no/image151018-10.png)
5. ビルド定義を作成するため、**BUILD**をクリックします。  
![Create a Build Definition 1](https://lh4.googleusercontent.com/-fLAjAC3vH7g/ViTJC5_mdQI/AAAAAAAABuA/gRmZle-J-Zw/w1800-h1288-no/image151018-11.png)
6. **+**をクリックします。  
今回はNode.jsのため、Visual StudioやXamarin、Xcodeではないので、**Empty**をクリックし、空のテンプレートを作成します。  
その後、**OK**をクリックします。  
![Create a Build Definition 2](https://lh3.googleusercontent.com/-6Mk0Sndae-A/ViTJC6hXcoI/AAAAAAAABuA/2EaieFtnrsM/w1856-h1422-no/image151018-12.png)
7. **+ Add build step…**をクリック後、**Utility**をクリックします。
8. **Command Line**の横にある**Add**を2回クリックし、**Close**をクリックします。  
![Create a Build Definition 3](https://lh5.googleusercontent.com/-lVmcgGTSoOA/ViTJC6NHf8I/AAAAAAAABuA/hwA8DwiHBao/w2048-h1352-no/image151018-13.png)
9. 1つ目の**Command Line**をクリックします。
10. **Tool**に*git*を入力します。  
**Arguments**に**remote add azure https://{user name}:{password}@{your new web app}.scm.azurewebsites.net:443/{your new web app}.git**を入力します。  
e.g. remote add azure https://[username]:[password]@[sitename].scm.azurewebsites.net:443/[sitename].git  
![Create a Build Definition 4](https://lh3.googleusercontent.com/-RnMiTePopIY/ViTJC6SindI/AAAAAAAABuA/OD7yoXXeAdQ/w2048-h900-no/image151018-14.png)
11. 2つ目の**Command Line**をクリックします。
12. **Tool**に*git*を入力します。  
**Arguments**に**push azure master**を入力します。  
13. **Triggers**をクリックします。  
![Create a Build Definition 5](https://lh3.googleusercontent.com/-am3txWmBKgY/ViTJCy0pbII/AAAAAAAABuA/5X2KFgy3Jas/w2048-h902-no/image151018-15.png)
14. **Continuous integration (CI)**にチェックをし、**Save**をクリックします。  
![Create a Build Definition 6](https://lh5.googleusercontent.com/-sdKZknViZYw/ViTJCwC7U7I/AAAAAAAABuA/BIntiP7VDS8/w2048-h924-no/image151018-16.png)
15. このbuild definitionの名前を**Name**に入力し、**OK**をクリックします。  
![Create a Build Definition 7](https://lh5.googleusercontent.com/-AtuY3U8g7IM/ViTJCzm28sI/AAAAAAAABuA/JLU4Uj9Q12I/w2048-h980-no/image151018-17.png)

これで継続的インテグレーションと継続的デプロイの準備が整いました。

## アプリケーションを発行する

すべての準備が整ったため、Node.jsアプリケーションをVisual Studio OnlineにGitでpushし、継続的インテグレーションと継続的デプロイが行われることを確認します。

1. **Git**をインストールしていない場合は、Gitをインストールする必要があります。
手順は[Git download page](http://git-scm.com/download)を参照してください。
2. コマンド ラインから、Node.jsアプリケーションのある*helloworld*ディレクトリに移動し、以下のコマンドでローカルのGitリポジトリの初期化を実行します。
    $ git init
3. 以下のコマンドを実行し、ファイルをリポジトリに追加します。
    $ git add .
    $ git commit -m "Initial commit"
4. 以下のコマンドを実行し、先程作成したリポジトリをVisual Studio Onlineに反映するために、remoteを追加します。
    $ git remote add azure https://{your_account}.visualstudio.com/DefaultCollection/_git/{your_team_project}
5. 以下のコマンドを実行し、ローカルのリポジトリをVisual Studio Onlineに反映します。
    $ git push azure master
6. Web ブラウザーでチーム プロジェクトを開きます。
7. **BUILD**をクリックします。  
![Publish your application 1](https://lh3.googleusercontent.com/-wC0DL-cmz64/ViTJCxWB_jI/AAAAAAAABuA/qlDBAqJv5RY/w2048-h944-no/image151018-18.png)
8. ビルド中のため、**Queued**をクリックし、確認します。  
![Publish your application 2](https://lh6.googleusercontent.com/-DEPlbTU4EBU/ViTJC-2FpdI/AAAAAAAABuA/OGxF7Wp5cXg/w2048-h688-no/image151018-19.png)
9. ビルドが終わると**Queued**から消えるので、**Completed**をクリックします。  
![Publish your application 3](https://lh3.googleusercontent.com/-tK-nzdGowZE/ViTJC_2IYsI/AAAAAAAABuA/t7oOqBk5HV8/w2048-h696-no/image151018-20.png)
10. デプロイ結果を確認するため、あなたのサイト: http://{your new web app}.azurewebsites.net をWeb ブラウザーで確認します。
![Publish your application 4](https://lh4.googleusercontent.com/-DGNFXXFbkaA/ViTJC8lNWSI/AAAAAAAABuA/xxEDVobJMLw/w2048-h350-no/image151018-21.png)

## アプリケーションへの変更を発行する

1. *server.js*を開き、'Hello World\n' を 'Hello Azure\n'に変更します。
2. ファイルを保存します。
3. **helloworld**フォルダで、以下のコマンドをコマンドラインから実行します。
    $ git add .
    $ git commit -m "Modify Hello World -> Hello Azure"
    $ git push azure master
4. Wevアプリのページのウィンドウを更新すると、'Hello Azure'というメッセージが表示されます。