---
title: "Learnjavascript02"
date: 2020-06-02T17:50:31+08:00
draft: false
---

# Let we build a calculator on the browser
## desgin the web page by HTML
``` js
html=' \
    <div> \
        <input type="text" id="inputBox" value="0"> \
        <button type="button" id="addSign">+</button> \
        <button type="button" id="subtractSign">-</button> \
        <button type="button" id="multiplySign">*</button> \
        <button type="button" id="divideSign">/</button> \
        <button type="button" id="equalSign">=</button> \
        <button type="button" id="cleanSign">Clean</button> \
    </div>';
document.body.innerHTML = html;
```

## Add, subtract, multiply and divide
``` js
function sum(a1, a2){
    return a1+a2;
}

function substract(a1, a2){
    return a1-a2;
}

function multiply(a1, a2){
    return a1*a2;
}

function divide(a1, a2){
    var tmp = a1/a2;
    return isNaN(tmp)? 0 : tmp;
}

```

## How to work?
let we get elements.
``` js
var inputBox = document.getElementById('inputBox');
var addSign = document.getElementById('addSign');
var subtractSign = document.getElementById('subtractSign');
var multiplySign = document.getElementById('multiplySign');
var divideSign = document.getElementById('divideSign');
var equalSign = document.getElementById('equalSign');
var cleanSign = document.getElementById('cleanSign');
```

We Write a function what name is preRun,

it will pre-process the data when you type numbers.

``` js
function preRun(signType){
    var data = Number(inputBox.value);
    if(isNaN(data)){
        alert('please type number');
        return;
    }
    if(typeof preRun.tmp !== 'number'){
        preRun.tmp = data;
    }
    if(typeof preRun.sign !== 'string'){
        preRun.sign = signType;
        return;
    }
    preRun.sign = signType;
    run();
}
```
We Write a function what name is run,

it will process the data and show the result on inputBox when you type button of equal-sign.
``` js
function run(){
    var data = Number(inputBox.value);
    if(typeof preRun.sign !== 'string' || typeof preRun.tmp !== 'number')
        return;
    var result = 0;
    switch(preRun.sign){
        case 'add' :
            result = sum(preRun.tmp, data);
            break;
        case 'subtract' :
            result = substract(preRun.tmp, data);
            break;
        case 'multiply' :
            result = multiply(preRun.tmp, data);
            break;
        case 'divide' :
            result = divide(preRun.tmp, data);
            break;
    }
    preRun.tmp = result;
    inputBox.value = result;
}
```
just clean data function.
``` js
function cleanData(){
    delete preRun.tmp;
    delete preRun.sign;
    inputBox.value = "0";
}
```
let we regist event.
``` js
addSign.addEventListener('click',function(){ preRun('add'); });
subtractSign.addEventListener('click',function(){ preRun('subtract'); });
multiplySign.addEventListener('click',function(){ preRun('multiply'); });
divideSign.addEventListener('click',function(){ preRun('divide'); });

equalSign.addEventListener('click',function(){ run(); });
cleanSign.addEventListener('click',function(){ cleanData(); });
```


