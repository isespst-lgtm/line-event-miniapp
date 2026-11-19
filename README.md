# line-event-miniapp

LINEミニアプリ（イベント申込）のフロント。申込内容は Make のWebhook 経由で Google スプレッドシート（`申込者`シート）に保存されます。

## 構成

- `index.html` … 申込フォーム（LIFF SDK を使用）
- Make シナリオ「イベント申込受付」… Webhook → LINE IDトークン検証 → スプレッドシート追記 → 応答

## 設定

1. `index.html` の `LIFF_ID` を、LINE Developers コンソール［ウェブアプリ設定］タブの LIFF ID に置き換える。
2. LINE Developers コンソールの［エンドポイントURL］に、このページの公開URL（GitHub Pages のURL）を設定する。
3. 申込ページは、イベントごとに次の形式で開く。

   `https://miniapp.line.me/{LIFF ID}?event_id=evt_001&org_id=org_001`

## セキュリティの注意

- このリポジトリは公開です。Make の Webhook URL はページに含まれますが、LINE の ID トークン検証を通らない送信は Make 側で拒否されます。
- APIキーやアクセストークンなど、秘密の値はこのリポジトリに入れないでください。
- ID トークン検証のチャネルID（Make シナリオ内の `client_id`）は、内部チャネル（開発用・審査用・本番用）ごとに異なります。公開環境を切り替えるときは Make 側も合わせて変更してください。
