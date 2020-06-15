# es6-const

> const和let完全相同，仅在于用const声明的变量，必须在声明时赋值，而且不可以重新赋值。

### 常量声明时必须赋值

```js
const a;
console.log(a) // 报错（缺失初始化 在 一个常量的声明中）
```
### 常量不可以重新赋值

```js
const a = 1;
a = 2; 
console.log(a) // 报错（赋值给常量）
```
### 要注意的细节

#### 常量不可变

常量不可变，是指声明的常量的内存空间不可变，并不保证内存空间中的地址指向的其他空间不可变。
```js
// 不能给a直接重新赋值，但是可以改变a里面的值 
const a = {
    name: 'sunny'
};
a.name = 'lisa'; 
console.log(a) // {name: 'lisa'}

a = {
    name: 'kevin'
};
console.log(a) // 报错 Uncaught TypeError: Assignment to constant variable.
```
    
#### 常量的命名

1. 特殊的常量： 该常量从字面意义上，一定是不可变的，比如圆周率、月地距离和其他一些不可更改的配置。通常，**该常量的名称全部使用大些写，多个单词之间用下划线分割。**
    ```js
    const PI = 3.14;
    const MOON_EARTH_DISTANCE = 384403.9;
    ```
2. 普通常量：使用和之前一样的命名即可。
3. 在循环中，循环变量不可以使用常量。（因为常量不可重新赋值，let声明的变量可以重新赋值）
    ```js
    for(const i = 0; i < 10; i++){
        console.log(i) // 0 报错
    }
    
    // 补充 ：for in 当中可以使用const（因为在每个块级作用域当中，使用的是全新的常量）
    let obj = {
        name:'lisa',
        age: 20
    }
    for(const prop in obj){
        console.log(prop) // name age
    }
    ```    
    ```js
    for(let i = 0; i < 10; i++){
        console.log(i)
    }
    ```    
    
    

