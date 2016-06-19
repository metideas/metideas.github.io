---
title: Core-Python-Programming
tags:
  - Python
categories:
  - Reading
cc: true
comments: true
date: 2016-06-03 16:44:01
---
## 中英对照表
|     英文     |  中文  |
| :--------: | :--: |
|   colon    |  冒号  |
|    wrap    |  封装  |
| assertions |  断言  |
| statement  |  语句  |
|            |      |
<!-- more --><!-- indicate-the-source -->
### ch10 异常处理

#### 使用异常的理由

> 在应用层处理错误的能力近来变得更为重要, 用户已不再是应用程序的的唯一的直接运行者.  
> 随着互联网和网上电子商业应用越来越普及, web 服务器将成为应用软件的主要客户. 这意味着应用
> 程序再也不能只是直接的失败或崩溃, 因为如果这样, 系统错误导致浏览器的错误, 这反过来又
> 会让用户沮丧. 失去眼球意味着失去广告收入和和潜在的大量无可挽回的生意.    
>
> 如果错误的确发生了, 它们一般都归因于用户输入的数据无效. 运行环境必须足够强健,来处
> 理应用级别的错误,并提供用户级别的错误信息.就服务器而言,这必须转化为一个"非错误" . 因为
> 应用必须要成功的完成, 即使所做的不过是返回一个错误的信息, 向用户是提供一个有效的超文本
> 标记语言(HTML)的网页指明错误.    
>
> 这种类型的执行错误不应该被允许, 无论情况如何. 随着系统变得更加复杂, 又牵涉到更多的
> 新手用户, 要采取额外的措施, 确保用户平滑的学到应用经验. 即使面对一个错误, 应用应该成功
> 的中止, 不至于灾难性的影响其执行环境. Python 异常处理促使成熟和正确的编程.

#### try-except-else-finally 的应用和熟悉    

try:

​	...

except:

​	...

else:

> 在try...except块可以有一个else子句，就像if语句，如果在try中没有异常引发，然后else子句就执行！！！

如果在 finally 的语句块内发生了一个异常,你可以创建一个同现有的异常
处理器在同一个(外)层次的异常处理器来处理它.这样,从本质上来说,就可以同时处理在原始的 try
语句块和 finally 语句块中发生的错误.这种方法唯一的问题是,当 finally 语句块中的确发生异常
时,你会丢失原来异常的上下文信息,除非你在某个地方保存了它.  

如果 finally 中的代码引发了另一个异常或由于 return,break,continue 语
法而终止,原来的异常将丢失而且无法重新引发.

```Python
try:
    try_suite

except Exception1:
    suite_for_Exception1

except (Exception2, Exception3, Exception4):
    suite_for_Exceptions_2_3_and_4

except Exception5, Argument5:
    suite_for_Exception5_plus_argument

except (Exception6, Exception7), Argument67:
    suite_for_Exceptions6_and_7_plus_argument

except:
    suite_for_all_other_exceptions

else:
    no_exceptions_detected_suite
finally:
    always_execute_suite
```
#### wtih 语句[待理解]
`应用场景: `类似try-except-finally , with语句也是用来简化代码的,这与用try-except和try-finally
所想达到的目的前后呼应.try-except 和 try-finally 的一种特定的配合用法是保证共享的资源的
唯一分配,并在任务结束的时候释放它.比如文件(数据,日志,数据库等等),线程资源,简单同步,数
据库连接,等等. with 语句的目标就是应用在这种场景.
#### 触发异常
- 上述是由解释器产生的异常
- 执行期间的错误, 比如在编写 API 时候希望能够在遇到错误输入时触发异常 → 使用raise 语句
> raise [SomeException [, args [, traceback]]]   
> 第一个参数,SomeExcpetion,是触发异常的名字.如果有,它必须是一个字符串,类或实例(详见下文).如果有其他参数(arg 或 traceback),就必须提供 SomeExcpetion. 第二个符号为可选的 args(比如参数,值),来传给异常. 最后一项参数,traceback,同样是可选的(实际上很少用它),如果有的话,则是当异常触发时新生成的一个用于异常-正常化(exception—normally)的追踪(traceback)对象.

#### assertation
断言语句可以认为是 (raise-if-not)语句

`效果`

`语法 `   assert expression[,&nbsp arguments]

`使用场景 `
```Python
try:
    assert 1 == 0, 'One does not equal zero silly!'
except AssertionError, args:
    print '%s: %s' % (args.__class__.__name__, args)

#输出 AssertionError: One does not equal zero silly!
```
#### 标准异常

#### sys module 下的异常

`sys.exc_info()`

- exc_type: exception class object


- exc_value: (this) exception class instance object [same with exception argument]
- exc_traceback: traceback object

####  Q&A

1. 哪些因素会引发异常: the interpreter & the program

2. which could raise exceptions while running within the interactive interpreter(交互解释器): user & the interpreter & the program

3. 用来引发异常的关键字有哪些? (Name the keyword(s) which is (are) used to raise exceptions.)

   `try   except     finally     raise`  

4. 剩余问题参考[该篇文章][1]

### Chapter11 函数和函数式编程

#### Type of Object That Python Returns

overloading is not a feature of Python




`效果`

`语法`

`使用场景`

[1]: http://www.voidcn.com/blog/birdzb/article/p-4912342.html
