# 我遇到的面试题

1.算法：16进制转10进制。（美团出行）

2.算法：单链表检查是否有环，未追问检查环位置（贝壳||美团）

3.算法：N叉数深度（美团）

4.算法：有15个瓶子，其中最多有一瓶有毒，现在有四只老鼠，喝了有毒的水之后，第二天就会死。如何在第二天就可以判断出哪个瓶子有毒 （滴滴客户端）

5.算法：给300亿地图数据点，如何快速找到用户当前周边20个点。（美团）

6.算法：找出倒数第n个节点（别人遇到的）

7.算法：镜像二叉树（别人遇到的）

8.算法：写一个快速排序 （爱奇艺）

9.算法：n个数里面查找中位数，例如（5，6，2，7，1，4，3），找出4。（爱奇艺）

（算法一般只需要讲思路就行，即便让写）

此博客覆盖了不少题，可以看一下：

[https://cloud.tencent.com/developer/article/1165416](https://cloud.tencent.com/developer/article/1165416)

---

1.git rebase 和 git merge的区别

2.block修饰，strong和copy区别

3.FPS指什么，怎么实现的

4.weak 处理

5.runtime 项目中的使用（1.category 2.字典转模型 3.exchange 4.崩溃三次尝试拦截）

1).追问:+load方法调用时机及为什么在这种时机

2).追问: +load方法，一个class的4个category都有+load方法，调用顺序。为什么？

3).追问: 接2，如果每个category都转换了系统方法，例如viewDidAppear，则最终结果怎样，如何避免。

4.)追问：class的isa方法查找流程，实例方法和类方法

5.)追问：category内存处理机制

6.)exchang方法交换 和 replace 方法替换 的区别

7.）你知道有哪些情况会导致app崩溃，分别可以用什么方法拦截并化解

6.应用从点击到启动时调用逻辑。

7.GCD相关知识，什么是GCD，信号量，group，栅栏等
1).追问，这些使用时，如何选择
2).追问，group是怎样使用的，（除了dispatch_group外，还需要知道enter和level的用法）
3).追问，GCD的队列（dispatch_queue_t）怎么管理队列的。队列不是先进先出吗，这里怎么不是？

8.线程和进程的区别

9.category和extention的区别

10.遇到过一次代码风格面试（爱奇艺）
![](../../resource/image/687474703a2f2f692e696d6775722e636f6d2f4f375a657639342e706e67.png)

11.以下打印结果是什么：（爱奇艺）

```
  NSLog(@"1");
    dispatch_async(dispatch_get_main_queue(), ^{
        NSLog(@"2");

        dispatch_after(dispatch_time(DISPATCH_TIME_NOW, (int64_t)(0 * NSEC_PER_SEC)), dispatch_get_main_queue(), ^{
            NSLog(@"3");
            
            dispatch_async(dispatch_get_global_queue(0, 0), ^{
                NSLog(@"4");
            });

        });
        
        dispatch_async(dispatch_get_global_queue(0, 0), ^{
            NSLog(@"5");
        });
    });
    
    dispatch_async(dispatch_get_global_queue(0, 0), ^{
        NSLog(@"6");
    });
    
    NSLog(@"7");
```

打印结果如下：

```
2018-09-11 17:25:17.420211+0800 TestOCDemo[1293:7549260] 1
2018-09-11 17:25:17.420341+0800 TestOCDemo[1293:7549260] 7
2018-09-11 17:25:17.420350+0800 TestOCDemo[1293:7549296] 6
2018-09-11 17:25:17.425499+0800 TestOCDemo[1293:7549260] 2
2018-09-11 17:25:17.425643+0800 TestOCDemo[1293:7549296] 5
2018-09-11 17:25:17.426039+0800 TestOCDemo[1293:7549260] 3
2018-09-11 17:25:17.426153+0800 TestOCDemo[1293:7549296] 4
```

12.沙盒目录下有几个文件夹。NSUserDefaults存储格式，及在哪个文件夹下。

1).追问：版本升级会保留哪些文件夹

13.性能优化之类的

1.)如何进行的性能优化

2.）FPS静态是多少，滑动列表是多少

3.）你的项目crash率多少

13.观察者的底层逻辑

14.CALayer和UIView

15.autoreleasepool的实现原理，考察autoreleasepoolPage。
1).追问2个@autoreleasepool{} 会生成几个autoreleasepoolPage。

16.SDWebImage 流程及架构模式

17.https连接流程（TLS/SSL）
1).非对称加密
2).说出一些常用的错误码及对应信息
3).什么是网络堵塞和流畅

18.timer 在主线程启动，在子线程关闭，会出现什么问题。

19.能否向编译后得到的类中增加实例变量？能否向运行时创建的类中添加实例变量？为什么？

20.ARC内存管理

1.）追问什么时机增加autorelease

21.内存区（静态区，堆区，栈区，常量区）

22.自己写runtime解析属性时，比如一个integer属性，如何解析。

23.设计准的timer

1.)displaylink

2.)gcd_timer

24.面向对象编程，面向切面编程，面向接口编程，(彩琴遇到的，😀)


25.关联对象有什么应用，系统如何管理关联对象？其被释放的时候需要手动将其指针置空么？

26.离屏渲染原理

[https://blog.ibireme.com/2015/11/12/smooth_user_interfaces_for_ios/](https://blog.ibireme.com/2015/11/12/smooth_user_interfaces_for_ios/)

27.NSOperation的一些知识。例如（追问了，NSOperation能pause吗）

28.说出你所知道的设计模式。（当然不仅仅指的是当前那些常用的，而是那些不常用的，比如策略模式，抽象模式等，工厂模式等等）

1.)可能会追问

29.静态库和动态库区别

30.响应链和查找第一响应

1.)追问，如何扩大button的点击区域（hintTest:event:）

2.)追问，在A View 上add B view，B view的frame 在A的外面，点击会如何。




----

### 其他：(weak被问的很多，可以按照此深度准备)

```
为什么 iOS 开发没人要了？

从历年 weak 看 iOS 面试：

2013年
面试官：代理用 weak 还是 strong ?
我 ：weak 。 
面试官：明天来上班吧

2014年
面试官：代理为什么用 weak 不用 strong?
我 ： 用 strong 会造成循环引用。
面试官：明天来上班吧

2015年
面试官：weak 是怎么实现的？
我 ：weak 其实是 系统通过一个 hash 表来实现对象的弱引用
面试官：明天来上班吧

2016年
面试官：weak 是怎么实现的？
我 ：runtime 维护了一个 weak 表，用于存储指向某个对象的所有 weak指针。weak 表其实是一个 hash（哈希）表，key 是所指对象的地址，Value 是 weak 指针的地址（这个地址的值是所指对象指针的地址）数组。
面试官：明天来上班吧

2017年
面试官：weak 是怎么实现的？
我 ：

初始化时：runtime会调用objc_initWeak函数，初始化一个新的weak指针指向对象的地址。
添加引用时：objc_initWeak函数会调用 storeWeak() 函数， storeWeak() 的作用是更新指针指向，创建对应的弱引用表。
释放时,调用clearDeallocating函数。clearDeallocating函数首先根据对象地址获取所有weak指针地址的数组，然后遍历这个数组把其中的数据设为nil，最后把这个entry从weak表中删除，最后清理对象的记录。
面试官：明天来上班吧
2018年
面试官：weak是怎么实现的？
我 ：跟2017年说的一样，还详细补充了objc_initWeak, storeWeak, clearDeallocating的实现细节。
面试官：小伙子基础不错。13k ,996干不干？干就明天来上班… 下一个

2019年
面试官：weak是怎么实现的？
我 ：别说了，拿纸来，我动手实现一个。
写完后
面试官：小伙子不错，我考虑考虑，你先回去吧么实现的？
我 ：别说了，拿纸来，我动手实现一个。
写完后
面试官：小伙子不错，我考虑考虑，你先回去吧
```