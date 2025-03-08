# docker-latex

Docker + VSCode Dev Container を使って、簡単かつ統一された LaTeX 環境を構築できるテンプレートリポジトリです。  
**初回だけ Docker イメージをビルド** すれば、2 回目以降はビルド不要でいつでも開発を再開できます。

## 1. テンプレートの利用方法

### 1.1 テンプレートから新しいリポジトリを作成

1. GitHub 上で本リポジトリ (docker-latex) のページを開く
2. 「**Use this template**」ボタンをクリック
3. 新しいリポジトリ名を入力 (例: `my-latex-project`) して、Create repository

### 1.2 リポジトリをクローン

ローカルで作業する場合は、次のようにクローンしてください。

```bash
git clone git@github.com/YOUR-ORG/my-latex-project.git
cd my-latex-project
```

## 2. 初回の Docker イメージビルド

1. リポジトリに含まれている .devcontainer/Dockerfile を利用し、以下のコマンドを実行します。

```bash
docker build -t my-latex-image:latest -f .devcontainer/Dockerfile .
```

my-latex-image は任意の名前で構いません。

2. ビルドが完了すると、ローカルに統一された LaTex 環境を構築できます。

**※ 2 回目以降はビルド不要です。**

## 3. VSCode Dev Container の起動

1. VSCoode で my-latex-project ディレクトリを開きます。
2. 左下の「**><**」をクリックし、**Reopen in Container** を選択します。
3. 初回の起動時は、Docker イメージのビルドが行われます。

## 4. LaTeX の執筆・コンパイル

1. Dev Container 内で main.tex などの LaTeX ファイルを編集します。
2. 自動コンパイルを使う場合は、LaTeX Workshop の設定により保存時に自動ビルドが走ります。
3. ビルドエンジンを切り替えたい場合

   - コマンドパレット (Ctrl + Shift + P) で「**LaTeX Workshop: Build With Recipe**」を選択します。
   - 以下のビルドエンジンから自身のプロジェクトに合ったものを選択します。
     - **pdflatex**
     - 欧文のみの文書に適しています。
     - コンパイル速度が速いです。
     - **platex**
     - 和文のみの文書に適しています。
     - コンパイル速度が速いです。
     - **lualatex**
     - 欧文・和文の両方に対応しており、様々なカスタマイズが可能です。
     - コンパイル速度が遅いです。

4. コンパイル結果は out ディレクトリに保存されます。

2 回目以降、環境を立ち上げるときは、**docker build** は不要です。
**Dev Containers** で「**Reopen in Container**」を選択するだけで、いつでも開発を再開できます。

## 5. トラブルシューティング

1. **Docker が起動していない場合**
   - Docker Desktop などを起動してください。
2. **LaTeX Workshop の拡張機能が見当たらない場合**
   - コマンドパレットで Extensions: Show Installed Extensions を選び、James-Yu.latex-workshop が入っているか確認してください。
   - 入っていなければ一度コンテナを再ビルド (Dev Containers: Rebuild Container) してみてください。
3. **コンテナのビルドが失敗する場合**
   - ネットワークの問題や apt-get エラーが考えられます。
   - Dockerfile を適宜修正して再度 docker build をお試しください。
4. **Remote - Container 上から git 管理をしたい場合**
   - git credential の設定が必要です。[公式ドキュメント](https://code.visualstudio.com/remote/advancedcontainers/sharing-git-credentials#_using-ssh-keys) を参考に設定してください。
