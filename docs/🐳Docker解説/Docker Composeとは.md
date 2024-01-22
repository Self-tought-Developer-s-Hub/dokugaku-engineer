# Docker Composeとは
Docker Composeは、複数のコンテナを管理するためのDockerのツールです。このツールは、特に複数の連携するコンテナ（例えば、ウェブアプリケーションサーバ
ー、データベース、キャッシュサーバーなど）を同時に扱う際に便利です。

公式ドキュメント: https://docs.docker.com/compose/

### Docker Composeの主な特徴と利点

1. **定義と管理の簡素化**：Docker Composeを使用すると、`docker-compose.yml`というYAML形式のファイルに、複数のコンテナに関する設定を記述できます。このファイルには、使用するイメージ、コンテナ間の依存関係、ポートマッピング、ボリュームマウント、環境変数などの設定が含まれます。

2. **一括操作**：Docker Composeコマンドを使って、定義されたすべてのコンテナを一度に起動、停止、再構築することができます。これにより、個々のコンテナを個別に操作する手間が省けます。

3. **開発環境の標準化**：開発チーム全体で`docker-compose.yml`ファイルを共有することで、全員が同じ環境で作業できるようになります。これにより、"私のマシンでは動くけど他の人のマシンでは動かない"という問題が減少します。

4. **マイクロサービスのサポート**：マイクロサービスアーキテクチャを採用している場合、Docker Composeは各サービスを個別のコンテナとして定義し、それらを連携させるのに役立ちます。

5. **開発とテストの自動化**：Docker Composeを使って、開発、テスト、CI/CDパイプラインでのアプリケーションの環境を自動化し、標準化することができます。

Docker Composeは、特に開発とテストのフェーズで非常に有用であり、複雑なアプリケーションの管理を簡単にするために広く使われています。

### よく使うコマンド
Docker Composeを使用する際によく使うコマンドとその使い方を説明します。これらのコマンドは、`docker-compose.yml` ファイルが存在するディレクトリで実行されることが一般的です。

### 1. `docker-compose up`
- **用途**：`docker-compose.yml` ファイルに定義されたサービス（コンテナ）を起動します。
- **使い方**：
  - `docker-compose up`：バックグラウンドで実行する場合は `-d` フラグを使用します。
  - `docker-compose up -d`：サービスをバックグラウンドで起動します。

### 2. `docker-compose down`
- **用途**：起動中のサービスを停止し、関連するネットワークやリソースを削除します。
- **使い方**：`docker-compose down`

### 3. `docker-compose ps`
- **用途**：現在起動中のコンテナの状態を表示します。
- **使い方**：`docker-compose ps`

### 4. `docker-compose logs`
- **用途**：サービスのログを表示します。
- **使い方**：
  - `docker-compose logs`：すべてのサービスのログを表示します。
  - `docker-compose logs [サービス名]`：特定のサービスのログを表示します。

### 5. `docker-compose restart`
- **用途**：サービス（コンテナ）を再起動します。
- **使い方**：`docker-compose restart`

### 6. `docker-compose build`
- **用途**：Dockerfileに基づいてサービスのイメージをビルドします。
- **使い方**：`docker-compose build`

### 7. `docker-compose exec`
- **用途**：実行中のコンテナ内でコマンドを実行します。
- **使い方**：`docker-compose exec [サービス名] [コマンド]`
  - 例：`docker-compose exec web sh`（`web`サービスのコンテナでシェルを開く）

### 8. `docker-compose stop` と `docker-compose start`
- **用途**：サービスを停止（`stop`）または開始（`start`）します。
- **使い方**：
  - `docker-compose stop`：すべてのサービスを停止します。
  - `docker-compose start`：停止中のサービスを開始します。

これらのコマンドを適切に使用することで、Docker Composeを使ったマルチコンテナ環境の管理が容易になります。