
### Html Code

```
<html>
  <body>
    <textarea id="inputText"/>
    <span id="textNumber">0</span>
  </body>
</html>
```

### javascript Code

```

var obj_textarea = document.getElementById("inputText");
var obj_textNumber = doucument.getElementById("textNumber");
//控制开关
var clickSwitch = false;

textarea.addEventListener("keyup",function(){
  if(clickSwitch == false){
    obj_textNumber.textContent = obj_textarea.value.length;
  }
});

obj_textarea.addEventListener("compositionstart",function(){
  clickSwitch = true;
});
obj_textarea.addEventListener("compositionend",function(){
  clickSwitch = false;
})

```
