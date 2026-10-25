<a id="real-instrument-toolchain-sampler-samples--pluck-physically-modelled-plucked-strings"></a>
# 真实乐器工具链：采样器（样本）+拨弦（物理建模的拨弦）

用于为 Lemo-Opuscar 风格影片编写 **原始乐谱**。所有内容均通过 numpy/soxr 在 **48 kHz** 下离线合成，与 `sfx.py` 相同的约定（`SR`、`add()`、`limit()`）。
目标是“听起来像真正的乐器”：尽可能使用样本（97种乐器，真实录音），并用物理建模（11个预设）填充采样音色库缺乏的民谣拨弦（古琴，琵琶，三味线......）。

- 预览：该存储库没有现成的预览文件（`core/audio/*.wav` 不在 git 中，也不在示例包中）。下载样本包后，使用第 1 部分中的模式在每个乐器上演奏一个小的根五度八度音节主题，并渲染一个伸展来聆听自己的声音
- 采样音色库: `core/audio/instruments/`（无损 FLAC；每个库都保留其原始内容LICENSE/README）。不在 git 中；按库下载，仅下载影片用途：`sh tools/fetch.sh instruments <lib>` (`vsco2ce` 395 MB, `vcsl` 271 MB, `salamander` 218 MB, `freepats` 397 MB, `karoryfer` 74 MB), or `instruments all`（约 1.4 GB）。第 5 部分中的源列是仪器所在的库：VSCO 2 CE →`vsco2ce`, VCSL →`vcsl`, 蝾螈 →`salamander`、FreePats 和 MuldjordKit →`freepats`, 卡罗里弗 →`karoryfer`
- 索引：`core/audio/instruments/index.json`（每个库的包都会附带一份副本：每个样本的音高、速度层、起始点和电平；导入即可使用，无需重建）

---

<a id="1-thirty-second-start"></a>
## 1.三十秒启动

```python
import sys; sys.path.insert(0, '.')   # run from the repo root
import numpy as np, soundfile as sf
from core.audio import sampler as S, pluck as P
from core.audio.sfx import SR, add, limit

x = S.note('cellos', 'D3', 4.0, vel=.6)            # cello section long note, 4 s (extended seamlessly if the sample is too short)
y = S.hit('snare', 'roll', .5)                       # unpitched hit: instrument + variant + velocity
z = P.pluck('guqin', 'A3', 3, vel=.7, bend=[(.5, 0), (.9, 2)])   # guqin stopped note sliding up a whole tone

# score: (time s, instrument, pitch, duration s, velocity 0-1, pan -1..1[, gain])
mix = S.render([
    (0.0, 'piano',   'D4', 1.0, .70, -.2),
    (0.0, 'cellos',  'D3', 4.0, .55,  .2),
    (0.5, 'violins', 'A4', 3.5, .50,  .3),
    dict(t=1.0, inst='harp', pitch='F#5', dur=1, vel=.6, pan=-.4),
    (2.0, 'gong', None, None, .5, 0),              # unpitched: pitch is the variant name or None
], dur=8)                                           # → (N,2) float32, limited per channel automatically above 0.95
mix = S.room(mix, size=.45, mix=.18)                # simple convolution reverb (optional)
sf.write('cue.wav', mix, SR)
```

> 自行调用 `note()/hit()/pluck()` 得到 **mono float32 @48k**，长度 ≈ `dur + release`；将其放入 `sfx.add(buf, x, t, gain, pan)` 的立体声缓冲区中。

---

<a id="2-using-samplerpy"></a>
## 2.使用sampler.py

|功能|它的作用|
|---|---|
|`load(name)`|按名称加载仪器（惰性+缓存；第一次调用仅读取索引，使用时从磁盘读取样本）。返回 `Inst`； `print` 显示范围/速度层/变体|
|`note(inst, pitch, dur, vel=.8, release=None, attack=0, var=None)`|单注。 `pitch` 可以是 `'C#4'` `'Db3'` `'Bb-1'` 或 midi 数字（**C4=60**；允许的分数 = 微音）。 `dur` = 纸币持有多长时间； `release` = 音符停止后的释放时间（以秒为单位）（每个乐器的默认值）； `attack>0` 为弦乐垫添加淡入|
|`hit(inst, name_or_index=None, vel=.8, dur=None)`|无音击中。变体名称可以作为前缀/不带下划线（`'kick'`→`kick_drum_left`，`'hihat_open'`）；整数 = 第 n 个变体（`hit('timpani', 2)` = 第 3 个鼓）； `dur` 截断（30 毫秒淡出）。也适用于高音乐器：`hit('piano','A3')` 演奏整个自然衰减|
|`chord(inst, pitches, dur, vel, strum=0)`|和弦（单声道）； `strum>0` 依次延迟每个音符（琶音/扫弦）|
|`render(events, dur=None, master=True)`|配乐 → 立体声。事件是元组 `(t, inst, pitch, dur, vel, pan[, gain])` 或字典（可能携带 `release`/`attack`/`var`）|
|`room(x, size=.5, mix=.2, predelay=.015, damp=.5)`|具有去相关指数衰减噪声 IR 的卷积混响； `size` 0–1 → RT60 0.4–3.4 秒；返回相同长度的 (N,2)|
|`credits(names)`|从您使用的工具列表中，生成最终信用 CREDITS 行（所需的 CC BY 措辞 + CC0 确认）|
|`info(name=None)` / `instruments(fam=None)`|打印概述/列出名称（`fam` 采用弦乐弦乐/木管木管乐器/铜管黄铜/打击打击乐/键盘键盘/拨弦拨弦/民族民谣）|
|`midi(p)` / `hz(p)` / `name(m)` / `seed(n)`|注释名称实用程序； `seed` 修复了循环随机性（相同的调用顺序→相同的结果）|
|`build_index(names=None, force=False)`|重新扫描样本并重建 `index.json`（仅在交换或添加样本时才需要；约 15 秒；需要 librosa：`requirements-dev.txt`）|

**它在幕后做什么**
- **样本选择**：权衡“最接近目标音符”和“最接近力度层”（成本=半音距离+ 4×力度差，上移调时有一个小的额外惩罚）；同一单元内的多个循环随机轮换，避免机枪效应。
- **换位**：`soxr` HQ 重采样（也将 44.1k 转换为 48k）。将移调保持在 ±4 个半音范围内（样本通常每 2-3 个半音一个，因此默认值保持在该范围内）。采样范围之外的音符仍然可以发出声音，但音色变得“卡通化”。
- **速度**：多层乐器先拾取该层，然后在层内微调±4 dB；单层乐器按力度缩放增益，并在轻柔演奏时使高音稍微变暗（真实乐器在轻柔演奏时会更暗）。
- **长音符扩展**（`sustained, extendable`类型）：当`dur`超过录音长度时，从录音稳定部分随机取出0.4-1秒的颗粒，**通过基频互相关对齐period**，然后与 100 ms 升余弦交叉渐变拼接，每个颗粒的级别与稳定部分均值相匹配，因此没有硬剪切，也没有循环“嗡嗡声”周期性。 FreePats 的 accordion/bagpipe 带有循环点；它们的循环区域被直接使用。
- **注释**：在 `dur` 之后，`release` (-60 dB) + 5 ms 到零的指数衰减；衰减乐器（钢琴、拨奏、马林巴……）在 `dur` 之前自然衰减，当 `dur` 到达时，它们在释放时间内“衰减”。对于glockenspiel/tubular bells/gong之类的，如果你想让它们响铃，就写一个长的`dur`或一个大的`release`。
- **等级**：每个乐器都已经根据其录音测量进行了归一化（由最响亮的 0.4 秒窗口的 RMS 维持，通过 0.1 秒窗口衰减，通过每个变体的峰值进行打击），因此在 `vel=.8` 处，乐器的响度大致相同（±6 dB 以内）。写入配乐时直接用`vel`/`gain`进行平衡。
- **音调校准**：索引中的每个样本都有用阴测量的基波。在许多 VSCO/VCSL 文件夹中，文件名是 **an 八度，比实际音高低**（例如 `VlnEns_susVib_A2` 实际上是 A3），而 Karoryfer 的 erhu/bass 文件名是 **an 八度更高的**：所有这些都是根据测量结果自动校正的（index.json中的`octave_fix`），并且平均律的样本经过8-80音分的微调以达到平均律（Salamander使用其官方重新调音表）。 **写实际音高即可。**

---

<a id="3-using-pluckpy-physically-modelled-plucked-strings"></a>
## 3.使用pluck.py（物理模型拨弦）

```python
P.pluck(preset, pitch, dur=None, vel=.8, **kw)   # → mono float32 @48k; dur=None lets it decay out naturally
P.strum(preset, pitches, dur, vel=.8, spread=.025, up=False)   # strum / arpeggio
```

|预设|描述|笔记|
|---|---|---|
|`guqin`|古琴|丝弦，长延音（~7秒），低频体共鸣；支持`bend`的停音符滑动和`vib`的吟猱颤音，**滑动时自动添加丝弦摩擦噪音**； `harmonic=True` = 谐波（纯、钟状）|
|`pipa`|琵琶|亮拨片攻击，衰减~2.5 s； `trem=12~16` = 轮指（轮指，卷指颤音）|
|`shamisen`|三味线|拨片+皮肤拍击+**sawari嗡嗡声来自接触琴马的琴弦**（`buzz` 0–1，`thr`可调；测得的延音频谱质心1.5k→2.0k Hz）|
|`koto`|古筝（日本古筝）|`bend` 可以做押手（押手，按下琴弦提高音高）|
|`banjo`|班卓琴|鼓面共鸣，快速衰减，钢弦僵硬|
|`acoustic_guitar`|钢弦民谣吉他|与 `strum()` 配对进行扫弦|
|`nylon_guitar`|尼龙弦吉他|温暖（采样版：`guitar_nylon`）|
|`upright_bass_pizz`|低音提琴拨奏|沉闷的指尖重击+低频体（采样版：`jazz_bass`，更真实）|
|`harp`|竖琴|在琴弦的中点弹奏，温暖（采样版本：`harp`）|
|`kalimba`|卡林巴琴|模态合成：齿音分音 1 : 5.93 : 16.6 + 指甲点击 + 共鸣箱（采样版本：`kalimba`）|
|`music_box`|音乐盒|模态合成：梳齿部分 1 : 6.27 : 17.55，配对齿之间轻微跳动，机械“滴答声”，短暂的金属腐烂|

常用关键词：
- `bend=[(t, semitones), ...]` 分段线性音高包络（相对于 `pitch`）； `glide=(target pitch, seconds)` 滑向音符； `vib=(Hz, depth in semitones, start s)` 颤音 / 音闹
- `trem=Hz` 伦之/腰之（轮指/摇指，颤音：重复拨弦，力度稍微随机）； `harmonic=True` 谐波
- 覆盖物理参数：`t60`（基波衰减到 -60 dB 的秒数）、`damp`（0–0.9，较高 = 较暗）、`pos`（拨动位置 0–0.5，较小 = 较亮）、`bright`、 `buzz`/`thr`、`bmix`（车身比例）、`noise`、`release`

```python
# a guqin phrase: open string → stopped note sliding up → yin vibrato → harmonic
buf = np.zeros((int(8 * SR), 2), np.float32)
add(buf, P.pluck('guqin', 'D3', 2.5, .75), 0.0)
add(buf, P.pluck('guqin', 'A3', 3.0, .7, bend=[(0, 0), (.6, 0), (1.1, 2)], vib=(4.5, .2, 1.5)), 1.2)
add(buf, P.pluck('guqin', 'D5', 3.0, .6, harmonic=True), 4.0, .8, .2)
# pipa lunzhi tremolo + shamisen
add(buf, P.pluck('pipa', 'E4', 1.5, .7, trem=14), 0, .7, -.3)
add(buf, P.pluck('shamisen', 'C4', .6, .8, buzz=.7), 2, .8, .3)
```

---

<a id="4-licences-and-end-credit-attribution-must-read"></a>
## 4. 许可证和最终信用归属（必读）

|风格库|文件夹|执照|学分必须说明什么|
|---|---|---|---|
|VS 室内乐团：社区版（Versilian Studios，github.com/sgossner/VSCO-2-CE）|`instruments/vsco2ce/`|**CC0 1.0**|不需要；作者感谢“Versilian Studios / Sam Gossner”（管风琴由 Ivy Audio / Simon Dalzell 制作）|
|Versilian 社区采样音色库 (github.com/sgossner/VCSL)|`instruments/vcsl/`|**CC0 1.0**|不需要|
|FreePats (freepats.zenvoid.org)：古典吉他、四弦琴、干净电吉他、指拨电贝司、卡林巴、手风琴、玻璃竖琴、旧钢琴、风笛、世界打击乐|`instruments/freepats/<name>/`|**CC0 1.0**|不需要|
|Karoryfer 样本 (github.com/sfzinstruments)：二胡、爵士低音提琴 Sneakybass、中音萨克斯 Weresax|`instruments/karoryfer/`|**CC0 1.0**|不需要|
|**Salamander 大钢琴 V3**（Alexander Holm；FreePats FLAC 版本）|`instruments/salamander/`|**CC BY 3.0**|**使用 `piano`** 时必填 ↓|
|**MuldjordKit**（Lars Muldjord；FreePats 版本）|`instruments/freepats/muldjord_kit/`|**CC BY 4.0**|**使用 `drum_kit`** 时必填 ↓|

如果您使用 `piano`，请在 CREDITS 中准确写入：

```
Piano: "Salamander Grand Piano V3" by Alexander Holm, licensed under CC BY 3.0 (https://creativecommons.org/licenses/by/3.0/)
```

如果您使用 `drum_kit`，请在 CREDITS 中准确写入：

```
Drums: "MuldjordKit" by Lars Muldjord (drumgizmo.org), FreePats version, licensed under CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/)
```

建议（对于CC0部件，可选，一行就足够了）：`Samples (CC0): Versilian Studios VSCO 2 CE & VCSL, FreePats, Karoryfer Samples`。
最简单：`print('\n'.join(S.credits(['piano', 'cellos', 'drum_kit'])))` 自动生成它们。 `pluck.py` 是纯合成，没有许可证要求。

应用于样本的处理（全部在许可证允许的范围内）：VSCO/VCSL/Karoryfer WAV 被转换为 **无损的** 到 FLAC（逐个样本验证相同）；对于 Salamander，仅保留 16 个速度层中的 5 个 (v2/v6/v10/v13/v16)； FreePats 包中的照片（一些 CC BY-NC）已被删除，仅保留音频和 sfz/notes.

---

<a id="5-available-instruments"></a>
## 5. 可用仪器

“采样范围”是录音实际覆盖的范围（修正为实际音高，C4=60）；超出几步它仍然有效，只是换位时间更长。 “力度层” = 该乐器上同一音符的记录层数（1 = 仅通过增益 + 变暗模拟的力度）。

<a id="strings"></a>
### 弦乐

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`violins`|小提琴部分，持续（颤音）|VSCO 2 CE|CC0 1.0|G3–D6|2|持续的、可扩展的|
|`violins_trem`|小提琴部分、颤音|VSCO 2 CE|CC0 1.0|G3–D6|2|持续的、可扩展的|
|`violins_pizz`|小提琴部分，拨奏|VSCO 2 CE|CC0 1.0|G3–D6|2|自然腐烂|
|`violins_spic`|小提琴部分，留奏（短音符）|VSCO 2 CE|CC0 1.0|G3–D6|2|自然腐烂|
|`violin`|小提琴独奏，持续|VSCO 2 CE|CC0 1.0|G3–C7|2|持续的、可扩展的|
|`violin_pizz`|小提琴独奏、拨奏|VSCO 2 CE|CC0 1.0|G3–C7|2|自然腐烂|
|`violas`|中提琴部分，持续|VSCO 2 CE|CC0 1.0|C3-D6|2|持续的、可扩展的|
|`violas_pizz`|中提琴部分，拨奏|VSCO 2 CE|CC0 1.0|C3-D6|2|自然腐烂|
|`cellos`|大提琴部分，持续|VSCO 2 CE|CC0 1.0|C2–F5|2|持续的、可扩展的|
|`cellos_pizz`|大提琴部分，拨奏|VSCO 2 CE|CC0 1.0|C2–F5|2|自然腐烂|
|`cellos_spic`|大提琴部分，留奏|VSCO 2 CE|CC0 1.0|C2–F5|2|自然腐烂|
|`contrabass`|低音提琴，持续|VSCO 2 CE|CC0 1.0|F#1–B3|2|持续的、可扩展的|
|`contrabass_pizz`|低音提琴、古典拨奏|VSCO 2 CE|CC0 1.0|E1-B3|2|自然腐烂|
|`harp`|竖琴|VCSL|CC0 1.0|E1-F7|4|自然腐烂|

<a id="woodwinds"></a>
### 木管乐器

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`flute`|长笛，持续|VSCO 2 CE|CC0 1.0|C4–C7|1|持续的、可扩展的|
|`flute_stac`|长笛、断奏|VSCO 2 CE|CC0 1.0|A4-C7|4|自然腐烂|
|`piccolo`|短笛|VSCO 2 CE|CC0 1.0|G5–G7|1|持续的、可扩展的|
|`clarinet`|单簧管，持续|VSCO 2 CE|CC0 1.0|D3–F#6|3|持续的、可扩展的|
|`clarinet_stac`|单簧管、断奏|VSCO 2 CE|CC0 1.0|D3-F6|3|自然腐烂|
|`oboe`|双簧管，持续|VSCO 2 CE|CC0 1.0|A#3–F6|2|持续的、可扩展的|
|`oboe_stac`|双簧管、断奏|VSCO 2 CE|CC0 1.0|A#3–F6|3|自然腐烂|
|`bassoon`|巴松管，持续的|VSCO 2 CE|CC0 1.0|A#1–D#5|2|持续的、可扩展的|
|`bassoon_stac`|巴松管、断奏|VSCO 2 CE|CC0 1.0|A#1–C5|2|自然腐烂|
|`recorder`|中音竖笛（巴洛克）|VCSL|CC0 1.0|F4-E6|1|持续的、可扩展的|
|`ocarina`|陶笛|VCSL|CC0 1.0|A4–C#6|1|持续的、可扩展的|
|`tenor_sax`|次中音萨克斯、颤音|VCSL|CC0 1.0|A#2–D6|1|持续的、可扩展的|
|`tenor_sax_nv`|次中音萨克斯，直音|VCSL|CC0 1.0|G#2–E6|2|持续的、可扩展的|
|`tenor_sax_stac`|次中音萨克斯、断奏|VCSL|CC0 1.0|G#2–E6|2|自然腐烂|
|`alto_sax`|中音萨克斯 (Weresax)|卡罗里弗|CC0 1.0|C#3–G#5|2|持续的、可扩展的|
|`harmonica`|半音阶口琴|VCSL|CC0 1.0|C3–C7|1|持续的、可扩展的|

<a id="brass"></a>
### 黄铜

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`trumpet`|小号，持续|VSCO 2 CE|CC0 1.0|F3-C6|2|持续的、可扩展的|
|`trumpet_stac`|小号、断奏|VSCO 2 CE|CC0 1.0|F3-C6|3|自然腐烂|
|`trumpet_mute`|喇叭，直静音|VSCO 2 CE|CC0 1.0|A#3–A5|2|持续的、可扩展的|
|`horn`|圆号，持续|VSCO 2 CE|CC0 1.0|A1-F5|4|持续的、可扩展的|
|`horn_stac`|圆号、断奏|VSCO 2 CE|CC0 1.0|A1-F5|3|自然腐烂|
|`trombone`|长号，持续|VSCO 2 CE|CC0 1.0|A#1–F4|3|持续的、可扩展的|
|`trombone_stac`|长号、断奏|VSCO 2 CE|CC0 1.0|A#1–F4|4|自然腐烂|
|`tuba`|大号，持续|VSCO 2 CE|CC0 1.0|F1-D4|3|持续的、可扩展的|
|`tuba_stac`|大号、断奏|VSCO 2 CE|CC0 1.0|A1-D4|2|自然腐烂|

<a id="percussion"></a>
### 打击乐器

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`timpani`|定音鼓（5 个鼓；音高 = 主振动模式 (1,1)，从频谱测量）；变种： `drum1` `drum2` `drum3` `drum4` `drum5`|VSCO 2 CE|CC0 1.0|F2-G3|3|自然腐烂|
|`glockenspiel`|钟琴|VCSL|CC0 1.0|G5–C8|3|自然腐烂|
|`xylophone`|木琴|VCSL|CC0 1.0|G4–C8|2|自然腐烂|
|`marimba`|马林巴琴|VCSL|CC0 1.0|F2–C7|3|自然腐烂|
|`vibraphone`|电颤琴、软木槌|VCSL|CC0 1.0|F3-E6|2|自然腐烂|
|`vibraphone_hard`|电颤琴、硬木槌|VCSL|CC0 1.0|F3-E6|2|自然腐烂|
|`vibraphone_bowed`|弓形电颤琴（轻快的长音符）|VCSL|CC0 1.0|A3-E6|1|持续的、可扩展的|
|`tubular_bells`|管状钟|VCSL|CC0 1.0|C4-E5|5|自然腐烂|
|`hand_chimes`|手铃（轻柔的铃声）|VCSL|CC0 1.0|C4–C7|1|自然腐烂|
|`kalimba`|卡林巴琴（拇指钢琴）|自由拍拍|CC0 1.0|F3–C#5|1|自然腐烂|
|`mbira`|mbira / 坦桑尼亚卡林巴（更坚韧；原始乐器不是等律，通过测量调为等律）|VCSL|CC0 1.0|G2–C#7|1|自然腐烂|
|`hang`|hang（D小调，仅在乐器本身的音符上听起来最好）|自由拍拍|CC0 1.0|A3-D5|1|自然腐烂|
|`glass`|玻璃竖琴|自由拍拍|CC0 1.0|A#4–F6|1|自然腐烂|
|`bass_drum`|音乐会低音鼓（7 个力度层）|VSCO 2 CE|CC0 1.0|—|7|未定调的|
|`gran_cassa`|低音鼓 2（带滚动/渐强）；变种： `hit` `roll` `roll_fast` `cresc` `rub`|VCSL|CC0 1.0|—|5|未定调的|
|`snare`|小军鼓（管弦乐）；变种： `on` `off` `roll` `roll_off`|VSCO 2 CE|CC0 1.0|—|5|未定调的|
|`snare2`|小军鼓 2（近距离拾音）；变种： `on` `off` `roll` `stick` `taps`|VCSL|CC0 1.0|—|5|未定调的|
|`toms`|汤姆斯（high/low × sticks/mallets）；变种： `high` `low` `high_mallet` `low_mallet` `roll`|VCSL|CC0 1.0|—|3|未定调的|
|`crash`|碎钹（管弦乐）|VSCO 2 CE|CC0 1.0|—|4|未定调的|
|`clash`|碎音钹 2；型号：`crash` `short`|VCSL|CC0 1.0|—|4|未定调的|
|`sus_cymbal`|悬钹（软mallet/stick/bell/roll/crescendo/bow）；变体：`hit` `stick` `bell` `roll` `cresc` `bow` `scrape`|VCSL|CC0 1.0|—|4|未定调的|
|`gong`|大锣/担担|VSCO 2 CE|CC0 1.0|—|4|未定调的|
|`gong2`|锣2（包括小锣、刮）；变种： `big` `small` `scrape`|VCSL|CC0 1.0|—|4|未定调的|
|`triangle`|三角形;变种： `open` `muted` `semi` `roll`|VCSL|CC0 1.0|—|2|未定调的|
|`tambourine`|手鼓|VSCO 2 CE|CC0 1.0|—|2|未定调的|
|`claves`|克拉夫斯|VSCO 2 CE|CC0 1.0|—|3|未定调的|
|`cowbell`|牛铃|VSCO 2 CE|CC0 1.0|—|4|未定调的|
|`sleighbells`|雪橇铃|VSCO 2 CE|CC0 1.0|—|1|未定调的|
|`log_drum`|原木滚筒/狭缝滚筒；型号：`hi` `lo`|VSCO 2 CE|CC0 1.0|—|3|未定调的|
|`woodblock`|雕版;变种： `a` `b` `c`|VCSL|CC0 1.0|—|4|未定调的|
|`frame_drum`|手鼓/框鼓；变种： `large` `small` `large_muted` `small_muted` `hand`|VCSL|CC0 1.0|—|2|未定调的|
|`hihat`|踩镲；变种： `closed` `open` `loose` `pedal`|VCSL|CC0 1.0|—|4|未定调的|
|`cajon`|卡洪鼓；变种： `bass` `slap` `tone`|VCSL|CC0 1.0|—|3|未定调的|
|`conga`|康加舞；变种： `conga` `quinto` `tumba` `muted`|VCSL|CC0 1.0|—|4|未定调的|
|`claps`|拍手；型号：`group` `solo`|VCSL|CC0 1.0|—|4|未定调的|
|`shaker`|摇床；变种： `down` `up` `slap` `roll`|VCSL|CC0 1.0|—|1|未定调的|
|`nepal_bells`|尼泊尔手铃|VCSL|CC0 1.0|—|1|未定调的|
|`world_perc`|世界打击乐（cajón/bongo/egg shaker/castanets/darbuka 等，info() 中的变体）；变体：`cajon_flamenco_1` `cajon_flamenco_3` `cajon_flamenco_2` `bongo_muted` `bongo_high` `bongo_low_low_velocity` `bongo_low_high_velocity` `egg_shaker_slow` `egg_shaker_fast` `egg_shaker_soft` `tambourine` `tambourine_fast` `hand_clap` `claves` `castanets` `conga` `low_conga` `high_conga` `muted_conga` `muted_low_conga` `maracas_fw` `maracas_bw` `darbuka_doom` `darbuka_tak` `darbuka_pa`|自由拍拍|CC0 1.0|—|2|未定调的|
|`drum_kit`|流行鼓套件 MuldjordKit (CC BY 4.0)；变体：`kick_drum_left` `kick_drum_right` `snare_1` `snare_2` `hi_hat_closed` `hi_hat_open` `ride_left` `ride_bell_left` `ride_right` `ride_bell_right` `crash_left` `crash_right` `china` `tom_1` `tom_2` `tom_3` `tom_4` `snare_rest_1` `snare_rest_2`|穆尔乔德套件|抄送4.0|—|16|未定调的|

<a id="keyboards"></a>
### 键盘

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`piano`|Salamander 三角钢琴（雅马哈 C5，5 个力度层）|蝾|抄送3.0|A0-C8|5|自然腐烂|
|`upright`|立式钢琴（温暖，略有磨损）|VSCO 2 CE|CC0 1.0|C1-G7|3|自然腐烂|
|`honky_tonk`|老演奏家钢琴（酒吧风格）|自由拍拍|CC0 1.0|G#0–B7|1|自然腐烂|
|`harpsichord`|大键琴（意大利语）|VCSL|CC0 1.0|F#1–B5|1|自然腐烂|
|`organ`|管风琴，全手动（带 16' 挡块，重型）|VSCO 2 CE|CC0 1.0|C2–C7|1|持续的、可扩展的|
|`organ_soft`|管风琴，软手动停止|VSCO 2 CE|CC0 1.0|C2–C7|1|持续的、可扩展的|
|`organ_pedal`|管风琴、踏板贝斯（测量音高）|VSCO 2 CE|CC0 1.0|F#1–F#4|1|持续的、可扩展的|
|`accordion`|按钮手风琴|自由拍拍|CC0 1.0|B2-G5|1|持续的、可扩展的|

<a id="plucked-strings"></a>
### 拨弦

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`guitar_nylon`|尼龙弦古典吉他|自由拍拍|CC0 1.0|G1–C6|1|自然腐烂|
|`ukulele`|尤克里里|自由拍拍|CC0 1.0|B2-C6|1|自然腐烂|
|`electric_guitar`|干净的电吉他|自由拍拍|CC0 1.0|C2–C#6|3|自然腐烂|
|`electric_bass`|电贝司，指法|自由拍拍|CC0 1.0|E1–D#2|1|自然腐烂|
|`jazz_bass`|低音提琴、爵士拨奏（Sneakybass）|卡罗里弗|CC0 1.0|C1–C4|1|自然腐烂|
|`strumstick`|扫弦器，扬琴风格的民间弹拨乐器（钢弦民谣感觉）|VCSL|CC0 1.0|D3–A5|3|自然腐烂|
|`dan_tranh`|越南古筝 Đàn tranh （与古筝同族，可代替古筝）|VCSL|CC0 1.0|B2-B5|3|自然腐烂|
|`dan_tranh_trem`|越南古筝，摇指（摇指，颤音）|VCSL|CC0 1.0|B2-B5|1|持续的、可扩展的|

<a id="folk"></a>
### 民间

|姓名|描述|来源|执照|采样范围|速度层|类型|
|---|---|---|---|---|---|---|
|`erhu`|二胡，持续|卡罗里弗|CC0 1.0|D4–A5|1|持续的、可扩展的|
|`erhu_stac`|二胡、短弓|卡罗里弗|CC0 1.0|D4–A5|1|自然腐烂|
|`bagpipe`|风笛（吟唱者；G2/G3 是无人机）|自由拍拍|CC0 1.0|G2-G5|1|持续的、可扩展的|

<a id="physical-modelling-pluckpy"></a>
### 物理建模（pluck.py）

`guqin` `pipa` `shamisen` `koto` `banjo` `acoustic_guitar` `nylon_guitar` `upright_bass_pizz` `harp` `kalimba` `music_box`：任何螺距（C4=60，允许分数），请参见第 3 节。

<a id="aliases"></a>
### 别名

`strings`→小提琴，`cello`→大提琴，`viola`→中提琴，`double_bass`→低音提琴，`upright_bass_pizz`→爵士低音，`french_horn`→喇叭， `glock`→钟琴、`vibes`→颤音琴、`chimes`→管铃、`grand_piano`→钢琴、`acoustic_guitar`→吉他_尼龙（在采样器中；在拨弦中，`acoustic_guitar`是钢弦型号）、`guzheng`/`zither`→dan_tranh、`sax`→次中音_萨克斯、`kick`→低音鼓、`cymbal`→碰撞、`tamtam`→锣、 `celesta`→钟琴（没有钢片琴样本；钟琴最接近）。

---

<a id="6-picking-instruments-by-style-quick-reference"></a>
## 6. 按风格挑选乐器（快速参考）

|你想要的感觉|建议组合|
|---|---|
|管弦乐/史诗/纪录片|`violins` `violas` `cellos` `contrabass` 作为床（`attack=.3~.8` 淡入）+ `horn` `trombone` `tuba` + `timpani` `gran_cassa` `sus_cymbal:roll` `gong`;对于轻快的通道，请使用 `violins_spic` `cellos_pizz` `flute_stac`|
|童话/温柔/手工|`glockenspiel` `celesta→glockenspiel` `pluck:music_box` `kalimba` `harp` `vibraphone` `hand_chimes` `ukulele` `guitar_nylon` + `clarinet` `flute`|
|中国人|样品：`erhu` `dan_tranh`（古筝） `dan_tranh_trem`（遥指颤音） `gong2:small` `frame_drum` `log_drum` `woodblock`；型号：`pluck:guqin`（带slides/harmonics）`pluck:pipa`（伦智颤音）；没有 dizi/xiao 样本，请使用 `flute` `recorder` `ocarina` 代替|
|日本人|`pluck:shamisen` `pluck:koto` + `flute`/`recorder`（代替尺八）+ `gran_cassa` `frame_drum:large` `toms:low_mallet`（没有CC0/CC BY taiko；将这些分层构建一个）|
|爵士乐/咖啡厅|`piano` `jazz_bass` `alto_sax` `tenor_sax` `trumpet_mute` `vibraphone_hard` + `drum_kit:ride` `drum_kit:hihat` `snare2:taps` `claps`|
|复古/老影片/轿车|`honky_tonk` `upright` `accordion` `harmonica` `banjo` `clarinet` `tuba_stac` `strumstick`|
|巴洛克/宫廷|`harpsichord` `organ_soft` `recorder` `violin` `cellos` `oboe` `bassoon`|
|教堂/神圣|`organ` `organ_pedal` `tubular_bells` `hand_chimes` `vibraphone_bowed` + 长`room(size=.8)`|
|流行/乐观|`drum_kit` `electric_bass` `electric_guitar` `piano` `glockenspiel` `claps` `shaker` `tambourine`|
|世界/民间|`world_perc` (cajón/bongo/darbuka/castanets/shaker) `cajon` `conga` `mbira` `hang` `bagpipe` `pluck:banjo` `guitar_nylon`|
|冷酷/空灵/科幻|`vibraphone_bowed` `glass` `hang` `sus_cymbal:bow` `violins_trem`（低速）+ `room(size=.9, mix=.35)`|

---

<a id="7-known-issues--cautions"></a>
## 7. 已知问题/注意事项

- **`organ`（全部止损）包括 16′**：测量的基波比键名称低一个八度（pyin 测量键 D4 的 D3）；这是器官的自然重量。如果您想要“键名称 = 实际音高”，请使用 `organ_soft`。 `organ_pedal` 螺距按测量值给出。
- **管钟`tubular_bells`**：管钟的“敲音”是虚拟音高（比例为2:3:4的分音4/5/6缺失的基音）；对照频谱检查并正确，但 pyin 报告 octave/fifth 高，这是正常的。
- **定音鼓`timpani`**：只有5个鼓（从F2、B2、D3、E3、G3左右的频谱测得的主要振动模式）； `note('timpani', X)` 从最近的鼓移调；最自然的用法是 `hit('timpani', 'drum1'...)` 或在 F2 和 G3 之间只写音符。
- **Hang `hang`**：原乐器为D小调（A3 D4 E4 F4 G4 A4 C5 D5等）；它本身的音符听起来最好；其他音符被移调，泛音也随之改变。
- **`tenor_sax`（颤音版）起音较慢**：对于短音符，请使用`tenor_sax_stac`/`tenor_sax_nv`； `contrabass` 持续录音包含真正的弓变化膨胀（大约每 2.3 秒一次）。
- **长音符扩展**已在25秒尺度上进行了测试：扩展部分的电平与原始录音的中位数不同，相差<1 dB, and level jumps between adjacent 0.1 s windows are mostly ≤3 dB (violin section/sax swing up to ~6 dB because of their own vibrato). For extremely long (>1分钟）持续音符，分段重新触发或与`attack`淡入重叠。
- **缺失乐器**：未发现**太鼓、中国锣鼓（大drum/cymbals/small锣为全套）、钢片琴、音乐盒样本、原声钢弦吉他样本等CC0/CC BY授权样本， dizi/xiao/shakuhachi**（Floe/SCC taiko 是 CC BY-SA，因此不属于许可政策范围）。替补：太鼓→`gran_cassa`+`frame_drum`+`toms:low_mallet`；锣→`gong`/`gong2:small`;钢片琴→`glockenspiel`（低速）；音乐盒→`pluck:music_box`；钢弦吉他→`pluck:acoustic_guitar`/`strumstick`。
- 下载中丢失的文件：使用 7-Zip 恢复了 FreePats 尤克里里的 `chuck.wav`（静音扫弦）；没有别的东西丢失了。
- 第一次调用 `pluck` JIT 编译（numba，约 0.5 秒，结果缓存在 `core/audio/__pycache__` 中）； `sampler` 第一次读取样本大约需要 10 毫秒，然后从内存缓存中提供它（转置结果也被缓存）。
- 立体声：读取时样本混合为单声道（一个统一的接口）；空间感来自`pan` + `room()`。

---

<a id="8-self-checks-done-no-listening-was-possible-everything-rests-on-data"></a>
## 8. 完成自检（无法监听：一切都取决于数据）

**已验证什么**
1. **沥青**：所有97个采样乐器的每个样本都用阴测量了基波并写入`index.json`；文件名的八度约定通过八度一致性投票进行了纠正（VSCO/VCSL 主要是+12，Karoryfer -12，来自主频谱振动模式的定音鼓）。 61 种乐器的第一个音符是 **自行渲染，并通过 librosa.pyin 进行抽查：59/61 在 ±50 音分之内，合格的中位偏差为 +3.7 音分，最大为 16 音分**；两个“故障”都是已知和经过检查的：管状钟（虚拟音高；2:3:4 频谱分音确认敲击音调正确）和 `organ`（16' 停止，基音低八度）。直接在成品混音中抽查相同的 61 个第一个音符：57/61 通过；其他 4 个（钟琴、管钟、二胡、班卓琴）受到前一乐器衰减的干扰或者是虚拟音高，并且在单独渲染/对照频谱检查时都是正确的（单独渲染的钟琴：频谱峰值 = D6 +12 音分）。
2. **物理建模**：11个预设×2-3个音高全部由pyin击中（±1音分以内）；古琴 `bend` 的 pyin 轨迹与设置相符（0.8→1.4 s 从 50 滑动到 52）；和声音高正确；琵琶论志测得每秒13.3（设置为14）；三味线锯片 on/off 维持 2030 Hz / 1500 Hz 的频谱质心；衰减时间古琴≈4.3 s，琵琶≈2.1 s，三味线≈0.9 s，班卓琴≈1.0 s（T60 从-30 dB 推断）。
3. **成品混音数字**：85.5秒，48 kHz立体声，无NaN/Inf，峰值-2.0 dBFS，0个削波样本；中值 0.5 s RMS -24 dBFS。
4. **长音符扩展**：小提琴section/cello section/flute/trumpet/horn/clarinet/oboe/accordion/bagpipe/erhu/sax/organ呈现为14-25秒长音符；扩展部分没有静音孔，其电平与原始录音匹配（请参见上一项中的数字）。
5. **每个乐器** 实际上已加载并渲染一次（无例外，无 NaN），每个打击乐变体敲击一次，每个变体的峰值标准化为 ~0.4。

**无法验证的内容**
- 主观音色是否“有说服力”、混音是否好听、力度层切换是否流畅、扩展拼接处是否有听得见的phase/timbre跳跃声：这些只能从数据间接判断。第一次使用它们时，用自己的耳朵聆听（每个乐器一个小主题就足够了）。
- 物理模型的“民间风味”（古琴松散、深沉的音色，三味线的锯成纹理）仅通过物理参数和频谱趋势进行调整，从未通过耳朵与真实录音进行比较。
- 微音和音符音色的移调超出了采样范围 ±6 个半音。

---

<a id="9-directory-layout"></a>
## 9. 目录布局

```
core/audio/
  sampler.py            sampled-instrument engine (section 2 of this file)
  pluck.py              physically modelled plucked strings + modal synthesis (section 3)
  instruments/
    index.json          pitch/velocity/level index (rebuildable with build_index())
    vsco2ce/            VSCO 2 CE selection (strings/woodwinds/brass/percussion/upright piano/pipe organ)  395 MB
    vcsl/               VCSL selection (harp/vibraphone/tubular bells/marimba/harpsichord/sax/harmonica/đàn tranh/percussion…) 271 MB
    salamander/         Salamander Grand Piano V3 (5 velocity layers, FLAC 48k/24bit)  218 MB
    freepats/           FreePats CC0 packs + MuldjordKit (CC BY 4.0)  397 MB
    karoryfer/          erhu / Sneakybass / Weresax  74 MB
```

源码链接：VSCO 2 CE https://github.com/sgossner/VSCO-2-CE · VCSL https://github.com/sgossner/VCSL · Salamander https://freepats.zenvoid.org/Piano/acoustic-grand-piano.html · FreePats https://freepats.zenvoid.org/ · Karoryfer https://github.com/sfzinstruments (aliexpress-erhu / karoryfer.sneakybass / karoryfer.weresax)

可用性：必须首先下载采样音色库（`sh tools/fetch.sh instruments <lib>`，请参阅此文件的顶部）。当使用尚未下载的库时，`sampler` 会在命名要运行的命令时引发错误。 `sampler.py` 只需要核心层Python包； `pluck.py` 需要 numba (`setup.sh deps music`)。
