# 次にやること（v3）

## 1. まず反映するファイル

既存リポジトリでは、以下を上書きしてください。

- `site/index.html`
- `site/app.js`
- `site/style.css`
- `data/briefings.csv`

v3ではニュースカードを少し厚くし、以下の項目を表示できるようにしました。

- 概要
- 何が起きたか
- 背景・文脈
- 見るポイント / なぜ重要か
- 活用メモ / 押さえどころ

## 2. 画像について

`data/briefings.csv` の `image_url` に画像URLを入れるとカードに表示されます。
空欄の場合はカテゴリ名入りのプレースホルダー画像が表示されます。

## 3. コメント自動保存の続き

コメント投稿を自動保存するには、`worker/` のCloudflare Workerをデプロイします。
デプロイ後に出るURLを `site/config.js` の `COMMENT_API_URL` に入れてください。

例：

```js
window.NEWS_BOARD_CONFIG = {
  COMMENT_API_URL: 'https://daily-news-comment-api.xxxxx.workers.dev/comment',
  PASSCODE_ENABLED: false
};
```

その後、`site/config.js` をGitHubにコミットするとGitHub Actionsでサイトが再公開されます。
