<p></p>

<h2 align="center">ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ПРОФЕССИОНАЛЬНОГО ОБРАЗОВАНИЯ <br> «САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ» <br> КАФЕДРА ИНФОРМАТИКИ </h2>
<p align="center">Лабораторная работа №5 <br>
по курсу «Web-технологии, языки и средства создания web-приложений» 

<p align="center"><b>"Node.js"</b><p>
<p align="right"><b>Выполнила: </b> студентка 331 группы Витковская Полина</p>
<p  align="right"><b>Принял: </b> Соболев Е. И., старший преподователь</p>
<br>
<br>
<br>
<p align="center">Южно-Сахалинск <br> СахГУ <br> 2023</p>
<h2> Введение </h2>
<p>Лабораторные работы по дисциплине «Web-технологии, языки и средства создания web-приложений» предназначены для освоения полученных теоретических знаний на практике. Перед началом лабораторной работы были поставлены цели: <br>
<ol>
  <li>Овладеть навыками работы с node.js. Используя Java Script, решить задачи.
</ol>
В соответствии с данными целями необходимо решить следующие задачи:
<ol>
   <li> Написать скрипты для решения данных задач.
   </ol>
Для реализации данной работы будет использоваться Visual Studio Code. Выполнение кода будет происходить в браузере Google Chrome с использованием node.js.
</p>
<h2>Решение задач</h2>
<p>Файл, запускающий сервер на node.js: </p>

```javascript
const express=require("express");
const app=express();

app.use(express.static(__dirname));
app.use("/",function(request,response) {
    response.sendFile("C:\\Users\\pvitk\\Desktop\\школа\\3курс\\Вебы\\lab5\\abs.html")
});
app.listen(3005);
console.log('Сервер работает');  
```
<p>HTML файл со скриптами:</p>

```javascript
 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
alert("Лабораторная 5");
//1
{
    var user = {};
    user.name = "John";
    user.surname = "Smith";
    alert(`name - surname: ${user.name} - ${user.surname}`);
    user.name = "Pete";
    alert(`name - surname: ${user.name} - ${user.surname}`);
    delete user.name;
    alert(`name - surname: ${user.name} - ${user.surname}`);   
}
//2

{
    function isEmpty(obj)
{
    return Object.keys(obj).length == 0;
} 
    let schedule = {};
    alert( isEmpty(schedule) ); // true
    schedule["8:30"] = "get up";
    alert( isEmpty(schedule) ); // false
}
//3
{
    const user = {
        name: "John"
    };
    // это будет работать?
    user.name = "Pete";
    alert(user.name); 
}
//4
{
    function isEmpty(obj)
{
    return Object.keys(obj).length == 0;
}
    let salaries = {
        John: 100,
        Ann: 160,
        Pete: 130
      };
    let sum = 0;
    if (isEmpty(salaries)) {
        alert(0);
        ;
    }
    else {
    for(const i in salaries)
    {
        sum += salaries[i];
    }
    alert(sum);
}
}
//5
{   
    function multiplyNumeric(obj)
    {
        for(const i in obj)
        {
        if (typeof obj[i] == "number") obj[i] *= 2; 
        }
        
    } 
    let menu = {
        width: 200,
        height: 300,
        title: "My menu"
      };
      
    multiplyNumeric(menu);
      
    alert(`menu = {\n width = ${menu.width}\n height = ${menu.height}\n title = ${menu.title}\n}`);
}
//6
{    
    let fruits = ["Яблоки", "Груша", "Апельсин"];

// добавляем новое значение в "копию"
let shoppingCart = fruits;
shoppingCart.push("Банан");

// что в fruits?
alert( fruits.length+" "+fruits);
 
}
//7
{    const styles = ["Джаз","Блюз"];
    alert(styles);
    styles.push("Рок-н-ролл");
    alert(styles);
    styles.splice(Math.floor(styles.length / 2), 1, "Классика" );
    alert(styles);
    alert("Удален: " + styles.shift());
    alert(styles);
    styles.splice(0, 0, "Рэп", "Регги");
    alert(styles);}
//8
{    let arr = ["a", "b"];
    arr.push(function() {
    alert( this );
    })
    arr[2](); // ?
}
//9
const arrayy = [];
{
    


while(true)
{
    var input = prompt("Введите число");
    if (input == undefined || input == "Отмена")
        break;
    else
        arrayy.push(parseInt(input));
}

let sum = 0;
for (let i = 0; i < arrayy.length; i++)
    sum += arrayy[i];

alert(sum);}
//10
{    let max = arrayy[0];

for(let i = 0; i < arrayy.length; i++)
{
    let sum = 0;
    for(let j = i; j < arrayy.length - i; j++)
    {
        sum += arrayy[j];
        if (max < sum)
        {
            max = sum;
        }
    }

}

let res= max > 0 ? max : 0;
alert(res);
}
//11
{    const array = [1, 1, 2, 3 ,4 ,5, 6, 6, 7 ,6 ,8, 6, 8]; // 1 1 2 3 4 5 7 8 8
    const result = [];
    for (let i = 0; i < array.length; i++)
    {
        let count = 0;
        if (result.indexOf(array[i]) != -1) continue;

        for(let j = 0; j < array.length; j++)
        {
            if (array[i] == array[j])
                {
                    count++;
                    if (count > 2)
                    {
                        result.push(array[i]);
                        break;
                    }
                }
        }
    }

    for(let i = 0; i < result.length; i++)
    {
        for(let j = 0; j < array.length; j++)
        {
            if(array[j] == result[i])
            {
               array.splice(j, 1);
               j--;
            }
        }
    }


    alert(array);}
//12
{    let array = [1, 2, 3, 4, 5, 10, 6, 7, 8 , 9];
    let max = array[0];
    for(let i = 0; i < array.length; i++) 
    {
        if(max < array[i]) max = array[i];
    }
    let array1 = array.slice(0, array.indexOf(max));
    let array2 = array.slice(array.indexOf(max) + 1, array.length);

    for(let i = 0; i < 3; i++) array1.unshift(array1.pop());
    array2.push(array2.shift())
    alert(array1.concat([max]).concat(array2));}
//13
{    const array = [-1, 2, 3, -2 , 4, -4, -10, -3]; // -20
    let sum = 0;
    for(let i = 0; i < array.length; i++)
    {
        if (array[i] < 0) sum += array[i];
    }
    alert(sum);}
//14
{    const array = [1, 2, 3, 4, 5, 6, 7]; // 105
    let result = 1;
    for (let i = 0; i < array.length; i++)
    {
        if(i % 2 == 1) result *= array[i];
    }
    alert(result);}
//15
{    const array = [1, 2, 0, 5, 5, 5, 5, 0, 1, 2, 3]; // 20
    let result = 0;
    let i = 0;

    if(array.indexOf(0) == - 1) {
        alert(0);
        
    }
    else {
    for(let i = array.indexOf(0) + 1; i < array.length; i++)
    {
        result += array[i];
        if(array[i] == 0)
        {
            
            break;
        }
    }
}
    alert(result);}
//16
{    const array = [1, 52, 1020, 1241, 5, 4444, 124]; // 4444
    let max = array[0];
    for(let i = 0; i < array.length; i++)
    {
        if (max < array[i]) max = array[i];
    }
    alert(max);}
//17
{    let array = [122, 52, 1020, 1241, 5, 4444, 124]; // 52
    let min = array[0];
    for(let i = 0; i < array.length; i++)
    {
        if(min > array[i] && (i + 1) % 2 == 0) min = array[i];
    }
    alert(min);}
//18
{    let array = [0, 2, 3, 0, 0, 1, 2, 0, 33, 4, 0];
    let indexNull = 0;
    for(let i = 0; i < array.length; i++)
    {
        if(array[i] == 0)
        {
            let temp = array[indexNull];
            array[indexNull] = 0;
            array[i] = temp;
            indexNull++;
        }
    }
    alert(array);}
//19
{    let array = [1, 2, 3, 4, 5, 0, 4, 3, 2, 1];// 4 + 5
    let min = 0;
    let max = 0;
    for(let i = 0; i < array.length; i++)
    {
        if (array[max] < array[i]) max = i;
        if (array[min] > array[i]) min = i;
    }
    alert(max + min);}
//20
{    let array = [10, -2, 4, -20, 2, 4, 15]; // -2
    let min = array[0];
    for(let i = 0; i < array.length; i++)
    {
        if(Math.abs(min) > Math.abs(array[i])) min = array[i];
    }
    alert(min);}
//21
{    let array = [];
    for(let i = 0; i < 10; i++)
        array.push(Math.floor(Math.random() * 10 - Math.random() * 10));

    let array1 = array.slice(0, 5).reverse();
    let array2 = array.slice(5, 10).reverse();
    alert(array);
    alert(array1.concat(array2));}
//22
{    let array = [];
    for(let i = 0; i < 12; i++)
        array.push(Math.floor(Math.random() * 12 - Math.random() * 12));
    
    alert(array);
    for(let i = 0; i < 4; i++) array.unshift(array.pop());
    alert(array);}
</script>
</body>
</html> 
```
<p>CodeWars:</p>

```javascript
  function calculate() {
  var first = 0; 
  for(var i = 0 ; i < arguments.length; i+=1) {
    first += arguments[i];
  }
  return function() {
  var second = 0;
  for(var j = 0 ; j < arguments.length; j +=1) {
    second += arguments[j];
  }
  return first+second;
  }
}
                      Array.prototype.map = function (callback, context) {
  const result = new Array(this.length);
  
  for (let i = 0; i < this.length; i++) {
    if (i in this)
      result[i] = callback.call(context, this[i], i, this);
  }
  
  return result;
};
Array.prototype.filter = function(f, receiver){
    var len = this.length;
    let result = [];
    for(let i = 0; i < len; i++)
    {
      if (i in this && f.call(receiver, this[i], i, this)){
        result.push(this[i]);
      } 
    }
  return result;
};
Function.prototype.bind = function(ctx){
  var func = this;
  return function(...args){
    return func.call(this == global ? ctx : this, ...args);
  };
};
function createFunctions(n) {
  var callbacks = [];

  for (var i=0; i<n; i++) {
    let j = i; // or const j = i;
    callbacks.push(function() {
      return j;
    });
  }
  
  return callbacks;
}
function createSecretHolder(secretj) {
  var obj = {};
  obj.secretj = secretj;
  obj.getSecret = () => obj.secretj;
  obj.setSecret = function(newSecret) {
    obj.secretj = newSecret;
  }
  return obj;
}
```
<p>API:</p>

```javascript
 </script>
<div>
    <p id="joke">
        
    </p>
    <button id="btn">Get random joke</button>
</div>
<script src="script.js"></script>

```
<p>Script.js:</p>

```javascript
const jokecontainer=document.getElementById("joke");
const btn=document.getElementById("btn");
const url="https://v2.jokeapi.dev/joke/Programming?blacklistFlags=nsfw,religious,political,racist,sexist,explicit&type=single";

let getjoke=()=>
{
    fetch(url)
    .then(data=>data.json())
    .then(item=>{
        jokecontainer.textContent=`${item.joke}`}
    );
}
btn.addEventListener("click",getjoke)
getjoke();
```
<h2>Вывод</h2>
<p>В ходе лабораторной работы были решены задачи на Java Script, выполнены задачи с Codewars, научились работать с API. Выполнение происходило с помощью Node.js</p>
