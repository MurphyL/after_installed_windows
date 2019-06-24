```
description: 异常
```

异常不要用来做流程控制，条件控制。

> 捕获异常是为了处理它，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请将该异常抛给它的调用者。最外层的业务使用者，必须处理异常，将其转化为用户可以理解的内容。


有 try 块放到了事务代码中，catch 异常后，如果需要回滚事务，一定要注意手动回滚事务。

不要在 finally 块中使用 return。

> finally 块中的 return 返回后方法结束执行，不会再执行 try 块中的 return 语句。

## 常见异常

### NPE - NullPointerException - 空指针

> 使用 JDK8 的 Optional 类来防止 NPE 问题。

1. 返回类型为基本数据类型，return 包装数据类型的对象时，自动拆箱有可能产生 NPE。
1. 数据库的查询结果可能为 null。
1. 集合里的元素即使 isNotEmpty，取出的数据元素也可能为 null。
1. 远程调用返回对象时，一律要求进行空指针判断，防止 NPE。
1. 对于 Session 中获取的数据，建议 NPE 检查，避免空指针。
1. 级联调用 obj.getA().getB().getC()；一连串调用，易产生 NPE。
