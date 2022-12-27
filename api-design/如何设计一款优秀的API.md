

如何设计一款优秀的API
==================
> Joshua Bloch，2014-02-18 (2006)
> [原文](https://www.csdn.net/article/2014-02-18/2818441-How-to-design-a-good-API)

随着近来软件规模的日益庞大，API编程接口的设计变的越来越重要。
**良好的接口设计**可以**降低系统各部分之间的相互依赖，提高`组成单元的内聚性`，降低`组成单元间的耦合度`**，从而**提高系统的维护性和稳定性。**

**Joshua Bloch**是美国著名程序设计师。
他为Java平台设计并实现了许多的功能，是Google的首席Java架构师(Chief Java Architect)。
他也是《Effective Java Programming Language Guide》一书的作者，就是人们常说的Effective Java。
本文翻译自Joshua Bloch所发表的一个PPT [How to design a good API and why it matters](https://ai.google/research/pubs/pub32713/)。

随着大数据、公共平台等互联网技术的日益成熟，API接口的重要性日益凸显。
从公司的角度来看，API可以算作是公司一笔巨大的资产，公共API可以捕获用户，为公司做出许多贡献。
对于个人来说，只要你编程，你就是一个**API设计者**，因为好的代码即是**模块——每个模块便是一个API**，而好的模块会被多次使用。
此外，编写API还有利于开发者提高代码质量，提高自身的编码水平。


## 1.优秀API所具备的**特征**
* **简单易学**
* **易于使用**，即使没有文档(**易用**)
* **很难误用**
* **易于阅读**，代码**易于维护**
* 足够强大，可以满足需求
* **易于扩展**
* 适合用户

了解了一款优秀API所具备的特征后，一起再来看看如何设计优秀的API，**有哪些流程和规则可循**，开发者**在设计时需要注意哪些事项**。


## 2.API设计流程中的注意事项

### 征集**需求**
在开始之前，你可能会收到一些解决方案，它们不一定会比现有的方案好。
而你的任务是以`用例`的形式**提取真实需求**，并**制定真正合适的解决方案**，这样构建出来的东西就会更加有价值。

### 从**简短的说明**开始
这时，编写简短的说明最为合适，编写时`需要考虑的因素`有：
* **灵活性**要远胜于完整性
* 跳出规则，听取意见并严阵以待
* **精炼短小**才易修改
* 获得信任之后将其**具体化/具象化**，在此之中，**编程**很重要

### 尽早**编写API**
* 对每一个实现进行保存，以防丢失
* 在开始之前，列出一些**合理的规定**，保存所写说明，以防丢失
* 继续编写和充实API

### **编写SPI**尤为重要
* **Service Provider Interface**即**服务提供商接口**，插件服务支持多种实现
* 发布之前编写多个插件
* **三次原则("The Rule of Threes")**：指的是当某个功能第三次出现时，才进行"抽象化"

### 维护**切实可行的期望**
* 大多数API设计都过于约束
* 对`可能会犯的错误`进行预计，要用**发展的思维**来编写API


## 3.API**设计原则**
**每个API接口应该只专注一件事，并做好**。
如果它`很难命名`，那么这或许是个不好的征兆，**好的名称可以驱动开发，并且只需拆分与合并模块**即可。

* **API应尽可能地轻小**：满足需求，对有疑问的地方可以暂时不使用(函数、类、方法、参数等，你可以不添加但千万不要删除)，概念性的东西比体积重要，寻找一个良好的动力体积比。
* 实现不要影响API：关注实现细节(`不要迷惑用户，不要随便改变实现方式`)，意识到具体的实现细节(不要有越权的方法行为，例如不要制订哈希函数、所有的调优参数都是可疑的)。
* **不要让实现细节“泄露”到API**：例如on-disk和on-the-wire格式等异常情况
* **最小化可访问**：设计人员**应尽量把类及成员设为私有**，公共类不应该有公共字段(包括异常实例)，**最大限度地提高信息隐藏，允许模块可以被使用、理解、构建、测试和独立调试**。
* **命名问题**：应该**见名知意**，`避免含糊的缩写`。**对同一样东西的命名应该有个一致性的前缀**(遍及整个平台API)，讲究对称，代码应该易读。

```
if (car.speed() > 2 * SPEED_LIMIT)
  generateAlert("Watch out for cops!");
```

### 重视**文档**
**开发API时要意识到文档的重要性**。**组件重用**不是纸上谈兵的东西，**既需要好的设计，也需要优秀的文档，这二者缺一不可**。即使我们看到了良好的设计而未见文档，那么组件重用也是不妥的。
—— 摘自 D. L. Parnas 在1994年第16届国际软件开发大会上的演讲内容

文档应包含每个类、接口、方法、构造函数、参数和异常，此外，还要小心对待文档的状态空间。

### **API设计决策**对性能的影响
* API设计决策对性能的影响是真实永久的
* 不好的决策会限制性能(类型易变，构造函数替代静态工厂，实现类型替代接口)
* **不得打包API来提升性能**(潜在的性能问题可能会得到修复，但救的了一时，救不了一世)
* **良好的设计通常与好的性能是一致的**

### **API与平台**和平共处
* **养成良好的习惯**：**遵守标准的命名约定**，避免陈旧的参数和返回类型，**核心API和语言的模仿模式**
* **利用API的友好功能**：泛型、可变参数、枚举、默认参数
* 了解和避免`API陷阱和缺陷`：Finalizers、公共静态final数组


## 4.API中**类的设计**

### 最小化**可变性**
* `最好不要随便改变类`，除非有一个非常合理的理由
* 如果是*可变类*，最好保持很小的状态空间，定义良好的结构，因时制宜地去调用方法

### **子类**只存在有意义的地方
* 子类具备可替代性(Liskov)
* 公共类不应该继承其它公共类

### 用于继承的设计和文档或者直接禁止继承
* `继承破坏封装`
* 如果你允许子类和文档自用，那么要考虑彼此该如何互相调用方法
* 保守策略：把所有类都设置成final


## 5.API中的**方法设计**
**模块能做到的，客户端就不要做。**

### 减少模板代码的使用
```
    // DOM code to write an XML document to a specified output stream.
    private static void writeDoc(Document doc, OutputStream out) throws IOException {
        try {
            Transformer t = TransformerFactory.newInstance().newTransformer();
            t.setOutputProperty(OutputKeys.DOCTYPE_SYSTEM, doc.getDoctype().getSystemId());
            t.transform(new DOMSource(doc), new StreamResult(out));
        } catch (TransformerException e) {
            throw new AssertionError(e); // Can’t happen!
        }
    }
```

### 遵守**最小惊讶原则**
**用户API只需根据需求来设计**即可，不必让客户感到惊讶，小心弄巧成拙。

```
public class Thread implements Runnable {
    // Tests whether current thread has been interrupted.
    // Clears the interrupted status of current thread.
    public static boolean interrupted();
}
```

### **故障快速报告**应尽快生成
* **编译时最好是静态类型、泛型**
* 方法里应该包含**错误自动提交机制**

```
// A Properties instance maps strings to strings
public class Properties extends Hashtable {
    public Object put(Object key, Object value);

    // Throws ClassCastException if this properties
    // contains any keys or values that are not strings
    public void save(OutputStream out, String comments);
}
```

### 以String形式对所有可用数据提供编程式访问
```
public class Throwable {
    public void printStackTrace(PrintStream s);

    public StackTraceElement[] getStackTrace(); // Since 1.4
}

public final class StackTraceElement {
    public String getFileName();

    public int getLineNumber();

    public String getClassName();

    public String getMethodName();

    public boolean isNativeMethod();
}
```

### **方法重载**要细心
* 避免模棱两可的重载，例如多个重载适用于同一个实物
* 即使你能分清，也最好不要这样做，**最好起个不同的名字**
* 如果非要定义这种重载，相同的参数确保相同的行为

```
public TreeSet(Collection c); // Ignores order
public TreeSet(SortedSet s);  // Respects order
```

### 使用**合适的参数和返回类型**
* 通过类来支持**接口类型输入**
* **尽可能地使用最特定的输入参数类型**
* 如果已经有一个更好的类型存在，就不要使用string类型
* `不要用浮点型来修饰货币值`(高精确不够)
* 使用double(64位)而不要使用float(32位)
* 在方法上参数顺序要一致，尤其是参数类型相同时，则尤为重要

```
#include <string.h>
    char *strcpy (char *dest, char *src);
    
    void bcopy (void *src, void *dst, int n);
```

```
java.util.Collections – first parameter always collection to be modified or queried
java.util.concurrent – time always specified as long delay, TimeUnit unit
```

### 避免使用**长参数列表**
* **三个或三个以内的参数是最完美的**
* 长参数列表是有害的，程序员容易出错，并且程序在编译、运行时会表现不好
* 缩短参数的两种方法：Break up method，创建*参数助手类*

最好避免这种情况出现：
```
// Eleven parameters including four consecutive ints
HWND CreateWindow(LPCTSTR lpClassName, LPCTSTR lpWindowName,
    DWORD dwStyle, int x, int y, int nWidth, int nHeight,
    HWND hWndParent, HMENU hMenu, HINSTANCE hInstance, LPVOID lpParam);
```

### **返回值**勿需进行异常处理
比如，返回零长度字符串或者空集合。

```
public interface BufferedImageOp {
    // Returns the rendering hints for this operation,
    // or null if no hints have been set.
    public RenderingHints getRenderingHints();
}
```


## 6.API中的**异常设计**
**抛出异常来说明异常状况**，不要强迫客户端使用异常来控制流。

```
private byte[] a = new byte[BUF_SIZE];

void processBuffer(ByteBuffer buf) {
    try {
        while (true) {
            buf.get(a);
            processBytes(tmp, BUF_SIZE);
        }
    } catch (BufferUnderflowException e) {
        int remaining = buf.remaining();
        buf.get(a, 0, remaining);
        processBytes(bufArray, remaining);
    }
}
```

反之，也不要静默失败。

```
ThreadGroup.enumerate(Thread[] list)
```

### 支持**不受检的异常(Unchecked Exceptions)**
* Checked——客户端肯定会做一些**恢复措施**(受检的异常)
* Unchecked——**编程错误**(不受检的异常)
* 过度使用Checked异常会产生一些模板代码

```
try {
    Foo f = (Foo) super.clone();
    // ....
} catch (CloneNotSupportedException e) {
    // This can't happen, since we’re Cloneable
    throw new AssertionError();
}
```

### **异常**中应该包含**捕获错误的(Failure-Capture)信息**
* **允许诊断和修复或恢复**
* 对于Unchecked异常，有异常消息就行了
* 对于Checked异常，提供访问器


## 7.**重构API设计**

### 在Vector中进行sublist操作
```
public class Vector {
    public int indexOf(Object elem, int index);

    public int lastIndexOf(Object elem, int index);
    // ...
}
```
分析：
* 在搜索上不强大
* 没有文档很难使用

### 重构sublist操作
```
public interface List {
    List subList(int fromIndex, int toIndex);
    // ...
}
```
分析：
* 非常强大——支持所有操作
* 使用*接口*来减少概念权重：较高的动力重量比(power-to-weight)
* 没有文档也易于使用

### 线程局部变量
```
// Broken - inappropriate use of String as capability.
// Keys constitute a shared global namespace.
public class ThreadLocal {
    private ThreadLocal() {
    } // Non-instantiable

    // Sets current thread’s value for named variable.
    public static void set(String key, Object value);

    // Returns current thread’s value for named variable.
    public static Object get(String key);
}
```

#### 线程局部变量重构1
```
public class ThreadLocal {
    private ThreadLocal() {
    } // Non-instantiable

    public static class Key {
        Key() {
        }
    }

    // Generates a unique, unforgeable key
    public static Key getKey() {
        return new Key();
    }

    public static void set(Key key, Object value);

    public static Object get(Key key);
}
```
可以运行，但是需要使用模板代码。
```
static ThreadLocal.Key serialNumberKey = ThreadLocal.getKey();
ThreadLocal.set(serialNumberKey, nextSerialNumber());
System.out.println(ThreadLocal.get(serialNumberKey));
```

#### 线程局部变量重构2
```
public class ThreadLocal {
    public ThreadLocal() {
    }

    public void set(Object value);

    public Object get();
}
```
从API和客户端代码中删除了无用代码。
```
static ThreadLocal serialNumber = new ThreadLocal();
serialNumber.set(nextSerialNumber());
System.out.println(serialNumber.get());
```


## 8.总结
API设计是一件非常高端大气上档次的工艺，对程序员、终端用户和公司都会有所提升。
不要盲目地去遵守文中所提及的规则、说明等，但也不要去侵犯他们，API设计不是件简单的工艺，也不是一种可以孤立行动的活。
**当然完美永远无法实现，但我们要努力去追求完美。**


**附上Joshua Bloch的PPT**：

来自[How to design a good API and why it matters](https://ai.google/research/pubs/pub32713/)

