# Footprints_SitePackages

[Footprints](https://github.com/bayashiP/Footprints)（行きつけの店・施設を記録する Android アプリ）の
**サイトパッケージ**配布リポジトリ。

サイトパッケージとは、似た種類の店舗・スポットをまとめた JSON です。アプリの
「設定 → サイトパッケージ」からカタログを開き、選んでインポートすると、その店舗がまとめて登録されます。

## 構成

| ファイル | 内容 |
| --- | --- |
| `index.json` | カタログ（アプリが最初に読む一覧） |
| `packages/<id>.json` | パッケージ本体（店舗データ） |

アプリは `https://raw.githubusercontent.com/bayashiP/Footprints_SitePackages/master/` 配下を
認証なしで取得します。

## パッケージの追加・更新

フォーマットの定義と作成手順は、Footprints 本体リポジトリの
`.claude/skills/create-site-package/SKILL.md`（Claude Code スキル `/create-site-package`）にあります。

原則:

- 緯度経度・住所を創作しない。OpenStreetMap（Overpass / Nominatim）など実在のデータソースから取得する
- `id` は一度配布したら変更しない（アプリがインポート済み判定に使う）
- `overview` に「どんな店舗のセットか」と**データの出典**を書く（アプリ上で表示される）
- 内容を更新したら `version` を +1 する

## ライセンス・出典

各パッケージの出典は、パッケージ内の `overview` に記載しています。OpenStreetMap 由来のデータは
[ODbL](https://www.openstreetmap.org/copyright) の下で提供されています（© OpenStreetMap contributors）。
