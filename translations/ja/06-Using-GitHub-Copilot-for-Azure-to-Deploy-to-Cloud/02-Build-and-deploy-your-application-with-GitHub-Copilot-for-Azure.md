# GitHub Copilot for Azure を使ったアプリケーションの構築とデプロイ

このモジュールはモジュール 1 の続きであり、GitHub Copilot for Azure Preview を使用して Azure に新しいウェブサイトを作成しデプロイするためのステップバイステップガイドを提供します。

GitHub Copilot for Azure を開発およびデプロイのワークフローにシームレスに統合する方法を紹介します。

## 前提条件

[モジュール 1 - GitHub Copilot for Azure の使い方を始める](./01-Getting-Started-with-GitHub-Copilot-for-Azure.md)を完了していること

## GitHub Copilot for Azure Preview を使ってウェブサイトを作成してデプロイする

1. GitHub リポジトリのローカルクローンを作成するために、ローカルコンピューター上に新しいフォルダーを作成します。
    1. VS Code で **File** をクリックし、「Open Folder」を選択します。
    1. **Open Folder** ダイアログボックスで **New Folder** をクリックし、フォルダーに名前を付け、選択してから **Select Folder** をクリックします。

1. VS Code が **このフォルダー内のファイルの作成者を信頼しますか？** と尋ねてきます。
    1. **Yes, I trust the authors** をクリックします。

1. Visual Studio Code で **View** > **Terminal** を選択します。ターミナルペインで、新しいフォルダーに移動します。

1. ステータスバーで **Chat** (GitHub) アイコンを選択し、チャットペインを開きます。

1. ペインのタイトルバーでプラスアイコン (**+**) を選択して新しいチャットセッションを開始します。

   ![GitHub Copilot チャットペインを示すスクリーンショット](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat.png "新しいチャットセッションを開始する")

> 前回のモジュールの後に GitHub Copilot Chat を閉じた場合は、ステータスバーの GitHub アイコンをクリックします（VS Code 画面の右下）。そして、オプションメニューで **"GitHub Copilot Chat"** を選択します。
>
> ![GitHub Copilot チャットペインを示すスクリーンショット](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-2.png "新しいチャットセッションを開始する")

6. チャットのテキストボックスに次のプロンプトを入力します。その後、**Send** (紙飛行機アイコン) を選択するか、キーボードの Enter を押します。

   ```prompt
   @azure can you help me deploy a C# api with mongodb and a web front end?
   ```

    > **IMPORTANT**
GitHub Copilot for Azure の回答は、大規模言語モデルがどのように応答を生成するかによって、毎回異なる表現になります。

   少し待つと、GitHub Copilot for Azure が `azd` template to use.  Or in some cases will provide an answer like the following:

    ![Screenshot that shows the GitHub Copilot chat pane](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-3.png "Screenshot that shows a response from GitHub Copilot for Azure with instructions for using a template to create a website in Azure.")

    Just Remember that the Large Language Model will understand what you tell it.  Therefore, just have the conversation with it.

1. If the answer provides a command that begins with `azd init` in a code fence, hover over the code fence to reveal a small pop-up action menu.

    ![Screenshot that shows the GitHub Copilot chat pane](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-4.png "Screenshot that shows a pop-up menu with an option to insert a code-fenced command into the Visual Studio Code terminal.")

    Select **Insert into Terminal** to insert the command into the terminal.

    ![Screenshot that shows the GitHub Copilot chat pane](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-5.png "Screenshot that shows the Visual Studio Code terminal after insertion of a code-fenced command.")

1. Before you run the `azd init` コマンドを提案する可能性があります。このコマンドがローカルコンピューターや Azure サブスクリプションにどのような影響を与えるかについて質問したくなるかもしれません。

   次のプロンプトを使用します：

   ```prompt
   @azure Before I execute azd init, what does it do?
   ```

   次のようなスクリーンショットに似た応答が表示される可能性があります。

   ![GitHub Copilot for Azure が初期化コマンドの説明を含む応答を示すスクリーンショット](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-6.png "初期化コマンドが何を行うかの説明を含む応答")

1. `azd` テンプレートについてさらに学ぶために、次のプロンプトを使用します：

   ```prompt
   @azure What resources are created with this template?
   ```

   次のようなスクリーンショットに似た応答が表示される可能性があります。

    ![GitHub Copilot for Azure が提案されたテンプレートで作成されるリソースの説明を含む応答を示すスクリーンショット](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-7.png "テンプレートで作成されるリソースの説明を含む応答")

1. テンプレートが使用するサービスについて質問する場合は、次のようなプロンプトを使用します：

   ```prompt
   @azure What are the capabilities of Azure App Service?
   ```

   次のようなスクリーンショットに似た応答が表示される可能性があります。

    ![GitHub Copilot for Azure が Azure App Service の機能に関する説明を含む応答を示すスクリーンショット](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-8.png "Azure App Service の機能の説明を含む応答")

1. 満足したら、次のコマンドをターミナルで実行して `azd init` command in the terminal. Answer its prompts. If you're unsure what to answer for a prompt, ask GitHub Copilot for Azure for help.

1. Before you can continue, you must authenticate the `azd` ツールを実行します：

    ```cmd
    azd auth login
    ```

    1. ブラウザが開き、Azure への認証が求められます。以前と同じ資格情報を選択してください。

1. 新しいプロジェクトが初期化され、Azure に認証した後、**azd up** コマンドを使用してアプリケーションをサブスクリプションにデプロイします。ターミナルで、元のプロンプトの応答に従ってコマンドを実行します。

    ```
    azd up
    ```

1. `azd up` コマンドは、サブスクリプション、リソースのデプロイ先などに関する情報を求めてきます。

    回答に迷った場合は、GitHub Copilot for Azure に助けを求めることができます。例えば、次のように質問できます：

    ```prompt
    @azure azd up is asking me what location I want to deploy the website into. How should I respond?
    ```

    次のようなスクリーンショットに似た応答が表示される可能性があります。

    ![GitHub Copilot for Azure が Azure のロケーションとその選び方に関する説明を含む応答を示すスクリーンショット](../../../06-Using-GitHub-Copilot-for-Azure-to-Deploy-to-Cloud/images/mod2-CopilotChat-9.png "Azure のロケーションに関する説明を含む応答")

5. `azd up`. Ask GitHub Copilot for Azure questions as needed.

    1. When asked the location select **Canada East (canadaeast)**.

    Depending on the `azd` template that you're deploying and the location that you selected, the template might take 10 minutes (or more) to deploy. But we can Move on to [Module 3](./03-Get-Answers-to-your-Questions-about-Azure-Services-and-Resources.md) while it completes

1. `azd up` でエラーが発生した場合は、GitHub Copilot for Azure にエラーとその解決方法を問い合わせてください。

    > **TIP**
    > For an easy way to attach the last terminal command results, use the paperclip icon at the bottom left of the chat pane. GitHub Copilot for Azure doesn't know the terminal command results unless they are copy/pasted or attached via the paperclip.


1. When you are done run `azd down` のプロンプトに引き続き回答し、すべてのリソースを削除します。

**免責事項**:  
本書類は、機械ベースのAI翻訳サービスを使用して翻訳されています。正確性を追求しておりますが、自動翻訳には誤りや不正確さが含まれる場合があります。元の言語で記載された原文を公式な情報源としてお考えください。重要な情報については、専門の人間による翻訳を推奨いたします。本翻訳の使用に起因する誤解や解釈の誤りについて、当方は一切の責任を負いかねます。
