String, StringBuffer and StringBuilder
1. 可变性
    - String 不可变
    - StringBuffer 和 StringBuilder 可变
2. 线程安全
    - String 不可变，因此是线程安全的
    - StringBuilder 不是线程安全的
    - StringBuffer 是线程安全的，内部使用 synchronized 进行同步