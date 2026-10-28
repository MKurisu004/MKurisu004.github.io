# Chu Liyun · Academic Homepage

简洁的单页学术主页，使用 Jekyll 在构建时将 YAML 内容渲染成静态 HTML。浏览页面无需 JavaScript，无前端框架或主题插件；使用系统字体，无第三方字体请求。可继续通过 GitHub Pages 部署。

## 日常修改：只编辑一个文件

**个人内容的统一入口是 [`_data/profile.yml`](_data/profile.yml)。**

| 想修改什么 | 对应字段 |
| --- | --- |
| 姓名、身份、网页简介 | `name`、`short_name`、`chinese_name`（仅用于大标题）、`tagline`、`description` |
| 照片 | `photo`、`photo_alt`；当前使用根目录 `chuliyun.jpg` |
| 自我介绍与研究兴趣 | `about`；每个列表项是一段，支持 Markdown |
| 邮箱、GitHub、CV 等链接 | `links` |
| 论文 | `sections` 中 `id: publications` 的 `items` |
| 研究与实习经历 | `sections` 中 `id: experience` 的 `items` |
| 教育经历 | `sections` 中 `id: education` 的 `items` |
| 荣誉与奖励 | `sections` 中 `id: honors` 的 `items` |

- **新增条目**：复制同类 `items` 中的一项，保留缩进并替换文字。
- **调整顺序**：直接移动条目或整个 section，页面与导航自动同步。
- **隐藏内容**：在对应 section、条目或链接下添加 `visible: false`。空 section 自动隐藏。
- **更新简历下载**：替换根目录 `resume.pdf`。网页内容和 PDF 独立维护，不会自动互相覆盖。
- **更新论文链接**：修改论文下 `links` 的 `url`。目前使用原简历及合作者主页提供的 arXiv 地址；网站展示名称已更新为 Octopus、会议为 ATC26。
- **添加链接**：在 `links` 中增加 `label` 和 `url`。无链接时删除该项或将 `url` 设为空字符串。

例如，新增一篇论文：

```yaml
      - title: "Your new paper title"
        authors:
          - name: "Liyun Chu"
            self: true
          - name: "Coauthor Name"
        venue: "Conference 2027"
        description: "A short description of the work."
        links:
          - label: "Paper"
            url: "https://example.com/paper"
```

作者的 `self: true` 会加粗姓名，`equal: true` 会显示共同一作星号。未使用的字段可以省略。

大标题的中文名使用系统楷体，macOS 优先使用 `Kaiti SC`，Windows 使用 `KaiTi`；均不可用时回退至系统衬线字体。半角括号 `()` 保持西文字体。可在 `assets/css/home.css` 的 `.name-chinese-text` 中调整中文字体。

也可以在 `sections` 中添加新的文字区域，例如：

```yaml
  - id: "service"
    title: "Academic Service"
    type: "text"
    paragraphs:
      - "Your service or teaching experience. **Markdown** is supported."
```

`id` 使用唯一的英文小写短横线名称，作为导航锚点。支持 `publications`、`experience`、`education`、`awards` 和 `text` 五种类型。`nav_title` 可为导航设置更短的名称。

## 本地预览

安装 Ruby 和 Bundler 后，在仓库根目录执行：

```sh
bundle install
bundle exec jekyll serve --livereload --host 127.0.0.1
```

打开 <http://127.0.0.1:4000>。修改 `_data/profile.yml`、HTML 或 CSS 会自动重建；修改 `_config.yml` 后需要重启服务。

构建静态文件：

```sh
bundle exec jekyll build
```

输出位于 `_site/`，无需安装 Node.js、npm 或 Docker。

## 页面结构与部署

```text
_data/profile.yml       ← 所有个人内容，在这里维护
_layouts/home.html      ← 单页 HTML 模板
assets/css/home.css     ← 布局、字体、颜色与移动端样式
assets/favicon.svg     ← 浏览器图标
index.html             ← 首页入口
_config.yml            ← GitHub Pages URL 与构建设置
Gemfile                ← 本地预览与构建依赖
chuliyun.jpg            ← 个人照片
resume.pdf             ← 下载的完整简历
```

`_config.yml` 中的 `url` 和 `baseurl` 用于部署路径；仓库根目录部署时 `baseurl` 留空。发布前先完成本地检查，再按已有 GitHub Pages 流程提交和推送。

旧模板、示例内容、生成脚本和工具配置已清理。导航直接根据 `_data/profile.yml` 的 `sections` 生成，所有个人内容均在这个文件中维护。`AGENTS.md` 提供贡献说明；`LICENSE` 保留代码的许可信息。
