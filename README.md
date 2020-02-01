# Minecraft 1.3.2-1.15.2 原版 / FML CoreMod 开发教程

[**蓝色**](#)的链接表示这部分已写完，**黑色**的文本表示尚未完成。

教程在 [GitHub](https://github.com/xfl03/CoreModTutor) 上开放 markdown 形式的源代码，希望可以请求给予一个star。

如果该教程以及其中的源代码存在问题或有其他疑问，欢迎通过 [GitHub Issue](https://github.com/xfl03/CoreModTutor/issues) 来提出。

这是一篇比较全面的 CoreMod 教程，也是对开发 CoreMod 过程的记录。请选择性阅读自己需要的部分，当然如果能有耐心阅读完所有内容当然是最好不过的。  
原版 CoreMod 部分是从 FML 如何向 Minecraft 注入代码的角度进行分析，非必读内容；FML CoreMod 部分也可以直接阅读欲开发的版本。

## 版权声明
本教程作者为 [xfl03](https://github.com/xfl03) ，Mixin部分作者为[ZekerZhayard](https://github.com/ZekerZhayard) 。感谢各位贡献者的辛勤付出，完整贡献者名单请参阅 [GitHub](https://github.com/xfl03/CoreModTutor/graphs/contributors) 。

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
    <img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" />
</a><br />本作品采用
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
    知识共享署名-相同方式共享 4.0 国际许可协议
</a>进行许可。

转载请附上GitHub地址：  
[https://github.com/xfl03/CoreModTutor](https://github.com/xfl03/CoreModTutor)


教程中的原创代码由MIT方式开源，可自由使用。  
教程中使用的Forge代码为LGPL形式开源，版权属于Forge团队。

## [目录](SUMMARY.md)

###  [0 绪论](0.md)

### 1 简介
 * [CoreMod](book/1.1.md)
 * [Minecraft混淆方式](book/1.2.md)

### [2 Java虚拟机](book/2.md)
* [ClassLoader类加载器](book/2.1.md)
* [ByteCode字节码](book/2.2.md)

### 3 原版 CoreMod
* [直接修改class文件](book/3.1.md)
* [JavaAgent](book/3.2.md)
* [LaunchWrapper](book/3.3.md)
* [ModLauncher](book/3.4.md)

### 4 FML CoreMod
* [1.3.2-1.5.2](book/4.1.md)
* [1.6.1-1.12.2](book/4.2.md)
* [1.13.2-1.14.4](book/4.3.md)

###  [5 Mixin](book/5.md)
* [配置](book/5.1.md)
* [引导](book/5.2.md)
* [注入](book/5.3.md)
* [修改](book/5.4.md)
* [定位](book/5.5.md)
* [融合](book/5.6.md)
* [扩展](book/5.7.md)
* [调试](book/5.8.md)

### 6 ASM

### 附录
* [附录A 相关工具下载](book/附录A.md)
* [附录B 常见Java字节码指令表](book/附录B.md)
* [附录C 参考资料](book/附录C.md)