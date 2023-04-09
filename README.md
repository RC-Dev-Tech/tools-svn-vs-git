# ![](https://drive.google.com/uc?id=10INx5_pkhMcYRdx_OO4rXNXxcsvPtBYq) 淺談SVN跟GIT有何不同

<br>

<!--ts-->
## 目錄
* [簡介](#簡介)
* [SVN](#SVN)
* [GIT](#GIT)
* [SVN和Git的命令比較表](#SVN和Git的命令比較表)
* [參考資料](#參考資料)
* [備註](#備註)
<!--te-->

---
<br>

## 簡介.
想當初使用SVN來做為主要版控工具多年，<br>
在某次專案的需求接觸到Git，從此就回不去了...<br>
今天就來淺談一下這兩者的差異.

---
<br>

## SVN
SVN的管理核心是將所有的版本放在一個服務器上集中管理。<br>
>所有的開發者都必須藉由這個服務器來獲得對應版本的資源。<br>
>開發完，在上傳回原本的服務器上。

<br>
GUI: [TortoiseSVN](https://tortoisesvn.net/index.zh.html)

<font color="#4169E1">簡易流程示意:</font><br>
![](https://drive.google.com/uc?id=1CN-MK3d4LO9QA3mTSwbprtYzbKYNFb6W)

<font color="#4169E1">優點:</font>
- 概念簡單、操作單純、容易上手
- 解決版本衝突的工具有很多選擇，而且直覺
- 查詢檔案修改歷程非常的直覺且便利
- 單一流水式的版本編號，管理直覺
  
<font color="#4169E1">缺點:</font>
- branch的使用很不便利，每用一個branch就要checkout一份
- branch merge 不夠直觀且操作很麻煩
  
<font color="#4169E1">特色:</font>
- 直覺、易懂、適合有檔案管理需求的人使用

---
<br>

## GIT
Git的管理一樣是有一個專門放置代碼的共用服務器，<br>
但是核心則是各個開發者可以分散在各自的本機端管理自己的代碼。<br>

>所有的開發者都可以在對應的版本上，建立一個副本並且在本機端進行版控。<br>
>開發完後，將開發過程中所進行的版控，整串上傳回原本的遠端版本上進行合併。

GUI: [SourceTree](https://www.sourcetreeapp.com/)

<font color="#4169E1">簡易流程示意:</font><br>
![](https://drive.google.com/uc?id=1sxiKtxiy05hBR1sYnPXy8k465HxkVZl2)

<font color="#4169E1">優點:</font>
- branch的切換非常的迅速且方便
- branch merge的功能操作容易且直覺
- pull request的功能，讓code review可以更加落實
  
<font color="#4169E1">缺點:</font>
- 沒有版控觀念的人不容易上手
- 解決版本衝突不夠直觀
- 查找檔案修改歷程不夠便利
- 128bit的ID編號，在管理上會需要特別注意版本對齊的問題
  
<font color="#4169E1">特色:</font>
- 輕巧、敏捷、很適合拿來做多人模組開發

---
<br>

## SVN和Git的命令比較表
| 操作               | SVN          | Git          |
| :----------------- | :----------- | :----------- |
| 建立數據庫         | svn checkout | git clone    |
| 提交 [^1]          | svn commit   | git commit   |
| 查看提交的詳細記錄 | svn cat      | git show     |
| 確認狀態           | svn status   | git status   |
| 確認差異           | svn diff     | git diff     |
| 確認歷程           | svn log      | git log      |
| 新增               | svn add      | git add      |
| 移動               | svn mv       | git mv       |
| 刪除               | svn rm       | git rm       |
| 取消修改 [^2]      | svn revert   | git reset    |
| 建立分支           | svn copy     | git branch   |
| 切換分支           | svn switch   | git checkout |
| 合併               | svn merge    | git merge    |
| 建立標籤 [^3]      | svn copy     | git tag      |
| 更新               | svn update   | git pull     |
| 刷新更新 [^4]      | -            | git fetch    |
| 上傳遠端 [^5]      | -            | git push     |
| 忽視檔案清單       | .svnignore   | .gitignore   |

---
<br>

## 參考資料
* [SVN和Git介绍,区别,优缺点,适用范围总结](https://blog.csdn.net/mine_song/article/details/70770467) <br>
* [連猴子都能懂的Git入門指南](https://backlog.com/git-tutorial/tw/) <br>
---
<!--ts-->
#### [目錄 ↩](#目錄)
<!--te-->
---
## 備註：

[^1]: SVN的 commit 是會直接將修改的內容上傳到遠端的數據庫上．
      Git的 commit 則是將異動的檔案上傳至本機端，在還沒有push之前，所有的異動都只會在本機端上       

[^2]: SVN的 revert 是用來將修改的內容回復到下載前的內容．
      Git的 revert 是用來取消提交到本機端．       

[^3]: SVN的分支與標籤在使用上概念是相同的，都是建立一個新的branch．
      Git的標籤則可以拿來做分類或版本查找用． 

[^4]: SVN可以直接查看log來得知檔案的異動．
      Git的 fetch 的功能則是刷新要更新的檔案有哪些，但不是真的把檔案下載到自己的本機端．

[^5]: SVN的commit就直接上傳到遠端數據庫了，所以沒有相關的指令可以操作．
      Git的 push 則是將commit到本機端的數據上傳到遠端的數據庫。
