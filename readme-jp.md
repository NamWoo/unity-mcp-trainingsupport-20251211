# MCP for Unity

## 概要

本ドキュメントでは、Unity 上で AI Agent を直接接続して開発するための  
**MCP（Model Context Protocol）** のインストールおよび設定方法を説明します。

Unity が無料で提供している **工場（Factory）および倉庫（Warehouse）シーン** を活用し、  
MCP を使用してロボットを配置し、動作させるところまでを試します。

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/9368f4cb-7b6b-42e6-91cb-d1e265f6fb93" />
<img width="1920" height="1017" alt="Image" src="https://github.com/user-attachments/assets/c0ab072c-8be0-46ff-af8c-efd49902ec55" />

### 使用するサンプルアセット

* **Unity Warehouse（HDRP）**  
  https://assetstore.unity.com/packages/3d/environments/industrial/unity-warehouse-276394
* **Unity Factory（HDRP）**  
  https://assetstore.unity.com/packages/3d/environments/industrial/unity-factory-276400

### 全体の流れ

1. GPT サービスのインストール  
2. Unity のインストール  
3. MCP for Unity のインストール  
4. Unity での開発開始  

---

## AI クライアントのインストール

MCP のクライアントとして使用する GPT サービスをインストールします。

![service-list](./imgs/03-MCP/2025-12-14%2009%2029%2008.png)

使用可能なサービスは以下の通りです。

1. Google **Antigravity**
2. **Cursor**
3. **Claude Code**
4. OpenAI **Codex**

上記のサービスはすべて動作確認済みです。  
最終的な性能は **使用するモデル** や **無料／有料プラン** によって変わります。  
すべて無料プランがあるため、まずは無料で試して問題ありません。

本ドキュメントでは以下の構成で進めます。

- **Cursor**：Cursor デスクトップアプリを使用  
- **Codex（OpenAI）**：CLI（ターミナル）を使用  

---

### Cursor のインストール

以下のサイトからダウンロードしてインストールするだけです。

1. https://cursor.com/download  
2. https://docs.cursor.com/ja/get-started/installation  

---

### Codex のインストール

#### Windows（WSL）

https://developers.openai.com/codex/windows

1. WSL 環境を構築
2. `Ctrl + R` を押す
3. `cmd` を実行
4. ターミナルで WSL に入る
   ```bash
   wsl
   ```
5. nvm をインストール
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
   ```
6. 新しい WSL ターミナルを開き、Node.js をインストール
   ```bash
   nvm install 22
   ```
7. Codex を起動
   ```bash
   codex
   ```

![wsl-install1](./imgs/03-MCP/2025-12-14%2009%2046%2054.png)  
![wsl-install2](./imgs/03-MCP/2025-12-14%2009%2047%2047.png)  
![wsl-install3](./imgs/03-MCP/2025-12-14%2009%2047%2059.png)

#### macOS

https://developers.openai.com/codex/cli

```bash
brew install codex
codex
```

---

## Unity のインストール

### Unity Hub のインストール

https://docs.unity3d.com/hub/manual/InstallHub.html

### Unity Editor のインストール

https://unity.com/releases/editor/archive

現在の日付 기준で **Unity 6000.3.1f1** までダウンロード可能です。

本ドキュメントでは以下のバージョンを使用します。

* **Unity 6000.0.64f1**

直接リンク：
```
unityhub://6000.0.64f1/5360b7cd7953
```

バージョン表記の意味：
- `6000` → Unity 6
- `6000.0` → Unity 6.0
- `6000.3` → Unity 6.3

---

## Unity プロジェクトの作成

### Unity Hub での作業

1. **Projects** → **New Project** を選択
2. インストール済みの Editor バージョンを確認
3. **【重要】** テンプレートは **High Definition 3D（HDRP）** を選択
4. プロジェクト名と保存先を設定
5. **Create Project** をクリック

![start-newproject](./imgs/02-start/2025-12-14%2008%2044%2032.png)

### Unity Editor での作業

1. **Window → Package Manager** を開く
2. 左側のタブ説明：
   - **In Project**：現在のプロジェクトに含まれるアセット
   - **Unity Registry**：Unity 提供のアセット
   - **My Assets**：所有しているアセット
3. 無料の Warehouse アセットを追加
   - https://assetstore.unity.com/packages/3d/environments/industrial/unity-warehouse-276394
   - **Add to My Assets** を選択

![start-download](./imgs/02-start/2025-12-14%2009%2004%2010.png)

4. Unity Editor に戻り：
   - **Package Manager** を開く
   - **Unity Warehouse** を確認
   - **Download** をクリック
   - ダウンロード完了後 **Import**
   - インポート画面で **Import** を選択

![start-import](./imgs/02-start/2025-12-14%2009%2012%2030.png)

---

## MCP for Unity のダウンロードと設定

### インストール

1. **Window → Package Manager** を開く
2. 上部の **+** をクリック → **Add package from git URL…**
3. 以下を入力
```
https://github.com/CoplayDev/unity-mcp.git?path=/MCPForUnity
```
4. インストール完了後、**Window → MCP for Unity** が表示されることを確認

![mcp-window-tap](./imgs/03-MCP/2025-12-14%2009%2025%2047.png)

---

### 設定（重要）

1. **Settings**
   - **Show Debug Logs** を有効化
2. **Connection**
   - **Transport** を `Stdio` に設定
   - **Start Session** をクリック
   - 緑色インジケーターを確認
3. **Client Configuration**
   - 使用する AI Agent（例：`Cursor`）を選択
   - **Configure** をクリック
   - 緑色インジケーターを確認

---

## 動作確認と開始

### Unity 側

1. **Window → MCP for Unity** を開く
2. 以下を確認：
   - Session が緑色
   - Client Configuration が緑色

![setting-green](./imgs/03-MCP/2025-12-14%2010%2026%2003.png)

### Cursor 側

1. Cursor の設定（歯車アイコン）を開く
2. **Tools & MCP** を選択
3. **Installed MCP Servers** に `unityMCP` が表示され、緑色であることを確認

### HDRP について

Unity Warehouse サンプルは **HDRP** ベースで作成されています。  
必ず **HDRP プロジェクト** を使用してください。

---

## 開始

以下すべてが緑色であれば準備完了です。

1. Unity プロジェクトが起動している
2. MCP セッションが有効
3. クライアントが接続済み

Cursor から LLM プロンプトを入力し、Unity 開発を開始できます。

---

## LLM コマンド例

```text
今開いているシーンに工場の warehouse を構成したい。
Project ウィンドウからアセットを探し、warehouse の建物アセットがあれば配置してほしい。
その中にラックやパレット、人などを配置して、内部が自然に埋まるようにしてほしい。
```
