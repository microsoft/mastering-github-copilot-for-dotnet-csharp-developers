## ステップ 1: VS Code と Codespaces を活用して Copilot を使おう

_「GitHub Copilot と VS Code を使った AI パワードコード提案で開発しよう」へようこそ！ :wave:_

GitHub Copilot は、コードをより速く、より少ない労力で書く手助けをする AI ペアプログラマーです。コメントやコードからコンテキストを読み取り、個々の行や関数全体を瞬時に提案します。GitHub Copilot は OpenAI の Codex によって動作しており、これは OpenAI によって作られた生成型の事前学習済み言語モデルです。

**Copilot は VS Code、Visual Studio、JetBrains IDE、Neovim を含む多くのコードエディタで動作します。**

さらに、GitHub Copilot は公開リポジトリに存在するすべての言語でトレーニングされています。各言語において、提案の品質は、その言語のトレーニングデータの量と多様性に依存する場合があります。

Codespace 内で Copilot を使用すると、GitHub の [Collaborative Coding](https://github.com/features#features-collaboration) ツール群を使い始めるのがいかに簡単かを実感できます。

> **注:**
> このスキル演習では、GitHub Codespace を活用することに焦点を当てます。この演習を進める前に、GitHub スキル [Codespaces](https://github.com/skills/code-with-codespaces) を完了することをお勧めします。

### ⌨️ アクティビティ: Codespace 内で Copilot を有効化する

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/microsoft/mastering-github-copilot-for-dotnet-csharp-developers?devcontainer_path=.devcontainer%2Fintroduction%2Fdevcontainer.json)

**以下のアクティビティを進める際は、この指示を参照できるよう、別のブラウザタブを開くことをお勧めします。**

リポジトリで Codespace を開く前に、開発コンテナを作成し、Codespace で使用またはインストールされる特定の拡張機能や設定を定義できます。この開発コンテナを作成し、拡張機能リストに Copilot を追加しましょう。

1. **.devcontainer/introduction/devcontainer.json** ファイルの本文に以下の内容があることを確認してください:
   ```
   {
       // Name this configuration
       "name": "Introduction to Copilot",
       "customizations": {
           "vscode": {
               "extensions": [
                   "GitHub.copilot",
                   "ms-dotnettools.csdevkit"
               ]
           }
       }
   }
   ```

問題が発生した場合は、以下の手順で新しい Codespace を作成できます:

1. 画面左上にある **Code** タブをクリックしてリポジトリのホームページに戻ります。
1. ページ中央にある **Code** ボタンをクリックします。
1. ポップアップで表示されるボックスの **Codespaces** タブをクリックします。
1. **Create codespace on main** ボタンをクリックし、「Introduction to Copilot」を選択します。

   **Codespace が起動するまで約 2 分待ちます。**

1. Codespace が実行中であることを確認してください。ブラウザには VS Code のウェブ版エディタが表示され、以下のようなターミナルが存在するはずです:
   ![Screen Shot 2023-03-09 at 9 09 07 AM](../../../../03-Introduction-to-GitHub-Copilot/steps/img/1-skills-0.png)
1. `copilot` 拡張機能が VS Code の拡張機能リストに表示されているはずです。拡張機能のサイドバータブをクリックしてください。以下のように表示されます:
   ![Screen Shot 2023-03-09 at 9 04 13 AM](../../../../03-Introduction-to-GitHub-Copilot/steps/img/1-skills-1.png)

[演習のパート 2](./2-skills-dotnet.md) へ進みましょう

**免責事項**:  
この文書は、機械翻訳AIサービスを使用して翻訳されています。正確性を追求していますが、自動翻訳には誤りや不正確な箇所が含まれる可能性があります。元の言語で記載された原文が正式な情報源とみなされるべきです。重要な情報については、専門の人間による翻訳を推奨します。この翻訳の使用に起因する誤解や誤認について、当方は一切の責任を負いません。
