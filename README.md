# footballteam-tools

【部活・草サッカー用】実力差が小さくなるよう均等チーム分けを即時生成する、ブラウザだけで動作するツールです。\
入力データは端末内（localStorage）に保存され、サーバへ送信されません。

## 使い方
1. 公開URLを開く（GitHub Pages もしくは Cloudflare Pages 等）
2. 名簿を「1行1人：`名前, 評価(1–5), 位置(GK/DF/MF/FW)`」で貼り付け
   - 区切りは `,` `，` `、` `・` に対応。全角英数は自動で半角に正規化
   - 評価・位置は省略可（未指定の評価は3）
3. チーム数・試行回数などを選び、「**バランス分けを実行**」

## 運用（管理者向け）
- ルートの `status.json` を編集すると、ユーザー画面に **バナー表示 / メンテナンスモード / 強制アップグレード / 緊急停止** が反映されます。
- バージョンは `index.html` 内の `APP_VERSION` と `status.json` の `version` を合わせてください。

### `status.json` の例
```json
{
  "version": "1.2.0",
  "banner": "9/1(日) 03:00-03:10 メンテナンス予定",
  "maintenance": false,
  "force_upgrade_min_version": "1.2.0",
  "kill_switch": false
}
```

## 開発メモ
- 完全静的（HTML/JS/CSSのみ）。CSP付与済み、描画は `textContent` でXSSを回避。
- 依存ライブラリなし。オフラインでも動作。

## ライセンス
MIT License
