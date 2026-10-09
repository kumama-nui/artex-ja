# ARTEX 日本語版

ARTEX を基にした自律型セキュリティテストシステムの日本語版です。Go バックエンドと Next.js フロントエンドで構成されています。

**日本語** · [English](README.en.md) · [한국어](README.ko.md)

## 出典

この公開リポジトリは、元のコミット履歴と AGPL-3.0 ライセンスを保持する [Hinln/ARTEX](https://github.com/Hinln/ARTEX) のフォークです。元プロジェクトは [Autumn-27/ARTEX](https://github.com/Autumn-27/ARTEX) です。英語・韓国語の言語切替基盤と関連コードは、同じ元プロジェクトのコミット `160fe13` から派生した [cskwork/ScopeWeaver](https://github.com/cskwork/scopeweaver) のコミット `75a706d` から取り込みました。ScopeWeaver 側の開発履歴はリンク先で確認できます。

元のソースコードと設計は ARTEX の作者に、言語切替基盤は ScopeWeaver の作者に帰属します。Go モジュール名 `github.com/Autumn-27/artex`、内部の `scopeweaver` 名、および既存の互換設定は維持しています。このリポジトリは両プロジェクトの公式リリースではありません。

## 日本語化

- 画面の翻訳カタログ 3,090 件と、サーバーの定型文 1,866 件に日本語訳を追加しました。日本語が既定で、画面上の言語メニューから英語・韓国語に切り替えられます。
- 日時と数値は日本語の形式で表示します。画面から送る API リクエストとダウンロードには選択した言語を渡します。
- エージェントには、ユーザー向けの説明・要約・新規レポートを日本語で書くよう指示します。元の証拠、ユーザー入力、コード、URL、識別子は翻訳対象にしません。

翻訳には機械翻訳を用い、主要な画面用語を校正しました。専門用語や長文には今後の校正が必要です。保存済みのユーザー文書、過去の実行結果、ツールが返す原文は自動翻訳されません。

## 起動方法

PostgreSQL と LLM の設定が必要です。Docker Compose を使う場合:

```bash
git clone https://github.com/kumama-nui/artex-ja.git
cd artex-ja
cp .env.example .env
# .env の POSTGRES_PASSWORD を変更し、必要な LLM API キーを設定
docker compose up -d --build
```

起動後に `http://localhost:8787` を開き、初回は管理者パスワードを設定してください。サーバーの既定言語は `SCOPEWEAVER_LANGUAGE=ja` です。既存の環境変数 `ARTEX_LANGUAGE=ja` も使用できます。データベースに保存済みの言語設定がある場合は、そちらが優先されます。

ソースからのビルド方法、設定項目、アーキテクチャの詳細は [英語版 README](README.en.md) を参照してください。英語版に記載された cskwork のクローン先や配布先は元の派生版の情報です。この日本語版を使う場合は、上記のリポジトリを指定してください。

## 利用範囲とライセンス

本ソフトウェアは **GNU Affero General Public License v3.0（AGPL-3.0）** で公開されています。全文は [LICENSE](LICENSE) を参照してください。元の ARTEX の使用上の制限と免責事項も引き継ぎます。個人学習、ソースコード研究、およびローカルの隔離環境での技術検証に限って使用してください。オンラインのシステムやウェブサイトに対する実際のテストには使用しないでください。詳しくは [英語版のライセンス・免責事項](README.en.md#license-and-disclaimer) を確認してください。

## 開発と翻訳への協力

翻訳の修正では、`web/src/i18n/ja.ts` と `locale/zz_ja.go` を更新してください。`{name}` 形式の画面用プレースホルダー、`%s` 形式の Go フォーマット指定、HTML タグ、技術的な識別子を保ってください。
