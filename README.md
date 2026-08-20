<img width="511" height="380" alt="image" src="https://github.com/user-attachments/assets/74cebc73-e0e2-4cbe-ac7c-a926f0c189fa" />
# Git/GitHub 共同開発演習

## 共有リポジトリモデル

## 1. 演習概要

本演習では、GitHubの**共有リポジトリモデル**を使用し、2人で共同開発を行った。

共有リポジトリモデルでは、複数の開発者が1つのGitHubリポジトリを共有し、それぞれが作業ブランチを作成して開発を行う。

今回の演習では、GitHubのWeb画面とVisual Studio Code（VS Code）のGUI機能を使用して、ブランチ作成、ファイル編集、Commit、Push、Pull Request、レビュー、Mergeなどの操作を行った。

### 役割

| 担当 | 役割          |
| -- | ----------- |
| A  | リード役・レビュー担当 |
| B  | 開発者         |

---

# 2. 使用した環境

今回の演習では、以下の環境を使用した。

* GitHub
* Visual Studio Code
* GitHubブラウザ
* VS Codeのソース管理機能

> ※今回の演習ではターミナルやコマンドプロンプトは使用していない。

---

# 3. 共有リポジトリモデルとは

共有リポジトリモデルとは、複数の開発者が**同じGitHubリポジトリを共有して開発する方式**である。

今回の演習では、AがGitHub上にリポジトリを作成し、Bもそのリポジトリにアクセスして作業を行った。

```text
                  GitHub
             共有リポジトリ
                    │
          ┌─────────┴─────────┐
          │                   │
          A                   B
      リード役              開発者
          │                   │
          └─────────┬─────────┘
                    │
                  main
                    │
              作業ブランチ
                    │
                   PR
                    │
                 Review
                    │
                  Merge
                    ↓
                  main
```

`main`ブランチを直接編集するのではなく、作業用のブランチを作成して変更を行い、Pull Requestを利用して`main`へ変更を取り込む。

---

# 4. AがGitHubにリポジトリを作成

最初にAがGitHub上で演習用のリポジトリを作成した。

GitHubの「New repository」から新しいリポジトリを作成し、`main`ブランチを用意した。

その後、Aが`index.html`を作成した。

内容は以下の通りである。

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

作成した`index.html`を`main`ブランチへ追加した。

---

# 5. Bがリポジトリを取得

BはAが作成した共有リポジトリをVS Codeで開いた。

VS Codeでは、GitHubとの連携機能を使用してリポジトリを取得した。

取得後、VS Codeのソース管理画面から現在のブランチを確認した。

```text
main
```

---

# 6. Bが作業ブランチを作成

BはVS Codeのブランチ操作から、`main`を元に作業ブランチを作成した。

今回作成したブランチ：

```text
work-branch-B
```

ブランチの状態は以下のようになる。

```text
main
 │
 └── work-branch-B
```

Bは以降の作業を`work-branch-B`上で行った。

---

# 7. Bがindex.htmlを編集

BはVS Codeで`index.html`を開き、内容を編集した。

例えば以下のように変更した。

```html
<body>
    Hello
    <p>Added by B</p>
</body>
```

変更すると、VS Codeの「ソース管理」画面に変更されたファイルが表示される。

```text
ソース管理
 └─ 変更
     └─ index.html
```

---

# 8. BがCommit・Push

BはVS Codeのソース管理画面を使用して変更をCommitした。

まず、変更された`index.html`をステージングし、Commitメッセージを入力した。

例：

```text
add line of B
```

その後、VS Codeの「変更の同期」などの機能を使用してGitHubへPushした。

これにより、GitHub上にBの作業ブランチの変更が反映された。

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

# 9. BがPull Requestを作成

GitHubをブラウザで開き、Bの作業ブランチから`main`ブランチへのPull Requestを作成した。

```text
変更元：
work-branch-B

変更先：
main
```

つまり、以下のような流れになる。

```text
work-branch-B
      │
      │ Pull Request
      ↓
     main
```

Pull Requestには変更内容を記入し、Aがレビューできるようにした。

---

# 10. AがPull Requestをレビュー

AはGitHubブラウザからBが作成したPull Requestを確認した。

変更されたファイルを確認し、以下の点を確認した。

* `index.html`の変更内容
* 不要な変更がないか
* 変更内容に問題がないか
* `main`へMergeして問題ないか

問題がないことを確認した後、AがPull Requestを承認し、`main`ブランチへMergeした。

```text
B
│
└─ work-branch-B
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

---

# 11. Aがmainブランチを最新化

Bの変更が`main`へMergeされたため、AはVS Codeでローカルの`main`ブランチを最新の状態に更新した。

まずVS Code上で`main`ブランチへ切り替えた。

その後、VS Codeのソース管理画面からGitHubの最新の変更を取得した。

```text
GitHub
  │
  │ 最新のmain
  ↓
VS Code
  │
  ↓
ローカルのmainを更新
```

これにより、Aのローカル環境にもBが行った変更が反映された。

---

# 12. Aが作業ブランチを作成

Aは最新化した`main`ブランチを元に、新しい作業ブランチを作成した。

例：

```text
work-branch-A
```

ブランチ構成は以下のようになる。

```text
main
 │
 ├── work-branch-B
 │       └── Merge済み
 │
 └── work-branch-A
```

---

# 13. Aがindex.htmlを編集

AはVS Codeで`index.html`を編集した。

Bが行った変更を残したまま、A自身の変更を追加した。

```html
<body>
    Hello
    <p>Added by B</p>
    <p>Added by A</p>
</body>
```

---

# 14. AがCommit・Push

AはVS Codeのソース管理画面から変更をCommitした。

Commitメッセージの例：

```text
add line of A
```

その後、VS CodeからGitHubへPushした。

```text
VS Code
   │
   │ Commit
   ↓
work-branch-A
   │
   │ Push
   ↓
GitHub
```

---

# 15. AがPull Requestを作成・Merge

AはGitHubブラウザから、自分の作業ブランチから`main`へのPull Requestを作成した。

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

# 16. Bがmainブランチを最新化

Aの変更が`main`へMergeされたため、BもVS Codeで`main`ブランチへ切り替えた。

その後、VS Codeのソース管理機能を使用してGitHubから最新の変更を取得した。

```text
GitHub
  │
  │ 最新のmain
  ↓
VS Code
  │
  ↓
Bのローカルmain
```

これにより、Bの環境にもAの変更が反映された。

---

# 17. Bがstylesheet.css用の作業ブランチを作成

Bは最新の`main`を元に、新しい作業ブランチを作成した。

例：

```text
work-branch-B-css
```

```text
main
 │
 ├── work-branch-B
 │       └── Merge済み
 │
 ├── work-branch-A
 │       └── Merge済み
 │
 └── work-branch-B-css
```

---

# 18. Bがstylesheet.cssを追加

BはVS Codeで新しく`stylesheet.css`を作成した。

例：

```css
body {
    font-family: sans-serif;
}

p {
    font-size: 20px;
}
```

VS Codeのソース管理画面から、新しく追加された`stylesheet.css`を確認した。

```text
ソース管理
 └─ 変更
     └─ stylesheet.css
```

---

# 19. BがCommit・Push

BはVS Codeのソース管理機能を使用して`stylesheet.css`をCommitした。

Commitメッセージの例：

```text
add stylesheet.css
```

その後、VS CodeからGitHubへPushした。

---

# 20. BがPull Requestを作成

BはGitHubブラウザから、`work-branch-B-css`から`main`へのPull Requestを作成した。

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

# 21. Aがレビュー・Merge

AはGitHubブラウザからBのPull Requestを確認した。

`stylesheet.css`の内容を確認し、問題がないことを確認した。

その後、Pull Requestを承認して`main`へMergeした。

これで今回指定された一連の演習が完了した。

---

# 22. 今回の作業全体

今回の作業をまとめると、以下の流れになる。

```text
【A】
GitHubにリポジトリ作成
        ↓
index.htmlをmainへ追加
        ↓
────────────────────────

【B】
リポジトリを取得
        ↓
作業ブランチ作成
        ↓
index.html編集
        ↓
VS CodeからCommit・Push
        ↓
GitHubでPull Request
        ↓
────────────────────────

【A】
Pull Requestレビュー
        ↓
mainへMerge
        ↓
mainを最新化
        ↓
作業ブランチ作成
        ↓
index.html編集
        ↓
Commit・Push
        ↓
Pull Request
        ↓
Merge
        ↓
────────────────────────

【B】
mainを最新化
        ↓
作業ブランチ作成
        ↓
stylesheet.css追加
        ↓
Commit・Push
        ↓
Pull Request
        ↓
────────────────────────

【A】
レビュー
        ↓
mainへMerge
        ↓
【完了】
```

---

# 23. GitHubとVS Codeの役割

今回の演習では、GitHubとVS Codeを以下のように使い分けた。

| 使用環境    | 主な操作             |
| ------- | ---------------- |
| GitHub  | リポジトリ作成          |
| GitHub  | Pull Request作成   |
| GitHub  | Pull Requestレビュー |
| GitHub  | Merge            |
| VS Code | ファイル編集           |
| VS Code | ブランチ作成・切り替え      |
| VS Code | 変更内容の確認          |
| VS Code | Commit           |
| VS Code | Push             |
| VS Code | Pull / 最新化       |

このように、今回の演習では**ターミナルを使用せず、VS CodeのGUIとGitHubのWeb画面だけでGitの基本的な共同開発手順を実施した。**

---

# 24. Gitの履歴

今回の演習では、複数の作業ブランチからPull Requestを作成し、`main`へMergeした。

Gitの履歴には、以下のようなMerge履歴が残っている。

```text
Merge pull request
       ↓
     main
       ↑
      PR
       ↑
  作業ブランチ
```

実際のGit Graphでは、複数のブランチが作成され、それぞれのPull Requestが`main`へMergeされていることを確認できる。

【ここに今回のGit Graphのスクリーンショットを貼る】

---

# 25. スクリーンショット

実際の演習で使用した画面を以下に掲載する。

### ① GitHubリポジトリ

【GitHubのリポジトリ画面】

### ② VS Codeのブランチ

【VS Codeのブランチ一覧画面】

### ③ VS Codeのソース管理

【変更されたファイルが表示されている画面】

### ④ Pull Request

【GitHubのPull Request画面】

### ⑤ Pull Requestのレビュー

【GitHubのReview画面】

### ⑥ Merge

【Merge完了画面】

### ⑦ Git Graph

【今回のGit Graphのスクリーンショット】

---

# 26. まとめ

今回の演習では、共有リポジトリモデルを使用して、2人でGitHubを利用した共同開発を行った。

実際の作業では、ターミナルを使用せず、**GitHubブラウザとVS CodeのGUI機能**を利用した。

基本的な流れは以下の通りである。

```text
main
 ↓
作業ブランチ作成
 ↓
VS Codeでファイル編集
 ↓
Commit
 ↓
Push
 ↓
GitHubでPull Request作成
 ↓
相手がレビュー
 ↓
Merge
 ↓
mainを最新化
 ↓
次の作業
```

この流れを繰り返すことで、`main`ブランチを直接編集することなく、2人で安全に共同開発を行うことができた。
