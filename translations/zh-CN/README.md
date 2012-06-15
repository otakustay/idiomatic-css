# 编写统一、符合习惯的CSS的原则

以下文档将提供一个合理的风格指导，用于CSS开发。
这个文档并不是规范，我也不希望将自己的风格喜好强加在其他人身上。但是这个指导手册确实强烈鼓励使用现有的、通用的、合理的模式。

这个文档将持续更新，欢迎提出新的想法。还请多多贡献。

[Principles of writing consistent, idiomatic CSS（原版）](https://github.com/necolas/idiomatic-css)

## 目录

1. [通用原则](#general-principles)
2. [空格](#whitespace)
3. [注释](#comments)
4. [格式](#format)
5. [命名](#naming)
6. [实例](#example)
7. [代码组织](#organization)
8. [构建及部署](#build-and-deployment)

[致谢](#acknowledgements)


<a name="general-principles"></a>
## 1. 通用原则

> “作为成功的项目的一员，很重要的一点是意识到只为自己写代码是很糟糕的行为。如果将有成千上万人使用你的代码，那么你需要编写最具明确性的代码，而不是以自我的喜好来彰显自己的智商。” - Idan Gazit

* 在任何代码库中，无论有多少人参与及贡献，所有代码都应该如同一个人编写的一样。
* 严格执行一致认可的风格。
* 如果有疑义，则使用现有的、通用的模式。

<a name="whitespace"></a>
## 2. 空格

在项目的所有代码中，应该只有一个风格。在空格的使用上，必须始终保持一致。使用空格来提高可读性。

* _永远不要_在缩进时混用空格和TAB。
* 在软缩进（使用空格）和真正的TAB间选择其一。并始终坚持这一选择。（推荐使用空格）
* 如果使用空格进行缩进，选择每个缩进所使用的空格数。（推荐：4个空格）

提示：将编辑器配置为“显示不可见内容”。这使你可以清除行尾的空格和不需要缩进的空行里的空格，同时可以避免对注释的污染。

<a name="comments"></a>
## 3. 注释

良好的注释是非常重要的。请留出时间来描述组件以及它们的运作方式、局限性和构建它们的方法。不要让你的团队其它成员来猜测一段不通用或不明显的代码的目的。

注释的风格应当简洁，并在代码库中保持统一。

* 将注释放在主题上方并独占一行。
* 避免在行未放置注释。
* 控制每行长度在合理的范围内，比如80个字符。
* 使用注释从字面上将CSS代码分隔为独立的部分。
* 注释的大小写应当与普通句子相同，并且使用一致的文本缩进。

提示：通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。

#### CSS示例：

```css
/* ==========================================================================
   区块注释段
   ========================================================================== */

/* 子区块注释段
   ========================================================================== */

/*
 * 分组注释段
 * 用于多行的释义或文档。
 */

/* 基本注释 */
```

#### SCSS示例：

```scss
// ==========================================================================
// 区块注释段
// ==========================================================================

// 子区块注释段
// ==========================================================================

//
// 分组注释段
// 用于多行的释义或文档。
//

// 基本注释
```

<a name="format"></a>
## 4. 格式

最终选择的代码风格必须保证：易于阅读，易于清晰地注释，最小化无意中引入错误的可能性，可生成有用的diff和blame。

1. 在多个选择器的规则集中，每个单独的选择器独占一行。
2. 在规则集的左大括号前保留一个空格。
3. 在声明块中，每个声明独占一行。
4. 每个声明前保留一级缩进。
5. 每个声明的冒号后保留一个空格。
6. 对于声明块的最后一个声明，始终保留结束的分号。
7. 规则集的右大括号保持与该规则集的第一个字符在同一列。
8. 每个规则集之间保留一个空行。

```css
.selector-1,
.selector-2,
.selector-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

(占位)

<a name="naming"></a>
## 5. 命名

不要试着把自己当作编译器或者预处理器，因此命名的时候尽量采用清晰的，有意义的名字。另外，对于
html文件和css文件中的代码，尽量采用一致的命名规则。


```css
/* 没有意义是命名  */
.s-scr {
    overflow: auto;
}
.cb {
    background: #000;
}

/* 比较有意义的命名方式 */
.is-scrollable {
    overflow: auto;
}
.column-body {
    background: #000;
}
```

<a name="example"></a>
## 6. 实例

下面是含有上述约定的示例代码：

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/*
 * Example HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Prevent inline-block cells wrapping */
    white-space: nowrap;
    /* Remove inter-cell whitespace */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Set the inter-cell spacing */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Reset white-space */
    white-space: normal;
    /* Reset font-size */
    font-size: 16px;
}

/* Cell states */

.cell.is-animating {
    background-color: #fffdec;
}

/* Cell dimensions
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell modifiers
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```

<a name="organization"></a>
## 7. 代码组织

对于css代码库来说，如何组织代码文件是很重要的，尤其对于那些很大的代码库显得更加重要。这里介绍
几个组织代码的建议：

* 逻辑上对不同的代码进行分离
* 不同的组件(component)的css尽量用不同的css文件（可以在build阶段用工具合并到一起）
* 如果用到了预处理器（比如less），把一些公共的样式代码抽象成变量，例如颜色，字体等等。


<a name="build-and-deployment"></a>
## 8. 构建及部署

任何一个项目，都应该有一个build的过程，在这个阶段我们可以通过工具对代码进行检测，测试，压缩等等，还
可以为生产环境准备好带有版本号的代码。在这里我推荐一下[grunt](https://github.com/cowboy/grunt)这个工具，我感觉它很不错。

<a name="acknowledgements"></a>
## 致谢

感谢所有对[idiomatic.js](https://github.com/rwldrn/idiomatic.js)作出贡献的网友。
