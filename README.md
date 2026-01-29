# 友情テスト - ランディングページ

友情テストアプリの招待リンク用ランディングページです。

## セットアップ手順

### 1. GitHubリポジトリの作成

1. GitHub で新しいリポジトリ `FriendshipTest-link` を作成
2. このフォルダの内容をアップロード

### 2. GitHub Pages の有効化

1. リポジトリの Settings → Pages
2. Source: `Deploy from a branch`
3. Branch: `main` / `root`
4. Save

### 3. ファイル構成

```
FriendshipTest-link/
├── index.html                      # トップページ
├── join/
│   └── index.html                  # 招待ページ（メイン）
├── .well-known/
│   └── apple-app-site-association  # Universal Links設定
├── ogp.png                         # SNSシェア用画像（要作成）
└── README.md
```

### 4. 重要: apple-app-site-association の設定

`.well-known/apple-app-site-association` ファイルを編集：

```json
{
  "applinks": {
    "apps": [],
    "details": [
      {
        "appID": "TEAMID.BUNDLEID",
        "paths": ["/FriendshipTest-link/join/*"]
      }
    ]
  }
}
```

- `TEAMID`: Apple Developer の Team ID（例: `82W29FYP37`）
- `BUNDLEID`: アプリの Bundle ID（例: `com.example.FriendshipTest`）

### 5. App Store ID の更新

`join/index.html` 内の以下の行を実際のApp Store IDに変更：

```javascript
const appStoreUrl = 'https://apps.apple.com/app/id0000000000';
```

### 6. OGP画像の作成

SNSでシェアされた時に表示される画像を `ogp.png` として配置：
- 推奨サイズ: 1200 x 630 px
- アプリのロゴや「友情テスト」のタイトルを含める

### 7. GitHub Pages のカスタムドメイン（オプション）

怪しくないURLにしたい場合：

1. 独自ドメインを取得（例: `yuujou-test.com`）
2. DNS設定でGitHub Pagesを指定
3. リポジトリのSettings → Pages → Custom domain

推奨ドメイン名:
- `yuujou-test.com`
- `friendship-test.jp`
- `tomosindan.com`

## URL形式

```
https://sota-7.github.io/FriendshipTest-link/join/?code=ABC123
```

このURLを友達に送ると：
1. アプリがインストール済み → アプリが開いてコードが自動入力
2. アプリ未インストール → ランディングページでApp Storeへ誘導

## 注意事項

- Universal Links が機能するには、HTTPS が必須
- GitHub Pages は自動で HTTPS 対応
- `apple-app-site-association` は JSON 形式で、拡張子なし
