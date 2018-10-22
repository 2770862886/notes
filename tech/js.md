% Javascript Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

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
