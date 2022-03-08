#Terminating app due to uncaught exception 'NSUnknownKeyException'错误解决办法
<p>今天遇到一个错误：
<strong>Terminating app due to uncaught exception 'NSUnknownKeyException’,
 reason: '[<ViewController 0x7f95aa40af70> setValue:forUndefinedKey:]: this class is not key value coding-compliant for the key lable.’</strong></p>

谷歌翻译了一下：
>由于未捕获的异常'NSUnknownKeyException'终止应用程序，原因：'[<ViewController 0x7f95aa40af70> setValue：forUndefinedKey：]：此类不是密钥值的密钥值编码兼容。

这么复杂的吗？?
![Alt text](https://ws3.sinaimg.cn/large/006tNbRwgy1fuirozsnybj306906975d.jpg)

后来在Stack Overflow上找到了答案。

第一位大大说：
>The most likely source of this error is that something has a connection to an action or outlet called done that doesn't exist in the code for that class.

意思就是有个东西联系了一个名叫done的action但是这个action在类中不存在。

第二位大大说：
>The easiest way to check that is to Ctrl+Click on your Controller in the Storyboard View and look for something in the resulting popup which has a yellow warning mark next to it. Simply delete it by pressing the (x) next to the Outlet name.


就是按住Ctrl键点击Controller类，如果有黄色的警告⚠️就点x。

![Alt text](https://ws4.sinaimg.cn/large/006tNbRwgy1fuirs7bi68j30910ciq4b.jpg)

我按照这个方法做的时候，发现**Received Actions**那里出现了黄色警告⚠️，就明白了，我一开始写了一个方法，联系了三个button，但是后来觉得还是分成三个方法比较好，于是就又写了三个方法，再分别联系每个button，然后删了原来的那个方法，才出现了这样的错误。

搞定，这个错误原因就是**有多余的连线**，以后明白怎么做了。

还有一个经常遇到的错误：

![Alt text](https://ws3.sinaimg.cn/large/006tNbRwgy1fuirtwxh30j30id00ejrq.jpg)
就是没有找到对应的方法，要么就添加相关的方法，要么就删除多余的连线。

![Alt text](https://ws4.sinaimg.cn/large/006tNbRwgy1fuirt7ku7qj305y06j0u5.jpg)
