---
title: 开发 - 样式指南适配器文档
lastChanged: 14.09.2018
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/dev/adapterdocstyleguide.md
translatedFrom: de
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
hash: ni5zAUPCMl/Fm3/zpYfGi+bO+bL3mzMVqh7e9//1jlE=
---
#Style指南，用于创建适配器文档
？&gt; ***这是一张通配符***。 <br><br>帮助ioBroker并扩展这篇文章。请注意[ioBroker风格指南](community/styleguidedoc)，以便更容易采用这些更改。

*文档使用“Markdown”语言创建。
*适配器文档的文件存储规定如下：
  *每个适配器项目中都有一个文件夹

    `/doc`。

  *如果文档是德语，则它将在子文件夹中

`de`已保存。目前支持的语言和文件夹名称是：`en, de, ru, pt, nl, fr, it, es, pl`。

  *实际的适配器文档位于文件`README.md`中，

    它直接位于相应的语言文件夹中。

  *媒体存储在子文件夹`media`中，该文件也在

    语言文件夹位于。

  *除README.md外，文件和文件夹名称均以小写字母书写。

允许使用字符`a-z`，`0-9`，下划线`_`和小数点`.`

*文档的换行符应为80个字符。
*文本格式最好按文件`.editorconfig`执行

  描述。

  * [插件] []自动应用这些规则是为了

    各种编辑可用。

*对于德语文本，遵守新的德语拼写

  首选。

*在参考文献中，使用人称代词（例如

  “我”，“你”，“我们”）要避免。

  *使用性别中性代词和多键名词。
    *好的：“她（好几个）”，“她（拥有）”，“人”，

      “人”，“开发者”

    *不行：“他的”，“她”，“他”，“她（女）”，“男人”，“女孩”
*使用支架元素（所有支架形状和

  引号），标点符号设置如下：

  *支架元件完整时支架内部

    包含句子（主语，谓语，宾语）。

  *括号外，如果括号元素只是一个子集

    包含的内容。

*文档始终以H1级别标题开头。
*链接不是内联的（例如使用`§§LLLLL_0§§`），

但是在文档末尾的内联`[a link][]`和`[a link]: https://a.link/to/know`的帮助下。

*如果使用破折号，请使用短符号

  在OSX中使用减号而不是“ - ”或`Option+Shift+"-"`。

*其他内容：
  *二进制文件，图片，视频或录音等文件将是

    存储在文件夹`media`中。

  *文本中包含的媒体用于一般文件

通过`§§LLLLL_0§§`和`![媒体概念](../../de/dev/media/{dateiname})`的图片。

  *图像最好以SVG格式存储。如果是SVG

是不可能的，然后作为PNG文件。请密切关注文件大小。

  *短视频可以嵌入为GIF文件。
  *每张图片下方是斜体内容的斜体描述

    指定。

*对于源代码部分，以下内容适用：
  *根据源代码语言，必须选择适当的标记。到

    JavaScript的示例`~~~javascript`。

  *源代码可能完整也可能不完整。的码块

例子是为了澄清刚才描述的jeweis。所以不能提供完全可执行的程序。但是，如果要提供完全可执行的程序，则这将作为文档`media/{code_beispieldatei}`中的媒体文件完成，并在文档中提供相应的链接。

*如果使用下划线，单引号，星号或反斜杠

应设置适当的转义字符：`\_`，`\*`，`\\`和``\`` anstelle von ``, `*§§ SSSSS_6§§\` und `§SSSSSSS_8§§``。

*为了强调注释，以下指南是

  注意：

  *“提示：”标识符必须设置为斜体，即`*Hinweis*:`。
  *在“注意：”标识符后，继续使用大写字母。
  *注释应放在新段落的开头，以便他

    更加明显。

*适配器文档有[template] []。相关的

  模板部分将用于存储的序列和表单中。

[插件]：http：//editorconfig.org/#download [Template]：dev / adaptertemplate