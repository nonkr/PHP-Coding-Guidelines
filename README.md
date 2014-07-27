PHP编程规范
=========

本规范参考自。

[RFC 2119][]中的`必须(MUST)`，`不可(MUST NOT)`，`建议(SHOULD)`，`不建议(SHOULD NOT)`，`可以/可能(MAY)`等关键词将在本规范中用来做一些解释性的描述。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt


1. 基本代码规范
---------
### 1.1. 文件
* 源文件中php代码的编码格式`必须`只使用不带`字节顺序标记(BOM)`的`UTF-8`。
* 源文件`必须`只使用 `<?php` 和 `<?=` 这两种标签，`不可`使用短标签。
* 如果是纯php源文件，`必须`不带结束标签`?>`。
* 一个源文件`建议`只用来做声明（`类(class)`，`函数(function)`，`常量(constant)`等）或者只用来做一些引起副作用的操作（例如：输出信息，修改`.ini`配置等）,但`不建议`同时做这两件事。
* 一个源文件`必须`只能包含一个`类(class)`。

### 1.2. 类
术语`类(class)`指所有的`类(class)`，`接口(interface)`和`特性(trait)`。

* 一个源文件中只能有一个`类(class)`，并且每个`类(class)`至少要有一级`空间名（namespace`：即一个顶级的`组织名(vendor name)`。
* `类名(class name)` `必须`使用`大驼峰式(UpperCamelCase)`写法。
* `类(class)`中的常量`必须`只由大写字母和`下划线(_)`组成。
* `属性(property)`和`方法名(method name)` `必须`使用`小驼峰式(lowerCamelCase)`写法。

### 1.3. 命名空间
* 一个完全标准的`命名空间(namespace)`和`类(class)`的结构是这样的：`\<Vendor Name>\(<Namespace>\)*<Class Name>`
* 每个`命名空间(namespace)`都必须有一个顶级的`空间名(namespace)`("`组织名(Vendor Name)`")。
* 每个`命名空间(namespace)`中可以根据需要使用任意数量的`子命名空间(sub-namespace)`。
* `组织名(vendor name)`，`空间名(namespace)`，`类名(class name)`都由大小写字母组合而成。

2. 代码风格指南
--------
### 2.1. 概述
* 代码`必须`使用4个空格来进行缩进，而不是用制表符。
* 一行代码的长度`不建议`有硬限制；软限制`必须`为120个字符，`建议`每行代码80个字符或者更少。
* 在`命名空间(namespace)`的声明下面`必须`有一行空行，并且在`导入(use)`的声明下面也`必须`有一行空行。
* `类(class)`的左花括号`必须`放到其声明下面自成一行，右花括号则`必须`放到类主体下面自成一行。
* `方法(method)`的左花括号`必须`放到其声明下面自成一行，右花括号则`必须`放到方法主体的下一行。
* 所有的`属性(property)`和`方法(method)` `必须`有可见性声明；`抽象(abstract)`和`终结(final)`声明`必须`在可见性声明之前；而`静态(static)`声明`必须`在可见性声明之后。
* 在控制结构关键字的后面`必须`有一个空格；而`方法(method)`和`函数(function)`的关键字的后面`不可`有空格。
* 控制结构的左花括号`必须`跟其放在同一行，右花括号`必须`放在该控制结构代码主体的下一行。
* 控制结构的左括号之后`不可`有空格，右括号之前也`不可`有空格。

#### 示例
> 这个示例中简单展示了上文中提到的一些规则：

```
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // 方法主体
    }
}
```

<script src="http://yandex.st/highlightjs/7.3/highlight.min.js"></script>
<link rel="stylesheet" href="http://yandex.st/highlightjs/7.3/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>