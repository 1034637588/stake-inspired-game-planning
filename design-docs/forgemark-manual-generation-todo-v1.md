# 铸痕工坊 · 手动生成执行 TODO

> 从 01 开始，按顺序往下做。每项提示词已独立写全，直接整段复制，不需要回总览拼接。
> 本清单配套 `forgemark-art-assets-and-prompts-v1.md`，文件名与总览保持一致。
> 这里只安排手动制作，不代表已经生成任何图片或声音。

## 开始前只读这页

### 保存在哪里

本文所有目录都相对于下面这个素材根目录：

`/Users/linyangzhou/Documents/ChatGPT/game/design-docs/forgemark-art/`

- `references/`：选定的风格参考。
- `source/generations/`：生成器下载的原图、场景母版，保留原始尺寸和文件名。
- `review/`：已处理到指定尺寸的待检查文件。**你完成后先放这里，后续再统一审核分类。**
- `approved/…`：审核通过后的归档位置，每项都已列出；不要把刚下载的图直接当作已审核资源。

不熟悉目录操作也没关系：先把原图留好，处理完成的文件按本清单命名，统一交到 `review/` 即可。

### 每项怎么做

1. 看“参考图”，有要求就上传已经选好的那张，不要随便换。
2. 在生成器参数里设置比例、可用尺寸和透明模式，再粘贴完整提示词。
3. 每次只生成当前这一项。可多做几个候选，但最后只选一个交付版本。
4. 下载原文件到 `source/generations/`；不使用网页截图。
5. 抠图、校正和缩放后，才按“交付文件名”存到 `review/`。
6. 勾“已生成”表示选出了候选；勾“已处理”才表示尺寸和透明度符合交付要求。

**提示词中的透明和精确尺寸都需要检查，不是模型保证。** 棋盘格图案不是透明；若工具不支持真实透明，先生成纯色底，再抠图。钢环内孔、模具中间开口也要抠透明。

- 所有独立物件一图一个，不生成合集，不生成图集，不生成动画帧表。
- 物件统一正交正面图、左上光，不是等距斜视角。
- 原图 1024 不能直接改名成 256；要实际缩放并保留标准透明画布。
- 生成器不支持指定尺寸时选最接近比例；后处理时等比缩放、补边或扩画，不能拉歪形状。
- 默认 PNG：sRGB、8-bit RGBA；背景远层和封面不透明。不要紧裁掉规定留白。
- 修改后文件版本递增为 `v002`、`v003`，保留旧版。
- 同时保存使用的提示词、模型、参考图及商用许可记录；可以记在自己的生成记录里。

### 第一轮只做这三个

- [ ] 01 风格参考。
- [ ] 02 铜片 A。
- [ ] 03 模具外框。

把三张放一起，确认颜色、质感和正面视角协调，再继续。铜片缩到约 48 屏幕像素、模具缩到约 350 屏幕像素看一次，不能只看大图。

### 总数量

- 图片任务 **01–26**：1 张选定风格参考 + 1 张场景母版 + 24 张最终图形来源。背景 3 层是编辑/拆层交付，不是三个独立随机场景。
- 声音任务 **27–35**：9 条单独音效，不使用文生图工具。
- 字体任务 **36**：下载并核对许可，不用 AI 画字。
- 所有方图/矩形图母版、重试候选和 SVG 派生预览不重复算最终图形来源。

---

# 第一组：风格、模具和四材料

## 01｜生成风格参考，只选一张

- [ ] 已生成并选定唯一参考
- 生成什么：一张用于统一风格的精密机械工坊参考，不是上线游戏背景。
- 参考图：无。
- 生成设置：1:1，优先 2048×2048；不支持则使用最大合适方图，不透明。
- 保存目录：`references/`
- 文件名：`fm_ref_style-workshop_v001.png`（参考文件名不编码尺寸）。
- 操作：可先出 2–4 个候选，选中一个；其他候选留原图区，后续统一使用选中版。

**直接复制：**

> Create one art-direction reference image for an original mobile 2D precision casting workshop game. Restrained semi-realistic hand-painted 2.5D art, dark blue-gray cast iron, brushed steel, muted reddish copper, pale brass and small teal-green accents. Calm precise handcrafted atmosphere, sparse purposeful wear, clean readable silhouettes, broad controlled highlights, not photorealistic. A compact orderly workshop seen directly toward a workbench, with gentle natural perspective. Small warm furnace light confined to the left side, cool dark ambient fill, organized tools near the outer edges. Keep the central half quiet, dark and low-detail for a separate gameplay board. No playable mold, no game grid, no material tokens, no interface, no text, no numbers, no logo, no watermark, no people, no coin piles, no neon, no dramatic explosion. Square composition, opaque complete environment.

**通过标准：** 深铁灰为主、侧边暖光、中心安静；不是满屏黄铜齿轮或混乱废土。

## 02｜生成铜片 A：以后其他材料跟它对齐

- [ ] 已生成
- [ ] 已抠图、缩放并检查
- 参考图：上传 01，只借用风格；不要复制场景布局。
- 生成设置：1:1，1024×1024，真实透明模式。
- 最终尺寸：256×256，RGBA；主体最长边约 192px，居中，四周透明。
- 待检查目录：`review/`
- 交付文件名：`fm_mat_copper-plate_base_256x256_v001.png`
- 审核后目录：`approved/images/materials/`

**直接复制：**

> Create exactly one isolated material sprite for a mobile 2D precision casting game, using the uploaded image only as a color and rendering style reference. Restrained semi-realistic hand-painted 2.5D rendering. One muted reddish copper square plate, axis-aligned, equal width and height, slightly beveled corners, three short parallel recessed grooves centered on the face. Strict orthographic front view, main face parallel to the canvas, no perspective tilt, no isometric view. Broad brushed face, clean silhouette, sparse edge wear, soft upper-left light and subtle lower-right shading. Upright square, never rotated into a diamond. Exactly one centered object occupying about 75 percent of the square canvas width, generous transparent padding, fully visible. Real alpha transparency outside the object, no floor, no backdrop, no external cast shadow. No text, letters, numbers, watermark, logo, coin, circle, hexagon, gold-yellow metal, surrounding objects, contact sheet, sprite sheet, fake checkerboard, heavy rust, noisy scratches, blur, bloom or lens flare. Readable when displayed at 48 screen pixels.

**通过标准：** 正方、红铜、三短槽；不能是金币或斜视厚砖。

## 03｜生成模具外框：中间必须空

- [ ] 已生成
- [ ] 已抠图、校正并检查
- 参考图：01 风格参考 + 02 铜片；只统一材质和光线。
- 生成设置：1:1，1024×1024，真实透明模式。
- 最终尺寸：1024×1024，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_board_mold-frame_base_1024x1024_v001.png`
- 审核后目录：`approved/images/board/`

**直接复制：**

> Create exactly one isolated perfectly square precision casting mold outer frame for a mobile 2D game. Match the uploaded workshop style and copper sprite rendering without copying the copper shape. Restrained semi-realistic hand-painted 2.5D, dark blue-gray cast iron, thin subdued pale brass inner rim, four small recessed corner fasteners. Strict orthographic front view, axis-aligned, symmetric, main face parallel to the canvas, soft upper-left light, restrained highlights, sparse purposeful wear. Large empty square opening in the middle, fully transparent, no bottom panel. Aim for a 1024 square canvas with outer structure inside 32 to 992 and inner square opening from 96 to 928 on each axis; exact coordinates will be corrected in post-processing. All decoration stays on the outer rim. No interior grid, no internal cells, no digits, no marks, no tokens, no press arm, no protrusions into the opening. Transparent outside and inside the frame, no floor, no baked cast shadow, no text, logo, watermark, fake checkerboard, perspective tilt, diagonal frame, isometric view, excessive rust, blur or glow. Frame should remain visually subordinate to material tokens.

**处理要求：** 画布不紧裁；中心透明开口精确校正为 `[96,928)×[96,928)`。程序之后在 `(112,112)` 起的 800×800 区域绘制 5×5 网格。AI 画出格线就清掉，不把它当盘面坐标。

## 04｜生成钢环 B

- [ ] 已生成
- [ ] 已抠图、缩放并检查
- 参考图：02 铜片，约束画法、光线和占比，不复制方形。
- 生成设置：1:1，1024×1024，透明。
- 最终尺寸：256×256，RGBA，外径约 192px，居中。
- 待检查目录：`review/`
- 交付文件名：`fm_mat_steel-ring_base_256x256_v001.png`
- 审核后目录：`approved/images/materials/`

**直接复制：**

> Create exactly one isolated blue-gray steel ring material sprite for a mobile 2D precision casting game. Match the uploaded copper sprite's restrained semi-realistic hand-painted 2.5D rendering, visual scale and upper-left light, but do not copy its square shape or copper color. Perfect circular outer silhouette, one large circular transparent hole in the center. Ring band radial thickness approximately one fifth of the outer diameter, four small evenly spaced recessed notches on the band, no gear teeth. Strict orthographic front view, no ellipse, no perspective tilt. Cool brushed blue-gray steel, broad restrained highlights, sparse edge wear. One centered object with outer diameter about 75 percent of canvas width, generous padding, complete silhouette. True alpha transparency both outside and through the hole. No solid disk, coin, gear, gemstone, multiple rings, text, numbers, watermark, logo, floor, shadow plane, external cast shadow, fake checkerboard, sprite sheet, neon, bloom or blur. Square canvas, readable at 48 screen pixels.

**通过标准：** 正圆，中心孔真透明；不是齿轮或椭圆戒指。

## 05｜生成棱晶 C

- [ ] 已生成
- [ ] 已抠图、缩放并检查
- 参考图：02 铜片 + 04 钢环，统一光线和绘制精度，不复制材质形状。
- 生成设置：1:1，1024×1024，透明。
- 最终尺寸：256×256，RGBA，主体最长边约 192px，居中。
- 待检查目录：`review/`
- 交付文件名：`fm_mat_teal-prism_base_256x256_v001.png`
- 审核后目录：`approved/images/materials/`

**直接复制：**

> Create exactly one isolated teal-green prism material sprite for a mobile 2D precision casting game. Match the uploaded sprites' restrained semi-realistic hand-painted 2.5D style, visual weight and upper-left light, but use a mineral surface, not copper or steel. Equilateral triangle silhouette with one apex pointing straight up and a horizontal bottom edge. Clean three-sided outline, shallow cut facets, one simple clearly readable inset triangular facet. Predominantly opaque polished teal-green mineral with only subtle internal luminosity, no surrounding glow cloud. Strict orthographic front view, main face parallel to canvas, no tilt or isometric view. One centered object occupying about 75 percent of the square canvas along its longest dimension, fully visible, generous transparent padding. True transparent background, no pedestal, floor or baked cast shadow. No crystal cluster, hexagonal crystal, diamond jewel, blue sapphire, ice shard, inverted triangle, fully transparent body, text, numbers, logo, watermark, sprite sheet, fake checkerboard, heavy bloom or blurry edge. Readable at 48 screen pixels.

**通过标准：** 上指正三角、青绿、不是多尖晶簇；不要过度透明。

## 06｜生成金印 D

- [ ] 已生成
- [ ] 已抠图、缩放并检查
- 参考图：02 铜片 + 04 钢环，统一画法与光线。
- 生成设置：1:1，1024×1024，透明。
- 最终尺寸：256×256，RGBA，主体最长边约 192px，居中。
- 待检查目录：`review/`
- 交付文件名：`fm_mat_gold-seal_base_256x256_v001.png`
- 审核后目录：`approved/images/materials/`

**直接复制：**

> Create exactly one isolated pale-gold metal seal material sprite for a mobile 2D precision casting game. Match the uploaded sprites' restrained semi-realistic hand-painted 2.5D rendering, visual weight and soft upper-left light, without copying their silhouettes. A symmetric solid rhombus-shaped metal block, long axis vertical, distinct top, bottom, left and right tips. One simple inset concentric rhombus groove on the face, pale warm gold brushed finish, beveled edges, sparse purposeful wear. Strict orthographic front view, front face parallel to the canvas, no perspective tilt, no handle or pedestal. One centered object, longest dimension about 75 percent of square canvas, complete silhouette and generous transparent padding. True alpha background, no floor, no external cast shadow. No square silhouette, coin, crown, star, gemstone, text, letters, numbers, watermark, logo, surrounding objects, sprite sheet, fake checkerboard, excessive bloom, noisy scratches or blur. Readable at 48 screen pixels.

**通过标准：** 竖轴菱形、浅金、内菱形槽；不能像金币或方片。

## 07｜生成入口印记 S

- [ ] 已生成
- [ ] 已抠图、缩放并检查
- 参考图：03 模具外框。
- 生成设置：1:1，1024×1024，透明。
- 最终尺寸：128×128，RGBA；主体最长边约 88px，居中。
- 待检查目录：`review/`
- 交付文件名：`fm_mark_entry-stamp_base_128x128_v001.png`
- 审核后目录：`approved/images/marks/`

**直接复制：**

> Create exactly one isolated compact entry-stamp emblem for a mobile 2D precision casting game. Match the uploaded mold's restrained hand-painted metal rendering and upper-left light. Flat neutral dark metal symbol with thin warm ivory highlights: one broken circular outer ring enclosing one short vertical recessed stroke meeting one short lower horizontal recessed stroke. Very simple readable geometry, strict orthographic front view, no handle, no pedestal. Simpler and less colorful than collectible material tokens, not an additional payable material. One centered emblem occupying about 69 percent of square canvas, generous transparent padding. Real alpha transparency, no backdrop or baked cast shadow. Do not draw the letter S, any letter, numeral 3, bonus wording, text, logo, watermark, coin, crown, sprite sheet, fake checkerboard, noisy detail, neon glow or blur.

**通过标准：** 简洁中性符号，没有字母 S 或数字 3；只做这一张，不另生成盖印状态。

---

# 第二组：两张特效纹理

## 08｜生成冲压接触亮形

- [ ] 已生成
- [ ] 已清理 Alpha、缩放并检查
- 参考图：不必上传，避免画出实体机器。
- 生成设置：1:1，1024×1024，真实透明。
- 最终尺寸：256×256，RGBA，四周完全透明。
- 待检查目录：`review/`
- 交付文件名：`fm_fx_press-flash_base_256x256_v001.png`
- 审核后目录：`approved/images/effects/`

**直接复制：**

> Create one isolated compact neutral warm-white impact-flash texture for a small precision metal press contact in a 2D mobile game. One small soft central light with four very short tapered rays and subtle irregularity. Restrained energy, warm-white to pale warm edge, smooth alpha falloff reaching fully transparent pixels well before the canvas edges. Centered square canvas with generous completely transparent padding. This is only one reusable flash primitive, not a full scene and not an animation. No metal object, material token, press machine, smoke, debris, large explosion, long streaks, text, numbers, watermark, logo, sprite sheet, painted checkerboard, gray rectangular haze, hard opaque background or lens flare. True alpha transparency; no background illumination plane.

**通过标准：** 小而短促的亮形，不是整张灰雾或大爆炸；在黑底上没有方框。

## 09｜生成一枚金属碎片

- [ ] 已生成
- [ ] 已抠图、缩放并检查
- 参考图：04 钢环，只参考灰金属质感。
- 生成设置：1:1，1024×1024，透明。
- 最终尺寸：256×256，RGBA；碎片最长边约 144px，居中。
- 待检查目录：`review/`
- 交付文件名：`fm_fx_metal-chip_base_256x256_v001.png`
- 审核后目录：`approved/images/effects/`

**直接复制：**

> Create exactly one isolated small neutral light-gray metal chip sprite for a mobile 2D precision casting game. Restrained semi-realistic hand-painted 2.5D style matching the uploaded metal reference, soft upper-left light, compact irregular quadrilateral silhouette, two or three broad readable facets, matte gray values suitable for runtime tinting. Strict orthographic front-facing presentation. One centered chip occupying about 56 percent of the square canvas along its longest dimension, generous empty padding. Real transparent alpha background, no floor or external cast shadow. No pile, no second chip, no scattered particles, no long needle, no trail, no glowing effect, no text, numbers, logo, watermark, sprite sheet, fake checkerboard, noisy scratches or blur.

**通过标准：** 只有一枚，不是一堆；不需要另做铜/钢/青绿/金四套。

---

# 第三组：六个无字 UI 底板

> UI 中心要有深色平整填充，**不是整张全透明空框**；只有控件外部透明。文字和状态以后由程序叠加。提示词不能保证九宫格可用，清理边框后必须检查拉伸。

## 10｜生成主按钮底板

- [ ] 已生成
- [ ] 已清边、缩放并检查拉伸
- 参考图：03 模具外框 + 02 铜片。
- 生成设置：2:1，优先 1024×512，透明。
- 最终尺寸：512×256，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_ui_primary-button_base_512x256_v001.png`
- 审核后目录：`approved/images/ui/`

**直接复制：**

> Create exactly one isolated blank primary action button skin for a mobile precision casting game. Match uploaded restrained hand-painted 2.5D industrial references: dark blue-gray cast-iron body, fine muted reddish copper rim, soft upper-left light, sparse edge wear. Horizontal 2-to-1 canvas, symmetric rounded rectangle with restrained machined corners and a broad quiet dark central face. Strict front orthographic view, no tilt, complete outline with transparent exterior padding. Flat uniform center suitable for live text, straight uninterrupted middle edges and simple corners suitable for later nine-slice cleanup. No label, letters, digits, icon, central emblem, lever, control panel, engraved line of text, celebratory glow, outer cast shadow, noisy scratches, watermark, logo, fake checkerboard or multiple buttons. One neutral idle plate only, not a screenshot or state sheet.

**处理要求：** 最终九宫格边距四边各 48px；边缘中段无固定装饰。只生成一张，不生成“启动/揭晓/忙碌/禁用”四张。

## 11｜生成规则、设置等共享面板

- [ ] 已生成
- [ ] 已清边、缩放并检查拉伸
- 参考图：10 主按钮底板，统一边框语言。
- 生成设置：1:1，1024×1024，透明。
- 最终尺寸：512×512，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_ui_shared-panel_base_512x512_v001.png`
- 审核后目录：`approved/images/ui/`

**直接复制：**

> Create exactly one isolated blank square modular dialog panel skin for a mobile precision casting game. Match the uploaded button's restrained hand-painted 2.5D industrial construction, dark blue-gray interior, thin subdued pale brass rim, soft upper-left lighting, symmetric simple corners. Keep a large flat uniform dark center, completely empty for localized live text and settings. Transparent exterior with uncropped outline and padding. Ornamentation confined to the narrow outer rim, straight uninterrupted edge middles suitable for nine-slice cleanup and resizing. No title plaque, close icon, controls, fake text lines, letters, digits, internal divisions, protruding rivets, large gradients, outer cast shadow, watermark, logo, fake checkerboard, heavy wear or multiple panels. One blank panel only.

**处理要求：** 九宫格四边各 32px；规则、设置、加载、错误、恢复回放共用这一张。

## 12｜生成 HUD 通用信息底板

- [ ] 已生成
- [ ] 已清边、缩放并检查拉伸
- 参考图：10 + 11。
- 生成设置：3:1，优先 1536×512，透明。
- 最终尺寸：768×256，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_ui_hud-plate_base_768x256_v001.png`
- 审核后目录：`approved/images/ui/`

**直接复制：**

> Create exactly one isolated blank low-profile horizontal HUD plate for a mobile precision casting game, on a 3-to-1 canvas. Match the uploaded restrained hand-painted 2.5D UI references. Dark cool blue-gray metal face, very thin desaturated brass rim, soft upper-left light, simple matching end caps, symmetric orthographic front view. Large nearly flat uniform empty center for dynamic cost or accumulated-return text, with straight extensible middle edges suitable for nine-slice cleanup. Quiet secondary emphasis, transparent exterior padding, complete outline. No predefined columns, labels, numbers, currency signs, icons, trophy, internal compartments, decorative center object, outer shadow, watermark, logo, fake checkerboard, noisy wear, large gradient, multiple plates or interface screenshot.

**处理要求：** 九宫格四边各 32px，不预画“成本/累计”两列。

## 13｜生成轮次条空底板

- [ ] 已生成
- [ ] 已清边、缩放并检查拉伸
- 参考图：12 HUD 底板。
- 生成设置：3:1，优先 1536×512，透明。
- 最终尺寸：768×256，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_ui_round-rail_base_768x256_v001.png`
- 审核后目录：`approved/images/ui/`

**直接复制：**

> Create exactly one isolated blank horizontal mechanical rail backing for a mobile precision casting game's round indicator, on a 3-to-1 canvas. Match uploaded restrained hand-painted 2.5D industrial UI: dark iron shallow recessed surface, simple pale brass end caps, soft upper-left light, symmetric front orthographic view. Entire middle is flat, empty and uninterrupted, suitable for live progress markers placed later by code. Transparent exterior, complete outline, generous padding, narrow simple border with straight extensible middle sections for nine-slice cleanup. Do not draw progress nodes, tick marks, dividers, three compartments, illuminated states, numbers, fractions, letters, text, icons, wires, outer cast shadow, watermark, logo, fake checkerboard, heavy scratches or multiple rails.

**处理要求：** 九宫格四边各 32px；三个节点、轮次数字和进度都不画。

## 14｜生成本次计算式空底板

- [ ] 已生成
- [ ] 已清边、缩放并检查拉伸
- 参考图：12 HUD 底板。
- 生成设置：3:1，优先 1536×512，透明。
- 最终尺寸：768×256，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_ui_formula-plate_base_768x256_v001.png`
- 审核后目录：`approved/images/ui/`

**直接复制：**

> Create exactly one isolated blank horizontal calculation readout plate for a mobile precision casting game, on a 3-to-1 canvas. Match uploaded restrained hand-painted 2.5D industrial UI, strict front orthographic view, dark flat slate-metal face, thin restrained teal accent confined to the outer rim, subtle upper-left light. Wide uniform empty center for a dynamic formula, straight extensible middle edges and simple corners for nine-slice cleanup. Calm precise instrumentation design, transparent exterior padding, uncropped outline. No engraved math, plus sign, multiplication sign, equal sign, digits, example values, letters, text, wires, arrows, central decoration, bloom, outer shadow, watermark, logo, fake checkerboard, noisy scratches or multiple plates.

**处理要求：** 九宫格四边各 32px；禁止把示例公式画进去。

## 15｜生成中性结果空底板

- [ ] 已生成
- [ ] 已清边、缩放并检查拉伸
- 参考图：12 HUD 底板。
- 生成设置：3:1，优先 1536×512，透明。
- 最终尺寸：768×256，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_ui_result-plate_base_768x256_v001.png`
- 审核后目录：`approved/images/ui/`

**直接复制：**

> Create exactly one isolated blank neutral final-result information plate for a mobile precision casting game, on a 3-to-1 canvas. Match uploaded restrained hand-painted 2.5D industrial UI: dark blue-gray metal face, fine subdued pale brass rim, soft upper-left light, balanced quiet symmetry, strict front orthographic view. Wide flat uniform empty central area for live result text. Simple corners and straight extensible middle edges suitable for nine-slice cleanup, complete outline and transparent exterior padding. Neutral appearance appropriate for zero return, a net loss, a net gain or a capped result; all meaning will be supplied by code. No coins, trophy, crown, confetti, celebratory glow, fixed values, text, numbers, icons, outer shadow, watermark, logo, fake checkerboard, noisy scratches or multiple plates.

**处理要求：** 九宫格四边各 32px；不另生成四种结算背景。

---

# 第四组：六个功能图标

> 手动文生图路线统一先交 128×128 PNG，不要求你现在转换 SVG。后续可以矢量重绘替换；若使用 SVG，文件名去掉 `_128x128` 并更换扩展名，不把 PNG 改扩展名伪装成 SVG。
> 六图统一暖象牙白单色、圆头线条，透明底；最终画布安全边约 20px、线宽约 8px。AI 不保证精确线宽，最后需一起检查。

## 16｜生成规则图标

- [ ] 已生成
- [ ] 已清边、统一线宽并缩放
- 参考图：无；选定这一张后作为 17–21 的线条风格参考。
- 生成设置：1:1，1024×1024，透明；最终 128×128。
- 待检查目录：`review/`
- 交付文件名：`fm_icon_rules_base_128x128_v001.png`
- 审核后目录：`approved/images/icons/`

**直接复制：**

> Create exactly one minimal functional rules icon for a mobile game. Flat pale ivory monochrome outline on a true transparent background. One simple document page with one slightly folded upper corner and exactly three short horizontal strokes inside, no readable text. Centered square composition, consistent rounded line caps and joins. Intended final design grid 128 by 128, approximately 8-unit stroke, at least 20-unit safe padding. Readable at 20 to 24 screen pixels. No letter i, question mark, numbers, text, enclosing button, 3D shading, metallic texture, gradients, shadows, glow, watermark, logo, checkerboard pattern, multiple icons or sprite sheet.

## 17｜生成声音图标

- [ ] 已生成
- [ ] 已清边、统一线宽并缩放
- 参考图：16 规则图标，仅参考颜色和线宽。
- 生成设置：1:1，1024×1024，透明；最终 128×128。
- 待检查目录：`review/`
- 交付文件名：`fm_icon_sound_base_128x128_v001.png`
- 审核后目录：`approved/images/icons/`

**直接复制：**

> Create exactly one minimal sound-enabled UI icon matching the uploaded icon's flat pale ivory line color, rounded caps, joins and stroke weight. A single simple speaker built from a small rectangular body and widening cone, with exactly two clean sound-wave arcs to the right. True transparent background, centered square composition. Intended final 128 by 128 design grid, approximately 8-unit stroke, at least 20-unit safe padding, readable at 20 to 24 screen pixels. No music note, mute slash, document, letters, numbers, text, enclosing button, 3D shading, metallic texture, gradient, shadow, glow, watermark, logo, fake checkerboard, multiple icons or sprite sheet.

## 18｜生成快速图标

- [ ] 已生成
- [ ] 已清边、统一线宽并缩放
- 参考图：16 规则图标，只参考线条。
- 生成设置：1:1，1024×1024，透明；最终 128×128。
- 待检查目录：`review/`
- 交付文件名：`fm_icon_turbo_base_128x128_v001.png`
- 审核后目录：`approved/images/icons/`

**直接复制：**

> Create exactly one minimal fast-mode UI icon matching the uploaded icon's flat pale ivory line color, rounded caps and consistent stroke weight. Exactly two matching right-pointing chevrons, horizontally aligned and evenly spaced. True transparent background, centered square composition. Intended final 128 by 128 design grid, approximately 8-unit stroke, at least 20-unit safe padding, readable at 20 to 24 screen pixels. No third chevron, enclosing circle, lightning bolt, document, text, letters, numbers, button plate, 3D shading, metallic texture, gradient, shadow, glow, watermark, logo, fake checkerboard, multiple icons or sprite sheet.

## 19｜生成减弱动态图标

- [ ] 已生成
- [ ] 已清边、统一线宽并缩放
- 参考图：16 规则图标，只参考线条。
- 生成设置：1:1，1024×1024，透明；最终 128×128。
- 待检查目录：`review/`
- 交付文件名：`fm_icon_reduced-motion_base_128x128_v001.png`
- 审核后目录：`approved/images/icons/`

**直接复制：**

> Create exactly one minimal reduced-motion UI icon matching the uploaded icon's flat pale ivory line color, rounded caps and consistent stroke weight. A compact group of exactly three short parallel horizontal motion lines crossed by one clear diagonal slash. Simple uncluttered geometry on a true transparent background, centered square composition. Intended final 128 by 128 design grid, approximately 8-unit stroke, at least 20-unit safe padding, readable at 20 to 24 screen pixels. No eye, speed meter, speaker, document, text, letters, numbers, enclosing button, 3D shading, metallic texture, gradient, shadow, glow, watermark, logo, fake checkerboard, multiple icons or sprite sheet.

## 20｜生成关闭图标

- [ ] 已生成
- [ ] 已清边、统一线宽并缩放
- 参考图：16 规则图标，只参考线条。
- 生成设置：1:1，1024×1024，透明；最终 128×128。
- 待检查目录：`review/`
- 交付文件名：`fm_icon_close_base_128x128_v001.png`
- 审核后目录：`approved/images/icons/`

**直接复制：**

> Create exactly one minimal close UI icon matching the uploaded icon's flat pale ivory color, rounded caps and consistent stroke weight. Exactly two straight equal-length diagonal strokes crossing at the center to form a perfectly symmetric X. True transparent background, centered square composition. Intended final 128 by 128 design grid, approximately 8-unit stroke, at least 20-unit safe padding, readable at 20 to 24 screen pixels. No circle, box, decorative corner, document, text, numbers, enclosing button, 3D shading, metallic texture, gradient, shadow, glow, watermark, logo, fake checkerboard, multiple icons or sprite sheet.

## 21｜生成回放图标

- [ ] 已生成
- [ ] 已清边、统一线宽并缩放
- 参考图：16 规则图标，只参考线条。
- 生成设置：1:1，1024×1024，透明；最终 128×128。
- 待检查目录：`review/`
- 交付文件名：`fm_icon_replay_base_128x128_v001.png`
- 审核后目录：`approved/images/icons/`

**直接复制：**

> Create exactly one minimal replay UI icon matching the uploaded icon's flat pale ivory line color, rounded caps and consistent stroke weight. One nearly circular counterclockwise return arrow with one clearly readable arrowhead and one small open gap. True transparent background, centered square composition. Intended final 128 by 128 design grid, approximately 8-unit stroke, at least 20-unit safe padding, readable at 20 to 24 screen pixels. No play triangle, second arrow, clock numerals, document, text, letters, numbers, enclosing button, 3D shading, metallic texture, gradient, shadow, glow, watermark, logo, fake checkerboard, multiple icons or sprite sheet.

---

# 第五组：工坊背景母版与三层交付

## 22｜生成完整工坊场景母版

- [ ] 已生成并选定母版
- 参考图：01 风格参考 + 03 模具，仅统一画风；**不要把模具画进背景**。
- 生成设置：1:1，优先 2048×2048，不透明。
- 保存目录：`source/generations/`
- 母版文件名：`fm_source_workshop-master_v001.png`（过程文件，不是运行时资源）。
- 说明：母版保留真实尺寸；若仅能生成 1024，先记录，之后三层统一处理到同一画布。单纯放大不会增加真实细节。

**直接复制：**

> Create one complete environment master image for a mobile 2D precision casting game, matching the uploaded restrained semi-realistic hand-painted 2.5D workshop style. Use the mold reference only for materials and rendering, do not include the mold itself. A compact orderly workshop looking directly toward a workbench with gentle natural perspective. Dark masonry and blue-gray metal wall in the far background, small warm furnace opening confined to the far left edge, organized tools and pipes confined to the outer sides, subtle peripheral workbench edges and corner brackets near the bottom corners. Cool dark ambient fill, muted copper and pale brass details, sparse purposeful wear. Central half must remain dark, low-contrast and low-detail, with no object silhouettes or bright lights. On a 2048 square layout keep approximately x500 to1548 and y500 to1548 quiet. No central machine, playable mold, square game grid, material tokens, control panel, buttons, interface, text, numbers, logo, watermark, people, coin piles, neon, explosion, heavy fog or blur. Opaque full square composition suitable for portrait cropping and centered desktop display.

**通过标准：** 中心没有“假盘面”；炉光在侧面，工具只在外围。接下来都基于这张母版，不独立重画三张场景。

## 23｜编辑母版，制作远层 far

- [ ] 已补画/编辑
- [ ] 已导出并检查
- 操作类型：图像编辑/局部重绘，**不是全新文生图**。
- 输入参考：22 母版原图。
- 最终尺寸：2048×2048，不透明。
- 待检查目录：`review/`
- 交付文件名：`fm_bg_workshop_far_2048x2048_v001.png`
- 审核后目录：`approved/images/backgrounds/`

**直接复制到图片编辑工具：**

> Edit this exact uploaded workshop master image into the FAR background layer. Preserve the original square canvas, camera, perspective, colors and lighting. Keep only the distant workshop wall, distant structural surfaces and the small side furnace opening and its restrained light. Remove all midground tools, side pipes that will be separate objects, foreground bench edges and corner brackets. Reconstruct the wall and floor surfaces behind removed objects consistently, leaving no holes or object-shaped residual shadows. Keep the central gameplay region quiet and low-contrast. This FAR layer must cover the entire canvas and remain fully opaque. Do not add a mold, grid, tokens, interface, text, numbers, logo, watermark or new objects. Do not crop, zoom, recompose or redesign the scene.

**检查：** 全画布有底，不留透明洞；不是简单删除工具后留白。没有图像编辑工具时保留母版，将本项标“待拆层”，不要用随机文生图冒充完成。

## 24｜从母版提取中层 mid

- [ ] 已提取/抠图
- [ ] 已导出并检查
- 操作类型：图像编辑/选区抠图。
- 输入参考：22 原始母版，**不是 23 已删工具的远层**。
- 最终尺寸：2048×2048，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_bg_workshop_mid_2048x2048_v001.png`
- 审核后目录：`approved/images/backgrounds/`

**直接复制到图片编辑工具：**

> Extract the MID layer from this exact uploaded workshop master. Keep only the organized peripheral tools, side pipes and midground structural objects. Preserve their exact original positions, scale, silhouettes, lighting and the full original square canvas. Remove the distant wall, distant furnace opening and all foreground workbench edges and corner brackets. Make every removed area truly transparent with an alpha channel, especially the central gameplay area. Do not bake a checkerboard or colored background. Do not retain a duplicate furnace glow or background-shaped shadows. Do not add new objects, mold, grid, tokens, interface, text or watermark. Do not crop tightly around the tools, move them, zoom, recompose or redraw their design.

**检查：** 中心透明；层的位置与母版一致；与 far 合成不重复炉口和管线。

## 25｜从母版提取近层 near

- [ ] 已提取/抠图
- [ ] 已导出并检查
- 操作类型：图像编辑/选区抠图。
- 输入参考：22 原始母版。
- 最终尺寸：2048×2048，RGBA。
- 待检查目录：`review/`
- 交付文件名：`fm_bg_workshop_near_2048x2048_v001.png`
- 审核后目录：`approved/images/backgrounds/`

**直接复制到图片编辑工具：**

> Extract the NEAR foreground layer from this exact uploaded workshop master. Keep only the peripheral foreground workbench edges and a few foreground corner brackets near the bottom corners. Preserve their exact original positions, scale, silhouettes, lighting and the full original square canvas. Remove all distant wall, furnace, side tools, pipes and midground objects. All remaining space must have true alpha transparency, especially the center and upper area. No tools lying in the center, no duplicate objects, no new mold, grid, tokens, interface, text or watermark. Do not paint a checkerboard. Do not crop tightly, zoom, move objects, recompose or redesign.

**检查：** 三层共用原点；按 far → mid → near 合成应接近母版。默认不做视差；如要移动图层，要额外处理阴影和露洞。方图桌面两边由页面渐变扩展，不直接横向拉伸。

---

# 第六组：封面，最后才做

## 26｜生成方形封面

- [ ] 已生成
- [ ] 已处理尺寸并检查
- 参考图：03 模具 + 02/04/05/06 四材料 + 22 场景母版；工具参考数量有限时优先确保形状一致。
- 生成设置：1:1，优先 2048×2048，不透明。
- 最终尺寸：2048×2048。
- 待检查目录：`review/`
- 交付文件名：`fm_cover_workshop-keyart_base_2048x2048_v001.png`
- 审核后目录：`approved/images/cover/`

**直接复制：**

> Create one square key-art cover for an original precision casting workshop game, matching the uploaded approved mold, four material sprites and workshop environment. Restrained semi-realistic hand-painted 2.5D rendering, dark cast iron, muted red copper, blue-gray steel, teal-green mineral and pale gold, warm side furnace light with cool dark ambience. A compact mold frame is the central hero object, viewed nearly front-on, with a small deliberate arrangement of the four exact material shapes: red-copper upright square plate with three short grooves, blue-gray circular steel ring with a transparent center hole, upward teal equilateral triangle with an inner triangular facet, pale-gold vertical rhombus with an inner rhombus groove. Preserve their identity and silhouettes, do not redesign them. Simple strong central composition, main subject within the central 80 percent, uncluttered workshop background, dark breathing room near the top for a separately typeset title. Opaque full image. No interface, numeric grid, money, coin piles, trophy, crown, characters, extra material types, bonus features, text, letters, numbers, logo, watermark, neon or excessive bloom.

**通过标准：** 与游戏资产是同一套形状；不要生成中文标题，后续用字体排。平台封面裁切尺寸另核，本项不是所有平台的提交尺寸。

---

# 第七组：9 条音效，可等图片完成后再做

> 以下用“文生音效/音频”工具，不能输入文生图工具。
> 每条独立生成和导出，不把一局过程合成一条音轨。生成器不保证亚秒准确，下载后剪辑、试听，不能只改扩展名转 WAV。
> 推荐最终 PCM WAV、48kHz / 24bit；若源为其他格式，保留原件再真实转码，转码不会增加原有音质。先去多余首尾静音，不截断自然衰减，避免削波。
> 生成原件留 `source/generations/`，处理后统一放 `review/`，审核后都进入 `approved/audio/`。

## 27｜冲压主音 S04-A，先做它作为音色标准

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：无。
- 目标时长：0.12–0.22 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_press-impact_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> Single compact precision metal press impact, immediate dry mechanical contact, firm short low-mid body, subtle metallic detail, fast decay, approximately 0.18 seconds. Isolated one-shot for a small precision workshop mechanism, not a heavy industrial crash. No music, voice, ambience bed, explosion, long reverberation or clipping. Immediate readable onset, compact controlled natural tail.

## 28｜成组落料 S02

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：27，只参考整体质感，不复制撞击力度。
- 目标时长：0.12–0.20 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_material-drop_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One compact grouped landing of small metal components into a precision casting mold. Two or three tightly clustered small contacts perceived as one event, firm but quiet, consistent dry close workshop sound. Approximately 0.16 seconds, not 25 separate hits. Isolated one-shot, no music, voice, ambience bed, long reverb, exaggerated crash or clipping. Immediate readable onset, compact controlled natural tail.

## 29｜按钮咔嗒 S01

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：27，只参考干燥机械质感。
- 目标时长：0.06–0.10 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_button-press_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One small precise mechanical button click, dry tactile contact, short muted metallic detail, approximately 0.08 seconds, quieter and lighter than a metal press impact. No springy cartoon sound. Isolated one-shot, no music, voice, ambience bed, long reverb or clipping. Immediate readable onset, compact controlled natural tail.

## 30｜刻度接入 S03

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：27，保持同一工坊音色。
- 目标时长：0.12–0.25 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_mark-connect_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One restrained ascending mechanical tonal cue for existing mold marks connecting to a calculation. Two or three soft short notes perceived as one compact UI cue, subtle precise metallic timbre, approximately 0.20 seconds. No jackpot flourish, no long pitch rise, no dramatic anticipation. Isolated single game effect, no music track, voice, ambience bed, long reverb or clipping. Immediate readable onset, compact controlled natural tail.

## 31｜冲压变体 S04-B

- [ ] 已生成
- [ ] 已剪辑、对齐音色并导出
- 参考音：上传 27 主冲压音；支持参考时基于它做变体。
- 目标时长：0.12–0.22 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_press-impact_b_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> Create one alternate take of the same small precision metal press impact as the reference. Similar perceived loudness, low-mid body, dry timbre, attack and duration, with only slightly different metallic contact detail. Approximately 0.18 seconds. Not a heavier or more dramatic slam. Isolated one-shot, no music, voice, ambience bed, long reverberation, extra repeated hits or clipping. Immediate readable onset, compact controlled natural tail.

## 32｜滚落碎屑 S05

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：28 落料音，质感一致但更轻。
- 目标时长：0.10–0.18 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_tumble-chip_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One quiet small metal chip shuffle and short drop, thin dry workshop details, low prominence, approximately 0.14 seconds. Lighter than the main material landing and much quieter than the press impact. No shattering glass or long rolling debris. Isolated single game effect, no music, voice, ambience bed, long reverb or clipping. Immediate readable onset, compact controlled natural tail.

## 33｜跨轮换挡 S06

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：29 按钮音，保持同一机械风格。
- 目标时长：0.08–0.12 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_round-shift_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One subtle precision mechanism shifting into the next material batch, a short dry gear-engagement click, approximately 0.10 seconds. Quieter and lighter than the main press impact, slightly distinct from a button click. Isolated one-shot, no long motor run, music, voice, ambience bed, long reverberation or clipping. Immediate readable onset, compact controlled natural tail.

## 34｜净盈利短收尾 S07

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：30 刻度接入音，只参考克制音色。
- 目标时长：0.25–0.40 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_result-profit_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One short restrained positive workshop-completion chime, warm clean two-note resolution with subtle metal resonance, approximately 0.32 seconds. Precise modest satisfaction, not a casino fanfare, no coin cascade or big-win celebration. Isolated single UI effect, no music track, voice, ambience bed, long reverb or clipping. Immediate readable onset, compact controlled natural tail.

**使用限制：** 只用于净盈利，不是只要有返还就播放。

## 35｜无返还/净损失中性收尾 S08

- [ ] 已生成
- [ ] 已剪辑、试听并导出
- 参考音：29 按钮音，只参考干燥质感，不复制含义。
- 目标时长：0.08–0.15 秒。
- 待检查目录：`review/`
- 交付文件名：`fm_sfx_result-neutral_a_v001.wav`
- 审核后目录：`approved/audio/`

**直接复制：**

> One neutral dry mechanical completion tick for a small precision workshop interface, approximately 0.12 seconds. Calm unambiguous ending, no rising anticipation, no failure buzzer, no celebratory notes, no near-success implication. Isolated one-shot, no music, voice, ambience bed, long reverberation or clipping. Immediate readable onset, compact controlled natural tail.

---

# 第八组：字体与最后交付

## 36｜准备字体，不是文生图任务

- [ ] 已从可信发行来源下载可商用中文字体
- [ ] 已保留实际字体文件的许可
- [ ] 已检查简体中文、英文、数字和符号覆盖
- [ ] 已记录字体版本和发行来源
- 准备什么：一套中文字体；可从思源黑体/Noto Sans CJK 等方向选择，但以实际文件许可为准。
- 提示词：不适用，不让 AI 画字。
- 待检查目录：`review/fonts/`
- 文件名：保留发行方原始字体文件名及原始扩展名，不把字体改名成 PNG，不编造版本名。
- 许可文件名：保留下载包中的原名，如 `LICENSE` 或 `OFL.txt`；不要自己编写授权书。
- 审核后目录：`approved/fonts/<实际字体家族及版本>/`
- 检查内容：`0–9`、小数点、千位分隔符、正负号、`×`、`=`、`/`、实际币种符号和所有上线文案；不只检查当前示例。

---

## 全部做完后的勾选清单

- [ ] 01 的唯一风格参考已放在 `references/`。
- [ ] 22 的母版已保存在 `source/generations/`，原始生成文件未丢失。
- [ ] `review/` 中有 24 个最终图形来源：3 背景 + 1 外框 + 4 材料 + 1 印记 + 2 纹理 + 6 UI + 6 图标 + 1 封面。
- [ ] 需要透明的文件真实带 Alpha，不含白底或伪棋盘格；钢环孔和模具开口也透明。
- [ ] 文件实际尺寸与文件名一致，标准画布没有被紧裁。
- [ ] 四材料都为正面、左上光，灰度下也能用形状区分。
- [ ] 背景三层尺寸和原点相同，叠加不重复，中心安静。
- [ ] UI 六底板没有文字、数字、图标；边框可被清理为可拉伸结构。
- [ ] 图标颜色和线宽一致，缩到 20–24 屏幕像素仍清楚。
- [ ] 若做声音，`review/` 中有 9 条独立 WAV，已经剪辑试听；没有把整局打包成一条。
- [ ] 字体和许可齐全；图片/音频生成来源及商用条件有记录。
- [ ] 未审核内容仍留在 `review/`，没有直接当作上线资源。

**不额外生成：** 25 张格子、0–4 刻度贴图、材料命中/移除状态图、四状态按钮、三轮换场景、公式数字图片、五种整屏面板、四张结算背景、Wild、额外奖励道具、AI 图集或整屏庆祝影片。

**现在的第一个动作：打开文生图工具，执行 01；选好参考后执行 02，再执行 03。后续按编号逐项勾选即可。**
