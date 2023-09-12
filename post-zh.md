# Rust 初体验

## 0. 引子

作为一名敏锐的前端开发者，您可能早已对 Rust 有所耳闻，毕竟近几年，使用 Rust 开发的前端构建工具每经发布，其卓越的性能数据总是能带来社区的一阵惊叹。

![](https://files.mdnice.com/user/14618/e0deac29-507f-43e6-9b53-4f6033a765e6.jpg)

> 🔗 来源：[https://swc.rs/](https://swc.rs/)

例如 [SWC](https://swc.rs/) 就在其官网宣称在单线程上的执行速度是传统代码转译工具 Babel 的 **20 倍**。如果在 4 核设备上开启并行计算，其执行速度将是 Babel 的 **70 倍**！

![](https://files.mdnice.com/user/14618/56fecde9-724e-4d6c-ab75-14ab1e9821cf.jpg)

> 🔗 来源：[https://turbo.build/pack](https://turbo.build/pack)

无独有偶，使用 Rust 编写的构建工具 [Turbopack](https://turbo.build/pack)，在构建 3 万个 React 组件的测试中，其性能也完全碾压了内置 webpack 5 的 Next.js 11。

这些现实示例都成功证明了一件事：**使用 Rust 编写前端构建工具是可行的，并且受益巨大！** 

但为什么使用 Rust 语言编写的程序能获得如此巨大的性能收益？Rust 究竟有怎样的魔力？

这就是本篇文章试图回答的问题，希望当您阅读完本篇文章后，您能对 Rust 是什么，为什么性能如此强劲以及一些 Rust 核心特性有一些基础的了解，更希望您能和我一样开始喜欢上这门语言：）

## 1. Rust 简介

### 1.1. 什么是

什么是 Rust？您或许可以从下面这张图中找到答案：

![](https://files.mdnice.com/user/14618/cb57f077-f6a3-463c-bb99-6fe0041f0995.jpeg)

> 🔗 来源：[https://twitter.com/ThePrimeagen/status/1690527161587728384/photo/1](https://twitter.com/ThePrimeagen/status/1690527161587728384/photo/1)

请不要小瞧这张图，它向我们至少传达了两点重要的信息：

1. Rust 和 C 站在一起，表明它们都是非常底层的**操作系统级别的语言**；
2. 相较于白发苍苍的 C，**Rust 非常新潮**！（虽然看起来 ZIG 更酷）；

让我们看看 Rust 官网是怎么宣称的：

> (Rust is) A language empowering everyone to build **reliable** and **efficient** software.
>
> 🔗 来源：[https://www.rust-lang.org/](https://www.rust-lang.org/)

没错，Rust 所标榜的就是「**安全可靠**」和「**性能出众**」，不过我认为还可以再加上一条「**对开发者非常友好**」（我们之后会见识到这一点）。

### 1.2. Rust 历史

> You have to know the past to understand the present.
> 
>― Carl Sagan

同样的，要了解一门语言的现在和未来，我们需要了解一门语言的过去，特别是，语言发明者当初是为了解决什么问题。

Rust 诞生于 2006 年。它的作者是 Mozilla 的工程师 Graydon Hoare。在 Rust 正式对外发布前，它大概花费了 10 年的时间进行设计。（众所周知，据说 JavaScript 的设计周期是 10 天）而 Graydon Hoare 发明这门语言的初心是为了**解决 C 和 C++ 所固有的安全问题**。

需要澄清的是，Rust 并不是 Graydon Hoare 一个人单打独斗的产物，在这门语言诞生的 3 年后（2009 年），Mozilla 团队就迅速意识到了这门语言的潜力，并将其转为企业内部项目进行孵化。直到 2015 年，Rust 终于亮相于公众视野。

而堪称传奇的是，自 2016 年起，Rust 就一直蝉联 Stack Overflow 年度最受欢迎的编程语言冠军。

![](https://files.mdnice.com/user/14618/18f76786-56e1-469b-9aec-469054f29025.jpg)

> 🔗 来源：[https://survey.stackoverflow.co/2022#technology-most-loved-dreaded-and-wanted](https://survey.stackoverflow.co/2022#technology-most-loved-dreaded-and-wanted)

顺便一提，在被统计的 42 种编程语言中，JavaScript，C++ 和 C 分别位于最受欢迎语言排行榜的第 16，25 和 33 位。

### 1.3. 谁在用 Rust?

看起来仿佛「人人都爱 Rust」，而 Rust 也并非叫好不叫座，它近些年来也逐渐在工业实践中崭露头角，例如：

* **Mozilla**：使用 Rust 开发其旗下 Firefox 浏览器的 CSS 引擎 —— Stylo；
* **Dropbox**：使用 Rust 编写其核心的文件存储组建；
* **Discord**：为了解决其延迟峰值的问题，直接使用 Rust 重构了其原先的 Go 代码；

从下图中可以看到，很多知名公司都开始在团队中使用 Rust：


![](https://files.mdnice.com/user/14618/0086ef21-97ed-49ae-8e0d-9b98c0288795.jpg)

> 🔗 来源：[https://yalantis.com/blog/rust-market-overview/](https://yalantis.com/blog/rust-market-overview/)

### 1.4. Rust 的优势

那么人人都爱 Rust 的原因为何？为什么众多大厂均开始选择 Rust 展开实践？要回答这个问题，让我们来倾听用户的声音：


![](https://files.mdnice.com/user/14618/7679679b-a7e0-4492-ab33-6137b7d2e8d2.jpg)

> 🔗 来源：[https://www.bilibili.com/video/BV1WJ411L7Sa/?spm_id_from=333.337.search-card.all.click&vd_source=ae392961974373709ae423de6331ecf2](https://www.bilibili.com/video/BV1WJ411L7Sa/?spm_id_from=333.337.search-card.all.click&vd_source=ae392961974373709ae423de6331ecf2)

下面是 Rust 在 2022 年针对 9,354 名 Rust 开发者做出的调研结果：

1. 96% 的开发者选择 Rust 是因为使用 Rust 能够开发出**正确，没有 bug 的程序**；
2. 92% 的开发者选择 Rust 是因为它所提供的**高性能**；
3. 89% 的开发者则认为使用 Rust 开发的程序更加**安全**；

> 🔗 完整报告可以参考：[https://blog.rust-lang.org/2022/02/15/Rust-Survey-2021.html](https://blog.rust-lang.org/2022/02/15/Rust-Survey-2021.html)

## 2. Rust 的特性

在大致介绍了 Rust 是什么，创建，发展的历史，谁在用，谁爱用以及原因之后，终于，我们可以把聚光灯照射在这门语言身上，近距离观察它的魅力。希望通过本章的介绍，您能够了解到使用 Rust 编写程序，为什么快的原因。

不过在那之前，让我们先通过一些代码增强对 Rust 语言的亲近感。

### 2.1. 使用高级语法但底层透明

首先，让我们先看看下面这段 TypeScript 代码：

```ts
function main() {
  let s: number[] = [1, 2, 3];
  let t = s;
  let u = s;
  
  console.log(s, t, u);
}
```

这段代码并不复杂，但是我想请您尝试回答以下三个问题：

1. 变量 `s` 存储在栈内存中还是堆内存中？
2. 变量 `s` 占用多少内存空间？具体来说，多少 bit？
3. 变量 `s` 所占用的内存空间什么时候会被回收？

即使是富有经验的前端开发者似乎也很难全部答对以上三个问题，现在让我们把这些问题先放在一边，看看如何用 Rust 实现相同逻辑的代码：

```rs
fn main() {
  let s: Vec<i8> = vec![1, 2, 3];
  let t = s;
  let u = s;
  
  println!("{:?}, {:?}, {:?}", s, t, u)
}
```

对比这两段代码，你是否感觉与之前的代码相比非常相似？这就是 Rust 语言带给开发者的第一个好处，它**继承了很多高级语言的语言特性**，因此无论你是什么背景语言的开发者，在使用 Rust 开发程序时，都会有熟悉的感觉。

现在，让我们继续尝试回答刚才的三个问题：

1. 变量 `s` 存储在栈内存中还是堆内存中？ ➡️ **堆内存，因为 `Vector` 类型默认存储于堆内存**；
2. 变量 `s` 占用多少内存空间？具体来说，多少 Bit？ ➡️  **3 * 8 = 24bit，因为我们通过 `Vec<i8>` 声明了 `Vector` 类型成员的内存占用为 8bit**；
3. 变量 `s` 所占用的内存空间什么时候会被回收？ ➡️  **在函数 `main` 的最后一行，因为 Rust 一般总是在变量所在作用域末尾回收内存空间**；

没错，对于 Rust 开发者，始终能够非常清楚的知道自己的代码在机器中的状态，它存储在哪里，占用多少内存以及何时被回收，这不是靠博学做到的，这是语言本身所提供的透明度。

这就是 Rust 的带来的第二个好处：**开发者能够清楚地理解代码作用在机器底层上的效果**，这不仅使得 Rust 开发者能够对自己的代码更自信，也基于开发者更多控制权，使其有机会编写出性能更佳，内存占用更少的代码。

### 2.2. 独特的所有权机制

我想现在是时候揭秘 Rust 为什么快的秘诀了，不过要想搞明白这一点，我们需要先退一步，了解一下内存管理的一些知识。

**一门编程语言极致的性能在于对计算机硬件资源的极致利用**，这其中就包含了对内存的使用，在众多编程语言中，关于内存管理可以大致分为两大阵营：

1. **手动内存管理**：代表语言是 C，C++ 等，它给开发者足够的自由度去掌控内存资源，但是它经常会带来一个问题 —— **开发者无法保障内存安全**；
2. **自动内存管理**：代表语言有 Java，Python，JavaScript 等，它通过专门的 GC 机制（垃圾回收器）让开发者不必关心内存回收问题，GC 会以一定频率检查和释放不在被使用的内存，这种自动管理内存的机制也有一个天然的症结 —— **GC 会损耗程序性能**；

> 💡 关于手动内存管理不当所产生的安全问题，可以搜索关键字「**Use after free**」「**Double Free**」获得更多信息，简单来说就是开发者在错误的时机进行内存回收，造成了程序崩溃并难以排查问题。
> 
> 这种状况其实非常常见，毕竟是人就会犯错。

虽然看起来好像对于一门编程语言，在内存管理上，性能和安全二者不可兼得，但是 Rust 的出现，却给出了一个可以二者兼得的新方案「**没有 GC 的自动内存管理**」！这正是 Rust 为什么快的秘诀，在 Rust 中，这被称为「**所有权机制**」。

让我们来详细解释它：

#### 2.2.1 Python 内存分配机制

首先，让我们看一段 Python 代码在内存中的反映，您可以将这段代码理解为我们之前给出的代码示例的变种，变量 `s` 的值不再是数字而是三个字符串。

```py
  s = ['udon', 'ramen', 'soba']
  t = s
  u = s
```

![](https://files.mdnice.com/user/14618/a7f210db-1244-4a47-9d2a-7b0567c30705.jpg)

> 🔗 *本章代码示例和图片均来源自 《Programming Rust, 2nd Edition》, 第四章*

从图中可以看出，变量 `s` 在内存中存储着一个指向 `list` 的指针，这个指针指向的对象占用 4 个 memory slot，分别是：

1. 引用计数；
2. `list` 长度；
3. 指向 `list` 内容地址的指针；
4. `list` 容量值；

真正想要读取 `list` 的值，我们需要根据指针找到 `list elements`，然后根据索引获取对应值所在的内存地址。

最终，字符串 `udon`，`ramen`，`soba` 实际上占用 2 + x（x 代表字符数） 个 memory slot，分别是：

1. 引用计数；
2. 字符串长度；
3. 字符；

当我们执行 `t = s`，`u = s` 操作时，其反映在内存中如下图所示：

![](https://files.mdnice.com/user/14618/68b283a8-a56f-43bc-abe6-17c8c11923ec.jpg)

可以看到，我们的赋值操作本质上只是创建了一些对值的引用，换句话说，一些指向值内存地址的指针，除此之外，会累加值的第一个 memory slot 值 —— 引用计数。

而程序的内存回收器会每隔一段时间检查内存值的引用计数，一旦其降为 `0` 就意味着这个值不再被任何变量使用，也就是说，内存空间应该被释放。

这种内存设计避免了冗余，但是变相的，会给 GC 更大的压力，一旦程序中出现循环引用，值的引用计数无法归零，就会造成内存始终无法得到回收，在最坏的情况下会导致内存泄漏，程序崩溃。

#### 2.2.2 C++ 的内存分配机制

让我们再来看看 C++ 在相同情况下的内存分配机制：

```c++
using namespace std;
vector<string> s = { "udon", "ramen", "soba" };
vector<string> t = s;
vector<string> u = s;
```

这段代码在内存中的表现如下：

![](https://files.mdnice.com/user/14618/704f6e5a-fb76-4863-889c-2573b0401c1b.jpg)

可以看到，在 C 中，内存分配非常直接，它会为 `s` 开辟 3 个 memory slot，分别是：

1. 指向堆内存空间的指针；
2. capacity；
3. length；

对应 vector 的值占据 3 * 3 个堆内存的 slot，分别是：

1. 指向字符串所在内存地址的指针；
2. capacity；
3. length；

当我们执行 `vector<string> t = s`，`vector<string> u = s` 操作时，其反映在内存中如下图所示：

![](https://files.mdnice.com/user/14618/565e504d-7710-483f-950d-96818785466a.jpg)

可以看到，赋值操作在 C++ 中非常直接，它只是将 `s` 的值深拷贝至 `t` 和 `u`。

所以在 C++ 中，内存回收的时机变得非常明确，只要 `s`，`t`，`u` 所在的作用域消失（换句话说，函数被弹出栈），其所关联的内存空间就可以被释放。

我们可以看出，C++ 和 Python 在内存分配机制上似乎是硬币的两面：

1. **在 Python 中，将值重新赋值给一个变量的内存开销很小，但是内存回收开销却很大**；
2. **在 C++ 中，将值重新赋值给一个变量的内存开销很大，但是却几乎没有内存回收开销**；

#### 2.2.3. Rust 的内存分配策略

现在，让我们看看 Rust 在内存分配上的独到策略，先让我们使用 Rust 实现同样的代码逻辑：

```rs
let s = vec!["udon".toString(), "ramen".toString(), "soba".toString()];
let t = s;
let u = s;
```
> 💡 Rust 默认会将字符串放入只读的内存中，为了和上面的示例保持一致，我们使用 `toString()` 方法强制字符串放入堆内存。

这段代码在内存中的反映您应该非常眼熟，它和之前展示的 C++ 是相同的：

![](https://files.mdnice.com/user/14618/4d906e04-2245-4542-b4c1-3fb70b69d84c.jpg)

但是当我们执行 `let t = s` 操作时，事情就开始变得有意思了，它反映在内存中是这样的：

![](https://files.mdnice.com/user/14618/bfebe48a-9d61-4f13-a7d7-1a4f26d11147.jpg)

注意到了吗？当将 `s` 的值赋值给 `t` 时，我们实际上将 `s` 所拥有的 vector 值完全**转移**给了 `t`，此时的 `s` 回退到了未被初始化的状态，它不再**拥有任何值**。

这就是 Rust 独有的「**所有权机制**」：**一个值始终只被一个变量所拥有**。

所以，当我们继续执行下面的代码 `let u = s;` 时，Rust 会抛出一个错误，因为 Rust 不允许我们使用一个未初始化的值（Rust 是一门非常小心谨慎的语言）。

为什么 Rust 要这样设计？答案是这样可以同时获得 C++ 和 Python 内存分配机制的好处：

1. **重新赋值的开销非常小，但是没有引用计数（不存在循环依赖），没有 GC 带来的性能开销**；
2. **值的所有者非常明确，内存有明确的回收时机**（一般在变量所在作用域消失前）；

这就是 Rust 能编写出高性能且安全的程序的核心原因。

> PS: 而如果您确实需要 C++ 式的内存分配，您可以通过 `t = s.clone()` 的方式实现这一点，而若您想要使用 Python 的值引用的方案，也同样可以使用 `t = &s` 做到。

### 2.3. 友好的使用体验

得益于 `rust-analyzer`（一个遵循 [LSP](https://microsoft.github.io/language-server-protocol/) 协议的库，可以集成至各类编辑器）提供的如代码提示，类型推导，代码静态分析等强大功能以及 Rust 本身严格的代码约束，编写出正确，安全，高效的 Rust 代码将非常容易（*虽然在一开始，您可能会被 Rust 各种错误提示或建议搞的有些抓狂，但相信我，这只是暂时的*）。让我们通过具体的事例说明这一点。

#### 2.3.1. 贴心的建议

下面我使用了我喜欢的 nvim 编辑器编写了一段 Rust 代码，这段代码声明了一个枚举类型 `Fruits`，并声明了一个函数打印出对应的水果名称。

![](https://files.mdnice.com/user/14618/d5b6ba75-3ec9-45c2-8355-649bbe9214e3.jpg)

您应该可以看到编辑器左边出现了 🍩 和 ⛔️，它们分别表示 Rust 的「警告」和「错误」（如果您的编辑器没有这两个符号，别担心，这是我自定义的）。让我们 hover 上去，分别看看 Rust 提示的内容：

首先让我们看看 error 类型的提示：

![](https://files.mdnice.com/user/14618/75e9bb8e-1691-419e-9d2a-5452fb0ff999.jpg)

看到了吗？Rust 给了我们非常直白且有意义的错误提示，它告诉我们的代码在没有命中 `if` 条件语句时，会默认返回一个空元组： `()` ，而我们声明了函数的返回类型是 `&str`（您可以暂时理解为是字符串类型），并且，Rust 的提示并没有止步于此，它还**建议**我们添加 `else` 语句去返回期望的类型。

Rust 的建议通常非常有用，它不仅告诉开发者 `Why` 错误发生了，还能告诉开发者应该 `How` 解决问题。因此即使是初级的 Rust 开发者，也能在 Rust 的帮助下写出正确的，安全的代码。

现在再让我们看一个 warning 类别的提示：

![](https://files.mdnice.com/user/14618/e820597c-c232-4b8a-8701-bbd302609741.png)

在上图中，Rust 提示开发者应该选择首字母大写的方式声明枚举成员，您从中可以再次感受到 Rust 提示文本的「**友好**」。

#### 2.3.2. 严格的要求

使用 Rust 编写的代码之所以非常安全，是因为 Rust 的设计原则是，**尽可能通过静态代码分析和语法规则，让所有可能在代码运行时出现的错误在代码编译时甚至是代码编写时暴露给开发者**。类似的哲学是：「把简单留给用户，把复杂留给自己」，当然，这里的「自己」是指 Rust 开发者。

所以刚刚入门 Rust 的开发者通常会在编写 Rust 代码时遇到各种问题导致编译无法通过（这有时的确让人恼火），这是因为 Rust 编译器确实非常严格。但这同时也使得使用 Rust 编写的程序相对**非常**安全。

让我们看看下面这个代码示例，唯一与之前代码不同的是，这里我们使用了类似 `switch` 关键字的 `match` 方法：

![](https://files.mdnice.com/user/14618/08371d0a-0aa9-4575-bb65-3e0687924bee.jpg)

从左侧的 emoji 就可以看出，这段代码并不能顺利通过 Rust 的编译，让我们来看看为什么：

![](https://files.mdnice.com/user/14618/d64658b3-6643-4f58-8faa-b3bd0cfd02f0.jpg)

从图上我们可以看到，Rust 提示我们，`match` 方法漏掉了 `PineApple` 枚举成员，对于严格的 Rust 而言，这显然是「不可饶恕」的，让我们试着修正这段代码看看会发生什么：

![](https://files.mdnice.com/user/14618/e5845dca-9346-4412-938b-e565e9e8b0ff.png)

虽然我们的 `say_fruit` 函数终于顺利通过了 Rust 的检查，但是 Rust 却提示我们有两个枚举成员实际上并没有被使用（dead code），事实也的确如此。

通过这个示例，我们可以看到 Rust 不仅在尽力让我们的代码变得更安全，还在帮助我们减少代码的冗余。Thanks Rust！

## 3. 小结

在本篇文章中，我向您介绍了 Rust 是什么，它的历史以及 Rust 是如何备受开发者和行业的青睐。并通过一些具体事例想您展示了 Rust 的一些核心特性，特别是 Rust 的「所有权设计」使其在内存使用效率和安全性上都具备显著的优势。希望本篇文章能帮助您对 Rust 这门语言有一个大概的了解，更希望本篇文章能激发您对 Rust 语言进一步研究实践的兴趣。

Rust 在国内目前处于渐渐兴起的状态，我十分欢迎您和我一同在国内落地各类 Rust 实践，也欢迎您和我交流 Rust 学习心得和问题，衷心祝福您旅途愉快！

## 4. 参考资料

* 🎥 [The History of Rust](https://www.youtube.com/watch?v=79PSagCD_AY)
* 📄 [Stackoverflow 2022 survey](https://survey.stackoverflow.co/2022/?utm_source=so-owned&utm_medium=announcement-banner&utm_campaign=dev-survey-2022&utm_content=results#section-most-loved-dreaded-and-wanted-programming-scripting-and-markup-languages)
* 📄 [Rust market overview: reasons to adopt Rust, Rust use cases, and hiring opportunities](https://yalantis.com/blog/rust-market-overview/)
* 📄 [State of the developer nation 22nd edition](https://slashdata-website-cms.s3.amazonaws.com/sample_reports/VZtJWxZw5Q9NDSAQ.pdf)
* 📄 《Programming Rust, 2nd Edition》, chap.4