

JDK Release Notes
=================
> [JDK Release Notes](https://www.oracle.com/technetwork/java/javase/jdk-relnotes-index-2162236.html)
>
> 2019-08-29



## JDK 12 Release Notes
> [JDK 12 Release Notes](https://www.oracle.com/technetwork/java/javase/12u-relnotes-5211424.html)

### JDK 12 (GA)
> [JDK 12 (GA)](https://www.oracle.com/technetwork/java/javase/12-relnote-issues-5211422.html)



## JDK 11 Release Notes
> [JDK 11 Release Notes](https://www.oracle.com/technetwork/java/javase/11u-relnotes-5093844.html)

### JDK 11 (GA)
> [JDK 11 (GA)](https://www.oracle.com/technetwork/java/javase/11-relnote-issues-5012449.html)



## JDK 10 Release Notes
> [JDK 10 Release Notes](https://www.oracle.com/technetwork/java/javase/10u-relnotes-4108739.html)

### JDK 10
> [JDK 10](https://www.oracle.com/technetwork/java/javase/10-relnote-issues-4108729.html)



## JDK 9 Release Notes
> [JDK 9 Release Notes](https://www.oracle.com/technetwork/java/javase/9u-relnotes-3704429.html)
>
> 非LTS/长期支持版本

### JDK 9
> [JDK 9](https://www.oracle.com/technetwork/java/javase/9-relnotes-3622618.html)



## JDK 8 Release Notes
> [JDK 8 Release Notes](https://www.oracle.com/technetwork/java/javase/8u-relnotes-2225394.html)
> 
> **LTS/长期支持版本**

### JDK 8 (GA)
> [JDK 8 (GA)](https://www.oracle.com/technetwork/java/javase/8-relnotes-2226341.html)

#### [What's New in JDK 8](https://www.oracle.com/technetwork/java/javase/8-whats-new-2157071.html)
* Java Programming Language
  * Lambda Expressions Lambda/闭包表达式
  * Method references 方法引用
  * Default methods 默认方法
  * Repeating Annotations
  * Type Annotations
  * Improved type inference 类型推导
  * Method parameter reflection.
* Collections
  * Stream API to support functional-style operations on streams of elements 支持函数式操作
  * Performance Improvement for HashMaps with Key Collisions 散列表的键冲突的性能改进
* Date-Time Package - provide a comprehensive date-time model.
* IO and NIO
  * New SelectorProvider implementation for Solaris
  * Performance improvement for the java.lang.String(byte[], *) constructor and the java.lang.String.getBytes() method.
* java.lang and java.util Packages
  * Parallel Array Sorting
  * Standard Encoding and Decoding Base64
* Concurrency
  * Classes and interfaces have been added to the java.util.concurrent package.
  * Methods have been added to the java.util.concurrent.ConcurrentHashMap class to support aggregate operations based on the newly added streams facility and lambda expressions.
  * Classes have been added to the java.util.concurrent.atomic package to support scalable updatable variables.
  * Methods have been added to the java.util.concurrent.ForkJoinPool class to support a common pool.
  * The java.util.concurrent.locks.StampedLock class has been added to provide a capability-based lock with three modes for controlling read/write access.
* HotSpot
  * Removal of PermGen.
  * Default Methods in the Java Programming Language are supported by the byte code instructions for method invocation.
* Java Mission Control 5.3 Release Notes



## JDK 7 Release Notes
> [JDK 7 Release Notes](https://www.oracle.com/technetwork/java/javase/jdk7-relnotes-429209.html) 

### Java SE 7 Features and Enhancements
> [Java SE 7 Features and Enhancements](https://www.oracle.com/technetwork/java/javase/jdk7-relnotes-418459.html) 

#### 1.Highlights of Technology Changes in Java SE 7
* [IO and New IO](https://docs.oracle.com/javase/7/docs/technotes/guides/io/enhancements.html#7) 
  (java.nio.file, File I/O (NIO 2.0), File System Provider)
* [Networking](https://docs.oracle.com/javase/7/docs/technotes/guides/net/enhancements-7.0.html) 
  (`URLClassLoader.close`, Sockets Direct Protocol (SDP))
* [Security](https://docs.oracle.com/javase/7/docs/technotes/guides/security/enhancements-7.html) 
* [Concurrency Utilities](https://docs.oracle.com/javase/7/docs/technotes/guides/concurrency/changes7.html) 
  (fork/join framework, `ForkJoinPool`, `ThreadLocalRandom`, `Phaser`)
* [Internationalization](https://docs.oracle.com/javase/7/docs/technotes/guides/intl/enhancements.7.html) 
  (Unicode 6.0.0)
* [java.lang Package](https://docs.oracle.com/javase/7/docs/technotes/guides/lang/enhancements.html#7) 
  * [Multi-threaded Custom Class Loaders in Java SE 7](https://docs.oracle.com/javase/7/docs/technotes/guides/lang/cl-mt.html) 
* [Java Programming Language](https://docs.oracle.com/javase/7/docs/technotes/guides/language/enhancements.html#javase7) 
  * [Binary Literals](https://docs.oracle.com/javase/7/docs/technotes/guides/language/binary-literals.html) 
  * [Strings in switch Statements](https://docs.oracle.com/javase/7/docs/technotes/guides/language/strings-switch.html) 
  * [The try-with-resources Statement](https://docs.oracle.com/javase/7/docs/technotes/guides/language/try-with-resources.html) 
    (使用`try`的资源清理语句 (`AutoCloseable/Closeable`))
  * [Catching Multiple Exception Types and Rethrowing Exceptions with Improved Type Checking](https://docs.oracle.com/javase/7/docs/technotes/guides/language/catch-multiple.html) 
    (捕获多种异常类型和通过改进的类型检查重新抛出异常)
  * [Underscores in Numeric Literals](https://docs.oracle.com/javase/7/docs/technotes/guides/language/underscores-literals.html) 
  * [Type Inference for Generic Instance Creation](https://docs.oracle.com/javase/7/docs/technotes/guides/language/type-inference-generic-instance-creation.html) 
    (泛型实例创建的类型推导 (*diamond*))
  * [Improved Compiler Warnings and Errors When Using Non-Reifiable Formal Parameters with Varargs Methods](https://docs.oracle.com/javase/7/docs/technotes/guides/language/non-reifiable-varargs.html) 
* [Java Virtual Machine (JVM)](https://docs.oracle.com/javase/7/docs/technotes/guides/vm/) 
  * [Java Virtual Machine Support for Non-Java Languages](https://docs.oracle.com/javase/7/docs/technotes/guides/vm/multiple-language-support.html) 
    (JVM对非Java语言的支持 (`invokedynamic`))
  * [Garbage-First Collector](https://docs.oracle.com/javase/7/docs/technotes/guides/vm/G1.html) 
    (G1垃圾收集器(heap sizes > 6GB, pause time < 0.5s)，替代Concurrent Mark-Sweep Collector (CMS))
  * [Java HotSpot Virtual Machine Performance Enhancements](https://docs.oracle.com/javase/7/docs/technotes/guides/vm/performance-enhancements-7.html) 
    (Tiered Compilation/分层编译，Compressed Oops，Zero-Based Compressed Oops，Escape Analysis/逸出分析，NUMA Collector Enhancements)
* [JDBC](https://docs.oracle.com/javase/7/docs/technotes/guides/jdbc/) 

#### 2.Important RFEs Addressed in Java SE 7
**Area**: HotSpot  
**Synopsis**: The *JVM/TI version number* was changed from 1.1 to `1.2` in order to add the `GetLocalInstance` method.  
**RFE**: 7003782, 7004582

**Area**: Security  
**Synopsis**: *Security algorithm* requirements have been defined for Java SE 7 
  that provide a list of algorithms that all implementations of Java SE 7 must support. 
  The class summary of applicable classes (ex: `java.security.Signature`) has been updated to include the implementation requirements. 
  Also, all of the requirements are listed in the [Implementation Requirements](https://docs.oracle.com/javase/7/docs/technotes/guides/security/StandardNames.html#impl) 
  section of the Standard Algorithms document.  
**RFE**: 5001004

**Area**: API: JSSE  
**Synopsis**: Support for *TLS 1.2* has been added to the SunJSSE provider.  
**RFE**: 6916074

**Area**: API: Language  
**Synopsis**: *Class loading* can be prone to `deadlocks` if custom class loaders do not adhere to an `acyclic` *class loader delegation model*. 
  New APIs have been added to the `java.lang.ClassLoader` class to support 
  `parallel loading of classes` and finer-grained `locking mechanism for class loading operations`. 
  Custom class loaders which would like to leverage this functionality must 
  refer to the [Class Loader API Modifications for Deadlock Fix](https://openjdk.java.net/groups/core-libs/ClassLoaderProposal.html) documentation 
  for the suggested model and requirements and be implemented accordingly.

#### 3.Important RFEs Addressed in JDK 7
**Area**: Tools  
**Synopsis**: A succinct and concise *error message* is printed, as appropriate, when an error occurs during the Java launcher initialization. 
  The full *stack trace* will be printed when applicable, or when the error has trickled up from the ClassLoader or Reflection APIs.  
**RFE**: 6968053

**Area**: HotSpot  
**Synopsis**: *Classfiles* with version number `51` are exclusively verified using the *type-checking verifier*, 
  and thus the methods must have `StackMapTable` attributes when appropriate. 
  For classfiles with version `50`, the HotSpot JVM would (and continues to) failover to the *type-inferencing verifier* if the stackmaps in the file were missing or incorrect. 
  This failover behavior does not occur for classfiles with version `51` (the default version for `JDK7`).  
  Any tool that modifies *bytecode* in a version `51` *classfile* must be sure to update the *stackmap* information to be consistent with the bytecode in order to pass verification.  
**RFE**: 6693236

**Area**: HotSpot  
**Synopsis**: In JDK 7, *interned strings* are no longer allocated in the permanent generation of the Java heap, 
  but are instead allocated in the `main part of the Java heap` (known as the `young and old generations`), along with the other objects created by the application. 
  This change will result in more data residing in the main Java heap, 
  and less data in the permanent generation, and thus may require heap sizes to be adjusted. 
  Most applications will see only relatively small differences in heap usage due to this change, 
  but larger applications that load many classes or make heavy use of the `String.intern()` method will see more significant differences.  
**RFE**: [6962931](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6962931)

**Area**: HotSpot  
**Synopsis**: The default out-of-the-box heap size and shape parameters for the *concurrent mark sweep collector (CMS)* have been modified. 
  The new settings take advantage of faster platforms that have been introduced since JDK 6 was released. 
  Like the other collectors in HotSpot, CMS will now use the available *physical memory* on the platform to size its heap, 
  while attempting to shape that heap to keep `pause times` associated with minor collections "reasonable". 
  The specific shape of the heap may be platform-dependent in other ways as well. 
  Users can override all or some of these default settings by explicitly sizing or shaping the heap, 
  AKA "heap tuning", to suit their specific needs.  
  For more information on the default settings for this and other garbage collectors, 
  please see the [Heap Tuning Guide for JDK 6](https://www.oracle.com/technetwork/java/javase/gc-tuning-6-140523.html).  
**RFE**: [6896099](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6896099)

**Area**: HotSpot  
**Synopsis**: The *GarbageFirst (G1) garbage collector* is `experimental` in this release. 
  Some command line tools, such as `jstack` or `jmap`, may not work properly when using the *G1 collector*.  
**RFE**: [6966967](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6966967)

**Area**: API: Utilities  
**Synopsis**: Due to `an error` in `java.util.TreeMap`, it was previously possible to 
  insert invalid `null` elements and elements not implementing `Comparable` into `empty` `TreeMaps` and `TreeSets`. 
  Only a single invalid element could be inserted into the empty `TreeMaps` or `TreeSets`; 
  additional elements would cause the expected `NullPointerException` or `ClassCastException`. 
  Most other operations upon the collection would also fail. As of *JDK 7*, inserting an invalid `null` element or 
  an element not implementing *Comparable* into an empty `TreeMap` or `TreeSet` throws a `NullPointerException`.  
**RFE**: [5045147](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=5045147)

**Area**: API: NIO  
**Synopsis**: Prior to the JDK 7 release, *direct buffers* allocated using `java.nio.ByteBuffer.allocateDirect(int)` were `aligned` on *a page boundary*. 
  In *JDK 7*, the implementation has changed so that `direct buffers are no longer page aligned`. 
  This should reduce the memory requirements of applications that create lots of `small buffers`. 
  Applications that previously relied on the undocumented alignment can revert to previous behavior 
  if they are run with the command line option: `-XX:+PageAlignDirectMemory`. 
**RFE**: [4837564](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=4837564)


