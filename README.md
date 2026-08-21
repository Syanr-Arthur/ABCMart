# Git/GitHub 課題

## フォークとプルモデル

---

## 1. 課題概要

本課題では、GitHubの**フォークとプルモデル（Fork and Pull Model）**を使用し、3人で共同開発を行った。

フォークとプルモデルでは、開発者が元のリポジトリをForkし、自分のリポジトリ上で作業を行う。

作業した内容は、元のリポジトリへPull Request（PR）を作成して提出する。

元のリポジトリを管理するAがPull Requestをレビューし、問題がなければ`main`ブランチへMergeする。

今回の課題では、**ターミナルやコマンドプロンプトを使用せず、GitHubのWebブラウザとVisual Studio Code（VSCode）のGUI機能を使用した。**

---

# 2. チーム構成

今回のチームは3人で構成した。

| 担当 | 役割            |
| -- | ------------- |
| A  | リード役・元リポジトリ管理 |
| B  | 開発者1          |
| C  | 開発者2          |

Aが元となるリポジトリを管理する。

BとCはAのリポジトリをそれぞれForkし、自分のForkしたリポジトリで作業を行う。

---

# 3. フォークとプルモデルとは

フォークとプルモデルとは、開発者が元のリポジトリを**Forkして、自分のリポジトリ上で開発を行う方式**である。

共有リポジトリモデルとは異なり、BやCはAの元リポジトリに直接変更をPushするのではなく、自分自身のForkへ変更をPushする。

その後、自分のForkからAの元リポジトリへPull Requestを作成する。

```text id="g7x3u1"
                 AのGitHubリポジトリ
                  （元リポジトリ）
                         │
              ┌──────────┴──────────┐
              ↓                     ↓
            Fork                  Fork
              ↓                     ↓
      BのGitHubリポジトリ    CのGitHubリポジトリ
              ↓                     ↓
　　　　 Bの作業ブランチ        Cの作業ブランチ
              ↓                     ↓
            Push                  Push
              ↓                     ↓
             PR                    PR
              │                     │
              └──────────┬──────────┘
                         ↓
                     AがReview
                         ↓
                       Merge
                         ↓
                   Aのmainブランチ
```

### 共有リポジトリモデルとの違い

```text id="8eqr44"
【共有リポジトリモデル】

        B
        ↓
共有リポジトリへPush
        ↓
       PR
        ↓
      main


【フォークとプルモデル】

        B
        ↓
 B自身のForkへPush
        ↓
       PR
        ↓
  Aの元リポジトリ
        ↓
      main
```

---

# 4. 使用した環境

今回の課題では以下の環境を使用した。

* GitHub
* Visual Studio Code（VSCode）
* Webブラウザ

### GitHubで行った操作

* リポジトリ作成
* Fork
* Pull Request作成
* Pull Request確認
* Pull Requestレビュー
* Merge
* Forkしたリポジトリの同期

### VSCodeで行った操作

* リポジトリの取得
* ブランチ作成・切り替え
* ファイル編集
* ファイル追加
* Commit
* Push
* Pull

> **今回の課題では、ターミナルやコマンドプロンプトは使用していない。**

---

# 5. Aが元リポジトリを作成

最初にAがGitHub上で課題用のリポジトリを作成した。

このリポジトリを、今回の開発における**元リポジトリ（Upstream Repository）**とする。

```text id="w0ox5k"
AのGitHubリポジトリ
       ↓
  元リポジトリ
```

---

# 6. Aがindex.htmlを作成

Aは`index.html`を作成し、以下の内容を記述した。

```html id="z6n7ww"
Hello
```

作成した`index.html`を`main`ブランチへ追加し、Commitした。

その後、GitHubへPushして、元リポジトリの`main`に`index.html`を登録した。

この時点での構成は以下の通りである。

```text id="b0x5ql"
Aの元リポジトリ
└── main
    └── index.html
```

---

# 7. BがAのリポジトリをFork

BはGitHub上でAの元リポジトリを開き、「Fork」を実行した。

Forkによって、Aのリポジトリを元にしたB自身のリポジトリが作成される。

```text id="y7uw6r"
Aの元リポジトリ
      ↓
    Fork
      ↓
 Bのリポジトリ
```

Bは以降、自分のForkしたリポジトリを使用して開発を行う。

---

# 8. BがForkしたリポジトリをVSCodeで取得

Bは自分のForkしたリポジトリをVSCodeから取得した。

取得後、VSCodeでリポジトリを開いた。

この時点では、Bのローカル環境にもAの`main`と同じ`index.html`が存在する。

```text id="8g0xun"
Aの元リポジトリ
      ↓
    Fork
      ↓
   BのFork
      ↓
  BのVSCode
```

---

# 9. Bが作業ブランチを作成

BはVSCodeのブランチ操作から`main`を元に作業ブランチを作成した。

```text id="f6xw21"
BのFork
│
├── main
│
└── work-branch-B
```

Bは`main`ではなく、`work-branch-B`上で作業を行った。

---

# 10. Bがindex.htmlを編集

BはVSCodeで`index.html`を編集した。

変更後、VSCodeのソース管理画面から変更内容を確認した。

```text id="t6p8f7"
ソース管理
└── 変更
    └── index.html
```

---

# 11. BがCommit・Push

BはVSCodeのソース管理機能を使用して変更をCommitした。

その後、VSCodeから**B自身のForkしたリポジトリ**へPushした。

ここが共有リポジトリモデルとの大きな違いである。

```text id="a6v8b4"
BのVSCode
     │
     │ Push
     ↓
  BのFork
```
Aの元リポジトリにPushするのではなく、C自身のForkへPushする。

---

# 12. BがPull Requestを作成

BはGitHubのWebブラウザから、自分のForkの`work-branch-B`を元リポジトリの`main`へ取り込むPull Requestを作成した。

```text id="g6f3p9"
work-branch-B
      │
      │ Pull Request
      ↓
Aの元リポジトリ
```

つまり、Pull Requestの送信先は**B自身のリポジトリではなく、Aの元リポジトリ**である。

---

# 13. AがBのPull Requestをレビュー・Merge

AはGitHubブラウザからBが作成したPull Requestを確認した。

変更された`index.html`を確認し、問題がないかレビューした。

問題がなければPull Requestを承認し、Aの元リポジトリの`main`へMergeした。

```text id="a3q7vr"
work-branch-B
      ↓
Pull Request
      ↓
Aの元リポジトリ
      ↓
　Aがレビュー
      ↓
    Merge
      ↓
    main
```

---

# 14. CがAのリポジトリをFork

Bと同様に、CもAの元リポジトリをGitHub上でForkした。

```text id="c9d2xe"
Aの元リポジトリ
       ↓
     Fork
       ↓
  Cのリポジトリ
```

Cは以降、自分のForkしたリポジトリを使用して開発を行う。

---

# 15. CがForkしたリポジトリをVSCodeで取得

Cは自分のForkしたリポジトリをVSCodeから取得した。

その後、VSCodeでリポジトリを開いた。

```text id="p6w5ez"
Aの元リポジトリ
       ↓
     Fork
       ↓
　　CのFork
       ↓
　 CのVSCode
```

---

# 16. Cが作業ブランチを作成

CはVSCodeで`main`を元に作業ブランチを作成した。

```text id="c6wq5t"
CのFork
│
├── main
│
└── work-branch-C
```

Cも`main`を直接編集せず、作業ブランチ上で作業を行った。

---

# 17. Cがindex.htmlを編集

CはVSCodeで`index.html`を編集した。

変更内容をVSCodeのソース管理画面から確認した。

---

# 18. CがCommit・Push

CはVSCodeのソース管理機能を使用して変更をCommitした。

その後、C自身のForkへPushした。

```text id="r8q3nv"
CのVSCode
    │
    │ Push
    ↓
 CのFork
```

Aの元リポジトリへ直接Pushするのではなく、C自身のForkへPushする。

---

# 19. CがPull Requestを作成

CはGitHubブラウザから、自分のForkの`work-branch-C`からAの元リポジトリの`main`へのPull Requestを作成した。

```text id="0q3x2u"
work-branch-C
      │
      │ Pull Request
      ↓
Aの元リポジトリ
```

---

# 20. AがCのPull Requestをレビュー・Merge

AはGitHubブラウザからCのPull Requestを確認した。

Cが変更した内容をレビューし、問題がないことを確認した。

その後、Pull Requestを承認してAの元リポジトリの`main`へMergeした。

```text id="7i4x5s"
work-branch-C
      ↓
Pull Request
      ↓
Aの元リポジトリ
      ↓
  Aがレビュー
      ↓
    Merge
      ↓
    main
```

---

# 21. Aがmainを最新化

BとCのPull RequestがAの元リポジトリへMergeされたため、AはVSCodeでローカルの`main`を最新化した。

VSCodeで`main`へ切り替え、Pullを実行してGitHub上の最新の変更を取得した。

```text id="2d1g5x"
Aの元リポジトリ
       │
       │ Pull
       ↓
   AのVSCode
       ↓
   最新のmain
```

これにより、BとCが行った変更がAのローカル環境にも反映された。

---

# 22. Aが作業ブランチを作成

Aは最新化した`main`を元に、新しい作業ブランチを作成した。

```text id="5x7r2v"
Aの元リポジトリ
│
└── main
      │
      └── work-branch-A
```

---

# 23. Aがindex.htmlを編集

AはVSCodeで`index.html`を編集した。

---

# 24. AがCommit・Push

AはVSCodeのソース管理機能を使用して変更をCommitした。

その後、Aの元リポジトリへPushした。

```text id="c5p7m2"
  AのVSCode
      │
      │ Push
      ↓
Aの元リポジトリ
```

---

# 25. AがPull Requestを作成・Merge

Aも`main`へ直接変更を加えるのではなく、作業ブランチからPull Requestを作成した。

```text id="n3z5x1"
work-branch-A
      ↓
Pull Request
      ↓
    main
```

変更内容を確認した後、Pull RequestをMergeした。

---

# 26. B・Cがmainの最新状態を取得

Aの変更が元リポジトリの`main`へMergeされた。

しかし、**BとCのForkの`main`は自動的に最新状態になるわけではない。**

そのため、BとCはGitHub上で自分のForkを元リポジトリの最新状態と同期した。

```text id="x8n5p3"
     Aの元リポジトリ
           │
           │ Sync fork
           │
    ┌──────┴──────┐
    ↓             ↓
 BのFork       CのFork
    ↓             ↓
最新のmain     最新のmain
```

その後、それぞれVSCodeで`main`を最新化した。

```text id="z5r8q2"
 BのFork
    ↓
BのVSCode
    ↓
Pull / 更新


 CのFork
    ↓
CのVSCode
    ↓
Pull / 更新
```

---

# 27. Bがstylesheet.cssを追加

Bは最新の`main`から新しい作業ブランチを作成した。

その後、VSCodeで`stylesheet.css`を作成した。

---

# 28. BがCommit・Push

BはVSCodeのソース管理機能を使用して`stylesheet.css`をCommitした。

その後、B自身のForkへPushした。

```text id="m6v1p4"
BのVSCode
     │
     │ Push
     ↓
  BのFork
```

---

# 29. BがPull Requestを作成

BはGitHubブラウザから、自分のForkの`work-branch-B-css`からAの元リポジトリの`main`へのPull Requestを作成した。

```text id="s3q8w2"
work-branch-B-css
        ↓
  Pull Request
        ↓
  Aの元リポジトリ
        ↓
      main
```

---

# 30. AがBのPull Requestをレビュー・Merge

AはGitHubブラウザからBのPull Requestを確認した。

`stylesheet.css`の内容を確認し、問題がないことを確認した。

その後、Pull Requestを承認してAの元リポジトリの`main`へMergeした。

これで指定された一連の課題が完了した。

---

# 31. 今回の作業全体

今回の3人でのフォークとプルモデルによる作業をまとめると、以下のようになる。

```text id="d2m7x5"
                       A
                    リード役
                       ↓
                元リポジトリ作成
                       ↓
                  index.html
                       ↓
                     main
                       │
          ┌────────────┴────────────┐
          ↓                         ↓
          B                         C
        開発者1                   開発者2
          ↓                         ↓
        Fork                      Fork
          ↓                         ↓
       BのFork                   CのFork
          ↓                         ↓
   作業ブランチ作成            作業ブランチ作成
          ↓                         ↓
    index.html編集            index.html編集
          ↓                         ↓
       Commit                    Commit
          ↓                         ↓
        Push                      Push
          ↓                         ↓
         PR                        PR
          │                         │
          └────────────┬────────────┘
                       ↓
                   Aがレビュー
                       ↓
                 AのmainへMerge
                       ↓
                     main
                       ↓
                 AがmainをPull
                       ↓
               Aが作業ブランチ作成
                       ↓
                 index.html編集
                       ↓
                    Commit
                       ↓
                     Push
                       ↓
                      PR
                       ↓
                     Merge
                       ↓
                     main
                       │
            ┌──────────┴──────────┐
            ↓     　              ↓
            B      　             C
            ↓      　             ↓
        Forkを同期  　        Forkを同期
            ↓            　       ↓
        mainをPull  　        mainをPull
            ↓       　            ↓
　　　作業ブランチ作成　     作業ブランチ作成
            ↓       　            ↓
    stylesheet.css追加    stylesheet_c.css追加
            ↓                     ↓
         Commit                Commit
            ↓                     ↓
          Push                  Push
            ↓                     ↓
           PR                    PR
            │                     │
            └──────────┬──────────┘
                       ↓
                   Aがレビュー
                       ↓
                     Merge
                       ↓
                     main
```

---

# 32. 共有リポジトリモデルとの違い

今回のフォークとプルモデルでは、BとCがAの元リポジトリへ直接Pushしない点が重要である。

### 共有リポジトリモデル

```text
      B
      │
      │ Push
      ↓
共有リポジトリ
      ↓
Pull Request
      ↓
    main
```

### フォークとプルモデル

```text
      B
      │
      │ Push
      ↓
   BのFork
      ↓
Pull Request
      ↓
Aの元リポジトリ
      ↓
    main
```

Cについても同様である。

```text
      C
      │
      │ Push
      ↓
   CのFork
      ↓
Pull Request
      ↓
Aの元リポジトリ
      ↓
    main
```

つまり、**Forkによって各開発者が自分専用のリポジトリを持ち、そのリポジトリから元リポジトリへPull Requestを送る**ことが、フォークとプルモデルの大きな特徴である。

---

# 33. GitHubとVSCodeの役割

今回の課題では、GitHubとVSCodeを以下のように使い分けた。

| 操作             | 使用した環境  |
| -------------- | ------- |
| 元リポジトリ作成       | GitHub  |
| Fork           | GitHub  |
| リポジトリ取得        | VSCode |
| ブランチ作成         | VSCode |
| ブランチ切り替え       | VSCode |
| ファイル編集         | VSCode |
| ファイル追加         | VSCode |
| 変更確認           | VSCode |
| Commit         | VSCode |
| Push           | VSCode |
| Pull           | VSCode |
| Forkの同期        | GitHub  |
| Pull Request作成 | GitHub  |
| Pull Request確認 | GitHub  |
| コードレビュー        | GitHub  |
| Merge          | GitHub  |

今回の課題では、**ターミナルを使用せず、GitHubブラウザとVSCodeのGUI機能のみで作業を行った。**

---

# 34. Gitの基本的な流れ

フォークとプルモデルでは、開発者は以下の流れで作業する。

```text id="x7m2q4"
元リポジトリをFork
        ↓
 自分のForkを取得
        ↓
 作業ブランチ作成
        ↓
   ファイル編集
        ↓
     Commit
        ↓
 自分のForkへPush
        ↓
  Pull Request
        ↓
  管理者がレビュー
        ↓
      Merge
        ↓
 元リポジトリのmain
```

---

# 35. Git Graphによる履歴確認

今回の課題では、複数の作業ブランチを作成し、それぞれからPull Requestを作成して`main`へ変更を取り込んだ。

Git Graphを確認すると、作業ブランチが作成され、Pull RequestによるMergeが行われた履歴を確認できる。

Git Graphには、例えば以下のようなMerge履歴が表示されている。

<img width="511" height="380" alt="image" src="https://github.com/user-attachments/assets/74cebc73-e0e2-4cbe-ac7c-a926f0c189fa" />

この履歴から、作業ブランチで変更を行い、Pull Requestを経由して`main`へ変更を取り込んだことが確認できる。

---

# 36. スクリーンショット

実際の課題で使用した画面を以下に掲載する。

## GitHub

### ① 元リポジトリ

【GitHubの元リポジトリ画面】

<img width="658" height="236" alt="スクリーンショット 2026-08-20 133816" src="https://github.com/user-attachments/assets/4881d210-ae1c-478e-ac72-bfded8823313" />

### ② Fork

【Fork作成後の画面】

<img width="886" height="441" alt="image" src="https://github.com/user-attachments/assets/545bea5c-4947-4660-95af-2afd3162b317" />

### ③ Pull Request

【Pull Request作成画面】

<img width="1310" height="753" alt="スクリーンショット_20-8-2026_153116_github com" src="https://github.com/user-attachments/assets/54295ddb-dd68-419a-b154-0dbbcc71746e" />

### ④ Pull Requestレビュー

【レビュー画面】

<img width="635" height="793" alt="スクリーンショット 2026-08-20 153246" src="https://github.com/user-attachments/assets/2d5945ac-ab8c-4c47-82c4-00eca97beb54" />

### ⑤ Merge

【Merge画面】

<img width="661" height="580" alt="スクリーンショット 2026-08-20 135048" src="https://github.com/user-attachments/assets/11b4013d-0ee1-47db-8e8f-42c03e82a9a5" />

### ⑥ Forkの同期

【Sync forkの画面】

<img width="886" height="892" alt="image" src="https://github.com/user-attachments/assets/89dcc572-193b-4b15-9900-b452842ace9e" />

---

## Visual Studio Code

### ⑦ ブランチ作成

【VSCodeのブランチ操作画面】

<img width="252" height="465" alt="スクリーンショット 2026-08-20 153759" src="https://github.com/user-attachments/assets/3d4c3ea6-19ad-42bb-9207-c03d376ed85d" />

### ⑧ ソース管理

【VSCodeのソース管理画面】

<img width="886" height="590" alt="image" src="https://github.com/user-attachments/assets/50af409f-99f8-49d4-9a86-9102af4c8bb1" />

### ⑨ Commit

【Commit時の画面】

<img width="296" height="258" alt="スクリーンショット 2026-08-20 152951" src="https://github.com/user-attachments/assets/4f20b987-4ca3-46f6-96a1-7bcd0845c1b3" />

### ⑩ Git Graph

【Git Graphのスクリーンショット】

<img width="511" height="380" alt="image" src="https://github.com/user-attachments/assets/74cebc73-e0e2-4cbe-ac7c-a926f0c189fa" />

---

# 37. まとめ

今回の課題では、A・B・Cの3人で**フォークとプルモデル**による共有を行った。

Aが元リポジトリを管理し、BとCはAのリポジトリをForkして、それぞれ自分のリポジトリ上で開発を行った。

BとCは作業ブランチで変更を行い、自分のForkへPushした後、Aの元リポジトリへPull Requestを作成した。

AはPull Requestの内容をレビューし、問題がなければ元リポジトリの`main`へMergeした。

今回の課題で行った基本的な流れは以下の通りである。

```text id="v8x3n2"
      Fork
        ↓
 作業ブランチ作成
        ↓
   ファイル編集
        ↓
     Commit
        ↓
 自分のForkへPush
        ↓
  Pull Request
        ↓
     レビュー
        ↓
元リポジトリへMerge
        ↓
      main
```

また、Aが`main`へ変更をMergeした後は、BとCが自分のForkを最新の状態へ同期し、その後VSCodeで`main`を更新することで、元リポジトリの最新状態を取得した。

この課題を通して、**Forkによって開発者ごとに独立したリポジトリを持ち、Pull Requestを利用して元リポジトリへ変更を提案するフォークとプルモデルの基本的な流れを実践した。**
作成し、Pull Requestを利用して`main`へ変更を取り込んだ。

今回の課題では、**GitHubブラウザとVSCodeのみを使用し、ターミナルを使用せずにGitのブランチ管理、Commit、Push、Pull、Pull Request、レビュー、Mergeという一連の共同開発の流れを実践した。**
