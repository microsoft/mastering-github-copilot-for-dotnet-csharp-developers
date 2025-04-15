## ステップ 3: 複数の提案が表示されるGitHub Copilotタブを確認

_お疲れ様です！GitHub Copilotを使ってC#ファイル内でAIコード提案を利用しましたね :sparkles:_

Copilotを使い続ける中で、GitHub Copilotが提供する提案の中には、必要ないものもあるかもしれません。GitHub Copilotは新しいタブで複数の提案を表示します。

### ⌨️ アクティビティ: 別のC#メソッドを追加して、全ての提案を確認

1. Solution Explorer内でプロジェクトを右クリックし、新しいファイルを作成します。

> 注: 上記でCodespaceを閉じた場合は、再度開くか、新しいCodespaceを作成してください。

2. **Class**を選択し、ファイル名を`Members.cs`に設定します。
3. `Members.cs`ファイル内で、`Member`クラスの中に次の関数を入力します。
   ```
   public strin
   ```
4. 入力を停止し、赤い波線のグレーのテキストの上にカーソルを合わせてCopilotの提案を確認します。その後、`...`
5. Click `Open Completions Panel`. 

   > **Note**
   > If you don't see the copilot code block suggestion or the red squiggly and the three dots `...`, you can type `control + enter` to bring up the GitHub Copilot completions panel.

6. Copilot will synthesize around 10 different code suggestions or press CTRL+Enter. You should see something like this:
   ![VS Code showing pop up with Completions Panel](../../../../03-Introduction-to-GitHub-Copilot/steps/img/3-copilot-hub-0.png)
7. 気に入った解決策を見つけて、`Accept Solution`をクリックします。
8. Your `Member.cs`ファイルがあなたのソリューションで更新されます。

### ⌨️ アクティビティ: Codespaceからリポジトリにコードをプッシュ

GitHub Copilotを使って変更内容を要約し、コードをコミットしてみましょう。

1. **Source Control**タブを開きます。
2. **Message**入力欄の ✨ ボタンをタップして、Copilotにメッセージを生成してもらいます。

![Copilotでメッセージを生成するために開かれたコミットタブ](../../../../03-Introduction-to-GitHub-Copilot/steps/img/2-skills-commit.png)

3. **Commit**ボタンをクリックします。

[演習のパート4へ進む](./4-copilot-comment.md)

**免責事項**:  
この文書は、機械ベースのAI翻訳サービスを使用して翻訳されています。正確性を追求しておりますが、自動翻訳には誤りや不正確さが含まれる可能性があります。元の言語で記載された原文が正式な情報源として優先されるべきです。重要な情報については、専門の人間による翻訳を推奨します。本翻訳の使用に起因する誤解や解釈の誤りについて、当方は一切の責任を負いません。
