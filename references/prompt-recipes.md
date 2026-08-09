# Prompt 与交付配方

所有最终图像生成 Prompt 都应删除艺术家姓名和原作标题，只保留材料、空间、表面与叙事机制。

## 配方 1：文本主题 -> 浅浮雕绘画

先填：

- 现实矛盾：`[谁/什么被改变]`
- 核心追问：`[作品不回答的问题]`
- 主材料前史：`[来自哪里、被谁使用]`
- 主锚点：`[最先看到的结构/物体]`
- 缺失连接：`[故意不解释的关系]`

Prompt 骨架：

```text
An original contemporary mixed-media relief painting about [specific conflict], viewed as a straight-on artwork documentation photograph. One dominant [anchor] is held by an incomplete [wood/metal/frame] structure, with [2-4 clues] arranged through splicing, interweaving, overlap and deliberate gaps rather than random collage. Use [3-5 materials with provenance], showing believable thickness, seams, gravity and support. The main field is [65% color], secondary field [25% color], with only [10% signal color]. Smooth painted quiet zones oppose concentrated mineral crust, exposed reclaimed edges and sanding marks where time and labor are carried. Keep one low-information resting area and one unresolved connection that leaves the viewer asking [question]. Neutral gallery light, real human scale, no frame mockup, no artist signature, no pseudo text. Avoid generic pastel abstraction, literal maze symbols, decorative Asian motifs, random scrap moodboard, uniform texture, glossy commercial 3D render, and any composition copied from a reference artwork.
```

## 配方 2：照片 -> 材料地形

先锁定源图：主体数量、轮廓、姿态、视线、地点特征、关键物件和原图比例。再选择一个转译档位：

- 用户明确要求保留身份、肖像、服装、建筑细节或纪实场景 -> `scene-preserving`。
- 普通“做成材料艺术 / 材料蒙太奇” -> 默认 `semantic-abstract`。
- 用户反馈“太像原图”“不适合”“不像独立作品”“更抽象”“不要写实”“只保留关系或动作” -> 立即切换 `semantic-abstract`，不再追问。

### 2A. `scene-preserving`

转译规则：

- 主体轮廓变成主锚点，不把所有摄影边缘都描出来。
- 中间调压缩为 2-4 个材料层：平滑色场、裸木/金属结构、矿物粗糙区、透明/网状遮挡。
- 背景可重组，但不能悄悄改变人物关系或地点故事。
- 标志性建筑保留整体轮廓、比例、中央轴线与 2-3 个身份特征；材料介入默认集中在局部，不能拆成通用废墟或让巨大空洞吞掉主体。
- 人物与动物保留完整身体、自然解剖、姿态和表情；除非用户明确要求，不截断、嵌墙、融合或标本化。
- 只有一个人物时，可高度抽象为连续材料轮廓、动作向量与 1-2 个身份色彩/物件锚点；仍保留单人数量、完整身体方向和主要动作。
- 两个及以上人物时默认中度抽象：保留人数、完整形体、相对位置、尺度、朝向与互动，把服装、五官和次要动作压缩；不要把群体统一替换为圆点、钉子或装饰性剪影。
- 用户要求干净时，收敛为一个主动作、2-3 个主材料场和一块大静区；只保留真正承重或推进叙事的连接件与纹理。
- 除非照片本身是夜景或主题明确要求低调光，默认抬起中间调：用柔和正面填充光、一个塑形侧光或顶光和可选的微弱轮廓光，让暗部材料仍可辨认。黑色只做结构锚点；避免统一棕灰罩染、死黑阴影、全局 HDR 和泛灰提亮。
- 至少一种材料来自照片真实地点或人物经历；无法确认时先标为假设。
- 不用“把照片贴到画框里”的方式假装转译。

Prompt 追加：

```text
Use scene-preserving translation. Preserve the source image's subject count, silhouette, pose, gaze direction, key place cues and original aspect ratio. Translate photographic midtones into a small number of physical material layers; do not trace every edge. Keep identity-bearing features quieter and more precise than the surrounding material field. Recompose only secondary background detail to strengthen the anchor, active boundary and unresolved gap. Unless the source is a night scene or the concept explicitly requires low-key light, keep the material midtones open and readable with soft frontal fill, one shaping side or top light, and only a restrained rim where needed. Use deep black only as a structural anchor; avoid crushed shadows, muddy brown-grey grading, global HDR and grey lifted blacks. Present the final artwork as a dead-on frontal documentation photograph: camera perpendicular to the backing plane, backing edges parallel to the image borders, no visible side face, receding return or three-quarter perspective; physical elements may still project toward the viewer.
```

人物 Prompt 追加规则：单人图加入 `The single figure may be highly abstracted into one continuous material body-vector while preserving the original action, body direction and one or two identity anchors.`；群体图加入 `Use medium abstraction for the group: preserve the exact visible figure count, complete small bodies, relative positions, scale, facing directions and interaction pattern; simplify facial and clothing detail rather than turning people into identical dots or pegs.`

### 2B. `semantic-abstract`

转译规则：

- 源图只作为语义证据。先写出必须保留的主体数量、相对位置、尺度、朝向、主要动作、互动关系与每个主体 1-2 个身份锚点；不保留像素布局、写实面孔、皮肤、服装褶皱或摄影景深。
- 每个人物对应一个完整材料身体向量。单人用连续体块、倾斜与支撑保留动作；多人用彼此可区分的织物柱、折板、矿物块或橡胶模块保留准确人数与关系。
- 手势、行走、借力、背负、并坐与远眺必须编码成真实的折、压、绑、吊、支撑、接触点或断裂路径；不能只把写实人物换成石膏质感。
- 动物用一个完整材料体量和物种锚点保留数量、方向和尺度；不写实复制毛发，也不做标本。
- 山体、建筑与地貌压缩为 2-4 个大材料板、轴线与 2-3 个身份轮廓，再通过错位、叠压、缺口、梁和支撑重组。
- 画面只保留一个主动作、2-3 个主材料场和一块大静区。背景不复刻摄影层次；材料结构应成为第一读取层。
- 缩到 10% 时，第一眼必须是材料装配，第二眼才能从数量、动作和身份锚点回认源图。如果仍像照片浮雕、油画摹写或滤镜，失败并定向重生成。

Prompt 追加：

```text
Use the source image only as semantic evidence for exact subject count, relative positions, scale, facing directions, primary actions, interaction pattern and one or two identity anchors per subject. Radically recompose it as an original non-photographic material assemblage. Replace each person or animal with one distinct complete material body-vector; encode gesture, walking, support, carrying or shared attention through folds, tension, rods, contact points, straps and deliberate gaps rather than realistic anatomy. Compress landmarks and terrain into two to four large material slabs that retain the identity silhouette and central axis while changing the spatial construction. Do not preserve pixel layout, realistic faces, skin, clothing folds, photographic depth of field or literal landscape rendering. At thumbnail size the result must read first as a constructed material artwork and only second as the source relationship. Avoid photo embossing, painterly tracing, uniform plaster texture, deleted subjects, altered count and identical pegs.
```

人物 Prompt 追加规则：单人图加入 `Build exactly one continuous material body-vector with the original action direction and one or two identity anchors; no portrait likeness or realistic anatomy.`；多人图加入 `Build the exact visible figure count as distinct complete material body-vectors, preserving relative positions, scale, facing directions and interaction; do not use realistic portraits, identical pegs or decorative dots.`

## 配方 3：机器镜像剧场

先选人机关系：`工具 / 替代者 / 陪伴者 / 战争参与者 / 劳动者 / 被观察者`。

Prompt 骨架：

```text
An original contemporary installation staged as a restrained micro-theater about [human-machine relationship]. A [specific machine/robotic fragment/device] occupies [posture and location] relative to [human trace or absent human], on a clearly constructed floor plane with one background panel and 2-3 purposeful props. Use [discarded machine part], [reclaimed wood], [wire/metal], and [one soft or mineral material], each visibly connected and structurally supported. The palette follows deep cobalt, bone white, charcoal, straw and one warning-red signal; no purple cyberpunk glow. The machine should mirror human [fear/desire/labor/power], not read as a product prototype or cute mascot. Neutral controlled exhibition light, credible scale, joints, weight and contact shadows, one empty zone that makes the absence of a person palpable. Avoid humanoid robot on a horse, seated black robot on a lotus, generic sci-fi laboratory, cinematic battle scene, UI holograms, fake labels and copied exhibition staging.
```

## 配方 4：透明核心

Prompt 骨架：

```text
An original translucent mixed-media object about [fragility/containment/time], consisting of a precise but incomplete [acrylic/resin/glass] container and an irregular core made from [material with provenance]. The container creates distance and observation; the core carries visible abrasion, pores and history. Use physically plausible refraction, wall thickness, joints, base support and a single soft light source. Frost white dominates, with restrained lilac, ice blue or resin green appearing through material depth rather than as a flat gradient. Keep the silhouette asymmetrical and the relation between container and core unresolved. Dead-on frontal object documentation on a neutral field, with the camera perpendicular to the backing plane and no visible side face or receding return. Avoid symmetrical collectible-toy geometry, a copied reference composition, glossy rendering, levitation, jewelry lighting and smooth gradient wallpaper.
```

## 配方 5：实体制作计划

输出顺序：

1. 一句话概念与核心追问
2. 正面图、侧面图、剖面和墙面/地面关系
3. 尺寸与重量假设
4. 主承重结构
5. 非承重材料层与表面步骤
6. 每个连接节点
7. 材料样与 1:1 节点样
8. 粉尘、锐角、易燃、重心、树脂、玻璃和电气风险
9. 拆分运输、编号和复装
10. 需要结构/电气/吊装专业复核的部分

图像只证明外观方向，不证明结构安全。

## 配方 6：审稿

按此顺序诊断：

1. **概念-材料是否有因果。** 哪种材料只是好看？
2. **主锚点是否明确。** 缩略图最先看到什么？
3. **框/梁/盒是否主动。** 它是否真的改变空间？
4. **拼接动作是否有层级。** 是否所有东西都平均散落？
5. **表面是否分工。** 是否全画面同一种颗粒？
6. **色彩是否只有一个分支。** 是否变成通用马卡龙或赛博朋克？
7. **文化与技术符号是否有现实关系。** 是否由主题需要而加入？
8. **物理可信度。** 重力、厚度、接缝、支撑与投影是否成立？
9. **原创距离。** 是否复用了原作标题、识别性组合或展陈关系？

每个问题返回：可见证据、影响、最小修改和 1-5 分。只改失败项，不整套推翻。

## 三个原创示例方向

这些示例用于理解机制，不作为固定模板。

### 被自动化替代的夜班记录

旧工厂储物柜木板、打孔考勤卡、废弃传送带橡胶与铜线组成不闭合框。考勤卡只在一个缺口处可见；机器不出现，让空下来的人的位置成为主角。

### 搬迁后仍在流动的灌溉记忆

旧门木、废弃灌溉软管、屋瓦粉末与河砂构成横向浅浮雕。软管穿出画框又返回，形成开放/封闭的双重路径；不依赖预设文化物件组合。

### 学会沉默的语音陪伴设备

废弃扬声器壳、黑化树脂、细金属线和一块被磨平的床头木组成小型剧场。设备面向一把空椅，但线缆被主动切断；问题是“陪伴来自回应，还是来自被允许沉默？”
