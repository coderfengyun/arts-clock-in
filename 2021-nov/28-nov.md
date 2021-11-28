##coderfengyun's review
Rust权威指南 第8章 module&crate&package
1. 一个package，可以包含多个binary crates(如果是多个需要放到src/bin目录下）以及一个lib crate.
2. Module系统，可以直接类比为文件系统。
3.引用其他crate时，可以使用绝对路径和相对路径。相对路径可以用self(./)，super(../)，以及同module下直接用identifier.
4. 在选择是使用绝对路径还是相对路径时，主要的判断点是二者之间的相对关系稳定还是绝对关系稳定，选择更稳定的那个。
5. 父module里元素不能引用子module中private的元素，而子module可以访问父module中的所有元素。
6. 即使一个module声明为pub，也不能访问其未声明为pub的方法或struct
7. pub struct，其中的field也可以独立定义可见性。enum一旦public，所有变体就都public了。
8. 使用use就像是文件系统中的软连接(快捷方式)。
9. 在use方法时，引入其父module路径，然后使用module::func访问，以明确表示使用的并不是local的方法，是个比较好的实践。而引入struct enum等时，直接引入struct路径是更好的选择。
10. As，作为别名(alis)，方便解决名称冲突问题。
11. 将其他name引入自己scope时，对本scope的使用者来说是private的。如果想pub也需要显示的pub use.
12. 使用pub use，可以将开发者module结构和scope视图与使用者看到的视图做单独的调整。
13. Module可以放入独立文件中，只要保证文件名与module name一致即可，并在父crate中声明module xxx.
