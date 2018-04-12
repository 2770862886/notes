% Javascript Tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

## isNaN ##

isNaN(undefined) === true;  
isNaN(null) === false;  
isNaN(123) === false;  
isNaN("123") === false;  
isNaN("test") === true;  

## template string ##

let i = 6;  
logger.i(`the string is ${i}`);  
