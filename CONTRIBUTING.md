**このガイドラインは現在工事中です。**

# Contributing Guide

## はじめに

このドキュメントは、プロジェクトの開発ガイドラインを提供することを目的としています。<br>
チームメンバー全員が効率的かつ一貫した方法で作業できるよう、以下のポリシーに従ってください。

## 機能の追加やバグの修正

新しい機能の提案やバグの報告は、Issues を通じて行います。新しい Issue は、各リポジトリのIssue Formから作成してください。

## ブランチ戦略について

このプロジェクトでは、以下のブランチ戦略を採用しています。

### ブランチの種類

- `main`: デフォルトブランチ。本番環境にデプロイされるコードがマージされます。
- `<issue-num>-<機能名>`: 新機能の追加やバグの修正など、機能単位での作業を行うブランチ。<br>
  開発はこのブランチで行います。ブランチ名は`kebab-case`で記述してください。<br>
  branch名の前には、**作業する内容に紐づいたissueの番号**を付けてください。
  またブランチ名は、そのブランチで何を行うかを簡潔に表現するようにしてください。以下に例を示します。

#### ブランチ名の例

- `11-add-camera-device`
- `27-fix-login-bug`
- `30-update-readme`
- `56-chore-update-dependencies`

など

## Pull Request の作成

新しい機能の追加やバグの修正を行う場合、Pull Request(PR)を作成してください。<br>

### PR の作成手順

1. ブランチを作成し、作業を行います。
2. 作業が完了したら、`main`ブランチに対して PR を作成します。
3. PR のタイトルには、作業内容を簡潔に記述し、本文はテンプレートに従って記述してください。
4. レビュワーを指定し、レビューを依頼します。全ての変更は、`CODEOWNERS` によって、@KorRyu3 が自動的にレビュワーに指定されます。

### コードレビュー

PR作成後、指定したレビュワーによってコードの査読が行われます。課題が発見された場合には、記述修正の提案がおこなわれます。

修正が必要な場合は、修正を行い、再度レビューを依頼してください。

その後、レビュワーはコードの変更内容に問題がないと判断した場合、PR を承認します。

このプロジェクトでは、基本的に1名以上のレビュワーによる承認が必要です。

### PR のマージについて

PR の Auto merge 設定は切ってあります。<br>
main へのマージは、PRを出したレビュイーが責任を持って行ってください。

## コミットの書き方

コミットメッセージは、[Conventional Commits](https://www.conventionalcommits.org/ja/v1.0.0/)の規約に従います。形式は以下の通りです：

```md
<type>(optional <scope>): <description>

[optional <body>]

[optional <footer(s)>]
```

`type`は変更の種類を示し、以下のものを指定する必要があります：

- `feat`: 新機能
- `fix`: バグ修正
- `docs`: ドキュメントのみの変更
- `style`: フォーマットの変更（コードの動作に影響しないスペース、フォーマット、セミコロンなど）
- `refactor`: リファクタリングのための変更（機能追加やバグ修正を含まない）
- `perf`: パフォーマンスの改善のための変更
- `test`: 不足テストの追加や既存テストの修正
- `build`: ビルドシステムや外部依存に関する変更（スコープ例: gulp, broccoli, npm）
- `ci`: CI用の設定やスクリプトに関する変更（スコープ例: GitHub Actions, Travis, Circle, BrowserStack)
- `chore`: その他の変更（ソースやテストの変更を含まない）
- `revert`: 以前のコミットに復帰

その他説明:

- `scope`は変更が影響を与える範囲です。（オプション）
- `description`は変更内容を簡潔に説明します。
- `body`は変更内容の詳細を記述します。（オプション）
- `footer`は関連する Issue 番号や、破壊的変更がある場合に記述します。（オプション）

### 例

```md
feat(login): ユーザーログイン機能を追加

ログイン API を実装し、セキュリティを強化しました。具体的には〜〜

BREAKING CHANGE: 新しい認証フローを導入したため、古い認証メソッドは削除されます。
```

<!-- 開発環境について -->

## 開発環境

Pythonランタイムとパッケージのバージョン管理には`uv`を使用しています。

コードのFormatter, Linterには、`Ruff`を使用しています。
VS Codeをメインで使っている方は、[Ruffの拡張機能](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff)をインストールしてください。

### uv のインストール

#### macOS

Homebrew というパッケージ管理ツールを使用して `uv` をインストールします。<br>
もし、Homebrew がインストールされていない場合は、[Homebrew 公式サイト](https://brew.sh/ja/)を参照してください。

```bash
brew install uv

# コマンド補完
echo 'eval "$(uv generate-shell-completion zsh)"' >> ~/.zshrc

exec "$SHELL"
```

#### Windows

インストールするにはPowerShellの実行ポリシーを変えなければならないので、下記を管理者権限のPowerShellで実行してください。

```powershell
PowerShell Set-ExecutionPolicy RemoteSigned
```

uvのインストール

```powershell
winget install --id astral-sh.uv --source winget
```

### cudaのインストール

お家のWindowsでGPUを使って学習/推論させる人は、`cuda 11.8`, `cuDNN 8.9.2.26`, `Visual C++ 2019 runtime`を事前にインストールしてください。

- [cuda 11.8](https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Windows&target_arch=x86_64&target_version=11&target_type=exe_local)
- [cuDNN 8.9.2.26](https://developer.nvidia.com/rdp/cudnn-archive)<br>
-> このサイトの"Download cuDNN v8.9.2 (June 1st, 2023), for CUDA 11.x"の"Local Installer for Windows (Zip)"をインストールする
- [Visual C++ 2019 runtime](https://learn.microsoft.com/ja-jp/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-microsoft-visual-c-redistributable-version)<br>
-> このサイトのX86版をインストール

### 環境構築

環境構築については、各リポジトリのREADMEを参照してください。
