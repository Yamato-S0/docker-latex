# LaTeX DevContainer Template

このリポジトリは VSCode + Dev Container を使い、LaTeX 環境を簡単に構築できるテンプレートです。

## 使い方

1. **Docker イメージを事前に準備する**
   - どこかのリポジトリで用意されている Dockerfile を `docker build -t my-latex-image:latest .` する  
     もしくは  
   - `docker pull YOUR-ORG/my-latex-image:latest` (もし Docker Hub / GHCR などに公開済みなら)
   
2. **リポジトリをテンプレートから作成**
   - GitHub ページで “Use this template” → 新しいリポジトリを生成
   - 生成したリポジトリをローカルに `git clone` する

3. **VSCode で開き、Dev Container を起動**
   - `Dev Containers: Reopen in Container` を実行  
   - すでに `my-latex-image:latest` がローカルにある場合、ビルド不要ですぐにコンテナが起動します！

4. **LaTeX をビルド**
   - `main.tex` などを編集して、VSCode の LaTeX Workshop からコンパイル or ターミナルで `latexmk -pdf main.tex` 実行