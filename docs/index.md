


介绍
------------

Markdown 是一个用于网络作家的文本到 HTML 转换工具。降价
允许您使用易于阅读、易于编写的纯文本进行编写
格式，然后将其转换为结构上有效的 XHTML（或 HTML）。

因此，“Markdown”是两件事：（1）纯文本格式化语法；
(2) 一个用 Perl 编写的软件工具，用于转换纯文本
格式化为 HTML。有关详细信息，请参阅 [Syntax][] 页面
Markdown 的格式化语法。您可以立即使用
在线[丁格斯][]。

  [语法]：/projects/markdown/syntax
  [dingus]：/projects/markdown/dingus

Markdown 格式化语法的首要设计目标是使
它尽可能可读。这个想法是 Markdown 格式的
文档应按原样以纯文本形式发布，无需查看
就像它被标记了标签或格式说明一样。尽管
Markdown 的语法受到了几个现有的 text-to-HTML 的影响
过滤器，Markdown 的最大灵感来源
语法是纯文本电子邮件的格式。

感受 Markdown 格式化语法的最好方法就是
查看 Markdown 格式的文档。例如，您可以查看
此页面上文章文本的 Markdown 来源：
<http://daringfireball.net/projects/markdown/index.text>

（您可以使用这个 '.text' 后缀技巧来查看 Markdown 源
本节中每个页面的内容，例如这
[Syntax][s_src] 和 [License][l_s​​rc] 页。）

  [s_src]：/projects/markdown/syntax.text
  [l_src]：/projects/markdown/license.text

Markdown 是免费软件，在 BSD 风格的开源下可用
执照。有关详细信息，请参阅 [许可证] [pl] 页面。

  [pl]：/项目/降价/许可证


讨论列表 <a id="discussion-list" />
---------------

我已经建立了一个公开的 [用于讨论 Markdown 的邮件列表] [ml]。
任何与 Markdown 相关的主题——包括它的格式语法和
它的软件——是公平的讨论游戏。任何有兴趣的人
欢迎加入。

我希望邮件列表能为未来带来好主意
对 Markdown 的改进。

  [毫升]：http://six.pairlist.net/mailman/listinfo/markdown-discuss


安装和要求 <a id="install" />
-----------------------------------------

Markdown 需要 Perl 5.6.0 或更高版本。欢迎来到 21 世纪。
Markdown 还需要标准 Perl 库模块 [Digest::MD5]
[md5]，它可能已经安装在您的服务器上。

  [md5]：http://search.cpan.org/dist/Digest-MD5/MD5.pm


### 可动类型

Markdown 适用于 Movable Type 2.6 或更高版本（包括
可移动类型 3.0)。

1. 复制 "Markdown.pl" 文件到你的 Movable Type "plugins"
目录。 “插件”目录应该在同一目录中
作为“mt.cgi”；如果“插件”目录尚不存在，请使用
您的 FTP 程序来创建它。您的安装应如下所示
这个：

        (mt home)/plugins/Markdown.pl

2. 安装后，Markdown 将作为一个选项出现在 Movable Type 的
文本格式弹出菜单。这可以在每个帖子的基础上进行选择：

![Movable Type '文本格式'菜单截图][tfmenu]

当您发布时，Markdown 会将您的帖子翻译成 HTML；帖子
它们以 Markdown 格式存储在您的 MT 数据库中。

3. 如果您还安装了 SmartyPants 1.5（或更高版本），Markdown 将
提供第二个文本格式选项：“Markdown With
SmartyPants”。此选项与常规的“Markdown”相同
格式化程序，除了它自动使用 SmartyPants 来创建
排版正确的弯引号、破折号和省略号。看
[SmartyPants 网页][sp] 了解更多信息。

4. 将 Markdown（或“Markdown With SmartyPants”）设为默认
新帖子的文本格式选项，请转到博客配置：
喜好。

请注意，默认情况下，Markdown 会生成 XHTML 输出。配置
Markdown 以生成 HTML 4 输出，请参阅下面的“配置”。

  [sp]：http://daringfireball.net/projects/smartypants/



###开花###

Markdown 适用于 Blosxom 2.0 或更高版本。

1.将“Markdown.pl”插件重命名为“Markdown”（大小写为
    重要的）。 Movable Type 要求插件有一个“.pl”
    扩大; Blosxom 禁止它。

2. 将“Markdown”插件文件复制到您的 Blosxom 插件文件夹中。
    如果您不确定 Blosxom 插件文件夹在哪里，请参阅
    Blosxom 文档以获取信息。

3. 就是这样。您的博客中的条目现在将自动
由 Markdown 处理。

4. 如果您只想将 Markdown 格式应用于某些
帖子，而不是所有帖子，Markdown 可以选择用于
结合 Blosxom 的 [Meta][] 插件。首先，安装
元插件。接下来，在文本中打开 Markdown 插件文件
编辑器，并设置配置变量`$g_blosxom_use_meta`
到 1. 然后，只需包含一个“`meta-markup: Markdown`" 标题行
在您使用 Markdown 撰写的每篇文章的顶部。

  [元]：http://www.blosxom.com/plugins/meta/meta.htm


### BB编辑###

Markdown 适用于 Mac OS X 上的 BBEdit 6.1 或更高版本。它也适用
在 Mac OS 8.6 或更高版本上使用 BBEdit 5.1 或更高版本和 MacPerl 5.6.1。如果
您运行的是 Mac OS X 10.2 (Jaguar)，您可能需要安装
Perl 模块 [Digest::MD5] [md5] 来自 CPAN；摘要::MD5来了
预装在 Mac OS X 10.3 (Panther) 上。

1. 将“Markdown.pl”文件复制到您的相应过滤器文件夹中
“BBEdit 支持”文件夹。在 Mac OS X 上，这应该是：

        BBEdit 支持/Unix 支持/Unix 过滤器/

    有关位置的更多详细信息，请参阅 BBEdit 文档
    这些文件夹。

    您可以将“Markdown.pl”重命名为您想要的任何名称。

2. 就是这样。要使用 Markdown，请在 BBEdit 文档中选择一些文本，
然后从“#!”的 Filters 子菜单中选择 Markdown菜单，或
过滤器浮动调色板



配置 <a id="configuration"></a>
-------------

默认情况下，Markdown 为带有空元素的标签生成 XHTML 输出。
例如。：

    <br />

Markdown 可以配置为生成 HTML 样式的标签；例如。：

    <br>


＃＃＃ 可动类型 ＃＃＃

您需要在每个容器中使用特殊的“MTMarkdownOptions”容器标签
您想要 HTML 4 样式输出的 Movable Type 模板：

    <MTMarkdownOptions 输出='html4'>
        ...把你的条目内容放在这里...
    </MTMarkdownOptions>

使用 MTMarkdownOptions 的最简单方法可能是将
在你的`<body>`标签之后的开始标签，以及在右边的结束标签
在`</body>`之前。

抑制特定模板中的 Markdown 处理，即
发布未经翻译的原始 Markdown 格式文本
(X)HTML，将 `output` 属性设置为 'raw'：

    <MTMarkdownOptions 输出='raw'>
        ...把你的条目内容放在这里...
    </MTMarkdownOptions>


＃＃＃ 命令行 ＃＃＃

使用 `--html4tags` 命令行开关从
Unix 风格的命令行。例如。：

    % perl Markdown.pl --html4tags foo.text

键入 `perldoc Markdown.pl`，或阅读 POD 文档中的
Markdown.pl 源代码以获取更多信息。


致谢 <a id="acknowledgements" />
----------------

[Aaron Swartz][] 对于他对
Markdown 的格式化语法设计。降价是*多*更好谢谢
亚伦的想法、反馈和测试。另外，Aaron 的 [html2text][]
是一个非常方便（且免费）的实用程序，用于将 HTML 转换为
Markdown 格式的纯文本。

[Nathaniel Irons][]、[Dan Benjamin][]、[Daniel Bogan][] 和 [Jason Perkins][]
也值得感谢他们的反馈。

[Michel Fortin][] 已将 Markdown 移植到 PHP；这是一个出色的端口，强烈推荐给任何正在寻找 Markdown 的 PHP 实现的人。

  [亚伦斯沃茨]：http://www.aaronsw.com/
  [纳撒尼尔铁杆]：http://bumppo.net/
  [丹本杰明]：http://hivelogic.com/
  [丹尼尔·博根]：http://waferbaby.com/
  [杰森帕金斯]：http://pressedpants.com/
  [米歇尔福廷]：http://www.michelf.com/projects/php-markdown/
  [html2text]：http://www.aaronsw.com/2002/html2text/
 
  [tfmenu]：/graphics/markdown/mt_textformat_menu.png