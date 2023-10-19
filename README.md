***
# 1.  Git とは
  
- **About / 利点**  
ソースコードやファイルの変更履歴を管理できる、分散型バージョン管理ができるシステムである。変更履歴が分かり、以前の状態に戻したり、思わぬ上書き保存を防止できることから、チームでスムーズに開発したり、個人での利用でも有効なシステムである。  

- **基本的な仕組み**  
変更履歴を順々に記録することができる。記録する際はメッセージをつけることができる。（いつ、誰が、何のために、何を変更したか、など）

- **基礎的な用語**  
リポジトリ：変更履歴を記録する場所のこと  
commit：個人リポジトリに変更履歴を記録すること  
push：共有リポジトリに変更を共有すること

- **基本的なワークフロー**  
① 変更したファイルを(git addで)ステージングエリアに追加する  
② (git commitで)ローカルリポジトリにコミットする  
③ (git pushで)リモート（共有）リポジトリにファイルをアップする

 
***

# 2.  GitHub とは  

- **About / 利点**  
GitHubは、Gitで管理しているソースコードをチームで共有するためのサービスであり、Gitリポジトリ（コード）のホスティングサービスである。さらに世界中の人々がコードを保存、公開できるソーシャルコーディングの場でもある。Github以外には、Bitbucketなどがある。

- **基本的なワークフロー**  
プルリクエストによるコラボレーションによる複数人開発：コードのレビュー、チームの開発がしやすい。他のチームのソフトウエアも見える。
また、ブランチ機能を使って複数人がコードの変更作業を同時で行い、履歴を保存することができる。分岐されたブランチは他の影響を受けないので、１つのコード（ソフトウエア）に対して複数人で同時にバグの修正や新しい機能追加を行うことができる。
  
  複数人での開発の基本的な流れとしては、以下である。    
① pullで共有から個人へ情報取得する  
② commitで個人の変更を記録する  
③ pushで変更を共有に登録する  
④ 個人ローカルの変更を共有(オリジナル)に反映させたい場合は、pullリクエストでオリジナルのオーナーに通知をする

***
# 3.  Markdown とは  

- **About / 利点**  
Markdownはメモ、ドキュメントを書くための記法の一つ。エンジニア、IT業界の人なら誰でも使えた方が良い記法である。  
HTMLよりも簡単で、文字や文章の装飾（CSS）を簡単に行うことができる。
Markdownのエディタは様々なものが存在し、Visual Studio Codeが有名である。Githubでも書くことができる。  
マークダウンで書いておけばいろんなPFで使えて、簡単に所望の見た目にすることができる。  

- **主なMarkdownによる装飾**  
① 見出しをつける（見出しの大きさも調整できる）  
② 箇条書き  
③ リンク挿入  
④ 改行、段落  
⑤ 引用  
⑥ 画像の挿入  
⑦ 文字の装飾(斜体、太字、訂正線)  
⑧ テーブル

***
# ４. 出題1~3を１つのテキストREADME.mdにして公開
[【リンク】GitHubの公開URL](https://github.com/omi-tamu/mau-j2n)

***
# ５. 出題1~4までの実現に必要となった作業をREADME.mdに追記

## - **gitとは**  
出題１で回答済みのため、ここではGitのWikipediaリンクを掲載する  
[wikipediaリンク（Git）](https://ja.wikipedia.org/wiki/Git)  

## - **gitインストール**  
Mac OSではデフォルトでインストールされているということを聞いたので、ターミナルにて `git ver`コマンドで確認したが  
```
xcode-select: note: No developer tools were found, requesting install.
If developer tools are located at a non-default location on disk, use `sudo xcode-select --switch path/to/Xcode.app` to specify the Xcode that you wish to use for command line developer tools, and cancel the installation dialog.
See `man xcode-select` for more details.
```
と表示されたのでインストールされていないと判断し、[gitの公式HP](https://git-scm.com/download/mac)からMac用のgitをインストールした。  
再度 `git ver`コマンドで確認し  
```
git version 2.39.3 (Apple Git-145)
```   
と出力されたので、正しくインストールされていることを確認した。  

## - **gitの使い方**  
【初期設定】  
`git config --global user.name "omi-tamu"`　でユーザ情報を登録  
`git config --global user.email ***@***.com` でメールアドレスを登録  

  - **git init**   
  任意の場所フォルダを作成し、その中に情報を更新したいファイルを保存する  
  フォルダ：今回は`kadai_git`というフォルダをPCのデスクトップに作成した  
  ファイル：今回は課題の`README.md`を作成した（詳細は後述）  
  ターミナルで  
    `cd ~/Desktop` コマンドでデスクトップへ移動  
    `cd ~/kadai_git` コマンドで指定フォルダへ移動  
    `ls` コマンドで`README.md`があることを確認する  
    `git init`　コマンドで新規リポジトリを作成する  
    `ls -a` コマンドでリポジトリの` .git` その中にファイル`README.md`があることを確認

  - **git add**  
  ファイルの変更をステージングエリア＊へ追加すること  
  `git add README.md`     コマンドで追加される
  ＊ステージングエリア：コミットするファイルを選択するためにある控室のようなもの
  - **git commit**  
  ローカルリポジトリにコミットする
  `git commit` というコマンドでコミットメッセージ入力画面Vimというエディタで開かれる  
  ＜Vimエディタの使い方＞  
  ① ターミナルでgit commitを入力する  
  ② Vimエディタが立ち上がる  
  ③ 半角英数字に入力を切り替える  
  ④「i」を入力する （挿入モードになる）  
  ⑤ コミットメッセージを入力する  
  ⑥「esc」を押す （ノーマルモードに戻る）  
  ⑦「:wq」を入力してエンターを押す (commitメッセージを保存してエディタを閉じる)    

  - **git push**  
  リモートリポジトリにプッシュするために、GitHubのアカウントページの`「New repository」`から  
  Owner / `Repository name`　に以下を入力  
  omi-tamu / `mau-j2n`  
  入力したら`「Create repository」`でレポジトリの入力完了    
  ターミナルで`git push -u origin main`  を入力してプッシュ完了、GitHubに公開されていることを確認  

  - **コマンド集**  
  `git remote add`　：ローカルリポジトリをリモートリポジトリに登録する  
  `git remote add origin URL（https://github.com/user/repogitory.git）` :originという名前でGitHubリポジトリにアクセスできる  
  `git push origin main（ブランチ名）`　：ローカルリポジトリをリモートリポジトリに送信する   
  `git status`：gitリポジトリの状況（ステータス）を確認し、変更したファイルの状況を確認できる。  
  *ステージングエリアに上げられていないファイル名は`赤字`になる  
  *ステージングエリアに上げられているファイル名は`緑字`になる  
  `git add .` ：ステージングエリアに移動  
  `git commit -v`　：コミットした時に何が変更されたかが分かる  
  `git log`　：コミットの履歴が分かる  
  `git log --oneline`　：コミットの履歴が１行だけ（シンプルに）分かる  
  `git log -n 数字`　：表示するログ数を指定する  
  `git log -p`　：何のファイルを変更したか前回との差分が分かる  
  `git log -p ***.**`　：指定したファイルの前回からの変更履歴が分かる  
  `git diff`　：ファイルの変更差分を表示する（ローカルとステージングエリアとの差分）  
  `git diff HEAD`　：ファイルの変更差分を表示する（ステージングエリアと最新コミットとの差分）  
  `rm ***.**`　：gitからファイルを管理しないように削除  
  `git rm`　：削除されたファイルをステージングエリアに追加 


## - **githubアカウントの作成**
[GitHub公式ページ](https://github.co.jp/)  
Username（`tamu-omi`とした）、Email Address、Passwordを設定後、登録ボタンを押して、アンケートに回答して登録完了。


## - **githubへのREADME.mdの公開方法**
テキストエディタ`Visual Studio Code`で、Markdownファイルを作成した。（出題4の回答）    
`README.md`ファイルをデスクトップ上のフォルダ`kadai_git`に保存した。  
その後ターミナルで  
`cd ~/Desktop`  
`cd kadai_git`  
`ls`コマンド で「README.md」　があることを確認  
コマンド `git init` でリポジトリを新規作成  
コマンド `git remote add origin  https://github.com/omi-tamu/mau-j2n.git`  でステージングエリアに追加  
コマンド `git branch -M main`  念のためブランチmainを指定した。  
コマンド `git push -u origin main` でGitHub上にREADME.mdを公開しようとしたが、以下のUsenameとPasswordが求められた。
```
Username for 'https://github.com': 
Password for 'https://github.com': 
```  
GitHubのUsernameとPasswordを入力したところ以下のエラーが出た。  
```
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/omi-tamu/intro_git.git/'

```  
インターネットで上記エラーを調べたところ[参考サイト](https://kantaro-trainee-designer.com/?p=1162)に行き着いた。  
  
このサイトによると、この問題を解決するためには代替の認証方法を使用する必要があり、パーソナルアクセストークン（PAT）を取得する必要があるとのことなので、以下の手順で対応を行った。  

1.githubでログインをして、自分のアイコンマークをクリック  
![画像1](https://kantaro-trainee-designer.com/wp-content/uploads/2023/04/github_mypage-1-1536x758.png)  

2.Settingsをクリック  
![画像2](https://kantaro-trainee-designer.com/wp-content/uploads/2023/04/80bb7d95fc22630ae97304f67fdfb183-1.png)  

3.Developer settingsページを開き、「Personal access tokens」を選択  
![画像3](https://kantaro-trainee-designer.com/wp-content/uploads/2023/04/9a236337332a6dbebdbc26a3d6ae9763-1536x454.png)  

4.「Generate new token」で新しいトークンを生成する  
![画像4](https://kantaro-trainee-designer.com/wp-content/uploads/2023/04/43e8a2dbb3fef2b2cb5a495c2acea26c-1536x304.png)  

5.「Generate token」をクリックすると、パーソナルアクセストークン（PAT）の発行が完了。画面にAccess token文字列が表示されるのでコピー  
![画像5](https://kantaro-trainee-designer.com/wp-content/uploads/2023/04/4826b24af1c5fd7fb9bdaaf327401e79-1536x680.png)  

6.もう一度`git push`コマンドを打ち、パスワードが求められたところで先ほどコピーした文字列をペーストし、実行すると無事push完了させることができた。    
