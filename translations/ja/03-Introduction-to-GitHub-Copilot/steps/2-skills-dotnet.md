## ステップ 2: C# ファイルで Seeing AI のコード提案を試してみよう！

_よくできました！🎉 devcontainer ファイルを使って Codespace を作成し、Copilot をインストールしましたね！_

GitHub Copilot は多くのプログラミング言語やさまざまなフレームワークに対応していますが、特に Python、JavaScript、TypeScript、Ruby、Go、C#、C++ で効果的に動作します。以下のサンプルは C# を使用していますが、他の言語でも同様に機能します。

それでは、C# を使って Copilot を試してみましょう。

> **注:**:
> 先ほどの Codespace を閉じてしまった場合は、再度開くか新しい Codespace を作成してください。

### ⌨️ アクティビティ: C# ファイルを追加してコードを書いてみよう

> **Note**:
> **Solution Explorer** を開いて、プロジェクトを整理されたビューで確認し、新しいプロジェクトを簡単に追加して実行できるようにしてください。

1. `.NET: New Project...` コマンドを使用して新しい .NET プロジェクトを作成し、`Console App` を選択します。
2. **code** フォルダーを選択し、プロジェクト名を **Skills** とします。
3. `Program.cs` を開きます。
4. 新しいファイルが以下のようになっていることを確認します。
   ![VS code with a new Program.cs](../../../../03-Introduction-to-GitHub-Copilot/steps/img/2-skills-dotnet-0.png)

5. `Program.cs` ファイル内のコードをすべて削除し、次の関数ヘッダーを入力します。

   ```csharp
   void CalculateNumbers(int var1, int var2)
   {
   ```

   GitHub Copilot が自動的に関数全体の内容をグレーのテキストで提案します。以下は一般的に表示される例ですが、提案内容は若干異なる場合があります。
   ![VS Code with completions](../../../../03-Introduction-to-GitHub-Copilot/steps/img/2-skills-dotnet-1.png)

6. `Tab` キーを押して提案を受け入れます。

### ⌨️ アクティビティ: Codespace からリポジトリにコードをプッシュしよう

GitHub Copilot を使って変更内容を要約し、コードをコミットしてみましょう。

1. **Source Control** タブを開きます。
2. **Message** エントリ内の ✨ ボタンをタップして、Copilot にメッセージを生成させます。

![Commit tab open to generate message with Copilot](../../../../03-Introduction-to-GitHub-Copilot/steps/img/2-skills-commit.png)

3. **Commit** ボタンをクリックします。

[演習のパート 3](./3-copilot-hub.md) に進みましょう。

**免責事項**:  
この文書は、機械翻訳AIサービスを使用して翻訳されています。正確性を期すよう努めておりますが、自動翻訳には誤りや不正確な表現が含まれる可能性があります。本来の言語で記載された原文を公式な情報源としてお考えください。重要な情報については、専門の人間による翻訳を推奨します。この翻訳の使用に起因する誤解や解釈の相違について、当社は一切の責任を負いかねます。
