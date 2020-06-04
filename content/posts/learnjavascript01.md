---
title: "Learnjavascript01"
date: 2020-06-02T16:27:13+08:00
draft: false
---
## Learn Javascript for beginner.
Open your chrome browser, amd press key "F12".

You will see the develop tool, And look for the console panel.

Then you can writting code in the panel now.

``` js
alert('Hello world');
```
Do you see the alert box?
let's to next step
## Scope
``` js
var a = 1;
console.log(a);
```
print: 1

Some of code about function.

``` js
function test(){
    var b = 1;
    return b;
}
console.log(b);
console.log(test);
console.log(test());
```
print: Uncaught ReferenceError: b is not defined

print: ƒ test(){ var b=1; return b; }

print: 1

``` js
function test(a){
    if(a){
        let b = 'b';
    }else{
        var c = 'c';
    }
    if(a){
        return b;
    }else{
        return c;
    }
}
console.log(test(true));
console.log(test(false));
```
print: Uncaught ReferenceError: c is not defined

print: c

## switch & const
``` js
function test(a){
    switch (a) {
        case 1 :
            let b = 'b';
            b = 'bb';
            return b;
            //break;
        case 2 :
            var c = 'c';
            c = 'cc';
            return c;
            //break;
        case 3 :
            const d = 'd';
            d = 'dd';
            return d;
            //break;
        default :
            return 'type number';
            //break;
    }
}
console.log(test(1));
console.log(test(2));
console.log(test(3));
```
print: bb

print: cc

print: Uncaught TypeError: Assignment to constant variable.