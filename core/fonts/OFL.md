# `core/fonts/` 中的字体与许可

`fonts.css` 声明了四个字体家族，均使用 **SIL Open Font License 1.1**（OFL）许可。`f0`–`f7.woff2` 文件是**字体子集**，采用 Google Fonts 风格的 `unicode-range` 切片，只包含 `fonts.css` 列出的字形，并非完整字体。表格之后保留许可英文原文。

| 字体家族（字形） | 文件 | 字形子集（`unicode-range` 码位） | 字体自身名称表中的版权声明 | 字体中的许可网址 |
|---|---|---|---|---|
| ZCOOL KuaiLe（常规） | `f0.woff2` | 208 个字形，约 200 个为汉字：**不足以覆盖连续中文正文** | Copyright 2018 The ZCOOL KuaiLe Project Authors (https://github.com/googlefonts/zcool-kuaile) | https://openfontlicense.org |
| Fredoka（可变字体；使用字重 500、600、700；文件默认实例名为“Fredoka Light”） | `f1.woff2` (Hebrew, 172), `f2.woff2` (Latin Extended, 1162), `f3.woff2` (Latin, 387) | 见 `fonts.css` | Copyright 2016 The Fredoka Project Authors (https://github.com/hafontia/Fredoka-One) | http://scripts.sil.org/OFL |
| Lilita One（常规） | `f4.woff2` (Latin Extended, 1162), `f5.woff2` (Latin, 387) | 见 `fonts.css` | Copyright (c) 2011 Juan Montoreano (juan@remolacha.biz), with Reserved Font Names "Lilita One" | http://scripts.sil.org/OFL |
| IM Fell English（斜体与常规） | `f6.woff2` (Italic), `f7.woff2` (Regular), each Latin, 387 | 见 `fonts.css` | (c) 2007 Igino Marini (www.iginomarini.com) With Reserved Font Name IM FELL English Italic / IM FELL English Roman | http://scripts.sil.org/OFL |

表格制作方法：字体家族与文件的对应关系来自 `fonts.css`；版权与许可声明来自字体文件 `name` 表的记录（ID 0、14），使用 fontTools 4.66.0 从 `.woff2` 文件中直接读取。fontTools 未安装在共享 `.venv` 中，而是仅为读取文件而安装在临时环境中。这些文件的设计者字段（名称 ID 9）为空，因此以上版权声明用于署名。表格未从网页获取信息。

Lilita One 与 IM FELL English 声明了**保留字体名称**，见其版权声明。修改或重命名字体文件时，适用下方许可第 3 条。

下方为标准 OFL 1.1 英文许可原文，采用 ZCOOL KuaiLe 项目所附 `OFL.txt` 的纯文本排版（https://github.com/googlefonts/zcool-kuaile/blob/main/OFL.txt）。已与官方页面 https://openfontlicense.org/open-font-license-official-text/ 逐词核对：措辞一致，仅连字符和列表编号的排版不同。许可正文保持原样。


## SIL Open Font License 1.1

```text
SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007
-----------------------------------------------------------

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded, 
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF THE USE OR INABILITY TO USE THE FONT SOFTWARE OR FROM
OTHER DEALINGS IN THE FONT SOFTWARE.
```
