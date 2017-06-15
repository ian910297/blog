---
title: 使用 hexo
date: 2017-06-14 17:46:39
tags:
- hexo
- git
- github
- github pages
---

## 為什麼選擇 hexo
* 免費就能架設blog在網路上
* 順便練功, 熟悉一下新的小玩具
* 走過路過不要錯過, 很多事情是沒有理由的

## 開專案
#### 專案名稱

在 [github](https://github.com) 開一個專案來放你的 [hexo](https://hexo.io)
專案名稱不一定要叫做 [username].github.io
branch名稱是不是master, gh-pages也都不重要
因為github repo 的 setting可以設定
你現在要mapping 的 branch 到底要那一個
只不過預設mapping 是 gp-pages
去網頁按幾個按鈕就解決了
就看你把build出來的檔案放在那一個branch


以我自己為例
不使用[username].github.io為專案名稱
把hexo放在其他repo
網址會長這樣 https://username.github.io/repo

* 確保兩個branch不會互相污染
一邊放原始檔
一邊放發布的網頁
所以開branch上面我建議使用


    $ git checkout --orphan newbranch
    $ git rm -rf . # 砍掉所有檔案重來
    ...  # 加新檔案
    $ git add .
    $ git commit -m 'create new branch'
    $ git push -u origin newbranch


這樣就跟原本的 master 沒有關係了

## 環境架設
以下只列我覺得是重點的部份

    $ git clone your_project
    $ cd your_project
    $ git checkout source_branch # 切換到原始檔的branch, 沒有的話就開一個
    $ npm install hexo-cli -g # 安裝 hexo 可能需要 sudo
    $ hexo init blog # 隨便新開一個hexo專案
    $ cp blog/* ./ # 複製所有的檔案到source_branch底下
    $ cp blog/.gitignore ./ # 不要忘了.gitignore
    $ rm -rf blog # blog 已經沒有利用價值了
    ... # 以下調整 hexo
    ... # 
    ... # themes 要特別注意
    ... # git clone themes 之後
    ... # 要將資料夾名稱的 hexo-theme- 移除
    ... # 只留下後面
    ... # 然後要刪掉裡面的 .git 資料夾
    $ git clone https://github.com/iissnan/hexo-theme-next themes/next
    $ rm -rf themes/next/.git
    ... # 
    ... # 寫設定檔 _config.yml
    ... # url 跟 repo 要特別修改
    ... # deploy git的相關設定也要寫好 
    ... # theme有修改在用就好
    $ hexo generate
    $ hexo deploy
    ... # deploy之前記得先用 hexo server自己測試
    ... # 最後記得把source_branch也push上去就大功告成

其他細節就參閱 [hexo 官網](https://hexo.io)
以及 [李广鹤的博客 - hexo 博客的神坑及本质原因](https://liguanghe.github.io/2017/05/21/blogRebuilt/)

## 參考資料
#### git
* [git orphan 這篇文章的方法二](https://ihower.tw/blog/archives/5691)

#### hexo
* [hexo github](https://github.com/hexojs/hexo)
* [hexo 官網](https://hexo.io/)
* [李广鹤的博客 - hexo 博客的神坑及本质原因](https://liguanghe.github.io/2017/05/21/blogRebuilt/)

#### superman 大神 不知道怎麼辦的時候就問他吧
* [dansnow](https://github.com/dansnow)

