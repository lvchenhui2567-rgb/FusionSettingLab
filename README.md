# Fusion Setting 属性编辑器

本地单文件 Web 工具，用于安全调整 DaVinci Resolve Fusion `.setting` 文件中的公开属性。

在线使用：https://lvchenhui2567-rgb.github.io/FusionSettingLab/

## 使用

1. 打开在线地址，或双击本地 `index.html`。
2. 拖入或选择 `.setting` 文件。
3. 从左侧节点树点击属性，添加或移除公开属性。
4. 在中间拖动排序，修改显示名称和页面。
5. 选择内部宿主节点，可添加可展开 Label、分隔线、Message、个人 Logo 或个人网站按钮。
6. 新增 Label 会自动在其后附带一条横线；横线计入 Label 的包含数量，用于直观分隔不同参数组。
7. Label 的包含数量决定其后折叠范围；Message 用于显示给用户的只读说明信息；Logo 会在本地压缩到最大 280 px 后嵌入文件。
8. 在右侧“预览”中按 DaVinci Inspector 的页面、顺序和分组查看近似呈现，也可操作滑块、开关和文本框体验交互。
9. 预览交互使用独立临时状态，不会修改模板或导出结果；再查看右侧检查与变更内容。
10. 点击“下载修改文件”可保存 `.setting`。
11. 如需安装包，选择 `Effects`、`Generators`、`Titles` 或 `Transitions`，再点击“打包 DRFX”。

## 安全原则

- 文件仅在本地浏览器中处理，不会上传。
- 普通属性操作只替换顶层 `GroupOperator` 或 `MacroOperator` 的公开 `Inputs = ordered() { ... }` 表体。
- Label、Separator、Message、Logo 和网站按钮仅额外修改所选宿主节点的 `Inputs` 与 `UserControls` 局部表体。
- 内部节点、动画、表达式、`Outputs`、`MainOutput1`、`ViewInfo` 和未知字段不会重新生成。
- 下载文件使用 `-edited.setting` 后缀，不覆盖原文件。
- DRFX 在浏览器本地生成，内部路径固定为 `Edit/<分类>/<模板名>.setting`，不上传文件或依赖外部库。
- 导出前会重新解析结果，验证允许区块之外的原文逐字一致，并检查特殊元素类型回读。
- Inspector 预览只读取解析结果并保留独立交互状态，不参与 `.setting` 序列化或 DRFX 打包。

## 当前范围

- 支持 `.setting`。
- 支持中文节点名、`["节点名"]` 键和嵌套 GroupOperator/MacroOperator。
- 支持公开属性排序、改名、页面调整、新增和移除。
- 支持导入、添加和编辑可展开 Label、Separator、Message、嵌入式 Logo 和跨平台网站按钮。
- 支持按 DaVinci Inspector 风格预览页面、Label 折叠、特殊元素及常见数值、开关、文本和颜色控件；无法精确还原的类型会标注“近似”。
- 支持将当前校验通过的结果打包为 `Effects`、`Generators`、`Titles` 或 `Transitions` 类型的 `.drfx`。
- 暂不导入或直接编辑现有 `.drfx` 压缩包，也不会自动收集外部媒体文件和缩略图。
- 预览用于确认布局和信息层级，不保证与不同 DaVinci Resolve 版本中的最终像素外观完全一致。
