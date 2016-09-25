# lab3

本节目标：

- 通过“星座计算”小程序，掌握 `JOptionPane` 的使用、字符串转换为数字、条件判断与逻辑表达式。
- 学习 Java Style Guide ，书写良好的代码风格。

## 星座计算

### 问题描述

通过 `JOptionPane` 输入一个字符串类型的日期，在命令行中输出这个日期对应的星座。

| 星座   | 起始日期          |
| ---- | ------------- |
| 魔羯座  | 12/22 - 1/19  |
| 水瓶座  | 1/20 - 2/18   |
| 双鱼座  | 2/19 - 3/20   |
| 牡羊座  | 3/21 - 4/20   |
| 金牛座  | 4/21 - 5/20   |
| 双子座  | 5/21 - 6/21   |
| 巨蟹座  | 6/22 - 7/22   |
| 狮子座  | 7/23 - 8/22   |
| 处女座  | 8/23 - 9/22   |
| 天秤座  | 9/23 - 10/22  |
| 天蝎座  | 10/23 - 11/21 |
| 射手座  | 11/22 - 12/21 |

新建一个 Java 文件，按顺序完成下面的三个部分，最终拼接成上述的小程序。

### 第 1 部分 - 判断日期对应的星座

假设我们已知年月日：

```java
int year = 1995;
int month = 7;
int day = 10;
```

然后使用 `if` 和 `else` 和逻辑表达式判断该日期对应的星座。以巨蟹座和狮子座为例：

```java
if ((month == 6 && day >= 22) || (month == 7 && day <= 22) {
  // 这是巨蟹座 🦀 
} else if ((month == 7 && day >= 23) || (month == 8 && day <= 22) {
  // 这是狮子座 🦁
} 
...
```

类似地，我们对每个星座分别做一次判断。

### 第 2 部分 - 字符串到整型的转换

事实上，我们从 `JOptionPane` 中读到的日期是字符串类型的。为了完成上一步中的星座判断，我们需要将这个字符串类型的日期转换成整型。

假设我们已知一个形如 `1995.07.10` 的日期字符串：

```java
String dateString = "1995.07.10";
```

我们需要将它转换成下面的形式：

```java
int year = 1995;
int month = 7;
int day = 10;
```
以年份为例，我们通过 `String` 的 `substring` 方法截取日期字符串中的年份子串。在这里，年份占了第 0 至 4 位。因此，通过如下的代码即可获得年份子串：

```java
// 这里的(0, 4)是一个前闭后开区间，即数学上的[0,4)位
String yearString = dateString.substring(0, 4); 
```

然后，我们通过 `Integer` 的 `parseInt` 方法将年份字符串转换成整型：

```java
int year = Integer.parseInt(yearString);
```

类似地，我们完成月和日的转换。

### 第 3 部分 - 输入输出

**请注意，在你的 Java 文件开头加上这行代码**，否则运行时 javac 将无法找到 `JOptionPane`。

```java
import javax.swing.*;
```

我们通过 `JOptionPane` 的 `showInputDialog` 方法弹出一个对话框，要求用户输入一个日期字符串：

```java
String dateString = JOptionPane.showInputDialog("输入日期");
```

规定输入的日期字符串形如 `YYYY.MM.DD`，如下所示：

![image](https://cloud.githubusercontent.com/assets/7262715/18815505/73bb0ca2-8366-11e6-9977-5817676280a9.png)

最后，在你第一部分完成的代码中插入下列语句输出结果：

```java
System.out.printf("巨蟹座");
```