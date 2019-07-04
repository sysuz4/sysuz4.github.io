#  浅析观察者模式与RxJava

## 什么是RxJava
  * Github上对于RxJava的介绍
    > RxJava:Reactive Extensions for the JVM – a library for composing asynchronous and event-based programs using observable sequences for the Java VM. 

    它的大概意思是：针对于JVM(Java虚拟机）的响应式扩展实现，一个在Java VM上使用可观察的序列来组合实现异步的、基于事件编程的库。

    RxJava是对于**观察者模式**的扩展，那么观察者模式又是什么呢？
## 什么是观察者模式
  * 观察者模式的不同解释：
    > 观察者模式是将观察者与被观察者分离开，实现了对象间一种一对多的组合关系，当被观察者的状态发生变化时，所有依赖于它的观察者就会检测到变化并且刷新自己的状态。
    
    > 观察者模式定义了一种一对多的依赖关系，让多个观察者对象同时监听某一个主题对象。

    > 观察者模式是关于多个对象想知道一个对象中数据变化情况的一种成熟模式。观察者模式中有一个称作“主题”的对象和若干个称作“观察者”的对象，“主题”和“观察者”之间是一种一对多的依赖关系。


  * 观察者模式中的角色
    * 抽象主题：定义添加和删除观察者的功能；
    * 抽象观察者：定义观察者收到主题通知后要做什么事情；
    * 具体主题：抽象主题的具体实现；
    * 具体观察者：抽象观察者的具体实现。
  * 观察者模式的UML类图
    
    ![观察者模式类图](img/observe_pattern_uml.PNG)

    * 对于观察者模式中角色的实现
      * Subject接口对应着角色中的抽象主题，它定义了需要实现的接口，包括添加与删除观察者，以及主题发生改变时的动作notifyAllObservers。
      * Observer接口对应着角色中的抽象观察者，它定义了观察者接收到主题发生变化时需要做出的动作update。
      * ConcreteSubject实现了Subject接口，具体了主题。
      * CconcreteObserver1-3具体了观察者，实现了Observer接口。

    * 具体实现的时候，先实例化一个ConcreteSubject对象,然后再实例化多个ConcreteObserver对象，将这些对象通过ConcreteSubject的addObserver方法添加到主题的私有成员列表mObserverList中;当主题发生变化时通过调用ntifyAllObserver方法，通过循环执行列表中每个ConcreteObserver对象的update方法就可以使得每个观察者对象进行更新操作。
    * 这里我们可以看到，当主题更新时，并不是通过观察者监测到主题的变化，而是主题会自己通知观察者它发生了变化并调用观察者的update方法，所以这个观察者并不是真正的在时时刻刻观察着主题的变化；而是被主题通知发生了变化。与其说是观察者**观察**变化，不如说是主题在**通报**变化。
    
## RxJava中的观察者模式

[参考博客](https://juejin.im/post/5b17560e6fb9a01e2862246f)
* 1.创建被观察者
```
Observable observable = Observable.create(new ObservableOnSubscribe<Integer>() {
    @Override
    public void subscribe(ObservableEmitter<Integer> e) throws Exception {
        Log.d(TAG, "=========================currentThread name: " + Thread.currentThread().getName());
        e.onNext(1);
        e.onNext(2);
        e.onNext(3);
        e.onComplete();
    }
});
```

* 2.创建观察者
```
Observer observer = new Observer<Integer>() {
    @Override
    public void onSubscribe(Disposable d) {
        Log.d(TAG, "======================onSubscribe");
    }

    @Override
    public void onNext(Integer integer) {
        Log.d(TAG, "======================onNext " + integer);
    }

    @Override
    public void onError(Throwable e) {
        Log.d(TAG, "======================onError");
    }

    @Override
    public void onComplete() {
        Log.d(TAG, "======================onComplete");
    }
};

```

* 订阅
```
observable.subscribe(observer);
```

* 被观察者发送给观察者发送的事件:

| 事件        | 作用    
| --------   | -----   |
|onNext()|发送该事件时，观察者会回调 onNext() 方法|
|onError()|发送该事件时，观察者会回调 onError() 方法，当发送该事件之后，其他事件将不会继续发送|
|onComplete()|发送该事件时，观察者会回调 onComplete() 方法，当发送该事件之后，其他事件将不会继续发送|


