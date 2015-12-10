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

## Visual Studio Team Servicesにチームプロジェクトを作成する

1. [Visual Studio Team Services](https://www.visualstudio.com/)にサインインします。
2. **New**をクリックします。  
![Create a team project on Visual Studio Team Services 1](https://lh3.googleusercontent.com/-ReuwtPz4lOM/Vmisc0MYdCI/AAAAAAAAB5U/ormPqPc-DRQ/s640-Ic42/image001.png)
3. **Project name**ボックスにチーム名を入力します。  
**Process template**を選択します。  
**Version control**から**Git**を選択し、**Create project**をクリックします。  
1分程待つと、Visual Studio Team Servicesが新しいチームプロジェクトの作成を終えます。  
![Create a team project on Visual Studio Team Services 2](https://lh3.googleusercontent.com/-EQf8-fCD4_s/Vmisc1lVH4I/AAAAAAAAB7I/Vyy0jK7QgEI/s640-Ic42/image002.png)
4. **Navigate to project**をクリックします。

## Work itemを作成する

1. **WORK**をクリックする。  
![Create work items 1](https://lh3.googleusercontent.com/-54nmXwTHK1E/VmiscmJoUjI/AAAAAAAAB4w/oh0Y3WjGFxI/s640-Ic42/image003.png)
2. **+ New item**をクリック後、**Product Backlog Item**をクリックする。  
![Create work items 2](https://lh3.googleusercontent.com/-CIQzn2puEfE/VmisdOdM5BI/AAAAAAAAB7M/j1ggFeOe2GE/s640-Ic42/image004.png)
3. *As a deeveloper, I want to get Visual Studio Team Services's benefits*と入力する。
4. **…**をクリック後、**+ Add task**をクリックする。  
![Create work items 3](https://lh3.googleusercontent.com/-Va-rbsaskXI/VmisdTaVw5I/AAAAAAAAB6I/va14EhT1ji4/s640-Ic42/image005.png)  
![Create work items 4](https://lh3.googleusercontent.com/-x92_rXABQns/VmisdVwu1FI/AAAAAAAAB48/x9xx3K0kNi0/s640-Ic42/image006.png)
5. *Create a build definition*を入力したらリターンキーを押下し、*Management of source code*を入力する。
6. **Create a build definition**をクリック後、番号をメモする。

Tip: "As a deeveloper, …"のような"開発者として…"は厳密にはユーザーストーリーではありません。ここでは説明のためのサンプルとしてこの記述を使っています。

## ビルド定義を作成する

1. **BUILD**をクリックする。
2. **+**をクリック後、**Empty**をクリックし、続けて**Next**をクリックする。  
![Create a build definition 1](https://lh3.googleusercontent.com/-qOPGt_YUKfk/VmisdvzlR5I/AAAAAAAAB7Q/Y6Iv3LVCyLE/s640-Ic42/image007.png)  
![Create a build definition 2](https://lh3.googleusercontent.com/-UnQtw7hoAXo/Vmisd2atxJI/AAAAAAAAB5M/p2U9aP-JpGc/s640-Ic42/image008.png)
3. **Continuous integration : build each check-in**をクリック後、**Create**をクリックする。  
![Create a build definition 3](https://lh3.googleusercontent.com/-uGUinxG1H38/Vmisd0KoysI/AAAAAAAAB5o/GIwULQ_wjSs/s640-Ic42/image009.png)
4. **+ Add build step…**をクリックする。  
![Create a build definition 4](https://lh3.googleusercontent.com/--pT6AmxnvlE/VmiseO0UJZI/AAAAAAAAB60/thqTUUI3Ygc/s640-Ic42/image010.png)
5. **Package**をクリック後、**npm**の**Add**をクリックする。  
![Create a build definition 5](https://lh3.googleusercontent.com/-mg4E7KIltXA/VmiseTzsk9I/AAAAAAAAB68/Kj8oifg3Plo/s640-Ic42/image011.png)
6. **Build**をクリック後、**gulp**の**Add**をクリックする。  
![Create a build definition 6](https://lh3.googleusercontent.com/-yJuKJYo4WjI/VmisejR6RkI/AAAAAAAAB5k/LIFCrcmo0F0/s640-Ic42/image012.png)
7. **Test**をクリック後、**Publish Test Results**の**Add**をクリックする。  
![Create a build definition 7](https://lh3.googleusercontent.com/-sYBD1QUkp3Y/VmisewX8zJI/AAAAAAAAB5w/931feG94WZg/s640-Ic42/image013.png)
8. **Deploy**をクリック後、**Azure Web App Deployment**の**Add**をクリックし、**Close**をクリックする。  
![Create a build definition 8](https://lh3.googleusercontent.com/-lhfer9KmhPE/VmisfBVLWFI/AAAAAAAAB6A/0akt1eAPh8I/s640-Ic42/image014.png)
9. **Publish Test Results**をクリックする。
10. **Test Results Files**に*test-results.xml*を入力する。  
![Create a build definition 9](https://lh3.googleusercontent.com/-r8K2AHXPeAc/VmisfLp2tgI/AAAAAAAAB58/4sC6aqC8WlA/s640-Ic42/image015.png)
11. **Azure Web App Deployment**をクリックする。
12. **Azure Subscription**を選択する。  
使用するサブスクリプションが選択されていることを確認し、サブスクリプションが使用できない場合は、以下の手順でサービスエンドポイントを追加する。
  1. **Manage**をクリックする。  
  ![Create a build definition 10](https://lh3.googleusercontent.com/-AjUWeFhYhcs/VmisfQL4NBI/AAAAAAAAB6w/Aow_NVnjddA/s640-Ic42/image016.png)
  2. **New Service Endpoint**をクリック後、**Azure**をクリックする。  
  ![Create a build definition 11](https://lh3.googleusercontent.com/-IYhV8uAPFtI/VmisgfvmswI/AAAAAAAAB6c/zlL4OTGhaxc/s640-Ic42/image017.png)
  3. Add New Azure Connectionダイアログボックスで:
      1. **Certificate Base**を選択する。
      2. **Connection Name**に名前を入力する。
      3. [ここ](https://go.microsoft.com/fwlink/?LinkId=254432)をクリックし、publishsettings xmlファイルをダウンロード後、ファイルを開く。
      4. 使用したいサブスクリプションのIDとName、ManagementCertificateの値をファイルからコピーし、それぞれAdd New Azure Connection dialogの項目にペーストする。  
      ![Create a build definition 12](https://lh3.googleusercontent.com/-Yi-NsbiKmh4/VmisgowbEtI/AAAAAAAAB6Y/lo7qrM0Wg6c/s640-Ic42/image018.png)
      5. **OK**をクリックする。
13. **Web App Name**にWeb Appの名前を入力する。  
Tip: ここであなたが入力した名前は一意か、既に作成済みのAzure Webアプリケーションの名前でなければならない。未作成の名前の場合、AzureはWebアプリケーションを作成し、サブスクリプションに追加する。
14. **Web Deploy Packagee**に*_package/package.zip*を入力する。
15. **Save**をクリックする。  
![Create a build definition 13](https://lh3.googleusercontent.com/-ytPyQVUuxic/VmisgiUYOHI/AAAAAAAAB6U/WZRO5PVdlwI/s640-Ic42/image019.png)
16. **Name**にビルド定義の名前を入力後、**OK**をクリックする。

## あなたのアプリケーションをアップロードする

1. あなたが**Git**をインストールしていない場合、**Git**をインストールする。  
使用しているプラットフォームのインストール手順については、[Git download page](http://git-scm.com/download)を参照する。
2. 私のシンプルなNode.jsアプリケーションをダウンロードするため、以下のコマンドを実行する:
    $ git clone https://github.com/changeworld/hello-world-nodejs-express.git
3. 以下のコマンドを使用して、先程クローンしたアプリケーションの更新をVisual Studio Team Servicesに反映するためにのGitのリモートを追加する:
    $ cd hello-world-nodejs-express
    $ git remote add azure https://{your_account}.visualstudio.com/DefaultCollection/_git/{your_team_project}
4. *hello-world-nodejs-express/server.js*ファイルをエディターで開き、空行を追加する。
5. 以下のコマンドを使用して、リポジトリにファイルを追加する:
    $ git add .
    $ git commit -m "Management of source code #{copy the task number}"
6. 以下のコマンドを使用して、Azureにpushする:
    $ git push azure master
7. あなたのチームプロジェクトをブラウザ上で開く。
8. **BUILD**をクリックする。
9. ビルド成功後、ビルド番号をクリックし、その後、あなたのWebサイト: http://{your web app name}.azurewebsites.net をチェックする。  
![Upload your application 1](https://lh3.googleusercontent.com/-Gtesh_MM0tA/VmishLC_EnI/AAAAAAAAB7E/tO6Q4rgcNSw/s640-Ic42/image021.png)  
![Upload your application 2](https://lh3.googleusercontent.com/-2jJU7iR63Vc/VmishU_HZuI/AAAAAAAAB6s/v683cG5R_8s/s640-Ic42/image022.png)

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
![Upload your application 1](https://lh3.googleusercontent.com/-j826snN-trg/VmishnAWyJI/AAAAAAAAB64/Oov-N4ENo-I/s640-Ic42/image023.png)  
![Upload your application 2](https://lh3.googleusercontent.com/-l8YCj91UY6s/Vmish5R2a3I/AAAAAAAAB7A/9hEQJsoUjug/s640-Ic42/image024.png)

Enjoy your development, have fun ;-)
