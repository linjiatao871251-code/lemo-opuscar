<a id="fact-sheet-二十一键-21-keys-opened"></a>
# 情况说明书：《二十一键》21键，已打开

影片中的每个数字和事实声明如下表所示：声明 → 来源 (URL) → 来源措辞。项目文件固定在 foostan/crkbd 提交 63366fb (2025-05-10)。于 2026 年 10 月 16 日检查。

屏幕标签和字幕为中文；它们按原样被引用，带有英文注释。

两种数字分开：

- **项目文件的措辞**：直接写入构建指南、BOM 和 KiCad 文件 (A)。
- **从 CAD 测量**：通过此影片从项目的 STEP / KiCad 几何体 (B) 测量；该方法如下所示，可以使用 `tools/` 进行重现。

<a id="a-wording-of-the-project-files-and-component-documentation"></a>
## A. 项目文件和组件文档的措辞

|#|影片中的索赔（图片/旁白）|来源|措辞|
|---|---|---|---|
|A1|旁白“二十一个键。半个键盘。”；副标题“二十一个键，半把键盘”（二十一个键，半个键盘）|自述文件 https://github.com/foostan/crkbd/blob/63366fb7f51cf2a796462fdd90527e99dd126055/README.md|“Corne 键盘是分体式键盘，具有 3x6 列交错键和 3 个拇指键”（每半个 3×6 + 3 = 21）|
|A2|标签“键帽 1u ×20 · 1.5u ×1”（键帽）|v4 构建指南 https://github.com/foostan/crkbd/blob/63366fb7f51cf2a796462fdd90527e99dd126055/docs/corne-cherry/v4/buildguide_en.md|”\|键帽\|42 - 46 \|1u 40个，1.5u 2个\|“（上下半场一起；每半场 20 + 1）|
|A3|标签“机械轴体十字轴×21”（机械开关，十字轴×21）； “热插拔×21”（热插拔×21）；旁白“可热插拔。无需焊接。”|与A2相同；自述文件|”\|按键开关\|42 - 46 \|仅兼容 Cherry MX \|"; README "v4 Hotswappable"。KiCad 中的左半部分有 21 个开关封装 `keyswitch_cherrymx_hotswap_1u` / `_1.5u`（热插拔插座封装）|
|A4|标签“定位板 FR-4·1.6 mm”（开关板）|与A2相同|”\|开关板\|1套\|FR4 1.6mm厚\|”|
|A5|标签“铜柱 M2 × 7.5 mm ×4”（黄铜支架）|与A2相同|”\|垫片M2 \|8 \|7.5 毫米用于外壳组装 \|“（两半在一起；每半 4 个）；螺丝“\|螺丝M2 \|16 \|5 毫米用于外壳组装 \|“; 脚 ”\|橡胶垫\|8 \|”|
|A6|标签“电路板双层·1.6 mm”（电路板，两层）|KiCad 板文件 https://github.com/foostan/crkbd/blob/63366fb7f51cf2a796462fdd90527e99dd126055/pcbs/corne-cherry/hotswap/corne-cherry.kicad_pcb|`(general (thickness 1.6))`；该叠层只有两层铜层：`"F.Cu"` 和 `"B.Cu"`、`(rev "4.1.0")`|
|A7|标签“主控RP2040·7×7毫米”（控制器）；旁白“一个 RP2040 芯片即可运行所有功能。”|物料清单 https://github.com/foostan/crkbd/blob/63366fb7f51cf2a796462fdd90527e99dd126055/pcbs/corne-cherry/hotswap/jlcpcb/production_files/BOM-corne-cherry.csv ； RP2040 数据表 https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf|物料清单: "RP2040,\"U1,rU1\",QFN-56-1EP_7x7mm_P0.4mm_EP3.2x3.2mm";数据表：“RP2040 7×7 mm QFN-56 封装……”|
|A8|标签“边框 16 MB”（flash）|BOM（如 A7）；华邦 W25Q128JV 数据表 https://www.winbond.com/resource-files/w25q128jv%20revf%2003272018%20plus.pdf|物料清单：“W25Q128JVSIQ，\“U4，rU4\”，SOIC-8_5.23x5.23mm_P1.27mm”；数据表：“W25Q128JV：128M 位/16M 字节”|
|A9|标签“灯珠×23·反贴”（LED×23·反贴）；旁白“二十三盏灯，倒置安装。”|BOM（如 A7）； KiCad 板文件|BOM 列出 YS-SK6812MINI-E：LED1–LED21、EXLED1–2（左半部分为 23；右半部分还有一个带 r 前缀的 23）；在 KiCad 中，所有这些封装都位于 `(layer "B.Cu")`（背面）上，零件号的 -E 后缀表示反向安装|
|A10|图中晶振、0402电阻和电容、USB-C、TRRS插孔和复位按钮的位置和占位面积|KiCad 板文件、BOM|按原样读取封装名称和坐标（例如“Crystal_SMD_3225-4Pin_3.2x2.5mm”、“TYPE-C-31-M-13C”、“PJ-398A-5A_PJ-399B-6A”）；没有文字标签|
|A11|旁白“每一张都是在打开的文件中绘制的。” /“每个号码都是公开的。”|存储库许可证 https://github.com/foostan/crkbd（LICENSE_CC、LICENSE_MIT）|该存储库在 CC BY 4.0 (LICENSE_CC) 和 MIT (LICENSE_MIT) 下发布； 影片使用的每个文件都在该存储库中|

<a id="b-measured-from-cad"></a>
## B. 从 CAD 测量

|#|影片中的索赔|方法|结果|
|---|---|---|---|
|B1|尺寸线“键距19.05毫米”（键距19.05毫米）；旁白“十九点五毫米。”|KiCad 板文件中相邻开关位置之间的中心距离：SW19 (−128.5875，−7.14375) 和 SW18 (−109.5375，−7.14375)|19.050mm（整板柱距19.05）|
|B2|尺寸线“138.4 mm”、“97.6 mm”、“11.1 mm”|使用 occt-import-js 进行三角测量后案例 STEP https://github.com/foostan/crkbd/blob/63366fb7f51cf2a796462fdd90527e99dd126055/cases/3x6/left.step 的边界框 (`tools/step2mesh.mjs`)|138.35 × 97.62 × 11.10 毫米，显示至小数点后一位|
|B3|标签“外壳底厚2.0毫米”（外壳，地板厚度2.0毫米）|与B2相同：箱体网格水平面的高度，底面-11.40，内底板-9.40|2.00毫米|
|B4|分解层数及组装高度（图中各零件的相对位置）|内底板 2.0 + 支座 7.5 (A5) + 板 1.6 (A4) = 11.1 毫米，正好是箱体边缘 (B2) 的高度；板的 4 个 Ø2.2 孔与外壳螺丝孔和电路板的 Ø5 孔对齐|三个文件彼此一致；电路板位于板下方 5.0 毫米处（十字开关的标准安装高度）|
|B5|旁白“拆开：六层。”|影片的层分组方式：键帽、开关、板、电路板、支架、外壳（螺钉和脚与相邻层一起使用）|编辑分组，而不是项目文件中的数字|

<a id="c-parts-of-the-picture-that-are-not-data"></a>
## C. 图片中非数据的部分

键帽轮廓、开关外壳、所有材料颜色、外壳的金属外观、脚的位置以及背面组件的高度都是基于通用规格的建模选择；屏幕上没有为他们标记任何数字。
