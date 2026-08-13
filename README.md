# Richard1037 · Personal Profile Card

一个使用纯 HTML / CSS / JavaScript 编写的单文件个人名片页面，采用玻璃拟态、渐变与微交互动效。支持日间 / 夜间双主题、鼠标视差、点击复制邮箱等交互。

## 预览

> 在 `index.html` 同级目录直接用浏览器打开即可预览，或在本地起一个静态服务器：

```bash
# 任选其一
python -m http.server 8000
npx serve .
```

随后访问 [http://localhost:8000](http://localhost:8000)。

## 特性

- **零依赖**：不依赖任何构建工具与前端框架，仅通过 CDN 加载 Iconify 图标。
- **玻璃拟态 + 渐变**：卡片、按钮、chips 均使用 `backdrop-filter` 与多层渐变叠加。
- **日 / 夜间双主题**：通过 CSS 变量切换 `[data-theme]`，主题状态可记忆。
- **动态背景**：
  - 跟随鼠标视差倾斜的全屏透视网格；
  - 两团缓慢漂浮的高斯模糊光斑（`blob`）；
  - SVG 噪点纹理叠层。
- **鼠标光斑跟随**：卡片内出现跟随光标的径向高光。
- **联系区交互**：
  - 点击邮箱图标一键复制邮箱地址并出现 `已复制 ✓` 反馈；
  - 其它社交链接为品牌官方 LOGO，悬停放大并显示 tooltip。
- **本地时间 chip**：自动渲染当前 `HH:MM` 并每 30 秒刷新。
- **响应式**：在 ≤ 720px 屏幕下自动收紧间距、缩小尺寸。
- **可访问性**：主题按钮、社交图标均带 `aria-label`，支持键盘聚焦。

## 项目结构

```
.
├── index.html      # 全部 HTML / CSS / JavaScript（含注释）都在此文件
└── .gitignore
```

## 技术栈

- HTML5
- 原生 CSS（CSS 变量、`backdrop-filter`、`aspect-ratio`、`clip-path`、3D 透视）
- 原生 JavaScript（`requestAnimationFrame`、`navigator.clipboard`）
- 图标：[Iconify](https://iconify.design/) CDN（simple-icons / material-symbols / mdi）

## 自定义

页面内容全部集中在 `index.html` 中，常见修改点：

| 想改的内容       | 位置                                              |
| ---------------- | ------------------------------------------------- |
| 姓名、昵称、签名 | `.nickname`、`.title`、`.signature`              |
| 状态 chips       | `.meta-chips` 内的 `.meta-chip`                   |
| 自我介绍 / 座右铭 | `.intro-text`、`.motto`                          |
| 项目 demo        | `.demos` 下的 `.demo-item`，将 `href="#"` 替换为真实链接 |
| 技术栈标签       | `.stack-grid` 下的 `.stack-item`                  |
| 兴趣图标         | `.interest-icons` 下的 `.interest-icon`           |
| 联系方式         | `.contact-icons` 下的 `.contact-icon`             |
| 主题色           | `:root` 与 `[data-theme="night"]` 中的 `--accent` 等 CSS 变量 |
| 底部 build 信息  | `.status-bar`                                     |

邮箱复制通过 `data-copy-email` 触发；如需更改为其它即时通讯，可将对应 `<a>` 的 `href` 替换为实际链接。

## 浏览器兼容

- Chrome / Edge / Safari / Firefox 最新两个大版本。
- `backdrop-filter` 在 Firefox 中需开启 `layout.css.backdrop-filter.enabled`（默认自 103 版本起已默认开启）。
- 移动端 Safari / Chrome 表现良好；`prefers-reduced-motion: reduce` 时会关闭漂浮动画。

## 许可

仅作个人主页演示使用。如需复用请自行替换其中所有个人信息（姓名、邮箱、社交账号、demo 链接等）。
