- **対象者**: 開発者、DevOpsエンジニア、ソフトウェア開発マネージャー、テスター  
- **学べること**: GitHub Copilotを使用してコードを作成し、作業にコメントを追加する方法  
- **作成するもの**: GitHub Copilot AIがコードやコメントの提案を生成するC#ファイル  
- **前提条件**: GitHub Copilotは無料で利用可能です。[GitHub Copilot](https://gh.io/copilot)にサインアップしてください。  
- **所要時間**: このコースは1時間以内で完了可能です。  

このモジュールを終了する頃には、以下のスキルを習得できます:  

- GitHub Copilotから提案を生成するプロンプトを作成する  
- GitHub Copilotを活用してプロジェクトを改善する  

## 必読資料:
- [GitHub Copilotを使ったプロンプトエンジニアリング入門](https://learn.microsoft.com/training/modules/introduction-prompt-engineering-with-github-copilot)  

- [Visual Studio用GitHub Copilot拡張機能とは？](https://learn.microsoft.com/en-us/visualstudio/ide/visual-studio-github-copilot-extension?view=vs-2022)  

## 必要条件  

1. [GitHub Copilotサービスを有効化する](https://github.com/github-copilot/signup)  

1. [このリポジトリとCodespaces](https://github.com/github/dotnet-codespaces)に慣れる  

## 💪🏽 演習  

**以下のCodespacesボタンを右クリックして、新しいタブでCodespaceを開いてください**  

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/github/dotnet-codespaces)  

"**GitHub Codespaces ♥️ .NET**"リポジトリはMinimal APIsを使用してWeather APIを構築し、Swaggerを開いてAPIを呼び出してテストし、Blazorと.NETを使用してWebアプリケーションにデータを表示します。  

この演習では、新しいエンドポイントを追加し、特定の場所をリクエストしてその場所の天気予報を返すようにWeather BackEnd Appを更新する手順を確認します。  

### 🤔 ステップ 0: "GitHub Codespaces ♥️ .NET"リポジトリに慣れる  

リポジトリをCodespacesで開くと、完全に機能するCodespaceが新しいブラウザウィンドウに表示されます。このリポジトリのすべてはこの1つのCodespace内に含まれています。例えば、エクスプローラーパネルでBackEndプロジェクトとFrontEndプロジェクトの主要なコードを見ることができます。  

![新しいCodespaceでリポジトリを実行](../../../04-Using-GitHub-Copilot-with-CSharp/images/005OpenRepoInCodeSpaces.png)  

プロジェクトを実行する前に、GitHub Copilot Chatを使用してプロジェクトの内容や異なるコンポーネントについて質問してみましょう。  

1. **GitHub Copilot Chat**をメインナビゲーションバーから開きます。  
1. `What is this project doing, and what are the key components?` を入力して**送信**をクリックします。  

GitHub Copilot Chatはプロジェクト全体を分析し、プロジェクトの目的、使用している技術、主要なコンポーネントについての概要を提供します。  

![Copilot Chatがプロジェクトを説明](../../../04-Using-GitHub-Copilot-with-CSharp/images/004AskCopilotAboutProject.png)  

ここからファイルをクリックしてナビゲートしたり、`What APIs are available?` のようなフォローアップの質問をすることができます。  

### 🚀 ステップ 1: プロジェクトを実行する  

プロジェクトの内容を理解したので、実際に実行してみましょう。  
BackEndプロジェクトを実行するには、「Run and Debug」パネルに移動し、「BackEnd」プロジェクトを選択します。  

![BackEndプロジェクトのprogram.csを開く](../../../04-Using-GitHub-Copilot-with-CSharp/images/006RunBackEndProject.png)  

選択したプロジェクトをデバッグ開始します。Weather APIプロジェクト（BackEndプロジェクト）はポート8080で実行されます。*Ports*パネルから公開されたURLをコピーできます。  

![PortsパネルからアプリのURLをコピー](../../../04-Using-GitHub-Copilot-with-CSharp/images/007ProjectRunningOpenInNewTab.png)  

> 注意: アプリケーションを実行すると「このページは動作していません」というエラーメッセージが表示される場合があります。それは、以下で説明するエンドポイントに移動する必要があるためです。  

BackEndアプリケーションはランダムな天気予報データを生成する`weatherforecast`というエンドポイントを公開しました。現在実行中のアプリケーションをテストするには、公開されたURLに`/weatherforecast`を追加します。最終的なURLは以下のようになります:  

```bash
https://< your url>.app.github.dev/weatherforecast
```  
ブラウザで実行中のアプリケーションは以下のようになります。  

![実行中のアプリケーションをテスト](../../../04-Using-GitHub-Copilot-with-CSharp/images/008TestRunningApi.png)  

次に、アプリケーションにブレークポイントを設定し、APIの各呼び出しをデバッグします。`Program.cs` file in the BackEnd project. The file is in the following path `SampleApp\BackEnd\Program.cs`. 

Add a breakpoint in line 24 (press F9) and refresh the browser with the Url to test the endpoint. The browser should not show the weather forecast, and in the Visual Studio Editor we can see how the program execution was paused at line 24.

![debug the running application.](../../../04-Using-GitHub-Copilot-with-CSharp/images/009DebugBackEndDemo.png)

Pressing F10 we can debug step-by-step until line 32, where we can see the generated values. The application should have been generated samples Weather values for the next 5 days. The variable `forecast` has an array containing these values.

![debug the running application.](../../../04-Using-GitHub-Copilot-with-CSharp/images/010DebugForecastValue.png)

これでデバッグを停止できます。

おめでとうございます！これで、GitHub Copilot を使用してアプリに機能を追加する準備が整いました。

### 🗒️ ステップ 2: GitHub Copilotのスラッシュコマンドに慣れる

コードベースで作業を開始すると、通常、コードをリファクタリングしたり、コードに関する詳細なコンテキストや説明を入手したりする必要が生じます。GitHub Copilot Chat を使用すると、AI を活用した会話を通じてこれらのタスクを実行できます。

BackEnd プロジェクトのファイル `Program.cs` を開きます。このファイルは `SampleApp\BackEnd\Program.cs` というパスにあります。

GitHub Copilot でスラッシュコマンドを使ってコードの一部を理解してみましょう。22行目から35行目までを選択し、`CTRL + I`を押してインラインチャットを開き、`/explain` と入力してください。

![コードの説明をするスラッシュコマンドを使用](../../../04-Using-GitHub-Copilot-with-CSharp/images/011SlashCommandExplain.gif)  

GitHub Copilotのバージョンに応じて、インライン応答またはチャットパネルの更新が表示されます。GitHub Copilotは選択したコードの詳細な説明を作成します。要約されたバージョンは以下のようになります:  

```
The selected C# code is part of an ASP.NET Core application using the minimal API feature. It defines a GET endpoint at "/weatherforecast" that generates an array of WeatherForecast objects. Each object is created with a date, a random temperature, and a random summary. The endpoint is named "GetWeatherForecast" and has OpenAPI support for standardized API structure documentation.
```  

**スラッシュコマンド**は、コードに対して特定のアクションを実行するためにチャット内で使用できる特別なコマンドです。例えば、以下を使用できます:  
- `/doc` to add a documentation comment 
- `/explain` to explain the code 
- `/fix` to propose a fix for the problems in the selected code 
- `/generate` to generate code to answer your question

`/tests` コマンドを使ってコードのテストを生成してみましょう。39行目から42行目までを選択し、`CTRL + I` を押してインラインチャットを開き、`/tests` と入力（または /tests スラッシュコマンドを選択）して、このレコードの新しいテストセットを生成します。

![Use slash command to generate tests for the selected piece of code](../../../04-Using-GitHub-Copilot-with-CSharp/images/012SlashCmdTests.gif)

この時点で、GitHub Copilot は新しいクラスを提案します。新しいファイルを作成するには、まず [Accept] を押す必要があります。

新しいクラス `ProgramTests.cs` が作成され、プロジェクトに追加されました。このテストはXUnitを使用していますが、`/tests use MSTests for unit testing` のようなコマンドを実行することで、別のユニットテストライブラリを使用してテストを生成することもできます。

***重要:** このプロジェクトではテストファイルは使用しません。続行するには、生成されたテストファイルを削除する必要があります。*

最後に、`/doc` を使ってコードのドキュメントを自動生成しましょう。39行目から42行目までを選択し、`CTRL + I` を押してインラインチャットを開き、`/doc` と入力（またはコマンドを選択）して、このレコードのドキュメントを生成します。

![Use slash command to generate the documentation for a piece of code](../../../04-Using-GitHub-Copilot-with-CSharp/images/013SlashCmdDoc.gif)

インラインチャット、チャットパネル、スラッシュコマンドは、GitHub Copilot を使った開発環境を支える素晴らしいツールの一部です。さあ、このアプリに新機能を追加する準備が整いました。


### 🗒️ ステップ3: 都市名を含む新しいレコードを生成する

BackEnd プロジェクトの `Program.cs` ファイルに移動します。このファイルは `SampleApp\BackEnd\Program.cs` というパスにあります。

![BackEndプロジェクトのprogram.csを開く](../../../04-Using-GitHub-Copilot-with-CSharp/images/011OpenBackEndProject.png)  

ファイルの最後に移動し、Copilotに都市名を含む新しいレコードを生成するよう依頼します。  

```csharp
// create a new internal record named WeatherForecastByCity that request the following parameters: City, Date, TemperatureC, Summary
```  

生成されたコードは以下のようになります:  

```csharp
// create a new internal record named WeatherForecastByCity that request the following parameters: City, Date, TemperatureC, Summary
internal record WeatherForecastByCity(string City, DateOnly Date, int TemperatureC, string? Summary)
{
    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
}
```  

以下のアニメーションでプロンプトがどのように機能するかを確認できます:  

![BackEndプロジェクトのprogram.csを開く](../../../04-Using-GitHub-Copilot-with-CSharp/images/014AddNewRecord.gif)  

### 🔎 ステップ 4: 都市の天気予報を取得する新しいエンドポイントを生成する  

次に、`/weatherforecast`に似た新しいAPIエンドポイントを生成し、都市名も含めます。新しいAPIエンドポイント名は**`/weatherforecastbycity`**になります。  

***重要**: コードは必ず`.WithOpenApi();`行の後に配置してください。この行は36行目に始まります。また、新しい提案された行をすべて定義するまで[Tab]を押して提案を受け入れてください。*  

次に、以下のコメントを追加してGitHub Copilotで新しいエンドポイントを生成します:  

```csharp
// Create a new endpoint named /WeatherForecastByCity/{city}, that accepts a city name in the urls as a paremeter and generates a random forecast for that city
```  
以下の例では、前のエンドポイントの後にいくつかの空行を追加し、その後GitHub Copilotが新しいエンドポイントを生成しました。エンドポイントのコアコードが生成されると、GitHub Copilotはエンドポイント名（49行目）とOpenAPI仕様（50行目）のコードも提案しました。[Tab]を押してこれらの提案を受け入れてください。  

![新しいエンドポイントのCopilotゴースト提案](../../../04-Using-GitHub-Copilot-with-CSharp/images/020GeneratedCode.gif)  

***重要**: このプロンプトは複数行のC#コードを生成します。生成されたコードが期待通りに動作することを確認するために必ずチェックしてください。*  

生成されたコードは以下のようになります:  

```csharp
// Create a new endpoint named /WeatherForecastByCity/{city}, that accepts a city name in the urls as a paremeter and generates a random forecast for that city
app.MapGet("/WeatherForecastByCity/{city}", (string city) =>
{
    var forecast = new WeatherForecastByCity
    (
        city,
        DateOnly.FromDateTime(DateTime.Now),
        Random.Shared.Next(-20, 55),
        summaries[Random.Shared.Next(summaries.Length)]
    );
    return forecast;
})
.WithName("GetWeatherForecastByCity")
.WithOpenApi();
```  

### 🐍 ステップ 5: 新しいエンドポイントをテストする  

最後に、「Run and Debug」パネルからプロジェクトを開始して新しいエンドポイントが動作していることを確認します。  
「Run and Debug」を選択し、「BackEnd」プロジェクトを選択します。  

![Run and Debugパネルを開き、BackEndプロジェクトを選択](../../../04-Using-GitHub-Copilot-with-CSharp/images/030RunAndDebugTheBackEndProject.png)  

次に、[Run]を押してプロジェクトをビルドして実行します。プロジェクトが実行されると、Codespace URLと元のエンドポイントを使用して元のURLをテストできます:  

```bash
https://< your code space url >.app.github.dev/WeatherForecast
```  

また、新しいエンドポイントもテスト可能です。以下は異なる都市でのサンプルURLです:  
```bash
https://< your code space url >.app.github.dev/WeatherForecastByCity/Toronto

https://< your code space url >.app.github.dev/WeatherForecastByCity/Madrid

https://< your code space url >.app.github.dev/WeatherForecastByCity/<AnyCityName>
```  

両方のテスト結果は以下のようになります:  

![Run and Debugパネルを開き、BackEndプロジェクトを選択](../../../04-Using-GitHub-Copilot-with-CSharp/images/032TestAndDebugUsingUrls.png)  

🚀 おめでとうございます！この演習を通じて、GitHub Copilotを使ってコードを生成するだけでなく、それをインタラクティブかつ楽しく実行しました！GitHub Copilotを使用してコード生成だけでなく、ドキュメント作成やアプリケーションのテストなども行えます。  

### ✨ ボーナス: GitHub Copilot Editsで新機能を追加する  

**Copilot Edits**を使用して、AIを活用したコード編集セッションを開始し、自然言語を使用して複数のファイルにわたるコード変更を迅速に反復します。Copilot Editsは、エディター内で直接編集を適用し、周囲のコードの完全なコンテキストで変更を確認できます。  

ユーザーが検索したい都市を入力し、新しいAPIを呼び出す新しい機能を追加してみましょう。  

1. **Edits**モードウィンドウをGitHub Copilot Chatで開きます。  

![**Edits**モードを選択](../../../04-Using-GitHub-Copilot-with-CSharp/images/OpenEditsWindows.png)  
2. Editsウィンドウの**+Add Files...**ボタンを選択し、**FetchData.razor**と**WeatherForecastClient.cs**を追加します。  
3. チャットに以下を入力します: `ユーザーが天気を知りたい都市を入力できるようにUIを更新し、新しいエンドポイントを都市で呼び出すforecastクライアントを使用してテーブルを更新し、都市も表示するようにしてください。`  
4. **送信**ボタンを選択すると、Editsが変更の反復計画を生成します。  
5. 編集内容を確認し、Editsウィンドウで**Accept**をクリックしてすべての変更を受け入れます。  
6. アプリケーションを実行します。  

> 注意: アプリケーションが実行されない場合や新しいエンドポイントが呼び出されない場合は、変更されたファイルの内容を確認し、エンドポイントが正しく呼び出されていることを確認してください。  

![都市入力を伴う天気ページの画像](../../../04-Using-GitHub-Copilot-with-CSharp/images/WeatherWithEdits.png)  

ここから、スタイリングやアプリケーションに追加する他の機能について質問しながら、さらに反復を続けることができます。  

## 法的通知  

Microsoftおよびその他の貢献者は、このリポジトリ内のMicrosoftドキュメントおよびその他のコンテンツについて[Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode)に基づくライセンスを付与します。詳細は[LICENSE](../../../04-Using-GitHub-Copilot-with-CSharp/LICENSE)ファイルをご覧ください。また、このリポジトリ内のコードについて[MITライセンス](https://opensource.org/licenses/MIT)に基づくライセンスを付与します。詳細は[LICENSE-CODE](../../../04-Using-GitHub-Copilot-with-CSharp/LICENSE-CODE)ファイルをご覧ください。  

Microsoft、Windows、Microsoft Azure、および/またはドキュメントで参照されているその他のMicrosoft製品およびサービスは、米国および/またはその他の国におけるMicrosoftの商標または登録商標である場合があります。このプロジェクトのライセンスは、Microsoftの名称、ロゴ、または商標を使用する権利を付与するものではありません。Microsoftの一般的な商標ガイドラインは、http://go.microsoft.com/fwlink/?LinkID=254653 で確認できます。  

プライバシー情報については、https://privacy.microsoft.com/en-us/ をご覧ください。  

Microsoftおよびその他の貢献者は、各自の著作権、特許、商標に基づくその他の権利を暗黙的、禁反言またはその他の方法で留保します。  

**免責事項**:  
この文書は、機械ベースのAI翻訳サービスを使用して翻訳されています。正確性を追求しておりますが、自動翻訳には誤りや不正確な箇所が含まれる可能性があります。元の言語で記載された原文が信頼できる情報源と見なされるべきです。重要な情報については、専門の人間による翻訳をお勧めします。この翻訳の利用に起因する誤解や解釈の誤りについて、当方は一切の責任を負いません。
