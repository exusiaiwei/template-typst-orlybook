# O'RLY Textbook Template

<div align="center">

![Typst](https://img.shields.io/badge/Typst-239DAD?style=flat-square&logo=typst&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=flat-square)

**一个 O'Reilly 风格的 Typst 教科书模板**

*融合经典 O'Reilly 封面设计 + 学术三线表 + Obsidian 风格 Callout*

</div>

---

## ✨ 特性

### 📕 O'Reilly 风格封面
- 经典的顶部色带 + 标语设计
- 图片可自由定位（宽度、对齐、偏移）
- 完全可配置的标题、副标题、作者信息
- 主题色一键更换

### 📊 学术三线表
- 自动应用标准三线表样式（顶线、表头线、底线）
- 表头自动加粗
- 符合学术出版规范

### 💬 Callout 提示框系统
- 9 种预设类型：Note、Tip、Warning、Important、Danger、Example、Definition、Theorem、Proof
- 左侧彩色边框 + 浅色背景
- 支持自定义标题

### 🎨 精致的排版细节
- 引用带主题色小圆圈 `○`
- 代码块带边框和背景
- 标题使用主题色
- 链接使用主题色高亮

---

## 🚀 快速开始

### 1. 克隆或下载

```bash
git clone https://github.com/your-username/orly-textbook.git
cd orly-textbook
```

### 2. 编辑配置

打开 `orly-config.typ`，修改书籍信息：

```typst
// 🎨 主题色
#let theme-color = rgb("#6C3483")  // 紫色

// 📖 书籍信息
#let book-title = "你的书名"
#let book-subtitle = "副标题"
#let book-author = "作者名"
#let book-top-text = "THE DEFINITIVE GUIDE"
#let book-publisher = "出版信息"
```

### 3. 添加封面图片

将封面图片放入 `images/` 文件夹，然后在 `main.typ` 中配置：

```typst
#make-cover(
  cover-image: image("images/cover.png"),
  image-width: 50%,        // 图片宽度
  image-align: center,     // left, center, right
  image-offset-x: 100pt,   // 水平偏移
)
```

### 4. 编写内容

在 `chapters/` 文件夹中创建章节文件：

```typst
// chapters/ch01.typ
#import "../orly-config.typ": tip, note, warning, definition, theorem

= 第一章标题

正文内容...

#tip[这是一个小提示]
```

### 5. 编译

```bash
typst compile main.typ
# 或实时预览
typst watch main.typ
```

---

## 📁 项目结构

```
orly-textbook/
├── orly-config.typ      # 核心配置文件（书籍信息、样式、封面、Callout）
├── main.typ             # 主文档入口
├── images/              # 图片文件夹
│   ├── cover.png        # 封面图片
│   └── ch1.jpg          # 章节图片
├── chapters/            # 章节文件夹
│   ├── 1_intro.typ      # 章节内容
│   └── appendix.typ     # 附录
├── citation.bib         # 参考文献（可选）
└── README.md            # 本文档
```

---

## 📖 使用指南

### Callout 提示框

在章节文件开头导入需要的函数：

```typst
#import "../orly-config.typ": tip, note, warning, important, example-box, definition, theorem, proof-box
```

然后使用：

```typst
#note[
  这是一个普通笔记。
]

#tip[
  这是一个小提示！
]

#warning[
  这是一个警告信息。
]

#important[
  这是重要提示。
]

#definition(title: "自定义标题")[
  这是一个定义。
]

#theorem(title: "定理 1")[
  这是一个定理。
]

#proof-box[
  这是证明过程。
]

#example-box[
  这是一个示例。
]
```

**支持的类型：**

| 类型 | 函数 | 图标 | 颜色 |
|------|------|------|------|
| Note | `#note` | 📝 | 蓝色 |
| Tip | `#tip` | 💡 | 绿色 |
| Warning | `#warning` | ⚡ | 橙色 |
| Important | `#important` | ⚠️ | 深橙 |
| Danger | `#callout(type: "danger")` | 🔥 | 红色 |
| Example | `#example-box` | 📌 | 紫色 |
| Definition | `#definition` | 📖 | 主题色 |
| Theorem | `#theorem` | 📐 | 深主题色 |
| Proof | `#proof-box` | ✎ | 灰色 |

### 三线表

表格自动应用三线表样式：

```typst
#figure(
  table(
    columns: 3,
    [*列1*], [*列2*], [*列3*],
    [数据1], [数据2], [数据3],
    [数据4], [数据5], [数据6],
  ),
  caption: [表格标题]
)
```

### 数学公式

标准 Typst 数学语法：

```typst
行内公式：$E = m c^2$

独立公式：
$ sum_(i=1)^n i = (n(n+1))/2 $
```

### 代码块

```typst
行内代码：`let x = 42`

代码块：
```python
def hello():
    print("Hello, World!")
```⁣
```

---

## 🎨 主题配色

预设配色方案（在 `orly-config.typ` 中修改 `theme-color`）：

| 颜色 | RGB 值 | 效果 |
|------|--------|------|
| 紫色 | `#6C3483` | 经典学术感 |
| 深蓝 | `#1B4F72` | 专业商务 |
| 深绿 | `#1E8449` | 自然科学 |
| 暗红 | `#922B21` | 热情活力 |
| 近黑 | `#1C1C1C` | 极简现代 |
| 深灰蓝 | `#2C3E50` | 优雅低调 |

---

## 🔤 字体配置

默认字体回退顺序：

- **正文**：Georgia → SimSun → Noto Serif CJK SC
- **标题**：Arial → SimHei → Noto Sans CJK SC
- **代码**：Consolas → SimSun

如需自定义，修改 `orly-config.typ`：

```typst
#let font-serif = ("你的衬线字体", "SimSun")
#let font-sans = ("你的无衬线字体", "SimHei")
#let font-mono = ("你的等宽字体", "Consolas")
```

---

## 📄 许可证

MIT License - 自由使用、修改和分发。

---

## 🙏 致谢

- 初始布局和章节设计灵感来自 [uwnibook-color](https://typst.app/universe/package/uwnibook-color) - 一个优秀的中文学术书籍模板
- 封面设计灵感来自 [O'Reilly Media](https://www.oreilly.com/) 的经典技术书籍封面
- Callout 系统和三线表参考 [tufte-textbook](https://github.com/exusiaiwei/template-typst-tufte) 模板
- Callout 视觉风格参考 [Obsidian](https://obsidian.md/) 的设计语言

---

<div align="center">

**Happy Writing! 📚**

*使用 [Typst](https://typst.app/) 构建*

</div>
