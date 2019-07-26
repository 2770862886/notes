% Javascript Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Javascript-algorithms](https://github.com/trekhleb/javascript-algorithms)

## Loop ##
* for ... in introduced in ES5 aim to enumerate keys of an array.
* for ... of introduced in ES6 aim to make up (for ... in), to enumerate values of an array.

## isNaN ##

isNaN(undefined) === true;  
isNaN(null) === false;  
isNaN(123) === false;  
isNaN("123") === false;  
isNaN("test") === true;  

## template string ##

let i = 6;  
logger.i(`the string is ${i}`);  

## time ##
1.new Date().getTime()
2.Date.now()
3.process.uptime()
4.process.hrtime()

## Math class ##
* abs()
* max()
* min()
* random()
* ceil(x)
* floor(x)
* round(x) 四舍五入
* sin() 正弦
* cos() 余弦
* tan() 正切
* acos() 反余弦
* asin() 反正弦
* atan() 反正切
* atan2(y,x) 返回从x轴到点(x,y)的角度(-PI/2, PI/2)之间
* exp(x) 返回e的x次幂
* pow(x,y) 返回x的y次幂
* log(x) 返回数的自然对数(底为e)

## console ##
console.trace();

## map/reduce ##
2003 SOSP publish GFS
2004 OSDI publish MapReduce
2006 OSDI publish BigTable

* map() 原数组中每个元素调用一个指定方法后，返回返回值组成的新数组

``` javascript
function pow(x) {
    return x^2;
}

let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
let result = arr.map(pow); // map 传入函数对象作为唯一参数
console.log(result);  // [1, 4, 9, 16, 25, 36, 49, 64, 81]

```

* reduce() 为数组中每一个元素依次执行回调函数

``` javascript
function cb(ac, cur) {
    console.log(ac);
    console.log(cur);
}
[x1, x2, x3, x4].reduce(cb, 0);

cb(0, x1);
cb(x1, x2);
cb(x1 + x2, x3);
cb(x1 + x2 + x3, x4);
```

