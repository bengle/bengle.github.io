---
layout: default
title: tips to comment your code
---
# {{ page.title }}
translate by bengle
{{ page.date | date_to_string }}
下面的13条贴士可以告诉我们怎样注释你的源代码可以让它更容易理解和持续维护。
## 1.每一级注释
给一个代码模块加注释，每一级都应该使用统一的方式。例如：
每一个类，注释应该包括：概要描述、作者以及最后一次修改的日期；
每一个方法，注释应该包括：方法作用的描述、函数、参数以及结果；
注释采纳的标准在团队合作中非常重要。当然，采用约定或者工具的方式来帮助完成注释是允许的，甚至是十分可取的。
## 2.分段注释
将代码模块分解成一个一个功能单一的片段，然后在每一块开始处添加注释告诉阅读者将要发生什么。

```javascript
// Check that all data records
// are correct 
foreach (Record record in records) 
{
		if (rec.checkStatus()==Status.OK)
			{ 
					. . . 
			} 
} 
// Now we begin to perform 
// transactions 
Context ctx = new ApplicationContext(); 
ctx.BeginTransaction();
```

## 3.连续多行注释要对齐

对于连续多行都有注释的情况，将注释对其可以让人更容易理解。

```javascript
const MAX_ITEMS = 10; // maximum number of packets 
const MASK = 0x1F;    // mask bit TCP
```

有些人使用tab键来对齐注释，有些人使用空格键。由于tab键在不同编辑器和IDE中设置的值不同，因此最好使用空格来对其注释。

## 4.不要侮辱读者的智商

避免毫无意义的注释，例如：

```javascript
if (a == 5)      // if a equals 5 
	    counter = 0; // set the counter to zero
```

写这种无意义注释不仅浪费你的时间，而且会影响读者理解本来不用想就能读懂的代码。

## 5.注意文雅

千万不要写这样的注释：“注意愚蠢的用户输入了一个负数”或者“修复了悲哀且愚蠢的开发者制造的副作用”。这种注释会给代码的作者带来不好的影响，而且你不知道未来谁会读这些注释（可能是你的老板，可能是用户，也可能是你所侮辱的悲哀且愚蠢的作者）

## 6.直截了当

不要写多余的注释，能表达意思就好。不要把注释写的象笑话、诗歌或者hyperverbosity。简而言之，注释要保持简单直接。

## 7.保持风格统一

有些人认为注释是必要的，这样非程序员就能看懂它们。有些人则认为注释只要程序员能看懂就好了。不管怎样，就像Successful Strategies for Commenting Code 中描述的那样，关键是你的注释应该始终针对统一的对象。个人看法是非程序员不会花时间去读代码，注释应该针对其他的程序员。

## 8.使用特殊标签

当在团队合作中，可以坚持采用一套标签方便程序员之间的沟通。例如：很多团队使用“TODO”标签来表明一段需要额外工作的代码。

```javascript
			int Estimate(int x, int y) 
			{
				    // TODO: implement the calculations 
						    return 0;
			}
```

标签注释并不用来解释代码，它们更多的用来引起注意或者传递信息。如果你使用这种技巧，那么请记住要完成标签注释信息中要求的事情。

## 9.在写代码的时候就添加注释

在写代码的时候就把注释给加上吧，因为这个时候你还清晰的记得它。如果你写完代码在从头添加注释，那么你将话费两倍的时间。“我没有时间写注释”，“我现在很忙”，“项目要延期了”这些都不是逃避你完成代码文档的借口。有些程序员认为写代码之前先写注释是规划最佳代码的一种方式。

```javascript
			public void ProcessOrder() 
			{
					// Make sure the products are available
					// Check that the customer is valid 
					// Send the order to the store 
					// Generate bill 
			}
```

## 10.象写给自己那样写注释（其实就是写给自己的）

给代码写注释的时候，不仅要想这是写给将来维护这段代码的人，还要想想这注释对自己有没有用。就像phil haack所说的：代码一出现在屏幕上，你就应该进入代码维护模式了。
总而言之，我们自己应该是好的（坏的）注释的第一个受益者（受害者）。

## 11.代码更新的时候更新注释

不随代码更新的注释是没有用处的。代码和注释应该齐头并进，否则对维护你代码的人来说就是灾难。需要特别注意的是那些那些可以自动更新代码但是对注释不做修改的重构工具应该立即放弃。

## 12.注释黄金定律：让你的代码可以读懂

最许多程序员来说代码可以让人读懂是一条基本定律。尽管提出这种说法的人可能本身不喜欢写注释，但是可读性强的代码确实可以让代码的可理解上走得更远，甚至完全不需要注释。例如，在我的Fluid Interfaces这篇文章中可以看到代码可以易读到什么程度：

```javascript
			Calculator calc = new Calculator();
			calc.Set(0);
			calc.Add(10);
			calc.Multiply(2);
			calc.Subtract(4);
			Console.WriteLine( "Result: {0}", calc.Get() );
```

这个例子中我们可以看到注释完全是没有必要的，看起来跟第4条冲突了。为了增强代码的可读性，你应该思考更加合适的命名方式，保持正确的缩进，采用正确的代码风格规范（coding style guides）。如果没有遵从这些建议，你的注释就会象在给糟糕的代码说抱歉。

## 13.与你的同事分享这些建议

虽然第10条告诉我们好的注释能给让自己马上受益，但是这些建议可以让所有开发者受益，特别是在团队合作中。所以尽情的将这些建议分享给你的同事吧，让你们创造的代码更容易理解和维护。

原文地址：[http://www.devtopics.com/13-tips-to-comment-your-code/](http://www.devtopics.com/13-tips-to-comment-your-code/)
