本规范参考自。

[RFC 2119][]中的`必须(MUST)`，`不可(MUST NOT)`，`建议(SHOULD)`，`不建议(SHOULD NOT)`，`可以/可能(MAY)`等关键词将在本规范中用来做一些解释性的描述。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt

文件
---------
* 源文件中php代码的编码格式`必须`只使用不带`字节顺序标记(BOM)`的`UTF-8`。
* 源文件`必须`只使用 `<?php` 和 `<?=` 这两种标签，`不可`使用短标签。
* 如果是纯php源文件，`必须`不带结束标签`?>`。
* 一个源文件`建议`只用来做声明（`类(class)`，`函数(function)`，`常量(constant)`等）或者只用来做一些引起副作用的操作（例如：输出信息，修改`.ini`配置等）,但`不建议`同时做这两件事。
* 一个源文件`必须`只能包含一个`类(class)`。

类
---------
术语`类(class)`指所有的`类(class)`，`接口(interface)`和`特性(trait)`。

* 一个源文件中只能有一个`类(class)`，并且每个`类(class)`至少要有一级`空间名（namespace`：即一个顶级的`组织名(vendor name)`。
* `类名(class name)` `必须`使用`大驼峰式(UpperCamelCase)`写法。
* `类(class)`中的常量`必须`只由大写字母和`下划线(_)`组成。
* 属性和`方法名(method name)` `必须`使用`小驼峰式(lowerCamelCase)`写法。

命名空间
---------
* 一个完全标准的`命名空间(namespace)`和`类(class)`的结构是这样的：`\<Vendor Name>\(<Namespace>\)*<Class Name>`
* 每个`命名空间(namespace)`都必须有一个顶级的`空间名(namespace)`("`组织名(Vendor Name)`")。
* 每个`命名空间(namespace)`中可以根据需要使用任意数量的`子命名空间(sub-namespace)`。
* `组织名(vendor name)`，`空间名(namespace)`，`类名(class name)`都由大小写字母组合而成。
