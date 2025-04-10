---
title: Hugo 博客搭建入门指南
date: 2025-04-11T00:55:35+08:00
lastmod: 2025-04-11T00:55:35+08:00
author: Author Name
# avatar: /img/author.jpg
# authorlink: https://author.site
cover: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - category1
tags:
  - tag1
  - tag2
# nolastmod: true
draft: true
---

## 一、Hugo 是什么？
Hugo 是一个基于 Go 语言开发的**静态网站生成器**，具有以下特点：
- ⚡ **极速构建**：生成速度可达每秒数百页
- 📦 **极简依赖**：仅需 Go 环境即可运行
- 🎨 **主题丰富**：支持 5000+ 社区主题
- 🔄 **热更新**：开发时实时预览

![Hugo Logo](https://gohugo.io/images/logo.png)

## 二、环境准备
### 1. 安装 Hugo
```powershell
# Windows 使用 Scoop
scoop install hugo-extended

# macOS 使用 Homebrew
brew install hugo
```

### 2. 验证安装
```bash
hugo version  # 应显示类似 hugo v0.145.0
```

## 三、创建首个站点
```bash
hugo new site my-blog  # 创建名为 my-blog 的站点
cd my-blog
git init  # 初始化 Git 仓库
```

## 四、主题配置
### 1. 安装主题（以 Even 为例）
```bash
git clone https://github.com/olOwOlo/hugo-theme-even themes/even
```

### 2. 修改配置文件
`config.toml` 关键配置：
```toml
baseURL = "https://yourdomain.com"
languageCode = "zh-cn"
title = "Your Blog"
theme = "even"

[params]
  author = "YourName"
  description = "技术博客描述"
  github = "https://github.com/yourname"
```

## 五、撰写第一篇文章
```bash
hugo new post/welcome.md  # 在 content/post 目录生成新文章
```

编辑 `welcome.md`：
```markdown
---
title: "欢迎来到我的博客"
date: 2025-04-11
draft: false
---

## 你好，世界！

这是我的第一篇 Hugo 博客文章，使用 **Markdown** 语法编写。

### 功能演示
- 代码块支持：
```go
package main
func main() {
    println("Hello Hugo!")
}
```
- 列表展示：
1. 技术分享
2. 开发教程
3. 生活随笔

## 站点部署
### 本地预览
```bash
hugo server -D  # 开启草稿模式
```
访问 `http://localhost:1313` 查看效果

### GitHub Pages 部署
```bash
hugo  # 生成 public 目录
cd public
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin git@github.com:yourname/your-repo.git
git push -u origin main
```
---

### 文章结构说明
| 部分         | 说明                                                                 |
|--------------|----------------------------------------------------------------------|
| Front Matter | 定义元数据，决定文章如何渲染                                       |
| 标题层级     | `#` 一级标题，`##` 二级标题，支持六级标题                          |
| 列表         | 支持有序/无序列表，可嵌套代码块、表格等                            |
| 图片插入     | 使用相对路径或绝对 URL，建议使用图床服务                           |
| 注释         | 使用 `<!-- 注释内容 -->` 添加编辑备注                              |

---

### 常见问题解决
1. **图片不显示**  
   - 检查路径是否正确（建议使用 `/images/xxx.jpg` 格式）
   - 确保图片已添加到 `static/images` 目录

2. **主题不生效**  
   - 确认 `config.toml` 中的 `theme` 字段与主题目录名一致
   - 执行 `hugo mod tidy` 同步依赖

3. **404 错误**  
   - 检查 URL 路径是否与 `config.toml` 中的 `permalinks` 配置匹配
   - 运行 `hugo --cleanDestinationDir` 清理旧文件

---

通过以上步骤，你可以快速创建并发布符合 Hugo 规范的博客文章。建议结合具体主题的网页进行深度定制，例如添加评论系统、SEO 优化等高级功能。
