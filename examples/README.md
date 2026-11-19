# 样片说明

这里有 40 张图：4 个真实场景 ×（1 张 Log 模拟帧 + 9 个 LUT 调色版）。所有调色帧都是用 ffmpeg `lut3d` 实跑对应 `.cube` 文件生成的，不是示意图，套上去就是这个效果。

## 样片是怎么做的（先说实话）

这 4 张底图**不是 iPhone 拍的**，是 Pexels 上的免费授权真实照片（摄影师见下表）。制作链路：

1. 真实照片（sRGB）→ 解码到线性 → BT.709 转 Apple Wide Gamut → 按白皮书公式做 Apple Log 2 编码，得到一张模拟 Log 帧（灰、平、对比低，和真正的 Log 素材一个样子）
2. 模拟 Log 帧进 ffmpeg `lut3d`，逐个套上 9 个 LUT，得到调色版

为什么不用 iPhone 实拍帧：目前没有现成的、能公开的实拍静帧。用真实照片 + 精确的 Log 2 模拟，照样能看清每个 LUT 的性格（色彩、对比、黑位）；等有合适的实拍帧会换上。LUT 本身的调色效果是在 iPhone 实拍素材的监看中验证过的，见主 README 的“为什么是 v2 底子”。

## 4 个场景

| 场景 | 文件夹 | 底图内容 | 摄影师 | 来源 |
|---|---|---|---|---|
| 街头日光 | `street/` | 伊斯坦布尔街头，行人过马路 | Emre Simsek | [Pexels](https://www.pexels.com/photo/20194548/) |
| 落日海滩 | `sunset/` | 海边落日，海浪与晚霞 | Bella White | [Pexels](https://www.pexels.com/photo/635279/) |
| 夜景霓虹 | `night/` | 东京涩谷夜景，霓虹与车流 | BabijaPhoto JB | [Pexels](https://www.pexels.com/photo/31338141/) |
| 室内暖光 | `indoor/` | 暖光客厅，女子在扶手椅上读书 | Ron Lach | [Pexels](https://www.pexels.com/photo/woman-sitting-in-armchair-reading-book-10677842/) |

底图均为 Pexels 免费授权照片（可免费使用、可商用，无需署名；这里仍列出摄影师表示感谢）。

## 文件对照表

| LUT | 街头 | 落日 | 夜景 | 室内 |
|---|---|---|---|---|
| Log 模拟帧（未套 LUT） | `street/street_log.jpg` | `sunset/sunset_log.jpg` | `night/night_log.jpg` | `indoor/indoor_log.jpg` |
| Gold 金胶卷 v2 | `street/street_gold-v2.jpg` | `sunset/sunset_gold-v2.jpg` | `night/night_gold-v2.jpg` | `indoor/indoor_gold-v2.jpg` |
| Portra 400 v2 | `street/street_portra-v2.jpg` | `sunset/sunset_portra-v2.jpg` | `night/night_portra-v2.jpg` | `indoor/indoor_portra-v2.jpg` |
| Ektar 100 v2 | `street/street_ektar-v2.jpg` | `sunset/sunset_ektar-v2.jpg` | `night/night_ektar-v2.jpg` | `indoor/indoor_ektar-v2.jpg` |
| 橙青大片 TealOrange | `street/street_teal-orange.jpg` | `sunset/sunset_teal-orange.jpg` | `night/night_teal-orange.jpg` | `indoor/indoor_teal-orange.jpg` |
| 漂白旁路 BleachBypass | `street/street_bleach-bypass.jpg` | `sunset/sunset_bleach-bypass.jpg` | `night/night_bleach-bypass.jpg` | `indoor/indoor_bleach-bypass.jpg` |
| 黑色电影 Noir | `street/street_noir.jpg` | `sunset/sunset_noir.jpg` | `night/night_noir.jpg` | `indoor/indoor_noir.jpg` |
| 暖调复古 WarmVintage | `street/street_warm-vintage.jpg` | `sunset/sunset_warm-vintage.jpg` | `night/night_warm-vintage.jpg` | `indoor/indoor_warm-vintage.jpg` |
| 709 OETF 版 | `street/street_709-oetf.jpg` | `sunset/sunset_709-oetf.jpg` | `night/night_709-oetf.jpg` | `indoor/indoor_709-oetf.jpg` |
| 709 Gamma 2.2 版 | `street/street_709-gamma22.jpg` | `sunset/sunset_709-gamma22.jpg` | `night/night_709-gamma22.jpg` | `indoor/indoor_709-gamma22.jpg` |

## 看图要点

- **先看 Log 模拟帧**：灰、平、对比低是正常的，这就是 Log 素材的样子。重点是看套上 LUT 之后，对比和色彩是不是回来了。
- **按场景看**：街头看肤色和建筑的色彩；落日看天空渐变顺不顺、有没有断层；夜景看暗部黑不黑、霓虹跳不跳；室内看暖调和肤色柔不柔。
- **709 两版对比**：直接对照任意场景的 `709-oetf` 和 `709-gamma22`，Gamma 2.2 版的中间调和暗部明显更亮，高光基本一样。
- **WarmVintage 和 Portra 黑位偏高是故意的**：WarmVintage 是褪色感，Portra 是柔和感，别拿它俩跟 Noir 比谁更黑。
- **选 LUT 别只看一张图**：同一个 LUT 在 4 个场景里各看一遍，有的 LUT 在落日下好看、在夜景里就太沉。按场景换 LUT，比死守一个 LUT 重要。

## 图片规格

长边 1600px JPEG。只是用来看效果、选 LUT 的预览图，不是原片。想看全分辨率效果，把 `luts/` 里的 `.cube` 套到你自己的 Apple Log 2 素材上。
