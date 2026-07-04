# カリドメ Web版 v0.2

Chrome拡張をやめてWebアプリ化。**テスターはURLを開いてGoogleログインするだけ**です。

## あなた(開発者)がやること — 1回だけ

### ① GitHub Pagesで公開(5分)
1. GitHubに公開リポジトリを作り、`index.html` をアップロード
2. Settings → Pages → Branch: main で公開
3. `https://あなたのID.github.io/リポジトリ名/` が本番URL

### ② Google CloudでOAuth設定(10分)
1. https://console.cloud.google.com/ でプロジェクト作成
2. 「ライブラリ」で **Google Calendar API** を有効化
3. 「OAuth同意画面」: 外部 / テストモード。テストユーザーに自分と試してもらう人のGmailを追加(メールを入れるだけ・審査不要・100人まで)
4. 「認証情報 → OAuthクライアントID → **ウェブアプリケーション**」
   - 承認済みのJavaScript生成元に ①のURL(例: `https://あなたのID.github.io`)を追加
5. クライアントIDを `index.html` 冒頭の `CLIENT_ID` に貼って再アップロード

### ③ 完了
以後、テスターへの案内は「**このURLを開いてログインしてね**」の一言だけ。
テスター追加 = Google Cloudの同意画面にメールアドレスを1行足すだけ。

## v0.1(拡張版)からの変更点
- zip渡し・デベロッパーモード読み込み → **廃止**。URLだけ
- chrome.identity → Google Identity Services(ログインはGoogle公式ポップアップ)
- 調整中データの保存先: ブラウザのlocalStorage(端末内のみ。サーバー保存なし)

## 変わらないこと
- カレンダーデータはブラウザ⇔Google間のみ。外部送信ゼロ
- 仮押さえ作成 → 敬語メール文生成 → 1クリック確定 → 残り自動リリース

## 将来ストア公開・一般公開する場合の宿題(今は不要)
- テストモードの100人を超えて一般公開するには、Googleの本番審査(プライバシーポリシーページ等)が必要
- そのタイミングでドメイン取得と利用規約を用意
