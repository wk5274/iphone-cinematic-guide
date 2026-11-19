# LUT 清单：9 个 Apple Log 2 专用 LUT

全部免费，全部只适用于 **Apple Log 2** 素材（iPhone 15 Pro 及之后机型 + Blackmagic Cam 等 App 拍摄）。输出 Rec.709，33³ `.cube` 格式，可直接导入 Blackmagic Cam 做监看，也可在 DaVinci Resolve / Premiere Pro / Final Cut Pro 里套用。

> ⚠️ 别用在一代 Apple Log 或普通（SDR）视频上，会偏色、会发灰。先确认你的素材是 Apple Log 2，再套 LUT。

## 一句话选法

| 你想要的效果 | 选这个 |
|---|---|
| 万能、暖而浓，第一次用不知道选啥 | Gold 金胶卷 v2 |
| 拍人、拍日常，柔和不抢戏 | Portra 400 v2 |
| 风景、要冲击力，颜色艳、对比强 | Ektar 100 v2 |
| 好莱坞大片味，橙青对撞 | 橙青大片 TealOrange |
| 冷峻、银灰、低饱和 | 漂白旁路 BleachBypass |
| 夜景、情绪片，暗部最沉 | 黑色电影 Noir |
| 暖黄怀旧、褪色胶片感 | 暖调复古 WarmVintage |
| 偏冷偏暗的电影感，我自己的 709 | 709 OETF 版 / 709 Gamma 2.2 版 |

## 柯达胶片三版（v2 底子）

这三版都按修好的 v2 底子做：黑位约 0.065、对比更陡、曝光 +0.17 档、饱和 1.12。室内欠曝一档和室外实拍都验证过，不发灰。

| LUT | 文件 | 黑位 | 风格 | 适合场景 |
|---|---|---|---|---|
| Gold 金胶卷 v2 | `KodakFilm_AppleLog2_Rec709_v2.cube` | 0.065 | 暖而浓，三版里最居中 | 通用，城市、旅行、日常，第一次用就选它 |
| Portra 400 v2 | `KodakPortra_AppleLog2_Rec709_v2.cube` | 0.081 | 最柔和，饱和最克制，肤色好看 | 人像、家庭、日常记录、室内自然光 |
| Ektar 100 v2 | `KodakEktar_AppleLog2_Rec709_v2.cube` | 0.066 | 最艳、对比最强 | 风景、蓝天大海、街头、要视觉冲击力时 |

Portra 黑位 0.081 比 Gold 高，是有意保留的柔和感，不是没修好——Portra 本来就是低对比胶片，黑位压太死就不是 Portra 了。

## 电影感四版（v2 底子）

| LUT | 文件 | 黑位 | 风格 | 适合场景 |
|---|---|---|---|---|
| 橙青大片 TealOrange | `TealOrange_AppleLog2_Rec709.cube` | 0.057 | 高光偏橙、阴影偏青，好莱坞大片味 | 旅行大片、汽车、运动、落日 |
| 漂白旁路 BleachBypass | `BleachBypass_AppleLog2_Rec709.cube` | 0.042 | 低饱和、高对比，银灰冷峻 | 城市冷调、工业风、阴天、纪实感 |
| 黑色电影 Noir | `Noir_AppleLog2_Rec709.cube` | 0.046 | 低调冷调，暗部最沉 | 夜景、雨夜、情绪片、悬疑感 |
| 暖调复古 WarmVintage | `WarmVintage_AppleLog2_Rec709.cube` | 0.081 | 黑位有意抬起的褪色感，暖黄怀旧 | 复古街景、老城、胶片回忆感、暖光室内 |

WarmVintage 的黑位 0.081 是故意抬的——褪色胶片本来就是黑不下去，这是风格，不是缺陷。另外三版黑位都在 0.06 以下，暗部很扎实。

## 自己的 709 两版

这两版是我自己的 Rec.709 创意 LUT（原先在 DaVinci Resolve 里做的）转换成的 Apple Log 2 版，偏冷偏暗的电影感。转换技术链：白皮书公式解码 → AWG 线性逐通道膝点 → AWG→709 矩阵 → 亮度高光膝点 → BT.709 OETF → 原 709 LUT。两个膝点只动高光，阴影和中间调与原 LUT 完全一致。

| LUT | 文件 | 黑位 | 差别 |
|---|---|---|---|
| 709 OETF 版 | `709_AppleLog2_Rec709.cube` | 0.0049 | 原版；18% 灰 0.371，偏冷偏暗 |
| 709 Gamma 2.2 版 | `709_AppleLog2_Rec709_gamma22.cube` | 0.0049 | 中间调、暗部更亮；18% 灰 0.423 |

选法：两版都导进 Blackmagic Cam，同一场景轮着监看——原版在手机上偏暗就留 Gamma 2.2 版，够亮就留原版。两版黑位同为 0.0049，高光基本一样，差别主要在中间调和暗部的亮度。

## 黑位是什么意思

黑位是 Log 纯黑输入时的输出亮度。越低，黑色越黑、越不容易发灰。第一版 Gold v1 黑位 0.104，室内偏暗场景直接发灰，已废弃，不在本仓库里。现行 9 版里，除了有意做褪色感的 WarmVintage（0.081）和柔和的 Portra（0.081），其余都在 0.066 以下。

## 导入方法（简版）

- **Blackmagic Cam 监看**：把 `.cube` 文件存到 iPhone 的“文件”App → 打开 Blackmagic Cam → 设置 → LUT → 导入 → 选文件。详细步骤见 [01 Blackmagic Cam 设置全攻略](../guides/01-blackmagic-cam-setup.md)。
- **DaVinci Resolve**：调色页面 → 右键节点 → 3D LUT → 选文件；或放进 `LUT` 文件夹后在 LUT 面板里调用。详细见 [04 LUT 工作流](../guides/04-lut-workflow.md)和 [05 Resolve 调色流程](../guides/05-davinci-resolve-grading.md)。
- **Premiere Pro**：Lumetri 颜色 → 创意 → 浏览 → 选 `.cube` 文件。
- **Final Cut Pro**：效果 → 颜色 → 自定 LUT → 选文件。

## 许可

这 9 个 LUT 全部免费，遵循 CC BY-NC-SA 4.0：可以免费使用、分享，须署名 Kai；**禁止商用**，禁止拿去售卖、打包进付费产品或付费 LUT 包；改了再分享必须用同样的许可。全文见仓库根目录的 [LICENSE](../LICENSE)。
