<img width="511" height="380" alt="image" src="https://github.com/user-attachments/assets/74cebc73-e0e2-4cbe-ac7c-a926f0c189fa" />

# Git/GitHub 共同開発演習

## 共有リポジトリモデル

---

## 1. 演習概要

本演習では、GitHubの**共有リポジトリモデル**を使用し、3人で共同開発を行った。

GitHub上に1つのリポジトリを作成し、3人が同じリポジトリを共有する。

開発者は`main`ブランチを直接編集するのではなく、それぞれ作業用のブランチを作成して編集を行う。

変更した内容はPull Request（PR）として提出し、リード役が内容をレビューした後、問題がなければ`main`ブランチへMergeする。

今回の演習では、**ターミナルやコマンドプロンプトは使用せず、GitHubのWebブラウザとVisual Studio Code（VS Code）のGUI機能を使用した。**

---

## 2. チーム構成

今回のチームは3人で構成した。

| 担当 | 役割          |
| -- | ----------- |
| A  | リード役・レビュー担当 |
| B  | 開発者1        |
| C  | 開発者2        |

Aは主にリポジトリの管理とPull Requestのレビューを担当した。

BとCは、それぞれ作業ブランチを作成して開発を行い、完成した変更をPull RequestとしてAへ提出した。

---

## 3. 共有リポジトリモデルとは

共有リポジトリモデルとは、複数の開発者が**1つのGitHubリポジトリを共有して開発する方法**である。

今回の演習では、Aがリポジトリを作成し、BとCも同じリポジトリを利用して開発を行った。

```text
                    GitHub
               共有リポジトリ
                      │
                     main
                      │
          ┌───────────┼───────────┐
          │           │           │
          ↓           ↓           ↓
          A           B           C
       リード役    開発者1      開発者2
                      │           │
                      ↓           ↓
                 作業ブランチ  作業ブランチ
                      │           │
                      ↓           ↓
                     PR          PR
                      │           │
                      └─────┬─────┘
                            ↓
                           A
                        レビュー
                            ↓
                          Merge
                            ↓
                           main
```

この方法では、全員が同じリポジトリを使用するため、変更内容を1つのリポジトリで管理できる。

---

# 4. 使用した環境

今回の演習では以下の環境を使用した。

* GitHub
* Visual Studio Code（VS Code）
* Webブラウザ

### GitHubで行った操作

* リポジトリの作成
* Pull Requestの作成
* Pull Requestの確認
* Pull Requestのレビュー
* Pull RequestのMerge
* ブランチの確認

### VS Codeで行った操作

* リポジトリの取得
* ブランチの作成・切り替え
* ファイルの編集
* ファイルの追加
* 変更内容の確認
* Commit
* Push
* Pull

> **注意：今回の演習ではターミナルやコマンドプロンプトは使用していない。**

---

# 5. AがGitHub上にリポジトリを作成

最初にAがGitHub上で演習用のリポジトリを作成した。

GitHubの「New repository」から新しいリポジトリを作成した。

リポジトリ作成後、`main`ブランチを使用して開発を開始した。

---

# 6. Aがindex.htmlを作成

Aは`index.html`を作成し、以下の内容を記述した。

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Git演習</title>
</head>
<body>
    Hello
</body>
</html>
```

作成した`index.html`を`main`ブランチへ追加し、Commitした。

その後、GitHubへPushして`main`ブランチに`index.html`を登録した。

この時点での構成は以下の通りである。

```text
main
└── index.html
```

---

# 7. Bがリポジトリを取得

BはAが作成した共有リポジトリをVS Codeから取得した。

VS CodeのGit機能を使用して、GitHub上のリポジトリをローカル環境に取得した。

取得後、VS Codeでリポジトリを開いた。

---

# 8. Bが作業ブランチを作成

BはVS Codeのブランチ操作から、`main`を元に作業ブランチを作成した。

例：

```text
work-branch-B
```

ブランチ構成は以下のようになる。

```text
main
 │
 └── work-branch-B
```

Bは`main`ではなく、`work-branch-B`上で作業を行った。

---

# 9. Bがindex.htmlを編集

BはVS Codeで`index.html`を開き、内容を編集した。

例えば以下のように変更した。

```html
<body>
    Hello
    <p>Added by B</p>
</body>
```

ファイルを保存すると、VS Codeのソース管理画面に`index.html`が変更されたファイルとして表示される。

```text
ソース管理
└── 変更
    └── index.html
```

---

# 10. BがCommit・Push

BはVS Codeのソース管理機能を使用して変更をCommitした。

Commitメッセージを入力し、Commitを実行した。

例：

```text
add line of B
```

その後、VS CodeのPush機能を使用してGitHubへ変更を送信した。

```text
VS Code
   │
   │ Commit
   ↓
work-branch-B
   │
   │ Push
   ↓
GitHub
```

---

# 11. BがPull Requestを作成

BはGitHubをWebブラウザで開き、自分の作業ブランチから`main`へのPull Requestを作成した。

```text
変更元：
work-branch-B

変更先：
main
```

Pull Requestの内容を確認し、Aがレビューできる状態にした。

---

# 12. AがBのPull Requestをレビュー・Merge

AはGitHubのWebブラウザからBが作成したPull Requestを確認した。

変更されたファイルを確認し、内容に問題がないかをレビューした。

問題がなければPull Requestを承認し、`main`ブランチへMergeした。

```text
work-branch-B
      │
      ↓
Pull Request
      │
      ↓
Aがレビュー
      │
      ↓
   Merge
      │
      ↓
    main
```

これにより、Bが行った変更が`main`へ反映された。

---

# 13. Cがリポジトリを取得

Bと同様に、Cも共有リポジトリをVS Codeから取得した。

CはGitHub上の共有リポジトリをローカル環境に取得し、VS Codeで開いた。

---

# 14. Cが作業ブランチを作成

CはVS Codeで`main`を元に作業ブランチを作成した。

例：

```text
work-branch-C
```

```text
main
 │
 ├── work-branch-B
 │       └── Merge済み
 │
 └── work-branch-C
```

Cは`main`を直接編集せず、`work-branch-C`上で作業を行った。

---

# 15. Cがindex.htmlを編集

CもVS Codeで`index.html`を編集した。

例えば、以下のようにCの変更を追加した。

```html
<body>
    Hello
    <p>Added by B</p>
    <p>Added by C</p>
</body>
```

変更したファイルはVS Codeのソース管理画面から確認できる。

---

# 16. CがCommit・Push

CはVS Codeのソース管理機能を使用して変更をCommitした。

例：

```text
add line of C
```

その後、VS CodeからGitHubへPushした。

```text
VS Code
   │
   │ Commit
   ↓
work-branch-C
   │
   │ Push
   ↓
GitHub
```

---

# 17. CがPull Requestを作成

CはGitHubのWebブラウザからPull Requestを作成した。

```text
変更元：
work-branch-C

変更先：
main
```

AがレビューできるようにPull Requestを作成した。

---

# 18. AがCのPull Requestをレビュー・Merge

AはGitHub上でCのPull Requestを確認した。

Cが変更した`index.html`の内容を確認し、問題がないことを確認した。

その後、Pull Requestを承認して`main`へMergeした。

```text
work-branch-C
      │
      ↓
Pull Request
      │
      ↓
Aがレビュー
      │
      ↓
   Merge
      │
      ↓
    main
```

これにより、BとCの変更が`main`へ反映された。

---

# 19. Aがmainブランチを最新化

BとCの変更が`main`へMergeされたため、AはVS Codeでローカルの`main`ブランチを最新化した。

まずVS Codeで`main`ブランチへ切り替えた。

その後、VS CodeのPull機能を使用してGitHub上の最新の変更を取得した。

```text
GitHub
   │
   │ 最新のmain
   ↓
VS Code
   │
   ↓
Aのローカルmain
```

これにより、Aのローカル環境にもBとCの変更が反映された。

---

# 20. Aが作業ブランチを作成

Aは最新の`main`を元に、新しい作業ブランチを作成した。

例：

```text
work-branch-A
```

```text
main
 │
 ├── work-branch-B
 │       └── Merge済み
 │
 ├── work-branch-C
 │       └── Merge済み
 │
 └── work-branch-A
```

---

# 21. Aがindex.htmlを編集

AはVS Codeで`index.html`を編集し、自分の変更を追加した。

```html
<body>
    Hello
    <p>Added by B</p>
    <p>Added by C</p>
    <p>Added by A</p>
</body>
```

---

# 22. AがCommit・Push

AはVS Codeのソース管理機能を使用して変更をCommitした。

例：

```text
add line of A
```

その後、VS CodeからGitHubへPushした。

---

# 23. AがPull Requestを作成・Merge

AはGitHubのWebブラウザから、自分の作業ブランチから`main`へのPull Requestを作成した。

```text
work-branch-A
      │
      ↓
Pull Request
      │
      ↓
    main
```

変更内容を確認した後、Pull RequestをMergeして`main`へ取り込んだ。

---

# 24. BとCがmainを最新化

Aの変更が`main`へMergeされたため、BとCはそれぞれVS Codeで`main`ブランチを最新化した。

```text
             GitHub
                │
          最新のmain
                │
       ┌────────┴────────┐
       ↓                 ↓
      BのVS Code        CのVS Code
       │                 │
       ↓                 ↓
   最新のmain        最新のmain
```

それぞれVS CodeのPull機能を使用して最新の変更を取得した。

---

# 25. Bがstylesheet.cssを追加

Bは最新の`main`から新しい作業ブランチを作成した。

例：

```text
work-branch-B-css
```

その後、VS Codeで`stylesheet.css`を新しく作成した。

```css
body {
    font-family: sans-serif;
}

p {
    font-size: 20px;
}
```

---

# 26. BがCommit・Push

BはVS Codeのソース管理画面から`stylesheet.css`をステージングし、Commitした。

例：

```text
add stylesheet.css
```

その後、VS CodeからGitHubへPushした。

---

# 27. BがPull Requestを作成

BはGitHubブラウザから`work-branch-B-css`から`main`へのPull Requestを作成した。

```text
work-branch-B-css
        │
        ↓
   Pull Request
        │
        ↓
      main
```

Aをレビュー担当としてPull Requestを作成した。

---

# 28. AがBのPull Requestをレビュー・Merge

AはGitHubブラウザからBのPull Requestを確認した。

`stylesheet.css`の内容を確認し、問題がなければPull Requestを承認して`main`へMergeした。

これで指定された一連の演習が完了した。

---

# 29. 今回の作業全体

今回の3人での作業をまとめると、以下のようになる。

```text
                         A
                    リード役
                       │
                       ↓
                リポジトリ作成
                       │
                       ↓
                  index.html
                       │
                       ↓
                      main
                       │
          ┌────────────┴────────────┐
          ↓                         ↓
         B                           C
      開発者1                     開発者2
          │                         │
   ブランチ作成                ブランチ作成
          │                         │
   index.html編集             index.html編集
          │                         │
       Commit                    Commit
          │                         │
        Push                      Push
          │                         │
          ↓                         ↓
         PR                        PR
          │                         │
          └────────────┬────────────┘
                       ↓
                  Aがレビュー
                       ↓
                    Merge
                       ↓
                     main
                       │
                       ↓
                  AがPull
                       │
                       ↓
              Aが作業ブランチ作成
                       │
                 index.html編集
                       │
                    Commit
                       │
                     Push
                       │
                       ↓
                      PR
                       ↓
                    Merge
                       ↓
                     main
                       │
              ┌────────┴────────┐
              ↓                 ↓
             B                   C
              │                 │
           mainをPull        mainをPull
              │                 │
              └────────┬────────┘
                       ↓
                  Bが作業
                       │
             stylesheet.css追加
                       │
                    Commit
                       │
                     Push
                       │
                       ↓
                      PR
                       ↓
                  Aがレビュー
                       ↓
                     Merge
                       ↓
                     main
```

---

# 30. GitHubとVS Codeの役割

今回の演習では、GitHubとVS Codeを以下のように使い分けた。

| 操作             | 使用した環境  |
| -------------- | ------- |
| リポジトリ作成        | GitHub  |
| リポジトリの取得       | VS Code |
| ブランチ作成         | VS Code |
| ブランチ切り替え       | VS Code |
| ファイル編集         | VS Code |
| ファイル追加         | VS Code |
| 変更確認           | VS Code |
| Commit         | VS Code |
| Push           | VS Code |
| Pull           | VS Code |
| Pull Request作成 | GitHub  |
| Pull Request確認 | GitHub  |
| コードレビュー        | GitHub  |
| Merge          | GitHub  |

今回の演習では、ターミナルを使用せず、**VS CodeとGitHubのGUIだけで一連のGit操作を行った。**

---

# 31. Gitの基本的な流れ

今回の演習を通して、Git/GitHubを使用した共同開発では、以下の流れで作業を行うことを確認した。

```text
main
 ↓
作業ブランチを作成
 ↓
ファイルを編集
 ↓
変更をCommit
 ↓
Push
 ↓
GitHubでPull Request作成
 ↓
レビュー
 ↓
Merge
 ↓
main
```

複数人で開発する場合も、基本的にはこの流れを繰り返す。

---

# 32. Git Graphによる履歴確認

今回の演習では、複数の作業ブランチを作成し、それぞれからPull Requestを作成して`main`へMergeした。

Git Graphを確認すると、複数のブランチが作成され、それぞれの変更が`main`へ取り込まれていることが確認できる。

### 実際のGit履歴

【ここにGit Graphのスクリーンショットを貼る】

今回のGit Graphでは、以下のようなMerge履歴を確認できる。

```text
Merge pull request
        ↓
      main
        ↑
      PR
        ↑
   作業ブランチ
```

この履歴から、作業ブランチで開発を行い、Pull Requestを経由して`main`へ変更を取り込んだことが分かる。

---

# 33. スクリーンショット

実際の演習で使用した画面を以下に掲載する。

## GitHub

### リポジトリ作成

【GitHubのリポジトリ画面】

### Pull Request

【Pull Requestの画面】

### Pull Requestレビュー

【レビュー画面】

### Merge

【Merge後の画面】

---

## Visual Studio Code

### ブランチ作成

【VS Codeのブランチ操作画面】

### ソース管理

【VS Codeのソース管理画面】

### Commit

【Commit時の画面】

### Push / Pull

【同期・Push・Pull操作の画面】

---

# 34. まとめ

今回の演習では、A・B・Cの3人で共有リポジトリモデルによる共同開発を行った。

Aがリード役としてリポジトリを管理し、BとCが開発者としてそれぞれ作業ブランチを使用して開発を行った。

開発者は`main`を直接編集せず、

```text
作業ブランチ作成
        ↓
ファイル編集
        ↓
Commit
        ↓
Push
        ↓
Pull Request
        ↓
Aによるレビュー
        ↓
Merge
        ↓
main
```

という手順で変更を`main`へ取り込んだ。

また、A自身が作業を行う場合も作業ブランチを作成し、Pull Requestを利用して`main`へ変更を取り込んだ。

今回の演習では、**GitHubブラウザとVS Codeのみを使用し、ターミナルを使用せずにGitのブランチ管理、Commit、Push、Pull、Pull Request、レビュー、Mergeという一連の共同開発の流れを実践した。**
