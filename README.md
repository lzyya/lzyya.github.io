# lzyya.github.io

```
const { promisify } = require('util')
// 不使用 promisify 的写法
fs.readFile('./db.json','utf8',(err,data)=>{
  if (!err) {
    var back = JSON.parse(data);
    res.send(back.users)
  } else {
    res.status(500).json({err});
  }
})
//使用 promisify 的写法
const fs = require('fs');
const { promisify } = require('util');
const readFile = promisify(fs.readFile);
try{
  let back = await readFile('./db.json','utf8');
  const jsonObj = JSON.parse(back);
   res.send(jsonObj.users)
}catch(error){
   res.status(500).json({err});
}
//客户端请求的数据格式 服务端如何处理
const { json, urlencoded } = require('express')
app.use(json());
app.use(urlencoded());
```


