# pagecache.js
  a cache that only live in a page, just like cookie cache but it is page cache

## Dependence
  no dependece

## Why Need It
  sometimes we got an API that returns like this: 
  
  `
  {
    comments: "1",
    likes: "2",
    reposts: "3"
  }
  `  
  
  usually we do this by one request:  
  ```javascript
  <script>
    jQuery.getJson("the API url", function(json){
      // handle the comments
      // handle the likes
      // handle the reposts
    });
  </script>
  ```
  
  but with pagecache we can do this by one reqeust only:
  ```javascript
  <script>
    $PC("the API url", function(json){
      // handle the comments
    });
    $PC("the API url", function(json){
      // handle the likes
    });
    $PC("the API url", function(json){
      // handle the reposts
    });
  </script>
  ```
  they are separate and independent
  

## Usage

### json
``` javascript
  $PC("http://jokinkuang.github.io/Postfile", function(json, state, xmlhttp_obj){
    // handle the json object
  }, function(state, xmlhttp_obj) {
    // handle the error
  });
```

### jsonp
``` javascript
  $PC("http://jokinkuang.github.io/Postfile?callback=?", function(json, state, jsonp_obj){
    // handle the json object
  }, function(state, jsonp_obj){
    // handle the error
  });
```
> just add a `callback=?` into the request URL

### open the log
  set `$PC.Log.level=2` before function call
  > DEBUG: 2  
  >  INFO: 1  
  > ERROR: 0

### $PC function
  $PC("url", successFunctionCall, errorFunctionCall);  
  
  `json`  
  successFunctionCall(json, state, xmlhttp_obj);  
  errorFunctionCall(state, xmlhttp_obj);  
  
  `jsonp`  
  successFunctionCall(json, state, jsonp_obj);  
  errorFunctionCall(state, jsonp_obj);  

### `NOTE` have not support POST 

## License
  Under The [MIT](https://tldrlegal.com/license/mit-license) License
