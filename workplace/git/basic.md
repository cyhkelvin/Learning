# git


## references
 - [hackmd note](https://hackmd.io/v6gdO7sYR6GyDKN2_Ak5TA)

## basic rules
  - branch
     - main/develop
     - feature/release/hotfix
  - release version naming rule: v[major].[minor].[patch] for break API/features not break API/bug fixs
  - title of commits: 
    1. feature : 新增、修改功能
    2. refactor : 重構，功能不變 e.g. 重構取得「簽核流程種類名稱」邏輯
    3. style : 不影響程式碼運行的格式變動 (white-space, formatting, missing semi colons)
    3. chore:  建構程序或輔助工具的變動 (maintain) e.g. 更新 testing 環境
    4. fix : 修 bug，可與 feature 同名
    5. test : 修改單元測試，可與 feature 同名
    6. performance : 改善效能
    7. doc : 新增、修改說明文字
    8. revert : 撤銷回覆先前的 commit 



## commands
 - pull
   - pull with token: `git pull https://<token>@<git_url>.git`
   - `git pull <my-remote> <my-branch>` (pull 遠端且試圖 merge 本地分支)
 - fetch
   - `git fetch --tags`  (從 remote pull tag)
 - push
   - `git push <my-remote> <my-branch>` (把 my-branch 的 commit push 上 my-remote 不包含 tag)
 - merge
 - rebase `-i`, `-i <commit-id>`
 - reset `--soft`, `--hard`, `--mixed`
 - revert
 - remote
   - update url: `git remote set-url origin https://<token>@github.com/<git_url>`
   - show detail: `git remote show`
   - show url: `git remote -v`
 - branch: `-D`, `-a`
 - checkout
 - init
 - clone
 - add
 - commit: `-m`
 - status
 - log: `--graph`, `-n 5`(for 5 lines), `--oneline`, `--pretty=oneline`, `--abbrev-commit`
 - difference
   - `git diff --name-status <branch-1> <branch-2>` show difference of files and their status
   - `git diff <filename> <branch-1> <branch-2>`
   - `git log <branch-1>..<branch-2>` (--abbrev-commit --oneline --date=relative)
 - cherry-pick

## command pratical instances
### submodule
 - [reference](https://blog.wu-boy.com/2011/09/introduction-to-git-submodule/)
 - [reference](http://jhjguxin.github.io/blog/2012/04/19/git-submodule-de-ren-shi-yu-zheng-que-shi-yong-!/)
 - initial
    1. e.g. `git submodule add https://github.com/cyhkelvin/leetcode.git interview_practice`
    * 不用預先建立 leetcode 資料夾，他會直接將 repository 建立為 leetcode 資料夾
    2. `git status` 會看到多了 `.gitmodules`, `career_development/interview_practice/leetcode`
    3. commit & push 後 github 上就會有連結了
    4. 本地端再使用 `git submodule init` 來讓 git 完成 submodule 初始化
 - update
    1. move to submodule dir and git pull
    2. move back to main module and git commit, git push
 - remove
    1. `git rm -cached <path>`
    2. `git rm <path>`
    3. modified `.gitmodule` remove submodule
    4. modified `.git/config` remove url
    5. `git submodule sync`
 - status
    `git submodule status`
### filter-branch
 - [reference](https://www.itread01.com/content/1541997604.html)
### compare reset, rebase, revert
 - reset/rebase/revert [reference](https://gitbook.tw/chapters/rewrite-history/reset-revert-and-rebase.html)
 
    | command | change history commit | introduction |
    | ------- | --------- | -------- |
    | reset   | True      | 把目前的狀態設定成某個指定的 Commit 的狀態，通常適用於**尚未推出去**的 Commit。|
    | rebase  | True      | 不管是新增、修改、刪除 Commit 都相當方便，用來整理、編輯**尚未推出去**的 Commit 相當方便。 |
    | revert  | False     | 新增一個 Commit 來反轉（或說取消）另一個 Commit 的內容，原本的 Commit 依舊還是會保留在歷史紀錄中。會增加 Commit 數，但通常比較適用於**已經推出去**的 Commit，或是不允許使用 Reset 或 Rebase 之修改歷史紀錄的指令的場合。(跟別人共用的branch) |
    ※ 若是要修改到遠端的 commit ，一般使用 push --force，會修改到遠端的歷史 commit 所以須謹慎使用，通常只使用在確定沒錯且只有本人使用的 branch 有小量 commit 誤推上遠端的情況。
    ※ 以 git 要版控的精神來說其實是盡量不要消除 commit 的，所以像 master branch 通常會盡量只以 pull request (單純merge) 操作而非一個一個 commit。
### basic push routine
  - basic:
    1. `git fetch` (確認與遠端同狀態)
    2. `git rebase -i origin <branch-name>` (把更動嫁接到遠端最新的變動)
        [ref_易懂](https://gitbook.tw/chapters/branch/merge-with-rebase.html), [ref_詳細](https://blog.yorkxin.org/posts/git-rebase.html)
    3. `git push origin <branch-name>:<branch-name>`
  - if conflict with remote: 先把自己的 commit 砍掉，重新 pull remote 最新的進度，再依序做 git add 、 git commit 、 git push
    1. `git rebase HEAD^`
    2. `git pull origin master:master`
    3. `git add -all`
    4. `git commit -m "msg"`
    5. `git push origin master:master`
    ※ 大量更改過去 commit ，參考[filter-branch](#filter-branch)
### modified author information of a commit
  - [reference](https://yulun.me/2014/git-tips-change-author-and-email-in-previous-commits/)
### set git editor to vim or somtimes use emacs as default
  - `git config --global core.editor vim` 即可將 vim 設為預設 editor，當然也可換成其他 editor
    - emacs
      - 保存 ctrl+x 離開 ctrl+c (用ctrl+h好像是 help可以看指令，有些環境會改變操作規則)
    - vim
      - 保存 :w 離開 :q

## github operations
 - Generate a new token from github's [dev settings](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)
 - github.com/.... -> github1s.com/.... : open vscode mode
 