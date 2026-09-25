# 自分だけで利用する公開構成

このリポジトリは **Privateのまま維持**してください。

## 推奨構成

- GitHub: Privateリポジトリとしてソースを保管
- Cloudflare Pages: Private GitHubリポジトリからデプロイ
- Cloudflare Access: 自分のメールアドレスだけ許可

## Cloudflare Pages

1. Cloudflareにログイン
2. Workers & Pages を開く
3. Create application → Pages → Connect to Git
4. GitHubを接続
5. GitHub AppのRepository accessは「Only select repositories」を選択
6. MonsterHunterSkillSim だけを許可
7. Production branch: main
8. Build command: 空欄 または exit 0
9. Build output directory: /

## Access制限

Pagesを公開しただけではURLを知る人がアクセスできる可能性があります。
Cloudflare Zero Trust → Access controls → Applications から、Pagesの本番URLを保護してください。

推奨ポリシー:
- Action: Allow
- Include: Emails
- Value: 自分のメールアドレスのみ

これにより、サイトにアクセスした際に認証が要求され、自分のメールアドレスで認証した場合のみ利用できます。

## 注意

GitHub Pagesを有効にしないでください。
この構成ではGitHub PagesではなくCloudflare Pagesを利用します。

## 登録データ

鑑定護石・巨戟アーティア・マイセットはブラウザのlocalStorageに保存されます。
同じ本番URLを使い続ければ、サイト更新後も同じブラウザでは原則そのまま利用できます。

念のため「全データ書き出し」で定期的にバックアップしてください。
