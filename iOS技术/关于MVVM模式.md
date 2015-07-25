#关于MVVM模式的一点理解
说起mvvm模式不得不先说一下我们熟悉mvc模式。我相信任何一个iOS程序员都知道mvc。


![mvc_model_image](http://img.objccn.io/issue-13/mvvm1.png)

上图是一个典型的 MVC 设置。Model 呈现数据，View 呈现用户界面，而 View Controller 调节它两者之间的交互。嗯，就是这样。
但是在使用的过程中，我们都有这种感觉。虽然 View 和 View Controller 是技术上不同的组件，但它们几乎总是紧密的联系在一起，几乎没有一个View 能够与不同 View Controller 配对。mvc模式实际是下图那样。

![mvc_model_real_image](http://img.objccn.io//issue-13/intermediate.png)

我们往往把很多业务逻辑写在Controller里面，这样造成Controller相当臃肿，又难以理解。特别是维护别人写的代码的时候，看着Controller里面成千的代码混乱的逻辑，也是醉了。而且Controller里面的代码是不能被复用的，相同的逻辑放在Controller里面可能要写很多遍。那么有什么方法可以解决这样的问题呢？MVVM模式是一个比较好的方法。看下图：

![mvvm_model_image](http://img.objccn.io//issue-13/mvvm.png)

这个图解准确地描述了什么是 MVVM。位于View/Controller 与 Model 之间的“View Model”，主要用来存放表示逻辑。View/Controller只要直接显示数据就可以而不需要去做数据加工或逻辑判断的工作。
实际上MVVM是一个 MVC 的增强版，我们正式连接了视图和控制器，并将表示逻辑从 Controller 移出放到一个新的对象里，即 View Model。MVVM 听起来很复杂，但它本质上就是一个精心优化的 MVC 架构，而 MVC 你早已熟悉。

现在我们知道了什么是 MVVM，但为什么我们会想要去使用它呢？在 iOS 上使用 MVVM 的动机，对我来说，无论如何，就是它能减少 View Controller 的复杂性并使得表示逻辑更易于测试。

此处有三个重点是我希望你看完本文能带走的：

1. MVVM 可以兼容你当下使用的 MVC 架构。
2. MVVM 增加你的应用的可测试性。一些大公司是需要单元测试的，如果使用MVC，呵呵！
3. MVVM 配合一个绑定机制效果最好。如我们之前所见，MVVM 基本上就是 MVC 的改进版，所以很容易就能看到它如何被整合到现有使用典型 MVC 架构的应用中。在条件的容许下，开始吧！

####下面举一个简单的例子说明一下MVVM模式。
在MVVM模式中，我们可以把model表示加工的原料或半成品，view model 当做加工厂，view/controller 比作店铺或商场用来展示产品。
我们先来看mvc模式，model和view/controller直接打交道，让店铺去直接加工原料，这确实强人所难，每一个店铺都需要自己去生产产品。这样做只会让店铺显得很糟糕，也很难出好的产品。
而mvvm模式就不一样了。view model这个工厂会直接把产品生产出来，店铺只要负责进货就可以了，不用管产品是怎么来的，而且工厂是可以复用的。通过这个里面大家应该都能理解mvvm模式了，虽然这个例子不能完全说明这个模式。总之，mvvm模式只是一种思想，属于道的范围。至于怎么实现还是根据实际情况，是术的事情。
