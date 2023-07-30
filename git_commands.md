## git fetch
git fetch: 相当于是从远程获取最新版本到本地，不会自动merge

```bash
git fetch origin master
git log -p master..origin/master
git merge origin/master

# 以上命令的含义：
# 	首先从远程的origin的master主分支下载最新的版本到origin/master分支上
# 	然后比较本地的master分支和origin/master分支的差别
# 	最后进行合并
```
上述过程其实可以用以下更清晰的方式来进行：
```bash
git fetch origin master:tmp
git diff tmp 
git merge tmp

# 从远程获取最新的版本到本地的test分支上,之后再进行比较合并
```

## git pull
git pull: 相当于是从远程获取最新版本并merge到本地
```bash
git pull origin master

# 上述命令其实相当于git fetch 和 git merge
# 在实际使用中，git fetch更安全一些
# 因为在merge前，我们可以查看更新情况，然后再决定是否合并
```

## git clone -b
```bash
git clone -b (分支项目名) http://myrepo.xxx.com/project/.git
```
此操作会将远端分支的 clone 下来，文件名还是项目的文件名，但是里面只有克隆下来的单个分支

## 先commit，然后pull，最后再push
通常在push之前需要进行 add - commit - pull 操作
- add 是为了追踪修改；
- commit 是为了保存修改
- pull 是为了将别人写好且 push 的模块保存下来。你写A模块，他写B模块，他已经写好且 push 上去了，此时你本地分支是没有B模块的，如果不 pull 直接 push，那么B模块就会消失。在 pull 的时候，会将B模块同步下来，由于你们互相负责的不同模块，因此一般也不会有冲突。
