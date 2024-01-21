# TODOアプリケーション開発初級
このアプリケーション開発課題では、TODOアプリケーションを実際に与えられた要件・デザインに沿って開発をします。
その中で、主にフロントエンドとバックエンドとの連携、特にフロントエンドでの適切なデータ構造の操作（配列、オブジェクト）
が実践できているかを確認していきましょう。

## 対象者
- React/Next.jsの基本を理解していること
- TypeScriptの基本を理解していること
- ajaxによるフロントエンド・バックエンドの通信方法の基本の理解
- 個別レクチャーはメンタリング受講生のみへのご提供です


## デザイン概観
- [figma](https://www.figma.com/file/pTZ2PGSxE7zX1MFzl3nZKb/IFX%E5%8B%89%E5%BC%B7%E4%BC%9A-TODO%E3%82%A2%E3%83%97%E3%83%AA%E3%80%80%E3%83%87%E3%82%B6%E3%82%A4%E3%83%B3?type=design&node-id=37%3A1345&mode=design&t=qyy2Loh3KNgmlJdZ-1)

### タスク一覧TOP
![task list](/img/docs/dev-tasks/todoapp/todoapp_task_list.png)

### タスク追加モーダル
![task add](/img/docs/dev-tasks/todoapp/todoapp_task_add_modal.png)

### タスク追加成功
![task add](/img/docs/dev-tasks/todoapp/todoapp_task_add_success.png)

## 想定技術スタック
### フロントエンド
- React/Next.js
  - Pages routes推奨
- TypeScript
- ChakraUI
  - デザインがChakraUI準拠になっているため、ChakraUIのインストールが必要です
- HTTP通信ライブラリ
  - FetchAPIもしくは
  - Axios等のHTTP通信ライブラリを推奨

### バックエンド
- 永続化は必須ではないので、ひとまずフロントエンドのみで動作させてもOK
  - フロントエンドとの接続がわからなければ飛ばしてください。個別でレクチャーします。
- 任意のバックエンドフレームワーク(Spring Boot, Laravel, Ruby on Railsなど)


## 開発タスク
### セットアップ編
#### フロントエンド
- Next.js/TypeScriptのプロジェクトを作成し、GitHubの自分のレポジトリを作成し、Push
- [ChakraUI](https://chakra-ui.com/getting-started)をインストールし、手順の通り設定をする
- TOPページ`pages/index.tsx`が動作することを確認し、ここにコードを書いていく

#### バックエンド
- 任意のバックエンド言語＋ライブラリでプロジェクトを作成し、GitHubに自分のレポジトリを作成し、Pushする
  - なお、簡単なスターターを一部言語に限っては用意している
    - [Java/Spring boot](https://github.com/Self-tought-Developer-s-Hub/java-spring-starter)
    - [PHP/Laravel](https://github.com/Self-tought-Developer-s-Hub/laravel-v10-starter)
- データベースと接続ができることを確認する

### タスク一覧TOP
![task list](/img/docs/dev-tasks/todoapp/todoapp_task_list.png)

- 右下の＋ボタンを押すと、モーダルを開くことができる
  - ChakraUIの[モーダルコンポーネント](https://chakra-ui.com/docs/components/modal/usage)が利用可能
- TODOタスクの一覧が表示できる
  - 未完了には、まだ終わっていないもの/作成した直後のものが表示される
  - 完了には、未完了のうちチェックをいれたものが振り分けられる
  - 完了の中から、チェックを外すと、また未完了状態として未完了に振り分けられる
  - タイトル（2024年１月２１日の部分）には、今日の日付をyyyy年mm月dd日のフォーマットで表示する

### タスク追加モーダル
![task add](/img/docs/dev-tasks/todoapp/todoapp_task_add_modal.png)

- タスクの追加というタイトルのモーダルを開くことができる
- 保存を押した場合、入力されたタスクを保存する
  - (Bonus) 何も入力されていない場合は、保存ボタンを非活性(disabled)に設定
  - (Bonus) タスクの入力文字数が191文字を超える場合は、保存ボタンを非活性(disabled)に設定
- キャンセルを押した場合、モーダルを閉じることができる
  - (Bonus) 入力したステートを破棄するようにする。もう一度モーダルを開いたときに、同じ入力テキストを出ないようにする
  - (Bonus) モーダルの外側をクリックして閉じたときも同様に、入力内容は破棄する

### タスク追加成功
![task add](/img/docs/dev-tasks/todoapp/todoapp_task_add_success.png)

- ChakraUIの[Toast](https://chakra-ui.com/docs/components/toast/usage)を利用し、成功した旨をモーダルを保存し、モーダルを閉じ、toastを表示するような実装をする
  - (Bonus) 保存に失敗した場合のtoastも表示するようにする

## 採点項目
総合点：250

- [100]フロントエンドのステートによって、TODOの保存、チェックボックスの状態を管理できる
- [50]フロントエンドのBonus実装ができた
- [100]バックエンドAPIを開発できた
  - [25]TODOタスク一覧APIを開発できた
  - [25]TODOタスク追加APIを開発できた
  - [25]TODOタスク状態アップデートAPIを開発できた
  - [25]各種APIに自動テストを追加できた