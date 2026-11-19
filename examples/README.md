# 样片说明

这里有 20 张图：两张测试帧 ×（1 张 Log 原片 + 9 个 LUT 调色版）。所有调色帧都是用 ffmpeg `lut3d` 实跑对应 `.cube` 文件生成的，不是示意图，套上去就是这个效果。

## 两张测试帧

| 测试帧 | 来源 | 说明 |
|---|---|---|
| 室外实拍帧 | iPhone 17 Pro Max 实拍 Apple Log 2 视频 | 正常曝光的室外场景，看每个 LUT 在充足光线下的色彩和对比 |
| 室内欠曝一档模拟帧 | 模拟的 Apple Log 2 室内图，欠曝一档 | 故意选了最难的场景：室内偏暗 + 欠曝一档。第一版 LUT 就是在这里翻车的（发灰），现行 9 版重点在这里验收 |

为什么要一张欠曝帧：室外大太阳下，几乎所有 LUT 看起来都不错，拉不开差距。室内偏暗 + 欠曝一档时，黑位抬得太高、暗部曲线太平的 LUT 会立刻发灰、发脏。这是验收 LUT 的试金石。

## 文件对照表

| LUT | 室外帧 | 室内帧 |
|---|---|---|
| Log 原片（未套 LUT） | `outdoor/outdoor_log.jpg` | `indoor/indoor_log.jpg` |
| Gold 金胶卷 v2 | `outdoor/outdoor_gold-v2.jpg` | `indoor/indoor_gold-v2.jpg` |
| Portra 400 v2 | `outdoor/outdoor_portra-v2.jpg` | `indoor/indoor_portra-v2.jpg` |
| Ektar 100 v2 | `outdoor/outdoor_ektar-v2.jpg` | `indoor/indoor_ektar-v2.jpg` |
| 橙青大片 TealOrange | `outdoor/outdoor_teal-orange.jpg` | `indoor/indoor_teal-orange.jpg` |
| 漂白旁路 BleachBypass | `outdoor/outdoor_bleach-bypass.jpg` | `indoor/indoor_bleach-bypass.jpg` |
| 黑色电影 Noir | `outdoor/outdoor_noir.jpg` | `indoor/indoor_noir.jpg` |
| 暖调复古 WarmVintage | `outdoor/outdoor_warm-vintage.jpg` | `indoor/indoor_warm-vintage.jpg` |
| 709 OETF 版 | `outdoor/outdoor_709-oetf.jpg` | `indoor/indoor_709-oetf.jpg` |
| 709 Gamma 2.2 版 | `outdoor/outdoor_709-gamma22.jpg` | `indoor/indoor_709-gamma22.jpg` |

## 看图要点

- **先看室内帧**：重点看暗部黑不黑、脏不脏。黑位扎实的 LUT 在室内帧里暗部是实的、干净的；发灰的 LUT 暗部会浮起一层灰雾。
- **再看室外帧**：重点看天空和肤色。Ektar 的蓝天最艳，Portra 的肤色最柔，TealOrange 的高光偏橙、阴影偏青。
- **709 两版对比**：直接对照 `outdoor_709-oetf.jpg` 和 `outdoor_709-gamma22.jpg`，Gamma 2.2 版的中间调和暗部明显更亮，高光基本一样。
- **WarmVintage 和 Portra 黑位偏高是故意的**：WarmVintage 是褪色感，Portra 是柔和感，别拿它俩跟 Noir 比谁更黑。

## 图片规格

960×540 JPEG。只是用来看效果、选 LUT 的预览图，不是原片。想看全分辨率效果，把 `luts/` 里的 `.cube` 套到你自己的 Apple Log 2 素材上。
