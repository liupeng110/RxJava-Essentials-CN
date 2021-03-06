# 微软响应式扩展

函数响应式编程是一个来自90年代后期受微软的一名计算机科学家Erik Meijer启发的思想，用来设计和开发微软的Rx库。

Rx 是微软.NET的一个响应式扩展。Rx借助可观测的序列提供一种简单的方式来创建异步的，基于事件驱动的程序。开发者可以使用Observables模拟异步数据流，使用LINQ语法查询Observables，并且很容易管理调度器的并发。

Rx让众所周知的概念变得易于实现和消费，例如**push方法**。在响应式的世界里，我们不能假装作用户不关注或者是不抱怨它而一味的等待函数的返回结果，网络调用，或者数据库查询的返回结果。我们时刻都在等待某些东西，这就让我们失去了并行处理其他事情的机会，提供更好的用户体验，让我们的软件免受顺序链的影响，而阻塞编程。

下表列出的与.NET 枚举相关的.NET Observable

| .NET Observable| 一个返回值| 多个返回值  |
| ------------- |:-------------:| -----:|
| Pull/Synchronous/Interactive|`T`| `IEnumerable<T>` |
| Push/Asynchronous/Reactive| `Task<T>`|`IObservable<T>`|

push方法把这个问题逆转了：取而代之的是不再等待结果，开发者只是简单的请求结果，而当它返回时得到一个通知即可。开发者对即将发生的事件提供一个清晰的响应链。对于每一个事件，开发者都作出相应的响应；例如，用户被要求登录的时候，提交一个携带他的用户名和密码的表单。应用程序执行登录的网络请求，接下来将要发生的情况有：

* 显示一个成功的信息，并保存用户的个人信息。
* 显示一个错误的信息

正如你用push方法所看到的，开发者不需要等待结果。而是在结果返回时通知他。在这期间，他可以做他想做的任何事情：

* 显示一个进度对话框
* 为下次登录保存用户名和密码
* 预加载一些他认为登录成功后需要耗时处理的事情