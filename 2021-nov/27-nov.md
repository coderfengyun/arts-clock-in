##coderfengyun's review
Rust权威指南第六/七章
1. 结构体如果要引用其他结构体，需要用生命周期做处理，以使得所有权系统正确运行。这是所有权系统复杂性的体现了。
2. 结构体的方法要单独定义在impl中，及impl 结构体名称。struct上的方法(即impl中定义的方法)，其实就是根据impl后的struct名称推断出了self的类型，其他的与普通函数是一致的。
3. 在给出调用者和方法名的前提下，rust可以准确推导出方法是否是只读的&self，还是需要修改数据& mut self，是否会过去数据所有权。这一段其实没太看懂，知道想表达所有权+推断的威力，但是是什么类型的引用不是已经在方法声明时声明好了吗？
4. Impl还可以定义不接受self的函数，及静态方法。
5. 每个结构体可以拥有多个impl块。挺好的，在实现多个trait时，以及区分方法与函数时，会挺有用。
6. Enum的不同变体，构造参数可以不同。如果采用多个结构体的方式实现，那么就无法清易定义能够统一处理这些类型的函数。只能是都实现共同的trait，失去了同一控制。
7. Tony Hoare讲：引入了null是一个当时实现很快，却非常错误的决定。这是非常值得深思的，设计的选择该如何做。
8. Match的能力不仅来自模式的丰富表达力，也来自编译器的安全检查，确保了所有可能情况都会得到处理。太棒了，这是我一直寻找的能力，省去了不少迂回的解决方案和额外测试。
9. 将match与枚举相结合，并绑定变量。太棒了。也显示出java社区对于optional最佳实践有些小家子气。
10. 在处理option时，如果遗漏了对于none的处理，编译器是不会通过的。

dingding:
1、学习和实践了，自动过hcaptcha程序
2、研究和学习了elrond这条链
