# MERN-recap

## Rest and WebApi
Rest - Restfull state transfer - It is a architectural style<br/>
Communication uses GET,POST,PUT,DELETE<br/>
supports json xml<br/>
WebApi-Boarder term accessed over the web<br/>
SOAP - Simple object access api - for secure , and for using multiple languages , it uses xml<br/>

## HTTP1 and HTTP2

http1.1 - loading , single connection  ,single request at a time, take time <br/>
http2 - compress http headers , allows server push , enaples muliplexing<br/>
uses HPACK wich compress <br/>
additional info : http/0.9 only get get request ,<br/>
/0.1 - get post ,head methods , content type , content length <br/>
/1.1 - pipelining ,better caching mechanism , put, delete , options <br/>
/2 - multiplexing , binary farming ,hpack(reduce size),connection priorization <br/>
/3 tcp to quic , reduce latency and quick performance <br/>

## TLS 

Transport layer security , a cryptographic protocol , that encrypts data to secure communication through internet</br>
Prevent unauthorized access</br>
SSL(secure socket layer) -  older version , alert message are unencrypted , older algorithm that has security vulnaribilities </br>

## Git Stashing

Temp store uncommited changes , without commiting them to your branch . used to switch to another branch for high priority task</nr>

### Commands
```
git stash - stash them
git stash list - list them 
git apply [stash @{n}]
git pop 
git drop [stash @{n}]
git stash clear 
git stash save "message"
git stash branch new-branch-name
```

## Git cherrypick

It is used so that you want to select a specific code , a fix or specific commit to mix with current instead of merging the whole branch. To merge the specific changes we use cherry pic</br>

```
git cherry-pick <commit-hash>
git log --oneline find the first commit 
conflicts --
git add <resolved file>
git chery-pick --continue
git chery-pick --abort
git chery-pick --skip
git cherry-pick -n <commit-hash>
git cherry-pick branchname <commit-hash>

```

## Git rebase 

Lets you move or combine a sequence of commits to a new branch. Means if u merge it will merge as a single commit but using git rebase every commit will be joined meaning you could have history of all the commits </br>

### commands
```
git rebase <branch>
git checkout <branch>
git rebase main
git rebase -i <commit>  (allows you to edit modify and squash, reorder them)
git rebase --continue (avoid conflice) 
git rebase --abort 
```
#### how to revert a merged commit?
```
git log --oneline </br>
git revert -m 1 <merge-commit-hash>
```


