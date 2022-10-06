Markdown 基本语法
=================

<ul id="ProjectSubmenu">
    <li><a href="/projects/markdown/" title="Markdown 项目页面">主要</a></li>
    <li><a class="selected" title="Markdown Basics">基础知识</a></li>
    <li><a href="/projects/markdown/syntax" title="Markdown 语法文档">语法</a></li>
    <li><a href="/projects/markdown/license" title="定价和许可信息">许可</a></li>
    <li><a href="/projects/markdown/dingus" title="在线 Markdown Web 表单">Dingus</a></li>
</ul>


了解 Markdown 格式化语法的要点
------------------------------------------------

本页简要概述了使用 Markdown 的感受。
[syntax page] [s] 提供完整、详细的文档
每个功能，但 Markdown 应该很容易上手
看看它的几个例子。此页面上的示例
以前后风格编写，显示示例语法和
Markdown 生成的 HTML 输出。

简单地尝试一下 Markdown 也很有帮助； [Dingus] [d] 是一个
允许您键入自己的 Markdown 格式文本的 Web 应用程序
并将其翻译成 XHTML。

**注意：**本文档本身是使用 Markdown 编写的；你
可以[通过将“.text”添加到 URL 来查看它的来源] [src]。

  [s]: /projects/markdown/syntax "Markdown 语法"
  [d]: /projects/markdown/dingus "Markdown Dingus"
  [src]：/projects/markdown/basics.text


## 段落、标题、大引号 ##

段落只是一个或多个连续的文本行，分开
一个或多个空行。 （空行是任何看起来像
空行——只包含空格或制表符的行是
视为空白。）正常段落不应缩进
空格或制表符。

Markdown 提供两种样式的标题：*Setext* 和 *atx*。
`<h1>` 和 `<h2>` 的 Settext 样式标头由
“下划线”分别带有等号 (`=`) 和连字符 (`-`)。
要创建 atx 样式的标头，请在
行首——哈希数等于结果
HTML 标头级别。

块引号使用电子邮件样式的“`>`”尖括号表示。

降价：

    一级标题
    =====================
    
    二级标题
    ---------------------

    现在是所有好男人都来的时候了
    他们国家的援助。这只是一个
    常规段落。

    敏捷的棕狐跳过懒惰的
    狗回来了。
    
    ### 标题 3

    > 这是一个块引用。
    >
    > 这是引用中的第二段。
    >
    > ## 这是块引用中的 H2


输出：

    <h1>一级标题</h1>
    
    <h2>二级标题</h2>
    
    <p>现在是所有好人都来的时候了
    他们国家的援助。这只是一个
    常规段落。</p>
    
    <p>敏捷的棕狐跳过懒惰的
    狗回来了。</p>
    
    <h3>标题 3</h3>
    
    <块引用>
        <p>这是一个块引用。</p>
        
        <p>这是引用中的第二段。</p>
        
        <h2>这是块引用中的 H2</h2>
    </blockquote>



### 短语强调###

Markdown 使用星号和下划线来表示强调的范围。

降价：

    其中一些词*被强调*。
    其中一些词_也被强调_。
    
    使用两个星号表示**强调强调**。
    或者，如果您愿意，可以__改用两个下划线__。

输出：

    <p>其中一些词<em>被强调</em>。
    其中一些词<em>也被强调</em>。</p>
    
    <p>使用两个星号表示<strong>强调</strong>。
    或者，如果您愿意，<strong>改用两个下划线</strong>。</p>
   


## 列表##

无序（项目符号）列表使用星号、加号和连字符（`*`，
`+` 和 `-`) 作为列表标记。这三个标记是
可互换；这个：

    *   糖果。
    *口香糖。
    * 酒。

这个：

    +糖果。
    +口香糖。
    + 酒。

和这个：

    -   糖果。
    - 口香糖。
    - 酒。

都产生相同的输出：

    <ul>
    <li>糖果。</li>
    <li>口香糖。</li>
    <li>酒。</li>
    </ul>

有序（编号）列表使用常规数字，后跟句点，如
列表标记：

    1. 红色
    2. 绿色
    3. 蓝色

输出：

    <ol>
    <li>红色</li>
    <li>绿色</li>
    <li>蓝色</li>
    </ol>

如果您在项目之间放置空行，您将获得 `<p>` 标记
列表项文本。您可以通过缩进创建多段列表项
4 个空格或 1 个制表符的段落：

    * 一个列表项。
    
        有多个段落。

    * 列表中的另一个项目。

输出：

    <ul>
    <li><p>一个列表项。</p>
    <p>有多个段落。</p></li>
    <li><p>列表中的另一个项目。</p></li>
    </ul>
    


### 链接###

Markdown 支持两种创建链接的方式：*inline* 和
*参考*。对于这两种样式，您都可以使用方括号来分隔
你想变成链接的文本。

内联样式的链接在 li 之后立即使用括号nk 文本。
例如：

    这是一个 [示例链接](http://example.com/)。

输出：

    <p>这是一个 <a href="http://example.com/">
    示例链接</a>.</p>

或者，您可以在括号中包含标题属性：

    这是一个[示例链接]（http://example.com/“带标题”）。

输出：

    <p>这是一个 <a href="http://example.com/" title="With a Title">
    示例链接</a>.</p>

引用样式的链接允许您按名称引用您的链接，这
您在文档的其他地方定义：

    我从 [Google][1] 获得的流量是从 [Google][1] 获得的流量的 10 倍
    [雅虎][2] 或 [MSN][3]。

    [1]：http://google.com/“谷歌”
    [2]：http://search.yahoo.com/“雅虎搜索”
    [3]：http://search.msn.com/ 《MSN 搜索》

输出：

    <p>我从 <a href="http://google.com/" 获得的流量增加了 10 倍
    title="Google">Google</a> 比来自 <a href="http://search.yahoo.com/"
    title="雅虎搜索">雅虎</a> 或 <a href="http://search.msn.com/"
    title="MSN 搜索">MSN</a>.</p>

标题属性是可选的。链接名称可能包含字母，
数字和空格，但*不*区分大小写：

    我以一杯咖啡开始我的早晨
    [纽约时报][纽约时报]。

    [纽约时报]：http://www.nytimes.com/

输出：

    <p>我从一杯咖啡开始我的早晨
    <a href="http://www.nytimes.com/">纽约时报</a>。</p>


### 图片 ###

图像语法非常类似于链接语法。

内联（标题是可选的）：

    ![替代文字](/path/to/img.jpg "标题")

参考风格：

    ![替代文字][id]

    [id]: /path/to/img.jpg “标题”

上述两个示例都产生相同的输出：

    <img src="/path/to/img.jpg" alt="alt text" title="标题" />



### 代码 ###

在常规段落中，您可以通过将文本换行来创建代码跨度
反引号引号。任何与号 (`&`) 和尖括号 (`<` 或
`>`) 将自动翻译成 HTML 实体。这使得
使用 Markdown 编写 HTML 示例代码很容易：

    我强烈建议不要使用任何 `<blink>` 标签。

    我希望 SmartyPants 使用命名实体，例如 `&mdash;`
    而不是像`&#8212;`这样的十进制编码的实体。

输出：

    <p>我强烈建议不要使用任何
    <code>&lt;blink&gt;</code> 标签。</p>
    
    <p>我希望 SmartyPants 使用命名实体，例如
    <code>&amp;mdash;</code> 代替十进制编码
    <code>&amp;#8212;</code>.</p> 等实体


要指定整个预格式化代码块，请缩进每行
由 4 个空格或 1 个制表符组成。就像代码跨度，`&`，`<`，
和 `>` 字符将自动转义。

降价：

    如果您希望您的页面在 XHTML 1.0 Strict 下进行验证，
    你必须把段落标签放在你的块引用中：

        <块引用>
            <p>例如。</p>
        </blockquote>

输出：

    <p>如果您希望您的页面在 XHTML 1.0 Strict 下进行验证，
    你必须把段落标签放在你的引用中：</p>
    
    <pre><code><blockquote>
        &lt;p&gt;例如。&lt;/p&gt;
    &lt;/blockquote&gt;
    </code></pre>Markdown：基础
=================

<ul id="ProjectSubmenu">
    <li><a href="/projects/markdown/" title="Markdown 项目页面">主要</a></li>
    <li><a class="selected" title="Markdown Basics">基础知识</a></li>
    <li><a href="/projects/markdown/syntax" title="Markdown 语法文档">语法</a></li>
    <li><a href="/projects/markdown/license" title="定价和许可信息">许可</a></li>
    <li><a href="/projects/markdown/dingus" title="在线 Markdown Web 表单">Dingus</a></li>
</ul>


了解 Markdown 格式化语法的要点
------------------------------------------------

本页简要概述了使用 Markdown 的感受。
[syntax page] [s] 提供完整、详细的文档
每个功能，但 Markdown 应该很容易上手
看看它的几个例子。此页面上的示例
以前后风格编写，显示示例语法和
Markdown 生成的 HTML 输出。

简单地尝试一下 Markdown 也很有帮助； [Dingus] [d] 是一个
允许您键入自己的 Markdown 格式文本的 Web 应用程序
并将其翻译成 XHTML。

**注意：**本文档本身是使用 Markdown 编写的；你
可以[通过将“.text”添加到 URL 来查看它的来源] [src]。

  [s]: /projects/markdown/syntax "Markdown 语法"
  [d]: /projects/markdown/dingus "Markdown Dingus"
  [src]：/projects/markdown/basics.text


## 段落、标题、大引号 ##

段落只是一个或多个连续的文本行，分开
一个或多个空行。 （空行是任何看起来像
空行——只包含空格或制表符的行是
视为空白。）正常段落不应缩进
空格或制表符。

Markdown 提供两种样式的标题：*Setext* 和 *atx*。
`<h1>` 和 `<h2>` 的 Settext 样式标头由
带有等号 (`=`) 和连字符 (`-`) 的“下划线”，respec