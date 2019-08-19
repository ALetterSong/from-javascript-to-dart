# From JavaScript To Dart

> Forked form [MindorksOpenSource/from-java-to-kotlin](https://github.com/MindorksOpenSource/from-java-to-kotlin)

## Dart 的一些特性

- 尽管 Dart 是强类型的，但是 Dart 可以推断类型
- 与 Java 不同，Dart 没有关键字 public， protected 和 private
- Optional named parameters 与 Optional positional parameters
- 函数是一等公民
- 级联操作符 / 条件成员访问操作符...
- 继承 / 抽象类 / 隐式接口 ( class 即 interface ) / Mixin / 枚举
- 支持泛型
- 支持元数据（注解）
- async 和 await 及 Future API / Stream API


## JavaScript to Dart

### 打印日志
 - JavaScript

```javascript
console.log('Hello World')
```

-  Dart

```dart
print('Hello World');
```

---

### 常量与变量
- JavaScript

```javascript
let num = 1;
const num = 1;
```

- Dart

```dart
int num = 1;
var num = 1;
const num = 1;
final num = 1;
```

---
### null声明
- JavaScript

```javascript
let lineCount = null;
```

- Dart

未初始化的变量默认值是 null

```dart
int lineCount;
```

---
### 空判断
-  JavaScript

```javascript
if (text) {
    const length = text.length();
}
```

-  Dart

```dart
// If p is non-null, set its y value to 4.
p?.y = 4;
```

---
### 字符串拼接

-  JavaScript

```javascript
let firstName = "Amit";
let lastName = "Shekhar";
let message = "My name is: " + firstName + " " + lastName;
```

-  Dart

```dart
var firstName = "Amit";
var lastName = "Shekhar";
var message = "My name is: $firstName $lastName";
```

---
### 换行
- JavaScript

```javascript
let text = "First Line\n" +
              "Second Line\n" +
              "Third Line";
```

- Dart

```dart
var text = """
        First Line
        Second Line
        Third Line
        """;
```

---

### 三元表达式
- JavaScript

```javascript
let text = x > 5 ? "x > 5" : "x <= 5";
```

- Dart

```dart
var text = x > 5 ? "x > 5" : "x <= 5";
String playerName = name ?? 'Guest';
```

---
### 操作符
- JavaScript

```javascript
const andResult  = a & b;
const orResult   = a | b;
const xorResult  = a ^ b;
const rightShift = a >> 2;
const leftShift  = a << 2;
const unsignedRightShift = a >>> 2;
```

- Dart

```dart
var andResult  = a & b;
var orResult   = a | b;
var xorResult  = a ^ b;
var rightShift = a >> 2;
var leftShift  = a << 2;
```

---
### 类型判断和转换 (声明式)
- JavaScript

```javascript
class Person {
  firstName;

  constructor(firstName) {
    this.firstName = firstName;
    console.log(`in Person${firstName}`);
  }
}

class Employee extends Person {

  constructor(firstName) {
    super(firstName);
    console.log(`in Employee${firstName}`);
  }
}

const emp = new Employee('Peter');
emp.firstName = 'Bob';
console.log(emp.firstName);

```

- Dart

```dart
class Person {
  String firstName;

  Person(this.firstName) {
    print('in Person$firstName');
  }
}

class Employee extends Person {
  Employee(firstName) : super(firstName) {
    print('in Employee$firstName');
  }
}

void main() {
  var emp = new Employee('Peter');
  if (emp is Person) {
    // Type check
    emp.firstName = 'Bob';
  }
  (emp as Person).firstName = 'Bob';
  print(emp.firstName);
}
```

---
### 类型判断和转换 (隐式)
- JavaScript

```javascript
"1" + 2
```

- Dart

```dart

```

---
### 多重条件

### case 语句

### for 循环

### 集合操作

- JavaScript 

```javascript
// Or simply use a list literal.
var fruits = ['apples', 'oranges'];

// Add to a list.
fruits.push('kiwis');

// Add multiple items to a list.
fruits = fruits.concat(['grapes', 'bananas']);
// Remove a single item.
var appleIndex = fruits.indexOf('apples');
fruits.splice(appleIndex, 1);
console.log(fruits);

```

- Dart

```dart
// Or simply use a list literal.
var fruits = ['apples', 'oranges'];

// Add to a list.
fruits.add('kiwis');

// Add multiple items to a list.
fruits.addAll(['grapes', 'bananas']);
// Remove a single item.
var appleIndex = fruits.indexOf('apples');
fruits.removeAt(appleIndex);
print(fruits);

fruits.clear();
print(fruits.isEmpty);
```

[control flow collections proposal](https://github.com/dart-lang/language/blob/master/accepted/2.3/control-flow-collections/feature-specification.md)

### 遍历

---
###  方法定义
- JavaScript

```javascript
function doSomething() {
   // logic here
}

function doSomething(numbers) {
   // logic here
}
```

- Dart

```dart
void doSomething() {
   // logic here
}

fun doSomething(List<int> numbers) {
   // logic here
}
```

---
### 带返回值的方法
- JavaScript

```javascript
function getScore() {
   // logic here
   return score;
}
```

- Dart

```dart
int getScore(int score) {
   // logic here
   return score * 100;
}

// as a single-expression function

int getScore(int score) => score * 100;
```

---
### constructor 构造器
- JavaScript

```javascript
class Point {
  constructor(x, y) {
    // There's a better way to do this, stay tuned.
    this.x = x;
    this.y = y;
  }
}
```

- Dart

```dart
class Point {
  num x, y;

  Point(num x, num y) {
    // There's a better way to do this, stay tuned.
    this.x = x;
    this.y = y;
  }
}

// another way

class Point {
  num x, y;

  // Syntactic sugar for setting x and y
  // before the constructor body runs.
  Point(this.x, this.y);
}
```

---
### Get Set 构造器
- JavaScript

```javascript
class Rectangle {
  left;
  top;
  width;
  height;

  constructor(left, top, width, height) {
    this.left = left;
    this.top = top;
    this.width = width;
    this.height = height;
  }

  // Define two calculated properties: right and bottom.
  get right() {
    return this.left + this.width;
  }

  set right(value) {
    this.left = value - this.width
  }

  get bottom() {
    return this.top + this.height;
  }

  set bottom(value) {
    this.top = value - this.height
  }

}
```

-  Dart

```dart
class Rectangle {
  num left, top, width, height;

  Rectangle(this.left, this.top, this.width, this.height);

  // Define two calculated properties: right and bottom.
  num get right => left + width;
  set right(num value) => left = value - width;
  num get bottom => top + height;
  set bottom(num value) => top = value - height;
}
```

---

### 克隆
- JavaScript

[lodash#clone](https://lodash.com/docs/4.17.15#clone)

```javascript
function jsonClone(obj) {
    return JSON.parse(JSON.stringify(obj));
}

```

-  Dart

```dart

```
### Class 静态方法

- JavaScript

```javascript
class Utils {
  static triple(value) {
    return 3 * value;
  }
}
```

- Dart

```dart
class Utils {
  static int triple(int value) {
    return 3 * value;
  }
}
```

### enum


### 排序

- JavaScript 

```javascript
var fruits = ['bananas', 'apples', 'oranges'];

// Sort a list.
fruits.sort();
```

- Dart

```dart
var fruits = ['bananas', 'apples', 'oranges'];

// Sort a list.
fruits.sort();
```

### 匿名类



