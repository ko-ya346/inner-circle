# command操作

### いまいるpathを確認 
```
pwd
```

### いまいる場所にあるファイルを確認
```
ls
```

### ドットファイルも含めて確認
```
ls -a
```

### ディレクトリ作成
```
mkdir 210523
```

### ちゃんとディレクトリが出来たかな？
```
ls
```

### 作ったディレクトリに移動
```
cd 210523
```

### pythonファイルを作ってみる
```
echo "print('hello world')" >> hello.py
```

### .pyファイルの中身を出力
```
cat hello.py
```

### pythonファイル実行
```
python hello.py
```

# git
## gitとは  
- version管理してくれるやつ  
- 更新した部分の確認、前のバージョンに戻す  
- ポートフォリオ的に見られる  
- IT系だとほぼ使ってる  

## 準備（dockerを使う場合、ローカルで作業する場合は必要なし）

```
docker build -t git-vim .  
docker run -it --name test-git git-vim /bin/bash
```

## ssh接続

- 安全にgithubと接続するためにこの作業をやります

1. githubにアカウント作る  
2. sshでkeyを作る  

```
cd ~
ssh-keygen -t rsa
```

- その後、Enterを3連打
- .sshというディレクトリ内のid_rsa.pubの中身(公開鍵)をコピー

3. 公開鍵をgithubに保存
4. 接続確認

```
ssh -T git@github.com
```

5. Hiとか言われたら完了

> https://qiita.com/shizuma/items/2b2f873a0034839e47ce

## 新規リポジトリの立て方

1. githubのwebページで新しいリポジトリを作る  
2. cloneして色々やる
3. 新規に作ったときに表示されるコマンド通りにやる

## よく使うコマンド

```
git add
git commit -m 
git push
git pull
git clone
git status
git diff
```

## 気をつけること
- 個人情報などはアップしない
    - .gitignoreというファイルにアップしたくないファイル名を入れるのが吉
- 基本的にgithubで管理するのはコードのみ
    - csvファイルとか大きいファイルを上げると動作がもっさりする

## 複数人で開発するとき（時間があればやる）
1. innercircleをclone  

```
git clone https://github.com/ko-ya346/inner-circle.git
```

2. ブランチを作って開発する  

```
git checkout 
```

3. commitしてmerge request送る  

# docker
## dockerとは  
- 仮想環境を作るやつ  
- ローカルの環境を汚さずに済む  

## pipenvと違い
- pipenvはpython環境のみ
- dockerはosより上の階層を用意できる（ちっさいPCのイメージ）

## 用語
- image
    - コンテナのもとになるやる（カメラのフィルム）
- container
    - imageをもとに作った仮想環境（現像した写真）

## 使ってみる
- 偉い人たちが用意してくれたdocker imageをありがたく使う

1. pythonのイメージを持ってくる

```
docker pull python:latest  
docker images
```

2. pythonのイメージからコンテナを作成して中に入る

```
docker run -it --name test-python python /bin/bash  
```

3. 中で色々やる  
4. コンテナを終了

```
exit
```

5. コンテナを確認

```
docker ps -a
```

6. 停止してるコンテナをもっかい動かす

```
docker start 
```

7. 起動中のコンテナに入る

```
docker exec -it [] bash
```

## ほかに出来ること 
- dockerfileを書くと自分で好き勝手imageを作れる
- コンテナ内でも色々パッケージを落とせる、そのコンテナからimageを作ることも出来る
- コンテナを停止するとコンテナ内で作成したファイルはすべて消えるので、残したい場合はマウント設定をする（むずい）
- jupyter notebookをコンテナ内で使いたいときは、portの設定が必要
- dockerのもろもろ設定を簡単な記述でまとめられるdocker-composeというものがあるらしい（勉強中）  

# 参考リンク

- gitのコマンド集
    - https://qiita.com/2m1tsu3/items/6d49374230afab251337
- https://qiita.com/gold-kou/items/7f6a3b46e2781b0dd4a0
