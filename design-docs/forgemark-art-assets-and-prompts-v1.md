# 铸痕工坊 · AI 美术素材清单与提示词规范 v1.0

- 配套策划：`forgemark-workshop-design-v1.md`。
- 编制日期：2026-11-23。
- 用途：文生图制作、后处理交付、后续目录整理和客户端引用。
- 本文是制作规范，不代表素材已经生成、授权已核验或通过引擎验收。
- 默认制作 2D 游戏素材，移动端竖屏优先，桌面端居中盘面；不扩展角色、商店、任务、买奖励或其他玩法。
- 本文建议采用“精密机械工坊、克制的半写实手绘 2.5D”美术方向。这是对原策划的美术补充，不是原策划已锁定的风格；先按第 12 节做小批样张，确认后再批量制作。

---

## 1. 先执行这几个结论

1. **默认一张图只生成一个资产。** 四种材料分别生成四张，不让 AI 把全部物件排在一张透明 PNG 上。
2. **不让 AI 直接生成可上线图集、精确 5×5 网格、数字、中文按钮、公式或动画帧表。** 这些需要准确坐标、文字和状态，由程序或矢量制作完成。
3. **背景和可交互物件分离。** 背景里不能画出可玩的模具、四种材料、按钮或数字，否则会出现重复元素和无法移动的假盘面。
4. **先做风格参考，再做母版，再做裁切/抠图/缩放。** 提示词写了透明、尺寸或角度，不等于模型一定做到。
5. **上线文件统一使用规范名，AI 原始结果另存。** 不把低清失败图、参考拼图或带背景原图混进开发目录。
6. **保留 24 个静态图形来源的预算口径。** 背景 3 + 模具 1 + 材料 4 + 入口印记 1 + 特效纹理 2 + 共享 UI 来源 6 + 图标 6 + 封面 1。
7. **24 个来源不等于 24 次生成，也不等于 24 个网络请求。** 背景分层可能来自同一张场景母版，重试和参考图不计生产来源；开发图集由工具统一打包。

### 1.1 到底哪些放一张图，哪些拆开

| 类型 | AI 阶段 | 开发交付 | 原因 |
| --- | --- | --- | --- |
| 铜片、钢环、棱晶、金印 | 每次只做一种、一个主体 | 四张独立透明 PNG | 独立缩放、命中、移除，避免风格和占比失控 |
| 入口印记 | 单张单图形 | 一张透明 PNG | 入口与材料不同，不混入四种材料 |
| 工坊场景 | 先做一张无 UI 的完整场景母版 | 远/中/近三层，共用同一画布和坐标 | 各层独立随机生成很难对齐，应编辑/拆层并补全遮挡区域 |
| 模具 | 单独生成外框 | 一张透明外框；内部底色和网格程序绘制 | 避免 AI 画错格数，也避免刻度烘焙 |
| UI 六个装饰来源 | 六张分别制作 | 六张透明图；可拉伸部分清理后九宫格使用 | 保持面板可伸缩，文字独立 |
| 六个功能图标 | 可以画风格参考合集 | 最终每个独立 SVG 或透明 PNG | 参考合集不能直接代替开发素材 |
| 火花、碎片 | 每张一个纹理原语 | 两张独立透明 PNG | 数量、方向、颜色、生命周期交给发射器 |
| 动画、命中、禁用状态 | 不生成多帧拼图 | 代码动画、遮罩、调色和状态控制 | 保持因果和尺寸稳定 |
| 最终图集 | 不交给 AI | 用图集打包器生成 PNG/WebP 与坐标数据 | 自动留边、消除串色、支持稳定寻址 |

---

## 2. 统一美术圣经

### 2.1 风格与材质

**关键词：** 小型精密铸造工坊、深色铸铁、拉丝金属、低饱和铜、克制黄铜、青绿色冷光、温暖炉光、干净轮廓、少量真实磨损。

- 画法：半写实手绘 2.5D 游戏资产；有金属厚度，但不是照片，也不是过度写实的电影渲染。
- 气质：安静、精密、可靠、有手作温度；不做混乱废土、恐怖场景、霓虹赌场或满屏金光。
- 细节：大形优先，细节少而准；缩到手机实际大小仍能辨认。
- 背景对比度低于模具；模具对比度低于材料轮廓和当前支付信息。
- 金属的磨损只出现在边角，不能被噪点、锈斑和裂痕覆盖。
- 不加入人物、动物、武器、钱币雨、钻石堆或无关机器。

### 2.2 色板参考

以下十六进制值是后处理与 UI 的校色目标，不指望模型精确输出数值。

| 用途 | 主色 | 处理要求 |
| --- | --- | --- |
| 深背景 | `#11191D` | 保留暗部层次，不能一片纯黑 |
| 模具铸铁 | `#293238` | 冷灰、中低明度 |
| 结构高光 | `#697980` | 克制，不做镜面白斑 |
| 铜片 A | `#B66C43` | 红铜，不偏黄金 |
| 钢环 B | `#8BA7B5` | 蓝灰，哑光，不能像银币 |
| 棱晶 C | `#35B8A3` | 青绿，不能变蓝宝石或圆形水晶 |
| 金印 D | `#D3AE58` | 浅金，形状必须为菱形 |
| 中性正文 | `#E9E4D6` | 由字体渲染，不画进图片 |
| 炉光/短接触光 | `#F4BE74` | 局部、小面积，不能遮数字 |

### 2.3 视角与光线

- 背景：正对工作台，轻微俯视的室内场景，可有自然透视；中心安静。
- 模具与四材料：**严格正交正面图，不是等距视角，不是斜着拍的物品。** 只靠内倒角、表面明暗表达厚度。
- 材料主体平面平行于画布；铜片正方、钢环正圆、棱晶正三角、金印正菱形。
- 统一左上柔和主光、右下弱暗面；允许很弱的暖色边缘反射。
- 单物件不能带地面、投影平面、环境反射图或镜头景深。
- 物件可以有贴近自身边缘的少量环境遮蔽，不要烘焙大幅外投影。外投影由程序统一生成。

### 2.4 形状识别锁定

| ID | 固定形状 | 内部纹样 | 明确禁止 |
| --- | --- | --- | --- |
| M01 | 轴对齐正方形铜片，轻微倒角 | 三条短平行凹槽 | 圆币、六边形、刻字、菱形姿态 |
| M02 | 正圆钢环，中心通孔 | 四个均匀短切口，不破坏圆环主形 | 实心圆、齿轮、多层同心环 |
| M03 | 尖端朝上的正三角青绿棱晶 | 一个清晰内三角切面 | 五角宝石、六角水晶、冰柱、斜放三角 |
| M04 | 竖直长轴的对称菱形金属印块 | 一个同心内菱形凹槽 | 方形金币、皇冠、字母、星形 |
| M05 | 圆形压印符号 | 中心一条短竖槽，下端一条短横槽，外围断开圆环 | 第五种支付材料、字母 S、数字 3、奖励文案 |

原策划允许字母/纹样识别，本规范选用纹样。A/B/C/D/S 只做逻辑 ID；确有教学需要时由程序加字母，不依赖 AI 写字。

---

## 3. 尺寸、透明底和坐标规范

### 3.1 设计与交付尺度

- 首轮布局检查：手机 `390×844`，桌面 `1440×900`，单位为 CSS 像素。
- 图片标注的尺寸均为实际像素，不是 CSS 尺寸；UI 通常按约 2× 分辨率准备，但最终以内存与显示效果为准。
- 移动端建议盘面外框显示约 `350×350` CSS 像素，每格有效宽度约 `58–62` CSS 像素。此为美术检查基线，不是已实现布局。
- 材料运行时一般显示约 `44–52` CSS 像素，256 方图足够覆盖该基线的高像素密度设备；桌面大幅放大时另行检查。
- 背景 2048 方图是源规格，不要求手机同时解码全部超大纹理。发布可按设备派生尺寸或格式，保留源图。

### 3.2 尺寸总表

| 类型 | 推荐生成母版 | 最终源交付 | 背景/Alpha | 主体约束 |
| --- | --- | --- | --- | --- |
| 背景母版 | `2048×2048`，不支持时最大方图 | 远/中/近各 `2048×2048` | 远层不透明；中/近层 RGBA | 三层同原点，严禁独立裁紧 |
| 模具外框 | `1024×1024` 或更大方图 | `1024×1024` | RGBA，内开口透明 | 外轮廓在 `[32,992)` 内，开口 `[96,928)` |
| 四材料 | `1024×1024` 方图 | 各 `256×256` | RGBA | 可见主体最长边约 192px，几何中心 `(128,128)` |
| 入口印记 | `1024×1024` 方图 | `128×128` | RGBA | 主体最长边约 88px，中心 `(64,64)` |
| 接触亮形、碎片 | `1024×1024` 方图 | 各 `256×256` | RGBA | 中心锚点，纹理不要碰边 |
| UI 按钮 | 支持矩形时 `1024×512` | `512×256` | RGBA | 无字，九宫格边距后处理锁定 |
| 共享面板 | `1024×1024` | `512×512` | RGBA | 中心平整，边框不超过 32px |
| HUD/公式/结果底板 | 支持矩形时 `1536×512` | 各 `768×256` | RGBA | 平整可拉伸中段，边框不超过 32px |
| 轮次槽底板 | 支持矩形时 `1536×512` | `768×256` | RGBA | 不画三格或数字，节点程序放置 |
| 六个图标 | AI 参考用 `1024×1024` | SVG 优先；PNG 备选 `128×128` | 透明 | PNG 安全边 20px；SVG 统一 viewBox |
| 封面 | `2048×2048` 或最大方图 | `2048×2048` | 不透明 RGB | 主体在中央 80%，不画品牌文字 |

若模型只支持有限分辨率，选最接近的比例与最大合适尺寸；输出后等比缩放、扩画或裁切到最终尺寸。禁止强行非等比拉伸材料。不把低分辨率放大后的文件称为新增真实细节的高分辨率原画。

### 3.3 模具网格的精确规则

以下是**后处理和程序坐标**，不是要求文生图精确画出：

- 模具画布 `1024×1024`；坐标从左上角开始。
- 透明内开口：左上 `(96,96)`，右下 `(928,928)`，范围为 `[96,928)×[96,928)`。
- 程序网格区域：左上 `(112,112)`，尺寸 `800×800`；5 列、5 行，每格节距 `160`。
- 列/行中心分别为 `192、352、512、672、832`。
- 开口周边有 16px 缓冲，不让装饰螺钉和机械凸起侵入网格。
- 网格线、单格背板、裁切遮罩、数字 1–4、短槽线、命中高亮全部程序化。
- 单格刻度可以放在左上小角标区；材料居中，不能把刻度角标印在材料上。
- 模具外框中心轴心为 `(512,512)`；运行时中心锚点。外框透明区域不应拦截输入，命中区域由程序指定。

先把 AI 生成外框清理、校正到这个模板，再导出。发现不对称或开口歪斜时不以“提示词已经写了”为验收理由。

### 3.4 透明 PNG 的硬要求

- PNG 格式不自动代表透明：背景、封面可不透明；独立物件必须具有真实 Alpha 通道。
- 棋盘格图案不等于透明，白色背景也不等于透明。
- 优先使用支持真实透明输出的模式；生成器不支持时，在纯色底生成后抠图。纯色底与主体颜色应有足够区分。
- 钢环中心孔必须透明；模具内开口必须透明；不留下白底、灰底或伪棋盘格。
- 源交付采用 sRGB、8-bit RGBA PNG、straight/unassociated Alpha；引擎是否预乘由导入管线统一决定，不重复预乘。
- 在黑、白、洋红底上检查半透明边缘，不能出现明显白边、黑边、背景残留或发光方框。
- 发光外围自然衰减到 Alpha 0；不能画一整块半透明灰雾。
- 不自行 trim 掉标准画布。若未来图集打包器执行 trim，必须保留原尺寸和偏移元数据。

### 3.5 背景与双端安全区

- 三层共享 `2048×2048` 画布，不分别裁到各自物件边界。
- 中央约 `[500,1548]×[500,1548]` 只放低对比的暗墙面/台面，没有亮灯、机器轮廓或必须看到的物体。
- 炉口和工具集中在左右外围，顶部不放强对比吊灯，底部不画按钮形物体。
- 方形背景不能保证同时在所有横竖屏全景可见。手机、桌面的裁切属于布局问题，不把关键叙事放在边缘。
- 手机采用背景覆盖裁切，保证模具和文字位于独立 UI 安全区；桌面可居中放方形场景并用纯色/渐变扩展两侧。
- 若桌面必须全幅铺景，后续从同一母版扩画横版作为派生资产，不直接拉伸方图；不计作 v1 额外原创场景。
- 默认不开视差。需要视差时移动幅度应小，并补画遮挡区域、预留超出可视区域的边缘，避免露洞。

---

## 4. 文件命名规则：以后就按这个交给开发

### 4.1 PNG 命名模板

`fm_<category>_<subject>_<variant>_<width>x<height>_v<revision>.png`

例：`fm_mat_copper-plate_base_256x256_v001.png`

| 字段 | 规范 |
| --- | --- |
| `fm` | 项目固定前缀，不更换 |
| `category` | `bg`、`board`、`mat`、`mark`、`fx`、`ui`、`icon`、`cover` |
| `subject` | 全小写英文；多个词用连字符 `-`，不得用下划线拆开 |
| `variant` | 初版固定使用清单中的 `far/mid/near/base` 等值；不能随意写 `final/new/ok` |
| `widthxheight` | 最终文件实际像素尺寸，使用小写 `x` |
| `revision` | 三位递增数字，`v001` 起；同一资产修改后用 `v002`，禁止覆盖旧版本 |

- 禁止空格、中文文件名、括号、`最终版`、`副本`、`final2` 和生成器自动长串文件名出现在交付目录。
- 不在文件名里编码价格、返还值、轮次、格位坐标或运行时高亮状态。
- 尺寸表示该文件真实像素，不是生成时口头要求的尺寸。2048 母版不能直接命名成 256。
- 逻辑资产 ID 不含尺寸和版本，例如 `fm.mat.copper-plate.base`；开发通过资源表映射到当前审核通过文件。
- 新版不自动上线。不能只按文件名字典序选最新，要以清单中明确标注的已通过版本为准。

### 4.2 SVG、参考与派生文件

- SVG 不写像素尺寸：`fm_icon_rules_base_v001.svg`；推荐统一 `viewBox="0 0 128 128"`。
- 若图标使用 SVG，其 PNG 预览只是派生文件，不算新的原创来源；最终任选一种作为运行时主引用。
- 参考图放 `references/`，如 `fm_ref_style-workshop_v001.png`，不得混入生产目录。
- 生成母版和原始结果保留在 `source/`；它们是过程文件，可以保留生成器原文件名，并用同名说明记录对应资产 ID。
- 发布 WebP 等派生图可沿用 PNG 名称仅替换扩展名，放 `runtime/`，不能伪装成 PNG。
- 不支持透明的生成结果可保留在 `source/`，但未抠图前不能进入 `approved/`。

---

## 5. 完整静态素材清单：24 个来源

说明：下列文件名均为 v001 交付目标。P0 为核心原型美术，P1 为氛围和装饰，P2 为发行封面。P0 中的矢量控件可先由程序占位，不必为了等待 AI 结果阻塞原型。

| 序号 | 策划对应 | 交付文件名 | 尺寸/通道 | 优先级 | 使用与制作方法 |
| --- | --- | --- | --- | --- | --- |
| 01 | B01 远层 | `fm_bg_workshop_far_2048x2048_v001.png` | 2048²，不透明 | P1 | 暗墙、远处炉光；场景母版拆层后补全 |
| 02 | B01 中层 | `fm_bg_workshop_mid_2048x2048_v001.png` | 2048²，RGBA | P1 | 左右工具与管线，中心透明 |
| 03 | B01 近层 | `fm_bg_workshop_near_2048x2048_v001.png` | 2048²，RGBA | P1 | 边缘台面和少量前景结构，中心透明 |
| 04 | B02 | `fm_board_mold-frame_base_1024x1024_v001.png` | 1024²，RGBA | P0 | 只有正交外框，中心透明，网格程序绘制 |
| 05 | M01 / A | `fm_mat_copper-plate_base_256x256_v001.png` | 256²，RGBA | P0 | 正方铜片，三短槽 |
| 06 | M02 / B | `fm_mat_steel-ring_base_256x256_v001.png` | 256²，RGBA | P0 | 蓝灰圆环，中心透明 |
| 07 | M03 / C | `fm_mat_teal-prism_base_256x256_v001.png` | 256²，RGBA | P0 | 尖端向上青绿正三角 |
| 08 | M04 / D | `fm_mat_gold-seal_base_256x256_v001.png` | 256²，RGBA | P0 | 竖轴金色菱形，内菱形槽 |
| 09 | M05 / S | `fm_mark_entry-stamp_base_128x128_v001.png` | 128²，RGBA | P0 | 几何入口印记；不当奖励符号 |
| 10 | V04 | `fm_fx_press-flash_base_256x256_v001.png` | 256²，RGBA | P0 | 一张中性接触亮形，不含材料 |
| 11 | V04/V05 | `fm_fx_metal-chip_base_256x256_v001.png` | 256²，RGBA | P0 | 一枚灰白碎片；程序调色复用 |
| 12 | U01 来源 | `fm_ui_primary-button_base_512x256_v001.png` | 512×256，RGBA | P0 | 无字主按钮底板 |
| 13 | U05 共享来源 | `fm_ui_shared-panel_base_512x512_v001.png` | 512²，RGBA | P0 | 规则、设置、异常等共用面板 |
| 14 | HUD 共享来源 | `fm_ui_hud-plate_base_768x256_v001.png` | 768×256，RGBA | P0 | 成本、累计等通用底板 |
| 15 | U02 来源 | `fm_ui_round-rail_base_768x256_v001.png` | 768×256，RGBA | P0 | 轮次组件装饰底板，无三格和数字 |
| 16 | U03 来源 | `fm_ui_formula-plate_base_768x256_v001.png` | 768×256，RGBA | P0 | 本次计算式底板，无公式 |
| 17 | U04 来源 | `fm_ui_result-plate_base_768x256_v001.png` | 768×256，RGBA | P0 | 中性结果底板，无奖杯、金币、数值 |
| 18 | U05 图标 | `fm_icon_rules_base_128x128_v001.png` | 128²，RGBA/SVG | P0 | 单页说明纸 + 三横线 |
| 19 | U05 图标 | `fm_icon_sound_base_128x128_v001.png` | 128²，RGBA/SVG | P0 | 扬声器 + 两条声波 |
| 20 | U05 图标 | `fm_icon_turbo_base_128x128_v001.png` | 128²，RGBA/SVG | P0 | 两个向右简洁箭头 |
| 21 | U05 图标 | `fm_icon_reduced-motion_base_128x128_v001.png` | 128²，RGBA/SVG | P0 | 短运动线 + 斜杠 |
| 22 | U05 图标 | `fm_icon_close_base_128x128_v001.png` | 128²，RGBA/SVG | P0 | 等长对角线构成 X |
| 23 | U05 图标 | `fm_icon_replay_base_128x128_v001.png` | 128²，RGBA/SVG | P0 | 单个逆时针回转箭头 |
| 24 | P01 | `fm_cover_workshop-keyart_base_2048x2048_v001.png` | 2048²，不透明 | P2 | 独立封面，不作为游戏背景 |

**对原策划的明确化：** 原表只列“共享 UI 来源 6”而未逐个命名，本文细化为按钮、共享面板、HUD、轮次底板、公式底板、结果底板。背景远层改为不透明是合成需求：完整铺底，避免整个场景穿透到页面底色；其余两层仍透明。不新增玩法资产。

---

## 6. 提示词如何拼装

### 6.1 使用公式

每个最终请求使用：

**对应类别公共前缀 + 该资产专用提示词 + 对应输出要求 + 通用负面词。**

- 四部分都要提交，不能只复制素材名称。
- 支持独立 negative prompt 的工具，把负面词放负面栏；不支持则在正文末尾写“禁止：……”的中文或英文要求。
- 参数栏另设比例/分辨率/透明模式，不能只在正文写尺寸。
- 模型支持参考图时，附已审核的风格图。对材料以已通过的铜片作为材质/光线参考，但不能要求其他材料复制铜片形状。
- 同一 seed 不保证跨提示词主体一致，也不保证跨模型复现；记录 seed 仅为辅助。
- 英文提示词用于减少语义歧义，不是保证模型一定更听话。可以整段输入中文模型，但不得删掉形状和排除要求。

### 6.2 风格基准图提示词：只做参考，不计 24 个来源

输出：方图，建议 1536 或 2048；文件放 `references/`。

> Art direction reference for FORGEMARK, a small precision metal casting workshop for a mobile 2D game. Restrained semi-realistic hand-painted 2.5D art, dark cast iron, brushed steel, muted red copper, pale brass and small teal accents. Warm furnace light at the side, soft cool fill, clean readable silhouettes, sparse purposeful wear, calm crafted atmosphere. Show a quiet front-facing workbench area with clear dark central space, a few organized peripheral tools, no playable game board. Prioritize large readable shapes over tiny surface noise. No interface, no text, no numbers, no logo, no characters, no coin piles, no dramatic explosion.

注意：这张参考图不是生产背景；批准后用于约束后续材料、外框和场景的色彩与材质。

### 6.3 场景公共前缀 BG

> Production environment art for a mobile 2D precision casting game. Restrained semi-realistic hand-painted industrial workshop, dark cast iron, brushed metal, muted copper and pale brass. Warm light from the side, cool dark ambient fill. Front-facing workbench environment with gentle natural perspective. Quiet low-contrast center reserved for a separate gameplay board. Peripheral detail only. Match the approved workshop style reference.

### 6.4 物件公共前缀 OBJ

> One isolated production sprite for a mobile 2D precision casting game. Restrained semi-realistic hand-painted 2.5D metal rendering, crisp readable silhouette, broad controlled highlights, sparse wear. Strict orthographic front view, the main face parallel to the image plane, no perspective tilt, no isometric view. Soft upper-left light, subtle lower-right shading, no external cast shadow. Exactly one centered object, fully visible, generous empty padding. Match the approved workshop style reference.

物件输出要求 OBJ-OUT：

> Square canvas. Real transparent background with an alpha channel if supported, not a painted checkerboard. No floor, no backdrop, no surrounding objects. Keep the geometric center at the exact canvas center. Do not crop any part of the silhouette. Render large and clean for later downsampling.

### 6.5 UI 公共前缀 UI

> One isolated blank interface plate for a precision casting mobile game. Restrained hand-painted 2.5D industrial UI, dark blue-gray cast iron, fine pale brass rim, subtle upper-left light, clean symmetric construction. Straight-on orthographic view. Flat quiet central fill suitable for readable live text. Minimal edge wear, no baked outer shadow. Designed for later nine-slice cleanup and resizing. Match the approved workshop style reference.

UI 输出要求 UI-OUT：

> Transparent exterior, complete uncropped outline, no text, no numbers, no icon, no decorative object in the central content area. Keep all ornamental detail near the outer rim. Straight uninterrupted edge middles, simple corners, uniform border width. No internal gradients or scratches that would visibly break when stretched.

### 6.6 图标公共前缀 ICON

> One minimal functional UI icon for a precision casting mobile game. Flat pale ivory monochrome line art, transparent background, consistent rounded line caps and joins, consistent stroke weight. No 3D shading, no metallic texture, no button plate, no text, no numbers. Centered simple geometry, generous padding, readable at 20 to 24 CSS pixels. Use a consistent 128 by 128 design grid, intended final stroke width approximately 8 units.

图标建议根据 AI 参考手工矢量重绘；文生图无法保证六张线宽和几何精度完全相同。最终 SVG 应使用路径/基础几何，不嵌位图、不带脚本、不依赖外链字体。

### 6.7 通用负面词 NEG

> text, letters, numbers, typography, watermark, signature, brand logo, interface screenshot, multiple unrelated objects, contact sheet, sprite sheet, grid layout, duplicate objects, cropped edges, inconsistent perspective, isometric item view, photorealistic photography, plastic toy, heavy rust, noisy scratches, oversaturated neon, excessive bloom, lens flare, depth of field, blurry edges, background shadow plane, fake checkerboard transparency, baked drop shadow

- 对背景不使用 `multiple unrelated objects` 排除组织有序的外围工具，但仍禁无关物件和 UI。
- 对封面允许有组织的多物件构图，去掉 `multiple unrelated objects` 与 `duplicate objects` 中对设计内重复材料的限制；保留禁字、禁 UI、禁水印。
- 对需要圆孔、开口或发光的对象，补充相应专用约束，不只依赖通用负面词。

---

## 7. 场景、模具、四材料和入口印记专用提示词

以下每项的“拼装”指第 6 节的公共段；专用提示词与输出尺寸共同约束后处理目标。

### 7.1 B01 工坊场景：先母版、后拆层

**第一步：完整母版。** 拼装 `BG + 下文 + 背景版 NEG`；方形 2048 母版，源图留存。

> A compact orderly precision casting workshop interior, looking directly toward a workbench. Dark masonry and metal wall in the far background, a small warm furnace opening confined to the far left edge, a few orderly tools and pipes confined to the outer sides, subtle workbench edges near the bottom corners. The central half of the image is an unobtrusive dark low-detail work area with no object silhouettes or bright lights. No central machine, no playable mold, no square game grid, no material tokens, no control panel, no UI. Soft atmospheric depth without fog covering the center. Balanced composition suitable for both portrait cropping and a centered desktop presentation.

**第二步：以同一母版编辑/拆层。** 不把下面三个提示词当成三次互不相干的随机文生图。使用图像编辑、选区、补画和分层工具；没有编辑能力时先交付母版，分层明确标记待处理。

| 最终层 | 编辑指令 | 合成要求 |
| --- | --- | --- |
| far | `Keep only the distant workshop wall, distant structural surfaces and the small side furnace light. Remove all midground tools and foreground bench edges. Reconstruct the wall and floor surfaces behind removed objects in the same lighting and perspective. Keep the exact original canvas and camera.` | 完整不透明底层，补全被遮挡处 |
| mid | `Extract only the organized side tools, side pipes and midground structural objects from this exact image. Preserve their original positions, scale and lighting. Remove the distant wall and all foreground bench edges. Make all remaining space truly transparent, especially the central gameplay area. Do not recompose.` | RGBA，全画布不变，不重复远层炉口 |
| near | `Extract only the peripheral foreground workbench edges and a few corner brackets from this exact image. Preserve exact original positions and scale. Remove every other element. The central gameplay area and upper area must be fully transparent. No tools lying in the center. Do not recompose.` | RGBA，只保留角部近景 |

合成后应接近原母版，不能炉口双重发光、管线重复、物体阴影凭空留在错误层。远层上的静态接触阴影可保留；若要移动中近层，相关阴影也必须拆出或重做。

### 7.2 B02 模具外框

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `1024×1024`。

> A single perfectly square precision casting mold outer frame, front-facing and axis-aligned. Dark blue-gray cast iron with a restrained thin pale brass inner rim, four small recessed corner fasteners, broad clean structural surfaces, symmetric construction. A large empty square opening in the middle with true transparency, no bottom panel inside the opening. No internal cells, no grid lines, no slots, no symbols, no counters, no material pieces. No mechanical arm or protrusion over the opening. Keep every decoration confined to the square rim. The frame should feel solid but visually subordinate to the material sprites.

额外禁止：`built-in board, checkerboard, 25 cells, engraved numerals, press arm, diagonal frame, solid center`。

后处理：按第 3.3 节模板校正透视、对称、开口与螺钉区域；不能直接相信 AI 的 96px 开口边界。

### 7.3 M01 铜片 A

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `256×256`。

> Exactly one red-copper material token. A centered axis-aligned square plate with slightly beveled corners, unmistakably square, equal width and height. Muted reddish copper color, broad brushed face, restrained edge thickness suggested only by internal shading. Three short parallel recessed grooves centered on the face, simple and legible. No letter, no number, no border frame. The square is upright, not rotated into a diamond. Strong silhouette readable at 48 CSS pixels.

额外禁止：`coin, circular token, hexagon, diamond orientation, embossed letters, golden yellow copper`。

### 7.4 M02 钢环 B

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `256×256`。

> Exactly one blue-gray steel material token. A perfectly circular thick steel ring with one large clean circular hole at the center, both the outside background and the inner hole fully transparent. The ring band is approximately one fifth of the outer diameter in radial thickness. Four small evenly spaced recessed notches on the band, not gear teeth. Cool brushed blue-gray metal, restrained highlights, complete circular silhouette, no perspective ellipse. Match the copper token's scale, rendering and light direction, but preserve this circular ring shape.

额外禁止：`solid disk, coin, gear, cog teeth, ellipse, filled hole, gemstone, multiple rings`。

### 7.5 M03 棱晶 C

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `256×256`。

> Exactly one teal-green prism material token with an equilateral triangle silhouette, single apex pointing straight upward and horizontal bottom edge. Clean three-sided shape, shallow cut facets, one clearly readable inset triangular facet on the face. Predominantly opaque polished teal mineral, only subtle internal luminosity, no surrounding glow cloud. Front face parallel to the canvas. Broad restrained highlights, similar visual weight and lighting to the approved metal tokens. No support base, no pedestal.

额外禁止：`hexagonal crystal, diamond gem, blue sapphire, crystal cluster, ice shard, inverted triangle, transparent entire body, neon aura`。

三角形按外接包围盒居中处理；光学重心可后处理微调，但保持统一画布与锚点，不靠随意裁边对齐。

### 7.6 M04 金印 D

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `256×256`。

> Exactly one pale-gold metal seal token with a symmetric rhombus silhouette. The long axis is vertical, with one clear top tip, one bottom tip, one left tip and one right tip. A single inset concentric rhombus groove on the front face. Pale warm gold, restrained brushed finish, beveled edges, no handle, no pedestal, no writing. It is a solid diamond-shaped metal block, not a jewel and not a square plate rotated casually. Front-facing, complete silhouette, comparable visual weight to the other material tokens.

额外禁止：`coin, crown, star, letter, number, gemstone, stamp handle, square silhouette, overflowing glow`。

### 7.7 M05 入口印记 S

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `128×128`。

> Exactly one compact abstract workshop entry-stamp emblem, designed as a flat readable press mark rather than a collectible material. A simple dark neutral metal symbol with a thin warm ivory highlight: a broken circular outer ring surrounding one short vertical recessed stroke meeting one short lower horizontal recessed stroke. Clear uncluttered geometry, frontal orientation, no raised handle. No letters, no numeral, no three-round text, no bonus wording. Much simpler and less colorful than the four payable material tokens.

原策划中的 S 是程序符号名，不要求画出英文字母 S。印记按压状态复用同一图变换，不生成第二张状态图。

---

## 8. 特效、UI 六来源与六图标专用提示词

### 8.1 V04 接触亮形

不拼 OBJ，使用下列整段 + NEG；最终 `256×256`。

> One isolated neutral warm-white impact flash texture for a small precision metal press contact in a 2D mobile game. A compact soft central light with four very short tapered rays, subtle irregularity, soft alpha falloff to fully transparent edges. Small, controlled and readable, not a violent explosion. No metal object, no material token, no press machine, no smoke, no debris, no ring of text. Square canvas, true transparent alpha background, centered texture, generous fully transparent border. Suitable for runtime tinting and a brief additive or normal-blended flash after visual testing.

不得预制“整盘亮起”贴图；高亮范围由单格/集群遮罩限定。减弱动态时可完全取消此纹理，仍保留轮廓和公式。

### 8.2 V04/V05 金属碎片原语

拼装 `OBJ + 下文 + OBJ-OUT + NEG`；最终 `256×256`。

> Exactly one small neutral light-gray metal chip, a compact irregular quadrilateral shard with two or three broad readable facets. No sharp weapon-like silhouette, no long needle, no glowing trail. Matte steel-gray values suitable for runtime tinting into copper, steel, teal and pale gold. Clean isolated object, centered, no pile, no multiple particles. Fully transparent background, no cast shadow.

主体最长边建议约 144px，不画散落一堆。实际使用时大幅缩小、多实例随机旋转和程序调色，不做四套材质碎屑。

### 8.3 U01 主按钮底板

拼装 `UI + 下文 + UI-OUT + NEG`；最终 `512×256`，宽高比 `2:1`。

> One blank horizontal primary action button plate, rounded rectangular silhouette with restrained machined corners, dark cast-iron body and a fine muted copper rim. Broad empty central face, physically readable but not bulky. Simple symmetric outline, no mechanical lever, no central emblem. Continuous straight middle sections suitable for horizontal stretching. Neutral idle appearance, no glow implying a win. Button label will be rendered separately by code.

交付九宫格边距建议 `[left:48, top:48, right:48, bottom:48]` px。生成后清理四边，不能未经检查直接拉伸。按钮“启动/揭晓/等待/禁用”复用此图，程序调整位置、明度、标签与加载图形。

### 8.4 U05 共享面板

拼装 `UI + 下文 + UI-OUT + NEG`；最终 `512×512`。

> One blank square modular dialog panel skin, dark blue-gray interior fill with very subtle uniform texture and a thin pale brass rim. Simple symmetric corners, no rivets protruding into the content area. Completely empty center for long localized rules and settings. No title plaque, no close icon, no controls, no lines of fake text. Designed to expand into different portrait and landscape dialog sizes without visual seams.

九宫格边距建议四边各 32px。规则、设置、加载、错误、恢复回放五面板使用同一皮肤，不能再生成五张整屏界面。

### 8.5 HUD 通用底板

拼装 `UI + 下文 + UI-OUT + NEG`；最终 `768×256`，比例 `3:1`。

> One blank low-profile horizontal HUD information plate, dark cool metal face, very thin desaturated brass boundary, nearly flat clean central surface. Quiet secondary emphasis, no trophy decoration, no label, no currency sign, no value. Intended as a reusable backing for cost and accumulated return readouts, each laid out by code. Straight extensible middle and simple matching end caps.

九宫格边距建议四边各 32px。不能把成本和累计画成固定两列，实际文本区域由布局决定。

### 8.6 U02 轮次槽底板

拼装 `UI + 下文 + UI-OUT + NEG`；最终 `768×256`，比例 `3:1`。

> One blank horizontal mechanical rail backing for a three-round progress widget. Dark iron shallow recessed surface, simple pale brass end caps, very low ornamentation. The entire middle is empty and uninterrupted. Do not draw any progress nodes, tick marks, dividers, three compartments, digits or illuminated states. All three markers and their labels will be placed precisely by code above this backing.

九宫格边距建议四边各 32px。三节点、1/3 等文字和 0/1/2/3 进度状态全部程序生成。

### 8.7 U03 计算式底板

拼装 `UI + 下文 + UI-OUT + NEG`；最终 `768×256`，比例 `3:1`。

> One blank horizontal calculation readout plate, dark flat slate-metal surface, a thin restrained teal accent along the outer rim, calm precise workshop instrumentation design. Large empty central area for a dynamic formula. No engraved math, no plus sign, no multiplication sign, no equal sign, no digits, no example value. No wires or arrows inside the content area. Suitable for stretching and for use beside an expandable text breakdown.

九宫格边距建议四边各 32px；公式、连线、展开箭头与明细行不烘焙。

### 8.8 U04 结果底板

拼装 `UI + 下文 + UI-OUT + NEG`；最终 `768×256`，比例 `3:1`。

> One blank neutral final-result information plate for a precision workshop game. Dark blue-gray metal with a fine subdued pale brass rim, balanced quiet symmetry, wide clean central face. No celebratory decoration, no coins, no trophy, no crown, no confetti, no engraved values. It must look appropriate for zero return, a net loss, a net gain and a capped result, with all status meaning supplied separately by live text and small UI accents.

九宫格边距建议四边各 32px。四结果状态只改变程序文本、局部强调和颜色，不生成四张盈利气氛不同的底图。

### 8.9 六图标

每个单独使用 `ICON + 下表对应专用段 + NEG`；方图母版，最终 SVG 或 `128×128` PNG。不要在一次生产请求中生成六图标九宫格。

| 文件 subject | 专用提示词 |
| --- | --- |
| `rules` | `A single simple outline document page with one slightly folded upper corner and three short horizontal lines inside. No letter i, no question mark, no readable text. Exactly one document.` |
| `sound` | `A single simple speaker silhouette built from a small rectangle and a widening cone, with two clean sound-wave arcs to its right. No music note, no mute slash. This is the enabled sound base icon.` |
| `turbo` | `Exactly two matching right-pointing chevrons, horizontally aligned and evenly spaced. No enclosing circle, no lightning bolt, no third chevron.` |
| `reduced-motion` | `A compact group of three short parallel horizontal motion lines crossed by one clear diagonal slash. Simple recognizable reduced-motion setting symbol, no eye, no speed meter, no text.` |
| `close` | `Exactly two straight equal-length diagonal strokes crossing at the center to form a symmetric X. No circle, no box, no decorative corners.` |
| `replay` | `A single nearly circular counterclockwise return arrow with one clear arrowhead and one small open gap. No play triangle, no second arrow, no clock numerals.` |

静音状态可以由程序在扬声器图标上叠加同风格斜线；快速与减弱动态开关通过独立开关组件表示选中，不再生成六套开/关图片。图标图形约 20–24 CSS 像素，但触控区域建议至少 44×44 CSS 像素。

---

## 9. 封面与不该生成的素材

### 9.1 P01 方形封面

独立完整提示词，配封面版 NEG；最终 `2048×2048`，不透明。

> Square key art for an original precision casting workshop game, restrained semi-realistic hand-painted 2.5D rendering. A compact dark cast-iron mold frame as the central hero object, viewed nearly front-on, with a small deliberate arrangement of four clearly distinct material shapes: one red-copper square plate, one blue-gray circular steel ring, one upward teal triangle and one pale-gold vertical rhombus. A subtle physical impression of shallow marks in the mold, warm side furnace light, cool dark workshop ambience, precise crafted metal surfaces. Strong simple central silhouette, uncluttered background, main subject contained within the central 80 percent, modest dark breathing room near the top for a separately typeset title. No interface, no numeric grid, no money, no coins, no trophy, no text, no logo, no watermark, no characters. Match the approved production assets and do not redesign their silhouettes.

优先在核心资产通过后，以这些资产为参考制作封面；不要先用封面里夸张的样式反向重做游戏物件。平台提交尺寸尚未锁定，正式方/横/竖封面从母版另行裁切/扩画，不能把本文 2048 方图当作平台强制尺寸。

### 9.2 不列入文生图任务的内容

| 内容 | 正确实现 |
| --- | --- |
| 5×5 格线、25 个格位遮罩 | 程序几何/矢量，精确定位 |
| 位置刻度 0–4 | 0 不显示；1–4 用字体和短槽线，固定在模具坐标 |
| 四材料静态/命中/移除 | 一张静态图，命中描边、位移、透明度、碎屑由程序实现 |
| 连片形状 | 根据真实集群坐标实时生成，只连接上下左右邻接 |
| 刻度接入公式的连线 | 矢量/程序绘制，一次一个公式焦点 |
| 金额、公式、成本、轮次、按钮文字 | 实时文本，支持本地化与长数字 |
| 主按钮四状态 | 程序状态机，不生成四张带字按钮 |
| 轮次四进度状态 | 代码切换三个节点和当前轮标签 |
| 明细折叠/展开 | 代码布局；小箭头可用几何形状 |
| 结果四状态 | 共用底板，文本表达返还/净结果/封顶 |
| 规则、设置、加载、错误、恢复回放 | 共用面板 + 实时内容；加载不伪造进度 |
| 入口按压、下落、滚落、接触、结果强调 | 代码时间线，不请求不可控 AI 动画帧表 |
| 品牌字标与中文标题 | 使用已获许可字体排版，必要时手工设计矢量字标；本版不新增独立原画 |

禁止生成：Wild、四材料之外的新支付符号、免费轮奖励牌、购买奖励按钮、角色立绘、跨局等级条、任务道具。它们不在当前最小范围内。

---

## 10. 字体与声音：完整清单中的非图片部分

### 10.1 F01 字体

- 需要一套可商用中文字体，覆盖简体中文、拉丁字母、数字和必要标点；数字优先支持等宽数字特性。
- 候选方向可选思源黑体/Noto Sans CJK 等，但必须对实际下载文件、发行来源和许可逐一核对，不把名称本身当作授权证明。
- 符号至少覆盖 `0–9`、小数点、千位分隔符、正负号、`×`、`=`、`/` 及最终支持币种所需字符。
- 若字体缺字，明确配置回退字体并检查基线。不要把金额做成图片规避缺字。
- 字体源文件和许可放 `fonts/`；子集化应基于实际语言与平台需求，不能只打包当前示例文案。

### 10.2 S01–08，共 9 条源声音

声音不是文生图任务；此处补齐命名与需求，便于后续统一归档。建议 PCM WAV 母版，48 kHz / 24 bit；单声道足够的 one-shot 不必伪立体声。保留自然尾音，剪去多余头尾静音，检查削波，发布格式按客户端兼容性转码。

公共约束：`Isolated single game sound effect, no music, no voice, no ambience bed, no long reverb, no clipping. Immediate readable onset, compact controlled tail.`

| ID | 文件名 | 目标时长 | 专用音频提示词 |
| --- | --- | --- | --- |
| S01 | `fm_sfx_button-press_a_v001.wav` | 0.06–0.10s | `One small precise mechanical button click, dry tactile contact, short muted metallic detail, no springy cartoon sound.` |
| S02 | `fm_sfx_material-drop_a_v001.wav` | 0.12–0.20s | `One compact grouped landing of small metal components into a mold, two or three tightly clustered contacts perceived as one event, firm but quiet, no 25 separate hits.` |
| S03 | `fm_sfx_mark-connect_a_v001.wav` | 0.12–0.25s | `One restrained ascending mechanical tonal cue for existing mold marks connecting to a calculation, two or three soft notes, no jackpot flourish, no long pitch rise.` |
| S04-A | `fm_sfx_press-impact_a_v001.wav` | 0.12–0.22s | `Single compact precision metal press impact, immediate dry mechanical contact, firm short low-mid body, subtle metallic detail, fast decay, approximately 0.18 seconds.` |
| S04-B | `fm_sfx_press-impact_b_v001.wav` | 0.12–0.22s | `An alternate take of the same compact precision metal press impact, similar loudness and timbre, slightly different contact detail, no heavier dramatic slam.` |
| S05 | `fm_sfx_tumble-chip_a_v001.wav` | 0.10–0.18s | `One quiet small metal chip shuffle and short drop, thin dry details, low prominence, no shattering glass, no long rolling debris.` |
| S06 | `fm_sfx_round-shift_a_v001.wav` | 0.08–0.12s | `One subtle precision mechanism shifting into the next batch, short gear engagement click, quieter and lighter than the main press impact.` |
| S07 | `fm_sfx_result-profit_a_v001.wav` | 0.25–0.40s | `One short restrained positive workshop completion chime, warm clean two-note resolution with subtle metal resonance, no casino fanfare, no coin cascade.` |
| S08 | `fm_sfx_result-neutral_a_v001.wav` | 0.08–0.15s | `One neutral dry mechanical completion tick, calm unambiguous ending, no rising anticipation, no failure buzzer, no celebratory notes.` |

每条完整提示词为专用段 + 公共约束。生成工具未必精确控制亚秒时长，母版仍需剪辑与试听，不用改变播放速率硬凑时长。S07 只用于净盈利；无返还或有返还但净损失都使用中性收尾，不为“有金额”一律庆祝。

---

## 11. 目录与开发资源引用约定

以下是后续整理目标，不要求现在创建空目录或占位图片。

```text
forgemark-art/
  references/                       风格参考、参考拼图，不参与运行时
  source/
    generations/                    AI 原始输出与母版
    layered/                        PSD/KRA 等可编辑拆层工程（如有）
  review/                           待抠图、待校色、待审批，禁止上线引用
  approved/
    images/
      backgrounds/                  3 张背景层
      board/                        模具外框
      materials/                    4 张材料
      marks/                        入口印记
      effects/                      2 张特效原语
      ui/                           6 张 UI 底板
      icons/                        6 个图标，主格式统一
      cover/                        封面
    audio/                          9 条 WAV 母版
    fonts/                          字体与许可
  manifests/                        资产清单、授权登记、打包映射
  runtime/
    textures/                       由 approved 派生的发布图片
    atlases/                        自动打包的图集与坐标数据
    audio/                          发布转码
    fonts/                          审核过的字体子集
```

### 11.1 文件名到目录的机械映射

| category | `approved` 子目录 |
| --- | --- |
| `bg` | `images/backgrounds/` |
| `board` | `images/board/` |
| `mat` | `images/materials/` |
| `mark` | `images/marks/` |
| `fx` | `images/effects/` |
| `ui` | `images/ui/` |
| `icon` | `images/icons/` |
| `cover` | `images/cover/` |
| `sfx` | `audio/`，使用声音专用命名模板 |

你可以先把完成图统一放到 `review/`，后续根据文件名自动检查尺寸、透明度并分类。**能按名字分类不代表通过审核**：待审核文件不能自动提升到 `approved/`；缺少许可、Alpha 不合格或尺寸错误都应报告并保留原件，不擅自覆盖。

### 11.2 资源清单应记录的字段

后续开发时建立机器可读清单，不在本次文档任务中创建假资源文件。每条至少记录：

- `assetId`：稳定逻辑 ID，例如 `fm.mat.steel-ring.base`。
- `designId`：M02 等原策划编号；共享来源允许映射多个 UI 用途。
- `file`：当前获批文件相对路径。
- `revision`、`width`、`height`、`format`、`alpha`、`colorSpace`。
- `anchor`：图像位置锚点；物件和模具一般为 `[0.5,0.5]`，背景层为 `[0,0]`；材料可另记光学微调，不能隐式修改。
- `nineSlice`：仅 UI 底板填写四边像素边距。
- `status`：`generated / processing / review / approved / rejected`。
- `promptVersion`、`model`、`generationSettings`、`seed`（支持时）、`referenceFiles`。
- `licenseRecord`：生成服务商用条款记录、参考图来源、字体许可或音频许可。
- `sourceFile`、`notes`：原始来源和后处理说明。

逻辑符号映射固定为：A → `fm.mat.copper-plate.base`，B → `fm.mat.steel-ring.base`，C → `fm.mat.teal-prism.base`，D → `fm.mat.gold-seal.base`，S → `fm.mark.entry-stamp.base`。不从文件列表顺序推断材料含义。

### 11.3 图集与性能约定

- 先按独立源图生产，再由打包工具合图；保留图集坐标、原始尺寸和 trim 偏移。
- 背景、封面通常不与 UI 小图混装，避免为一个小按钮加载大背景。
- 图集边缘挤出/留边可从 2–4px 起步，最终按缩放过滤和 mipmap 测试调整，不当成所有设备的固定保证。
- 原图没有 bake 阴影的情况下，运行时统一阴影方向与强度；需要遮罩的特效不越过盘面。
- 不预先承诺 atlas 页数或上线请求数，以实际打包结果为准。
- 2048² RGBA8 单张解码约 16 MiB，三层约 48 MiB，尚不含 mipmap、复制和其他资源；压缩后的文件体积不是解码/GPU 占用。
- 手机可派生 1024 背景或按需加载；封面不参与每局运行资源，隐藏页面不提前加载全部发行图。

---

## 12. 制作批次：按这个顺序生成，避免浪费

### 批次 A：先锁风格，少量投入

1. 生成 2–4 张风格参考，挑 1 张，明确唯一参考版本。
2. 生成铜片 A 与模具外框各 1 个候选，不急着全量导出。
3. 把铜片缩到约 48 CSS 像素、模具缩到约 350 CSS 像素，检查是否清楚、颜色是否克制、外框是否抢戏。
4. 背景参考与铜片/模具放一起检查。若不像同一套游戏，先修方向，不靠后续“加特效”掩盖。

### 批次 B：完成核心 P0

1. 以已批准铜片为材质和光线参考，分别做钢环、棱晶、金印。
2. 四种材料按统一 256 画布、统一大致占比导出，放到临时 5×5 布局中比较；不让高价值金印大一圈。
3. 生产入口印记、两张特效原语。
4. 做六个 UI 来源；图标优先直接矢量绘制，AI 只提供风格参考。
5. 核对字体覆盖和所有透明边缘。命中/消除状态此时不再新增图片。

### 批次 C：场景完善 P1

1. 依据已批准参考生成完整工坊母版。
2. 从同一母版拆分远/中/近三层，补全遮挡、抠除中心。
3. 用手机、桌面布局预览；背景不抢材料和计算式。
4. 动效依然由程序实现，背景只做轻微氛围，不自动增加重型烟雾或炉火序列帧。

### 批次 D：声音与发行图

1. 声音先制作主冲压 S04、落料 S02、按钮 S01，再补其他 6 条；试听检查并发。
2. 核心美术稳定后生成 P2 封面，单独排标题。
3. 平台要求明确后再做派生尺寸；不为尚未确定的平台提前批量裁图。

### 12.1 每次生成操作卡

1. 从第 5 节选定唯一交付文件名与资产 ID。
2. 复制类别公共前缀、专用段、输出要求和负面词。
3. 附审核过的参考，设置实际支持的比例、分辨率和透明选项。
4. 保存原图到 `source/`，记录模型、提示词、参数、时间和来源。
5. 去底、校正、校色、清边、等比缩放或补透明边；不把截图当源文件。
6. 按目标名称放 `review/`；通过第 13 节验收后再进入 `approved/`。
7. 修改保持资产 ID 不变、版本递增，保留旧版，清单明确当前采用版。

---

## 13. 验收清单与返工标准

### 13.1 所有位图通用

- [ ] 文件能正常解码，扩展名与真实格式一致，真实尺寸与文件名一致。
- [ ] 色彩空间为 sRGB；无意外 ICC 偏色，无水印、签名和文字残留。
- [ ] 单素材没有多余物件，主体完整、不裁边，没有孤立脏像素。
- [ ] RGBA 素材外部实际透明；在黑、白、洋红背景上都无明显毛边。
- [ ] 保留规范画布和锚点，不随意紧裁；边缘至少保留规定安全空间。
- [ ] 缩到实际显示大小仍清楚；不能只检查 1024 大图。
- [ ] 生成模型、参考、提示词和授权记录可追溯。

### 13.2 材料专项

- [ ] A 正方、B 正圆通孔、C 上指三角、D 竖轴菱形，灰度下也能辨认。
- [ ] 四者照明方向一致，画法一致，整体占比与视觉重量接近。
- [ ] 铜片不变金币，金印不变宝石，钢环不变齿轮，棱晶不变水晶簇。
- [ ] 一图一主体，没有叠加牌面、底座、字母或格位数字。
- [ ] 钢环内孔透明，青绿棱晶主体不因过度透明失去轮廓。
- [ ] 摆到 5×5 真实大小布局后可快速分辨；材料不遮挡固定刻度角标。

### 13.3 模具、背景和 UI 专项

- [ ] 模具内开口和坐标严格满足第 3.3 节，没有 AI 烘焙的错误网格。
- [ ] 背景三层原点一致，合成不重复；裁切/视差不露洞。
- [ ] 背景中央低对比，手机与桌面安全区无关键物体被 UI 误遮。
- [ ] UI 无固定文字和金额；九宫格拉伸后边角不变形、中段无明显接缝。
- [ ] 金额区预览短数字、长数字、负数和本地化文案，不能靠裁字适配。
- [ ] 图标线宽一致，20–24 CSS 像素时仍辨认；触控范围独立足够大。
- [ ] 无返还、净损失使用同一中性结果底板，不自带庆祝图形。

### 13.4 需要直接返工的情况

- 透明 PNG 内画了棋盘格；钢环通孔是灰底；素材带白色方块边。
- 四材料混在一张难以独立裁切的图里，或角度和光线明显不一致。
- 模具歪斜、带固定 4×5/6×5 网格、固定刻度、固定金额或机器臂遮住盘面。
- UI 中央有装饰雕刻，缩放后干扰公式；文字已经烘焙且无法可靠清除。
- 把“第 2 轮”“刻度 4”“命中 5 个”画进素材文件，造成业务含义与静态图片耦合。
- 发光纹理是整张灰雾、不衰减到透明，或碎屑贴图已经包含几十个粒子。
- 封面展示额外玩法、未存在角色、Wild 或无依据的奖励宣传。

---

## 14. 本版交付核对

### 你需要准备的源素材

- 静态图形：24 个来源，其中 6 个图标可使用 SVG 代替 PNG。
- 音效：8 个逻辑类，S04 两个变体，共 9 条 WAV 母版。
- 字体：1 套满足当前语言和数字显示需求的字体资源及许可；缺字回退资源另登记。
- 过程资料：风格参考、AI 原图/母版、提示词与参数记录、授权记录；这些不重复计入 24。

### 不需要额外花钱生成的数量

- 不需要 25 张不同格位图。
- 不需要 4 材料 × 3 状态的 12 张图。
- 不需要 5 套不同刻度底座。
- 不需要四张带字主按钮、四张整屏结算图或三张换轮场景。
- 不需要 AI 制作上线图集或全局庆祝影片。

### 后续交给目录整理时

提供按第 5 节命名的文件即可。未能完全命名的原始图也可保留，但放在 `source/` 或 `review/` 并说明对应资产；不要凭猜测改成已批准文件。后续可按 `category` 分类、核验尺寸/Alpha、登记审核版本，再建立稳定逻辑 ID 到文件的资源表，供开发引用。

**推荐现在开始的第一组：风格参考 + 铜片 A + 模具外框。确认这三个方向，再生成其余素材。**
