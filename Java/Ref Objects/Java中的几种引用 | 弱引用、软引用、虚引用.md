
# Java中的几种引用 | 弱引用、软引用、虚引用

Java中存在四种引用：**强引用、软引用、弱引用、虚引用**，这里来分别分析一下。


## StrongReference
**StrongReference（强引用）** 是最普通的引用类型，**只要强引用存在，GC就不会进行垃圾回收**。


## SoftReference
**SoftReference（软引用）** 用来描述一些**有用但是非必需的对象**。
如果一个对象只具有软引用，则内存空间足够，垃圾回收器就不会回收它；
如果**内存空间不足了，就会回收这些对象的内存**。只要垃圾回收器没有回收它，该对象就可以被程序使用。
软引用可以和一个**引用队列（ReferenceQueue）** 联合使用，
如果软引用所引用的对象被垃圾回收器回收，JVM就会把这个软引用加入到与之关联的引用队列中。
软引用可用来实现**内存敏感的高速缓存**。


## WeakReference
**WeakReference（弱引用）** 是一种**生命周期比软引用更短的引用**。
当**GC扫描**启动时，只要扫描到**只具有弱引用的对象，无论内存是否够用都会执行GC**，
但由于GC线程优先级很低，因此并不一定能迅速发现这些弱引用对象。弱引用也可以和一个引用队列联合使用。
WeakReference在Android中用的挺多。


## PhantomReference
**PhantomReference（虚引用）** 不同于其余三种引用，
虚引用不会影响对象的生命周期，也无法通过虚引用获得对象的一个实例；
如果一个对象仅持有虚引用，那么它就和没有任何引用一样(虚拟)，**在任何时候都可能被垃圾回收器回收**。
虚引用主要用来跟踪对象被垃圾回收器回收的活动，它必须和引用队列联合使用。


## 补充
【2015-7-16】逛InfoQ的时候又发现了一种FinalReference。用的不多就不总结了，
文章：[JVM源码分析之FinalReference完全解读](http://www.infoq.com/cn/articles/jvm-source-code-analysis-finalreference)


原文：[Java中的几种引用 | 弱引用、软引用、虚引用 | 「浮生若梦」 - sczyh30](http://www.sczyh30.com/posts/Java/java-reference-type/)
