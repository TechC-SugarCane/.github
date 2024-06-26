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
- `<機能名>`: 新機能の追加やバグの修正など、機能単位での作業を行うブランチ。<br>
  開発はこのブランチで行います。ブランチ名は`kebab-case`で記述してください。<br>
  またブランチ名は、そのブランチで何を行うかを簡潔に表現するようにしてください。以下に例を示します。

#### ブランチ名の例

- `add-camera-device`
- `fix-login-bug`
- `update-readme`
- `chore-update-dependencies`

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
main へのマージは、最後に承認したレビュワーが責任を持って行ってください。

## コミットの書き方

コミットメッセージは、[Conventional Commits](https://www.conventionalcommits.org/ja/v1.0.0/)の規約に従います。形式は以下の通りです：

```md
<type>(optional <scope>): <description>

[optional <body>]

[optional <footer(s)>]
```

`type`は変更の種類を示し、以下のものを指定する必要があります：

- `feat`: 新しい機能
- `update`: バグ以外の修正
- `fix`: バグの修正
- `docs`: ドキュメント関連
- `ci`: CI/CD 設定
- `refactor`: 仕様に影響がないコード改善（リファクタリング）
- `chore`: ビルド、補助ツール、ライブラリ関連

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

このプロジェクトでは、`Python 3.10.11`を使用しています。<br>
また、ランタイムのバージョン管理には`pyenv`を使用し、パッケージ管理には`venv`を使用しています。

### pyenv (pyenv-win) のインストール

#### macOS

Homebrew というパッケージ管理ツールを使用して `pyenv` をインストールします。<br>
もし、Homebrew がインストールされていない場合は、[Homebrew 公式サイト](https://brew.sh/ja/)を参照してください。

```bash
brew install pyenv

# パスを通す
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc

exec "$SHELL"
```

#### Windows

Windowsの場合、`pyenv-win`をダウンロードします。

```powershell
Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
```

### 環境構築

環境構築については、各リポジトリのREADMEを参照してください。

## コントリビューター向けガイドライン

コントリビューター向けのガイドラインについては、こちらの[CONTRIBUTING.md](https://github.com/TechC-SugarCane/.github/blob/main/CONTRIBUTING.md)を参照してください。
