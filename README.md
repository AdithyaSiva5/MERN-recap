# MERN-recap

## Rest and WebApi
Rest - Restfull state transfer - It is a architectural style<br/>
Communication uses GET,POST,PUT,DELETE supports json xml<br/>
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
git log --oneline 
git revert -m 1 <merge-commit-hash>
```

# JavaScript

## Event Handling (js)

check out the event handling in readme.md</br>
#### Event bubbling
 - When u click on inner box it bubbles up , through its parent divs , it is in the order</br>
inner -> middle -> outer </br>
#### Event Capture
 - in capturing phase it runs in opposite direction . if i click on child element it passes from parent to child </br>
 means it will be in the order outer -> middle -> inner </br>
#### Event Delegatioin
 - we could handle all the clicks through event listeners to each element individually , we could handle all clicks </br>
 through a single listener .

-event.preventDefault() - stops default behaviour such as form submission , or  navigating to link
-event.stopPropogation() - stops from bubbling up 
-event.stopImmediatePropogation() - Stop other element on the same from working 

## remove adjecent odd elements from the array

```
const array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

//using reduce
const a =array.reduce((acc,curr,index)=>{
    if(index % 2== 0) acc.push(curr);
    return acc;
},[])
console.log(a);

//using filter
const b = array.filter((ele,ind)=>{
    if(ind % 2 == 0) return ele
})

```
## Remove last Property of Object 

```
obj = {
    a : 'hello',
    b : 'hi',
    c : 'how are you'
}

obj.d = 'doing great'   //obj.d is not neccessary  
let keys = Object.keys(obj)
let lastKey = keys[keys.length - 1];
delete obj[lastKey]
console.log(obj)
```
## Reapeat a1b2c3

```
const sent = "a1b2c3";

let result = '';
for(let i = 0 ; i < sent.length ; i+=2){
    const char = sent[i]
    let number = parseInt(sent[i+1])
    result += char.repeat(number)
}
console.log(result)
```

## Count Zero using reccursion  [0, 1, [0, 1, [0, 1, [0, 1]]]]

function countZeros(arr){
    return arr.reduce((acc,curr)=>{
        if(Array.isArray(curr)){
            return acc + countZeros(curr)
        }
        return acc + (curr === 0 ? 1 : 0);
    },0)
}
const arr = [0, 1, [0, 1, [0, 1, [0, 1]]]];
console.log("Using reduce method:", countZeros(arr));

## Find sum

```
const simpleArray = [
    { af: [5, 34, 34] },    // First object
    { af: [5, 434, 34] },   // Second object
    { af: [54, 334, 34] }   // Third object
];

function sum(arr){

    return arr.reduce((acc,curr)=>{
        let newarr = curr.af
        let count = newarr.reduce((acc,cur)=>{
            return acc + cur
        },0)
        console.log(count)
        return acc + count;
    },0)
}

console.log(sum(simpleArray))
```

## Find sum2
```
const complexArr = [
    {af:[{fa:3,df:34}]},
    {af:[{fa:3,df:34}]},
    {af:[{fa:3,df:34}]},
    {af:[{fa:3,df:34}]},
    {af:[{fa:3,df:34}]}
];
function sum(complexArr){
    return complexArr.reduce((acc,curr)=>{
        let arr1 = curr.af;
        let obj = arr1[0];
        return acc + obj.fa + obj.df
    },0)
}
console.log(sum(complexArr))
```

## Binary Tree with that sum1 question


# Node JS

## File Exist or not 
```
const express = require("express");
const fs = require("fs");
const path = require("path");
const app = express();

app.get("/", (req, res) => {
  res.send("HEYY");
});
app.get("/file-exist", (req, res) => {
  if (fs.existsSync("./test.txt")) {
    console.log("FILE EXIST");
    res.send("EXIST");
  } else {
    console.log("DOESNT EXITS");
    res.send("Doesnt EXIST");
  }
});

app.get("/file-existasync", (req, res) => {
  fs.access("./test.txt", fs.constants.F_OK, (err) => {
    if (err) {
      res.send("ERRROR");
    }
    res.send("FILE EXIST");
  });
});

app.listen(4000, () => {
  console.log("Server Started");
});
```
There is sync and async version , path can also be usen


## Middleware to log names of all incomming request

```
const express = require("express");
const app = express();

const port = 3000;
app.use(express.json());

const logParamsMiddleware = (req, res, next) => {
  console.log("Route Params");

  Object.keys(req.params).forEach((param) => {
    console.log(`- ${param}  ${req.params[param]}`);
  });
  console.log("Query Param");
  Object.keys(req.query).forEach((query) => {
    console.log(` - ${query} ${req.query[query]}`);
  });
  if (Object.keys(req.body).length) {
    console.log("Body Parameter");
    Object.keys(req.body).forEach((bodyparam) => {
      {
        console.log(` -${bodyparam} ${req.body[bodyparam]}`);
      }
    });
  }
  next();
};
app.post("/user/:id",logParamsMiddleware, (req, res) => {
  const id = req.params.id;
  const queryParams = req.query;
  const bodyParams = req.body;

  res.json({
    id,
    queryParams,
    bodyParams,
  });
});

app.listen(4000, () => {
  console.log("Server started");
});
```


## Idempotent Api

If a http request run multiple times when it was suppoed to run only once. means if payment failed it when retried it shouldnt work again as it end up in losing money. It has a idempotent key which prevent further losing money.

## Content Negotiation

It is about supporting every Format . Return the data according to user. If the user wants xml data that data should be returned    

## 