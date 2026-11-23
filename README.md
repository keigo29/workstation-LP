# Workstation

作業計測タイマー・プロジェクト（ガントチャート・カレンダー）・ノート・図解・毎日確認・スキルツリー・ブックマーク・テンプレートを、ひとつの窓で。データは自分のパソコンの中だけに保存します。Mac・Windows 用、無料。

**ダウンロードと使い方は、このリポジトリのページ（GitHub Pages）を見てください。** ファイルは [Releases](../../releases/latest) にもあります。

| パソコン | ファイル |
|---|---|
| Mac（Apple シリコン：M1・M2・M3・M4 など） | `Workstation-arm64.dmg` |
| Mac（Intel） | `Workstation-x64.dmg` |
| Windows | `Workstation-Setup-x64.exe` |
| Windows（ARM） | `Workstation-Setup-arm64.exe` |

---

## このリポジトリについて（持ち主向け）

ここは配るための公開リポジトリです。アプリのソースは非公開のリポジトリ（`keigo29/WORKSTATION`）にあり、ここにはページのファイルもアプリのファイルも置きません。GitHub Actions がソースを読み込んで、ページとリリースを作ります。

| しくみ | すること |
|---|---|
| `.github/workflows/pages.yml`「ページを公開する」 | ソースの `site/` を GitHub Pages に公開する（手で動かす・アプリを配ったあと・毎日1回） |
| `.github/workflows/release.yml`「アプリを作って配る」 | Mac と Windows のファイルを作り、`v版の番号` のリリースに付ける（手で動かす） |

### はじめにすること（1回だけ）

1. **ソースを読むための鍵を作る**：GitHub の Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token
   - Repository access：**Only select repositories** → `keigo29/WORKSTATION` だけ
   - Permissions：**Contents：Read-only**（ほかは何もいらない）
   - 有効期限は好きな長さで（切れたら作り直して、下の2を入れ直す）
2. **鍵をこのリポジトリに入れる**：このリポジトリの Settings → Secrets and variables → Actions → New repository secret
   - 名前：`SOURCE_TOKEN`、値：1で作った鍵
3. **ページを Actions で出すようにする**：Settings → Pages → Build and deployment → Source を **GitHub Actions** に
4. **アプリを配る**：Actions →「アプリを作って配る」→ Run workflow（ソースのブランチは `main`）。Mac と Windows で作って、20分ほどでリリースができます。終わると「ページを公開する」も自動で動きます
5. ページ：`https://<持ち主>.github.io/<このリポジトリの名前>/`。ページのダウンロードのボタンは、このリポジトリの最新のリリースを指します

### 新しい版を配るとき

1. ソース（`keigo29/WORKSTATION`）の `package.json` の `version` を上げて、main に入れる
2. ここの Actions →「アプリを作って配る」→ Run workflow

ページだけ直したとき（ソースの `site/` を変えたとき）は、「ページを公開する」を手で動かすか、次の日の朝（日本時間 6時ごろ）まで待つと出ます。

### メモ

- ソースのリポジトリの名前を変えたときは、Settings → Secrets and variables → Actions → **Variables** に `SOURCE_REPO`（例 `keigo29/WORKSTATION`）を入れる
- アプリには署名をしていません（Apple・Microsoft の有料の登録が必要なため）。はじめて開くときの止められ方と開き方は、ページとリリースの説明に書いています
- GitHub Pages は月 100 GB・サイト 1 GB まで（このページは 1MB 未満）。アプリのファイルはリリースに置くので、ページの転送量には入りません
