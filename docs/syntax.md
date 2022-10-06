Markdown 语法
=================

<ul id="ProjectSubmenu">
    <li><a href="/projects/markdown/" title="Markdown 项目页面">主要</a></li>
    <li><a href="/projects/markdown/basics" title="Markdown 基础">基础</a></li>
    <li><a class="selected" title="Markdown 语法文档">语法</a></li>
    <li><a href="/projects/markdown/license" title="定价和许可信息">许可</a></li>
    <li><a href="/projects/markdown/dingus" title="在线 Markdown Web 表单">Dingus</a></li>
</ul>


* [概览](#overview)
    * [哲学](#philosophy)
    * [内嵌 HTML](#html)
    * [特殊字符自动转义](#autoescape)
* [方块元素](#block)
    * [段落和换行符](#p)
    * [标题]（#标题）
    * [块引用](#blockquote)
    * [列表](#list)
    * [代码块](#precode)
    * [水平规则](#hr)
* [跨度元素](#span)
    * [链接](#link)
    * [强调](#em)
    * [代码](#代码)
    * [图片](#img)
* [杂项](#misc)
    * [反斜杠转义](#backslash)
    * [自动链接](#autolink)


**注意：**本文档本身是使用 Markdown 编写的；你
可以[通过在 URL 中添加“.text”来查看它的来源][src]。

  [src]：/projects/markdown/syntax.text

* * *

<h2 id="overview">概览</h2>

<h3 id="philosophy">哲学</h3>

Markdown 旨在尽可能地易于阅读和编写。

然而，可读性是最重要的。 Markdown 格式的
文档应按原样以纯文本形式发布，无需查看
就像它被标记了标签或格式说明一样。尽管
Markdown 的语法受到了几个现有的 text-to-HTML 的影响
过滤器——包括 [Setext] [1]、[atx] [2]、[Textile] [3]、[reStructuredText] [4]、
[Grutatext] [5] 和 [EtText] [6] ——
Markdown 语法的灵感来自纯文本电子邮件的格式。

  [1]：http://docutils.sourceforge.net/mirror/setext.html
  [2]：http://www.aaronsw.com/2002/atx/
  [3]：http://textism.com/tools/textile/
  [4]：http://docutils.sourceforge.net/rst.html
  [5]：http://www.triptico.com/software/grutatxt.html
  [6]：http://ettext.taint.org/doc/

为此，Markdown 的语法完全由标点符号组成
字符，哪些标点字符是经过精心挑选的，所以
看起来像他们的意思。例如，实际上一个单词周围的星号
看起来像\*强调\*。 Markdown 列表看起来像，嗯，列表。甚至
假设您曾经使用过块引用，则看起来像引用的文本段落
用过的电子邮件。



<h3 id="html">内联 HTML</h3>

Markdown 的语法有一个目的：用作
用于网络的 *writing* 格式。

Markdown 不是 HTML 的替代品，甚至不能接近它。它的
语法非常小，只对应一个非常小的子集
HTML 标记。这个想法*不是*创建一种使其更容易的语法
插入 HTML 标签。在我看来，HTML 标签已经很容易
插入。 Markdown 的想法是使其易于阅读、编写和
编辑散文。 HTML 是一种*发布*格式； Markdown 是一个*写作*
格式。因此，Markdown 的格式化语法只解决了以下问题
可以以纯文本形式传达。

对于 Markdown 语法未涵盖的任何标记，您只需
使用 HTML 本身。无需为其添加前缀或将其定界为
表明您正在从 Markdown 切换到 HTML；你只是用
标签。

唯一的限制是块级 HTML 元素——例如`<div>`,
`<table>`、`<pre>`、`<p>` 等 -- 必须与周围分开
内容由空行组成，块的开始和结束标记应
不能用制表符或空格缩进。 Markdown 不够聪明
在 HTML 块级标签周围添加额外的（不需要的）`<p>` 标签。

例如，要将 HTML 表格添加到 Markdown 文章：

    这是一个常规段落。

    <表格>
        <tr>
            <td>美食</td>
        </tr>
    </table>

    这是另一个常规段落。

请注意，Markdown 格式化语法不在块级内处理
HTML 标记。例如，你不能在一个
HTML 块。

跨度级 HTML 标签——例如`<span>`、`<cite>` 或 `<del>` -- 可以是
在 Markdown 段落、列表项或标题中的任何位置使用。如果你
想要，你甚至可以使用 HTML 标签代替 Markdown 格式；例如如果
你更喜欢使用 HTML `<a>` 或 `<img>` 标签而不是 Markdown 的
链接或图像语法，继续。

与块级 HTML 标签不同，Markdown 语法 *is* 在内部处理
跨度级标签。


<h3 id="autoescape">特殊字符的自动转义</h3>

在 HTML 中，有两个字符需要特殊处理：`<`
和`&`。左尖括号用于开始标签；和号是
用于表示 HTML 实体。如果您想将它们用作文字
字符，您必须将它们作为实体转义，例如`&lt;`，和
`&`。

尤其是与符号对于网络作家来说是个麻烦事。如果你想
写“AT&T”，你需要写“AT&T”'。你甚至需要
转义 URL 中的 & 符号。因此，如果您想链接到：

    http://images.google.com/images?num=30&q=larry+bird

您需要将 URL 编码为：

    http://images.google.com/images?num=30&amp;q=larry+bird

在您的锚标记“href”属性中。不用说，这很容易
忘记，并且可能是最常见的 HTML 验证来源
其他标记良好的网站中的错误。

Markdown 允许你自然地使用这些字符，照顾
为您提供所有必要的逃避。如果您使用 & 符号作为
一个 HTML 实体，它保持不变；否则会被翻译
进入`&`。

因此，如果您想在文章中包含版权符号，您可以这样写：

    ＆复制;

Markdown 将不理会它。但是如果你写：

    美国电话电报公司

Markdown 会将其翻译为：

    美国电话电报公司

同样，因为 Markdown 支持 [inline HTML](#html)，如果你使用
尖括号作为 HTML 标签的分隔符，Markdown 会将它们视为
这样的。但是如果你写：

    4 < 5

Markdown 会将其翻译为：

    4＜ 5

然而，在 Markdown 代码的 spans 和 blocks、尖括号和
& 符号*总是*自动编码。这使它易于使用
Markdown 来写 HTML 代码。 （与原始 HTML 相反，它是
编写 HTML 语法的糟糕格式，因为每一个 `<`
并且您的示例代码中的 `&` 需要转义。）


* * *


<h2 id="block">块元素</h2>


<h3 id="p">段落和换行符</h3>

段落只是一个或多个连续的文本行，分开
一个或多个空行。 （空行是任何看起来像
空白行 - 只包含空格或制表符的行被视为
空白。）普通段落不应使用空格或制表符缩进。

“一行或多行连续文本”规则的含义是
Markdown 支持“硬包装”文本段落。这不同
与大多数其他 text-to-HTML 格式化程序（包括 Movable
类型的“转换换行符”选项）翻译每个换行符
将段落中的字符转换为 `<br />` 标记。

当你*确实*想使用 Markdown 插入一个 `<br />` 中断标签时，你
以两个或更多空格结束一行，然后键入 return。

是的，创建一个`<br />`需要更多的努力，但过于简单
“每个换行符都是`<br />`”规则不适用于 Markdown。
Markdown 的电子邮件样式 [blockquoting][bq] 和多段 [list items][l]
当您使用硬中断格式化它们时，效果最好 - 并且看起来更好。

  [bq]：#blockquote
  [l]：#列表



<h3 id="header">标题</h3>

Markdown 支持两种样式的标题，[Setext] [1] 和 [atx] [2]。

Settext 样式的标题使用等号“下划线”（对于第一级
标题）和破折号（用于二级标题）。例如：

    这是一个H1
    ==============

    这是一个H2
    -------------

任何数量的下划线 `=`'s 或 `-`'s 都可以。

Atx 样式的标题在行首使用 1-6 个哈希字符，
对应于标题级别 1-6。例如：

    # 这是一个H1

    ## 这是一个 H2

    ######这是H6

或者，您可以“关闭” atx 样式的标题。这纯粹是
化妆品 - 如果您认为它看起来更好，您可以使用它。这
关闭哈希甚至不需要匹配哈希的数量
用于打开页眉。 （打开哈希的数量
确定标题级别。）：

    #这是H1#

    ## 这是一个 H2 ##

    ### 这是一个 H3 ######


<h3 id="blockquote">块引用</h3>

Markdown 使用电子邮件样式的 `>` 字符进行块引用。如果你是
熟悉在电子邮件中引用文本段落，那么您
知道如何在 Markdown 中创建块引用。如果你努力看起来最好
包装文本并在每一行之前放置一个`>`：

    > 这是一个有两段的引用。 Lorem ipsum dolor sit amet，
    > consectetuer adipiscing elit。 Aliquam hendrerit mi posuere lectus。
    > Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus。
    >
    > Donec 坐在一起。 Aliquam semper ipsum 坐在amet velit。悬念
    > id sem consectetuer libero luctus adipiscing。

Markdown 允许你偷懒，只把`>`放在第一个之前
硬包装段落的行：

    > 这是一个有两段的引用。 Lorem ipsum dolor sit amet，
    consectetuer adipiscing 精英。 Aliquam hendrerit mi posuere lectus。
    Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus。

    > Donec 坐在一起。 Aliquam semper ipsum 坐在amet velit。悬念
    id sem consectetuer libero luctus adipiscing。

块引用可以嵌套（即块引用中的块引用）
添加额外级别的`>`：

    > 这是第一级引用。
    >
    > > 这是嵌套块引用。
    >
    > 返回第一级。

块引用可以包含其他 Markdown 元素，包括标题、列表、
和代码块：

> ## 这是一个标题。
>
> 1. 这是第一个列表项。
> 2. 这是第二个列表项。
>
>
这是一些示例代码：
>
> return shell_exec("echo $input | $markdown_script");

任何体面的文本编辑器都应该使电子邮件式引用变得容易。为了
例如，使用 BBEdit，您可以进行选择并选择增加
文本菜单中的报价水平。


<h3 id="list">列表</h3>

Markdown 支持有序（编号）和无序（项目符号）列表。

无序列表使用星号、加号和连字符——可互换
-- 作为列表标记：

    *   红色的
    *   绿色的
    *   蓝色的

相当于：

    + 红色
    + 绿色
    + 蓝色

和：

    -   红色的
    -   绿色的
    -   蓝色的

有序列表使用数字后跟句点：

    1.鸟
    2.麦克海尔
    3. 教区

重要的是要注意您用来标记的实际数字
list 对 Markdown 产生的 HTML 输出没有影响。的HTML
从上面的列表中产生的 Markdown 是：

    <ol>
    <li>鸟</li>
    <li>麦克海尔</li>
    <li>教区</li>
    </ol>

如果你改为像这样在 Markdown 中编写列表：

    1.鸟
    1.麦克海尔
    1. 教区

甚至：

    3.鸟
    1.麦克海尔
    8. 教区

你会得到完全相同的 HTML 输出。关键是，如果你愿意，
你可以在有序的 Markdown 列表中使用序数，这样
您的源代码中的数字与您发布的 HTML 中的数字相匹配。
但是，如果您想偷懒，则不必这样做。

但是，如果您确实使用惰性列表编号，您仍然应该启动
编号为 1 的列表。在将来的某个时候，Markdown 可能会支持
以任意数量开始有序列表。

列表标记通常从左边距开始，但可以缩进
最多三个空格。列表标记后面必须跟一个或多个空格
或选项卡。

为了使列表看起来不错，您可以使用悬挂缩进来包装项目：

    * Lorem ipsum dolor sit amet，consectetuer adipiscing elit。
        Aliquam hendrerit mi posuere lectus。前庭 enim wisi，
        viverra nec, fringilla in, laoreet vitae, risus。
    * Donec 坐在amet nisl。 Aliquam semper ipsum 坐在amet velit。
        Suspendisse id sem consectetuer libero luctus adipiscing。

但如果你想偷懒，你不必：

    * Lorem ipsum dolor sit amet，consectetuer adipiscing elit。
    Aliquam hendrerit mi posuere lectus。前庭 enim wisi，
    viverra nec, fringilla in, laoreet vitae, risus。
    * Donec 坐在amet nisl。 Aliquam semper ipsum 坐在amet velit。
    Suspendisse id sem consectetuer libero luctus adipiscing。

如果列表项用空行分隔，Markdown 将换行
HTML 输出中的 `<p>` 标记中的项目。例如，这个输入：

    *   鸟
    *   魔法

将变成：

    <ul>
    <li>鸟</li>
    <li>魔法</li>
    </ul>

但是这个：

    *   鸟

    *   魔法

将变成：

    <ul>
    <li><p>鸟</p></li>
    <li><p>魔法</p></li>
    </ul>

列表项可能包含多个段落。随后的每一个
列表项中的段落必须缩进 4 个空格
或一个标签：

    1. 这是一个有两个段落的列表项。 Lorem ipsum dolor
        坐在 amet，consectetuer adipiscing 精英。阿利康
        mi pouere lectus。

        Vestibulum enim wisi, viverra nec, fringilla in, laoreet
        简历，风险。 Donec 坐在amet nisl。 Aliquam semper ipsum
        坐在amet velit。

    2. Suspendisse id sem consectetuer libero luctus adipiscing。

如果你缩进后续的每一行看起来不错
段落，但在这里，Markdown 将允许您
懒惰的：

    * 这是一个包含两个段落的列表项。

        这是列表项中的第二段。你是
    只需要缩进第一行。 Lorem ipsum dolor
    坐在 amet，consectetuer adipiscing 精英。

    * 同一列表中的另一个项目。

要将块引用放在列表项中，块引用的`>`
分隔符需要缩进：

    * 带有块引用的列表项：

        > 这是一个块引用
        > 在列表项中。

要将代码块放在列表项中，代码块需要
缩进 *两次* -- 8 个空格或两个制表符：

    * 带有代码块的列表项：

            <代码在这里>


值得注意的是，可以通过以下方式触发有序列表
意外，通过写这样的东西：

    1986. 多么棒的一个赛季。

换句话说，一个 *number-period-space* 序列在一个
线。为避免这种情况，您可以反斜杠转义句点：

    1986 年\。多么棒的一个赛季。



<h3 id="precode">代码块</h3>

预先格式化的代码块用于编写有关编程或
标记源代码。而不是形成正常的段落，这些行
的代码块按字面意思解释。 Markdown 包装了一个代码块
在 `<pre>` 和 `<code>` 标签中。

要在 Markdown 中生成代码块，只需缩进每一行
至少用 4 个空格或 1 个制表符隔开。例如，给定这个输入：

    这是一个正常的段落：

        这是一个代码块。

Markdown 将生成：

    <p>这是一个普通的段落：</p>

    <pre><code>这是一个代码块。
    </code></pre>

一级索引
ntation -- 4 个空格或 1 个制表符 -- 从每个中删除
代码块的行。例如，这个：

    以下是 AppleScript 的示例：

        告诉应用程序“Foo”
            嘟
        结束告诉

将变成：

    <p>这是一个 AppleScript 的例子：</p>

    <pre><code>告诉应用程序“Foo”
        嘟
    结束告诉
    </code></pre>

代码块一直持续到它到达没有缩进的行
（或文章结尾）。

在代码块内，和号（`&`）和尖括号（`<` 和 `>`）
会自动转换为 HTML 实体。这使它非常
使用 Markdown 轻松包含示例 HTML 源代码 - 只需粘贴
它并缩进它，Markdown 将处理编码的麻烦
和号和尖括号。例如，这个：

        <div class="footer">
            ＆复制; 2004 富公司
        </div>

将变成：

    <pre><code>&lt;div class="footer"&gt;
        &amp;复制; 2004 富公司
    &lt;/div&gt;
    </code></pre>

常规 Markdown 语法不在代码块内处理。例如。，
星号只是代码块中的文字星号。这表示
使用 Markdown 来写 Markdown 自己的语法也很容易。



<h3 id="hr">水平规则</h3>

您可以通过放置三个或
更多的连字符、星号或下划线单独出现在一行上。如果你
希望，您可以在连字符或星号之间使用空格。每个
以下行将产生水平规则：

    * * *

    ***

    *****

    - - -

    --------------------------------------


* * *

<h2 id="span">跨度元素</h2>

<h3 id="link">链接</h3>

Markdown 支持两种样式的链接：*inline* 和 *reference*。

在这两种样式中，链接文本由 [方括号] 分隔。

要创建内联链接，请立即使用一组常规括号
在链接文本的右方括号之后。括号内，
将 URL 放在您希望链接指向的位置，以及*可选*
链接的标题，用引号括起来。例如：

    这是 [an example](http://example.com/ "Title") 内联链接。

    [此链接](http://example.net/) 没有标题属性。

将产生：

    <p>这是 <a href="http://example.com/" title="Title">
    一个示例</a>内联链接。</p>

    <p><a href="http://example.net/">这个链接</a>没有
    标题属性。</p>

如果您指的是同一服务器上的本地资源，则可以
使用相对路径：

    有关详细信息，请参阅我的 [关于](/about/) 页面。

参考风格的链接在内部使用第二组方括号
您放置一个您选择的标签来识别链接：

    这是 [an example][id] 参考样式链接。

您可以选择使用空格来分隔括号组：

    这是 [an example] [id] 参考样式链接。

然后，在文档中的任何位置，您都可以像这样定义链接标签，
单独一行：

    [id]: http://example.com/ "此处为可选标题"

那是：

* 包含链接标识符的方括号（可选
    从左边距缩进最多三个空格）；
* 后跟一个冒号；
* 后跟一个或多个空格（或制表符）；
* 后跟链接的 URL；
* 可选地后跟链接的标题属性，括起来
    双引号或单引号，或括在括号中。

以下三个链接定义是等价的：

[foo]: http://example.com/ “可选标题”
[foo]: http://example.com/ '可选标题'
[foo]: http://example.com/ （此处为可选标题）

**注意：** Markdown.pl 1.0.1 中存在一个已知错误，可防止
用于分隔链接标题的单引号。

链接 URL 可以选择用尖括号括起来：

    [id]: <http://example.com/> "可选标题"

您可以将标题属性放在下一行并使用额外的空格
或用于填充的选项卡，使用较长的 URL 看起来会更好：

    [id]：http://example.com/longish/path/to/resource/here
        “此处为可选标题”

链接定义仅用于在 Markdown 期间创建链接
处理，并在 HTML 输出中从您的文档中删除。

链接定义名称可以由字母、数字、空格和
标点符号——但它们*不*区分大小写。例如。这两个
链接：

[链接文字][a]
[链接文字][A]

是等价的。

*隐式链接名称*快捷方式允许您省略
链接，在这种情况下，链接文本本身用作名称。
只需使用一组空方括号 - 例如，链接单词
“谷歌”到 google.com 网站，你可以简单地写：

[谷歌][]

然后定义链接：

[谷歌]：http://google.com/

因为链接名称可能包含空格，所以此快捷方式甚至适用于
链接文本中的多个单词：

访问 [大胆火球][] 了解更多信息。

然后定义链接：

[大胆火球]：http://daringfireball.net/

链接定义可以放在 Markdown 文档中的任何位置。我
倾向于立即将它们放在在他们所在的每个段落中
用过，但如果你愿意，你可以把它们都放在你的末尾
文件，有点像脚注。

以下是实际参考链接的示例：

    我从 [Google] [1] 获得的流量是从 [Google] [1] 获得的流量的 10 倍
    [雅虎] [2] 或 [MSN] [3]。

      [1]：http://google.com/“谷歌”
      [2]：http://search.yahoo.com/“雅虎搜索”
      [3]：http://search.msn.com/ 《MSN 搜索》

使用隐式链接名称快捷方式，您可以改为编写：

    我从 [Google][] 获得的流量是从 [Google][] 获得的流量的 10 倍
    [雅虎][] 或 [MSN][]。

      [谷歌]：http://google.com/“谷歌”
      [雅虎]：http://search.yahoo.com/“雅虎搜索”
      [msn]: http://search.msn.com/ "MSN 搜索"

上述两个示例都将产生以下 HTML 输出：

    <p>我从 <a href="http://google.com/" 获得的流量增加了 10 倍
    title="Google">Google</a> 比来自
    <a href="http://search.yahoo.com/" title="雅虎搜索">雅虎</a>
    或 <a href="http://search.msn.com/" title="MSN 搜索">MSN</a>。</p>

为了比较，这里是使用相同的段落
Markdown 的内联链接样式：

    我从 [Google](http://google.com/ "Google") 获得的流量增加了 10 倍
    比来自 [Yahoo](http://search.yahoo.com/ "Yahoo Search") 或
    [MSN]（http://search.msn.com/“MSN 搜索”）。

参考风格链接的重点不是它们更容易
写。关键是，使用参考样式的链接，您的文档
源代码更具可读性。比较上面的例子：使用
参考风格的链接，段落本身只有 81 个字符
长;使用内联样式的链接，它是 176 个字符；作为原始 HTML，
它是 234 个字符。在原始 HTML 中，有比那里更多的标记
是文本。

使用 Markdown 的参考样式链接，源文档更多
与浏览器中呈现的最终输出非常相似。经过
允许您将与标记相关的元数据移出段落，
您可以添加链接而不会中断您的叙述流程
散文。


<h3 id="em">强调</h3>

Markdown 将星号 (`*`) 和下划线 (`_`) 视为
强调。用一个 `*` 或 `_` 包裹的文本将用一个
HTML `<em>` 标签；双 `*` 或 `_` 将用 HTML 包装
`<strong>` 标签。例如，这个输入：

    *单个星号*

    _单下划线_

    **双星号**

    __双下划线__

将产生：

    <em>单个星号</em>

    <em>单下划线</em>

    <strong>双星号</strong>

    <strong>双下划线</strong>

你可以使用任何你喜欢的风格；唯一的限制是
必须使用相同的字符来打开和关闭强调跨度。

强调可以用在单词中间：

    不*他妈的*可信

但是如果你用空格包围 `*` 或 `_`，它将被视为
字面星号或下划线。

在它所在的位置产生一个字面星号或下划线
否则将用作强调分隔符，您可以使用反斜杠
逃避它：

    \*此文本被文字星号包围\*



<h3 id="code">代码</h3>

要表示一段代码，请用反引号 (`` ` ``) 将其括起来。
与预先格式化的代码块不同，代码跨度表示一个代码块内的代码。
正常段落。例如：

    使用`printf()` 函数。

将产生：

    <p>使用 <code>printf()</code> 函数。</p>

要在代码范围内包含文字反引号字符，您可以使用
多个反引号作为开始和结束分隔符：

    ``这里有一个反引号（`）。``

这将产生这个：

    <p><code>这里有一个文字反引号（`）。</code></p>

围绕代码跨度的反引号分隔符可能包括空格——
一个在开盘后，一个在收盘前。这允许您放置
代码跨度开头或结尾的文字反引号字符：

代码跨度中的单个反引号：`` ` ``

代码跨度中的反引号分隔字符串：```foo```

将产生：

<p>代码跨度中的单个反引号：<code>`</code></p>

<p>代码跨度中的反引号分隔字符串：<code>`foo`</code></p>

使用代码跨度，和号和尖括号被编码为 HTML
实体自动，这使得包含示例 HTML 变得容易
标签。 Markdown 会变成这样：

    请不要使用任何 `<blink>` 标签。

进入：

    <p>请不要使用任何 <code>&lt;blink&gt;</code> 标签。</p>

你可以这样写：

    `&#8212;` 是 `&mdash;` 的十进制编码等价物。

生产：

    <p><code>&amp;#8212;</code> 是十进制编码
    相当于 <code>&amp;mdash;</code>.</p>



<h3 id="img">图片</h3>

诚然，为
将图像转换为纯文本文档格式。

Markdown 使用旨在类似于语法的图像语法
对于链接，允许两种样式：*inline* 和 *reference*。

内联图像语法如下所示：

    ![替代文字](/path/to/img.jpg)

    ![Alt text](/path/to/img.jpg "可选标题")

那是：

*感叹号：`!`;
* 后跟一组方括号，包含 `alt`
    图像的属性文本；
* 后跟一组括号，包含 URL 或路径
    图片，以及一个可选的“title”属性，包含在 double 中
    或单引号。

参考风格的图像语法如下所示：

    ![替代文字][id]

其中“id”是定义的图像引用的名称。图片参考
使用与链接引用相同的语法定义：

    [id]: url/to/image "可选标题属性"

在撰写本文时，Markdown 没有用于指定
图像的尺寸；如果这对您很重要，您可以简单地
使用常规 HTML `<img>` 标签。


* * *


<h2 id="misc">杂项</h2>

<h3 id="autolink">自动链接</h3>

Markdown 支持为 URL 和电子邮件地址创建“自动”链接的快捷方式：只需将 URL 或电子邮件地址用尖括号括起来。这意味着，如果您想显示 URL 或电子邮件地址的实际文本，并使其成为可点击的链接，您可以这样做：

    <http://example.com/>
    
Markdown 会将其变成：

    <a href="http://example.com/">http://example.com/</a>

电子邮件地址的自动链接的工作方式类似，除了
Markdown 还会执行一些随机的十进制和十六进制
实体编码以帮助掩盖您的地址以防止地址收集
垃圾邮件程序。例如，Markdown 会变成这样：

    <地址@example.com>

变成这样的东西：

    <a href="&#x6D;&#x61;i&#x6C;&#x74;&#x6F;:&#x61;&#x64;&#x64;&#x72;&#x65;
    &#115;&#115;&#64;&#101;&#120;&#x61;&#109;&#x70;&#x6C;e&#x2E;&#99;&#111;
    &#109;">&#x61;&#x64;&#x64;&#x72;&#x65;&#115;&#115;&#64;&#101;&#120;&#x61;
    &#109;&#x70;&#x6C;e&#x2E;&#99;&#111;&#109;</a>

它将在浏览器中呈现为“address@example.com”的可点击链接。

（这种实体编码技巧确实会欺骗很多人，如果不是的话
大多数地址收集机器人，但它绝对不会欺骗所有人
他们。有总比没有好，但这样发表的地址
最终可能会开始收到垃圾邮件。）



<h3 id="backslash">反斜杠转义</h3>

Markdown 允许您使用反斜杠转义来生成文字
否则在 Markdown 中将具有特殊含义的字符
格式化语法。例如，如果你想包围一个词
使用文字星号（而不是 HTML `<em>` 标记），您可以使用
星号前的反斜杠，如下所示：

    \*字面星号\*

Markdown 为以下字符提供反斜杠转义：

    \ 反斜杠
    ` 反引号
    * 星号
    _ 下划线
    {}  大括号
    []  方括号
    （）  括号
    # 哈希标记
+ 加号
- 减号（连字符）
    .点
    ！感叹号