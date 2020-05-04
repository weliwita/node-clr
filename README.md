Node-CLR: Is .NETCore clr host on node js similar to https://github.com/tjanczuk/edge.
====

The main differece compared to edge is that this project is focused only on wrapping a dotnetcore dll from a Node.js process. It uses N-API for native implemetation and very light weight compared to edge.


### How to Wrap C# hello, world library.

#### Create dotnet core library.

you will need to implement following interface for all the methods you need to export to javascript

```
ICreateWrappers.cs
Task<object> Create(object o);
```

The class name used in the actual object will be exported as a javascript object.

```
npm install node-clr
```

In your `application.js`:

```javascript
var node-clr = require('node-clr');

var node-clr = edge.func({
    assemblyFile: path.join(process.env.EDGE_APP_ROOT, 'EdgeApi.dll'),
    isStandalone: false, //clr loaded accordingly, optional
});

node-clr.exports.helloWorld('JavaScript', function (error, result) {
    if (error) throw error;
    console.log(result);
});
```



Run and enjoy:

```
$>node application.js
$>node server.js
.NET welcomes JavaScript
```

this is in new-branch gitlab
