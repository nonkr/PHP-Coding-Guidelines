PHP编程规范
=========

本规范参考自[PHP-FIG](框架协同工作组)的[PSR-0]，[PSR-1]，[PSR-2]。

[RFC 2119][]中的`必须(MUST)`，`不可(MUST NOT)`，`建议(SHOULD)`，`不建议(SHOULD NOT)`，`可以/可能(MAY)`等关键词将在本规范中用来做一些解释性的描述。

[PHP-FIG]: https://github.com/php-fig/fig-standards
[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt

1. 通则
---------
### 1.1. 术语
* 术语“类”指所有的`类(class)`，`接口(interface)`和`特性(trait)`。

### 1.2. 源文件
* 源文件的编码格式`必须`只使用不带`字节顺序标记(BOM)`的`UTF-8`。
* 源文件`必须`使用Unix LF(换行)作为行结束符。
* 源文件`必须`只使用 `<?php` 和 `<?=` 这两种标签，`不可`使用短标签，关闭标签`?>` `必须`省略。
* 源文件`必须`以一个空行结束。
* 一个源文件`建议`只用来做声明（`类(class)`，`函数(function)`，`常量(constant)`等）或者只用来做一些引起副作用的操作（例如：输出信息，修改`.ini`配置等）,但`不建议`同时做这两件事。
* 一个源文件`必须`只能包含一个`类(class)`。

### 1.3. 行
* 一行代码的长度`不建议`有硬限制；软限制`必须`为120个字符，`建议`每行代码80个字符或者更少；较长的行`建议`拆分成多个不超过80个字符的子行。
* 在非空行后面`不可`有空格。
* 空行`可以`用来增强可读性和区分相关代码块。
* 一行`不可`多于一个语句。

### 1.4. 缩进
* 代码`必须`使用4个空格，且`不可`使用制表符来作为缩进。
> 注意：代码中只使用空格，且不和制表符混合使用，将会对避免代码差异，补丁，历史和注解中的一些问题有帮助。空格的使用还可以使通过调整细微的缩进来改进行间对齐变得更加的简单。

### 1.5. 关键字和 True/False/Null
* PHP关键字([keywords][])`必须`使用小写字母。
* PHP常量`true`, `false`和`null` `必须`使用小写字母。

[keywords]: http://php.net/manual/en/reserved.keywords.php


2. `命名空间(Namespace)`和`导入(Use)`声明
--------
* 一个完全标准的`命名空间(namespace)`和`类(class)`的结构是这样的：`\<Vendor Name>\(<Namespace>\)*<Class Name>`
* 每个`命名空间(namespace)`都必须有一个顶级的`空间名(namespace)`("`组织名(Vendor Name)`")。
* 每个`命名空间(namespace)`中可以根据需要使用任意数量的`子命名空间(sub-namespace)`。
* `组织名(vendor name)`，`空间名(namespace)`，`类名(class name)`都由大小写字母组合而成。
* `命名空间(namespace)`的声明后面`必须`有一行空行。
* 所有的`导入(use)`声明`必须`放在`命名空间(namespace)`声明的下面。
* 一句声明中，`必须`只有一个`导入(use)`关键字。
* 在`导入(use)`声明代码块后面`必须`有一行空行。


3. 类
---------
* 一个源文件中只能有一个`类(class)`，并且每个`类(class)`至少要有一级`空间名（namespace`：即一个顶级的`组织名(vendor name)`。
* `类名(class name)` `必须`使用`大驼峰式(UpperCamelCase)`写法。
* `类(class)`中的常量`必须`只由大写字母和`下划线(_)`组成。
* `属性(property)`和`方法名(method name)` `必须`使用`小驼峰式(lowerCamelCase)`写法。

### 3.1. `扩展(extend)`和`实现(implement)`

* 一个类的`扩展(extend)`和`实现(implement)`关键词`必须`和`类名(class name)`在同一行。
* `类(class)`的左花括号`必须`放在下面自成一行；右花括号必须放在`类(class)`主体的后面自成一行。

```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // 常量、属性、方法
}
```

* `实现(implement)`列表`可以`被拆分为多个缩进了一次的子行。如果要拆成多个子行，列表的第一项`必须`要放在下一行，并且每行`必须`只有一个`接口(interface)`。

```
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // 常量、属性、方法
}
```

### 3.2. `属性(property)`

* 所有的`属性(property)`都`必须`声明其可见性。
* `变量(var)`关键字`不可`用来声明一个`属性(property)`。
* 一条语句`不可`声明多个`属性(property)`。
* `属性名(property name)` `不推荐`用单个下划线作为前缀来表明其`保护(protected)`或`私有(private)`的可见性。

一个`属性(property)`声明看起来应该像下面这样。

```
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 3.3. `方法(method)`

* 所有的`方法(method)`都`必须`声明其可见性。
* `方法名(method name)` `不推荐`用单个下划线作为前缀来表明其`保护(protected)`或`私有(private)`的可见性。
* `方法名(method name)`在其声明后面`不可`有空格跟随。其左花括号`必须`放在下面自成一行，且右花括号`必须`放在方法主体的下面自成一行。左括号后面`不可`有空格，且右括号前面也`不可`有空格。
* 一个`方法(method)`声明看来应该像下面这样。 注意括号，逗号，空格和花括号的位置：

```
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // 方法主体部分
    }
}
```

### 3.4. `方法(method)`的参数

* 在参数列表中，逗号之前`不可`有空格，而逗号之后则`必须`要有一个空格。
* `方法(method)`中有默认值的参数`必须`放在参数列表的最后面。

```
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // 方法主体部分
    }
}
```

* 参数列表`可以`被拆分为多个缩进了一次的子行。如果要拆分成多个子行，参数列表的第一项`必须`放在下一行，并且每行`必须`只有一个参数。
* 当参数列表被拆分成多个子行，右括号和左花括号之间`必须`有一个空格并且自成一行。

```
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // 方法主体部分
    }
}
```

### 3.5. `抽象(abstract)`，`终结(final)`和 `静态(static)`

* 当用到`抽象(abstract)`和`终结(final)`来做类声明时，它们`必须`放在可见性声明的前面。
* 而当用到`静态(static)`来做类声明时，则`必须`放在可见性声明的后面。

```
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // 方法主体部分
    }
}
```

### 3.6. 调用方法和函数

* 调用一个方法或函数时，在方法名或者函数名和左括号之间`不可`有空格，左括号之后`不可`有空格，右括号之前也`不可`有空格。参数列表中，逗号之前`不可`有空格，逗号之后则`必须`有一个空格。

```
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

* 参数列表`可以`被拆分成多个缩进了一次的子行。如果拆分成子行，列表中的第一项`必须`放在下一行，并且每一行`必须`只能有一个参数。

```
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

4. 控制结构
---------
下面是对于控制结构代码风格的概括：

* 控制结构的关键词之后`必须`有一个空格。
* 控制结构的左括号之后`不可`有空格。
* 控制结构的右括号之前`不可`有空格。
* 控制结构的右括号和左花括号之间`必须`有一个空格。
* 控制结构的代码主体`必须`进行一次缩进。
* 控制结构的右花括号`必须`主体的下一行。

每个控制结构的代码主体`必须`被括在花括号里。这样可是使代码看上去更加标准化，并且加入新代码的时候还可以因此而减少引入错误的可能性。

### 4.1. `if`，`elseif`，`else`

* 下面是一个`if`条件控制结构的示例，注意其中括号，空格和花括号的位置。同时注意`else`和`elseif`要和前一个条件控制结构的右花括号在同一行。

```
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

* `推荐`用`elseif`来替代`else if`，以保持所有的条件控制关键字看起来像是一个单词。

### 4.2. `switch`，`case`

* 下面是一个`switch`条件控制结构的示例，注意其中括号，空格和花括号的位置。`case`语句`必须`要缩进一级，而`break`关键字（或其他中止关键字）`必须`和`case`结构的代码主体在同一个缩进层级。如果一个有主体代码的`case`结构故意的继续向下执行则`必须`要有一个类似于`// no break`的注释。

```
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

### 4.3. `while`，`do while`

* 下面是一个`while`循环控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
while ($expr) {
    // structure body
}
```

* 下面是一个`do while`循环控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
do {
    // structure body;
} while ($expr);
```

### 4.4. `for`
* 下面是一个`for`循环控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 4.5. `foreach`

* 下面是一个`for`循环控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 4.6. `try`, `catch`

* 下面是一个`try catch`异常处理控制结构的示例，注意其中括号，空格和花括号的位置。

```
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

5. 闭包
---------

* 声明闭包时所用的`function`关键字之后`必须`要有一个空格，而`use`关键字的前后都要有一个空格。
* 闭包的左花括号`必须`跟其在同一行，而右花括号`必须`在闭包主体的下一行。
* 闭包的参数列表和变量列表的左括号后面`不可`有空格，右括号的前面也`不可`有空格。
* 闭包的参数列表和变量列表中逗号前面`不可`有空格，而逗号后面则`必须`有空格。
* 闭包的参数列表中带默认值的参数`必须`放在参数列表的结尾部分。

下面是一个闭包的示例。注意括号，空格和花括号的位置。

```
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

* 参数列表和变量列表`可以`被拆分成多个缩进了一级的子行。如果要拆分成多个子行，列表中的第一项`必须`放在下一行，并且每一行`必须`只放一个参数或变量。
* 当列表（不管是参数还是变量）最终被拆分成多个子行，右括号和左花括号之间`必须`要有一个空格并且自成一行。

下面是一个参数列表和变量列表被拆分成多个子行的示例。

```
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

* 把闭包作为一个参数在函数或者方法中调用时，依然要遵守上述规则。

```
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```


示例
---------
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





<script src="http://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.1/highlight.min.js"></script>
<link rel="stylesheet" href="http://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.1/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>