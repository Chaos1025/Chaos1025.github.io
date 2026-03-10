# Jekyll 学术网站使用指南

这是一个完整的中文使用指南，帮助网页开发新手快速上手和维护这个基于 Jekyll 的个人学术网站。

## 项目概述

这个网站使用了 [Academic Pages](https://academicpages.github.io/) 模板，专为学者和研究人员设计，包含以下主要功能：

- 📄 **论文发表管理**：展示研究成果
- 📚 **教学经历展示**：记录教学工作
- 🎤 **学术报告管理**：演讲和会议展示
- 📋 **简历系统**：支持 Markdown 和 JSON 格式
- 🌐 **博客功能**：分享想法和见解
- 🎨 **响应式设计**：适配所有设备
- 🔗 **社交媒体整合**：连接各种学术平台

## 开发环境搭建

### 方法一：本地 Ruby 环境（推荐）

1. **安装依赖**（首次运行）
   ```bash
   bundle install
   ```

2. **启动本地服务器**
   ```bash
   jekyll serve -l -H localhost
   # 或者使用
   bundle exec jekyll serve -l -H localhost
   ```

3. **访问网站**：打开浏览器访问 `http://localhost:4000`

**注意事项**：
- 修改 `.md` 和 `.html` 文件会自动重新构建
- 修改 `_config.yml` 需要重启服务器
- 按 `Ctrl+C` 停止服务器

### 方法二：Docker 环境

1. **设置权限**
   ```bash
   chmod -R 777 .
   ```

2. **启动容器**
   ```bash
   docker compose up
   ```

3. **访问网站**：浏览器打开 `http://localhost:4000`

## 项目结构详解

### 核心文件和目录

```
你的网站项目/
├── _config.yml              # 🔧 网站主配置文件
├── _data/                   # 📊 数据文件目录
│   ├── navigation.yml       # 🧭 导航菜单配置
│   ├── cv.json             # 📋 简历数据（JSON格式）
│   └── ui-text.yml         # 🌐 界面文本本地化
├── _includes/              # 🧩 可重用组件
│   ├── author-profile.html # 👤 作者信息侧边栏
│   ├── head.html          # 📝 网页头部
│   ├── footer.html        # 📋 网页底部
│   └── masthead.html      # 🔝 网站标题栏
├── _layouts/               # 📄 页面模板
│   ├── default.html       # 🏠 基础布局
│   ├── single.html        # 📃 单页布局
│   └── talk.html          # 🎤 演讲专用布局
├── _pages/                 # 📑 静态页面
│   ├── about.md           # 🏠 首页（关于我）
│   ├── cv.md              # 📋 简历页面
│   ├── publications.html  # 📄 论文列表页
│   └── teaching.html      # 📚 教学经历页
├── _publications/          # 📄 论文文件夹
├── _teaching/             # 📚 教学经历文件夹
├── _talks/                # 🎤 学术报告文件夹
├── _posts/                # ✍️ 博客文章文件夹
├── _sass/                 # 🎨 样式表源码
├── assets/                # 🖼️ 静态资源
│   ├── css/              # 🎨 编译后的样式
│   ├── js/               # ⚡ JavaScript文件
│   └── images/           # 🖼️ 图片文件
├── files/                 # 📎 下载文件（PDF等）
├── images/               # 📸 网站图片和图标
└── _site/                # 🏗️ 生成的网站（自动生成）
```

## 网站页面与文件对应关系

### 🏠 首页 (`/`)
- **文件位置**：`_pages/about.md`
- **作用**：网站主页，介绍你的基本情况
- **侧边栏**：显示你的头像和社交媒体链接

### 📄 论文页面 (`/publications/`)
- **列表页**：`_pages/publications.html`（显示所有论文）
- **单篇论文**：`_publications/` 文件夹中的每个 `.md` 文件
- **URL 格式**：`/publication/论文标识符`

### 📚 教学页面 (`/teaching/`)
- **列表页**：`_pages/teaching.html`
- **单项经历**：`_teaching/` 文件夹中的每个 `.md` 文件
- **URL 格式**：`/teaching/教学经历标识符`

### 🎤 演讲页面 (`/talks/`)
- **列表页**：`_pages/talks.html`
- **单次演讲**：`_talks/` 文件夹中的每个 `.md` 文件
- **URL 格式**：`/talk/演讲标识符`

### 📋 简历页面 (`/cv/`)
- **Markdown版本**：`_pages/cv.md`
- **JSON版本**：`_pages/cv-json.md`（从 `_data/cv.json` 生成）

## 日常使用指南

### 📝 修改基本信息

#### 1. 网站标题和描述
编辑 `_config.yml` 文件：
```yaml
title: "你的姓名 / 个人学术主页"      # 网站标题
name: "你的姓名"                    # 作者姓名
description: "你的学术简介"         # 网站描述
url: https://yourusername.github.io # 你的网站地址
```

#### 2. 个人信息和社交媒体
在 `_config.yml` 的 `author` 部分：
```yaml
author:
  avatar: "profile.jpg"           # 头像文件名（放在 images/ 文件夹）
  name: "你的姓名"
  bio: "南京大学电子学院硕士研究生"  # 个人简介
  location: "南京，中国"          # 地理位置
  email: "你的邮箱@example.com"   # 联系邮箱
  
  # 学术平台链接
  googlescholar: "https://scholar.google.com/citations?user=你的ID"
  orcid: "https://orcid.org/你的ORCID"
  researchgate: "https://www.researchgate.net/profile/你的用户名"
  
  # 社交媒体
  github: "你的GitHub用户名"
  linkedin: "你的LinkedIn用户名"
```

#### 3. 首页内容
编辑 `_pages/about.md`：
```markdown
---
permalink: /
title: "关于我"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

在这里写你的个人介绍...
```

### 📄 管理论文发表

#### 添加新论文
在 `_publications/` 文件夹创建新的 `.md` 文件，文件名格式：`YYYY-MM-DD-论文简称.md`

```yaml
---
title: "论文完整标题"
collection: publications
category: manuscripts          # 类型：manuscripts(期刊), conferences(会议), books(书籍), preprints(预印本)
permalink: /publication/2024-paper-key
date: 2024-10-17
venue: '期刊或会议名称'
paperurl: 'https://doi.org/论文链接'
repourl: 'https://github.com/你的用户名/代码仓库'
citation: '完整引用格式'
authors:                       # 作者列表（可选）
  - name: "第一作者"
    equal_contribution: true   # 共同第一作者标记
  - name: "通讯作者"
    corresponding: true        # 通讯作者标记
---

在这里写论文摘要和详细描述...
```

#### 论文分类
系统会自动按 `category` 字段分类：
- `manuscripts`：期刊论文
- `conferences`：会议论文
- `preprints`：预印本
- `books`：书籍章节

### 📚 添加教学经历

在 `_teaching/` 文件夹创建 `.md` 文件：

```yaml
---
title: "课程名称"
collection: teaching
type: "助教"                   # 角色类型
venue: "南京大学"              # 机构名称
date: 2024-09-01              # 开始日期
location: "南京，中国"         # 地点
---

在这里描述教学内容和职责...
```

### 🎤 记录学术报告

在 `_talks/` 文件夹创建 `.md` 文件：

```yaml
---
title: "报告标题"
collection: talks
type: "会议报告"               # 报告类型
venue: "会议名称"              # 场所
date: 2024-05-15              # 日期
location: "城市，国家"         # 地点
---

报告摘要和详细信息...
```

### 🧭 自定义导航菜单

编辑 `_data/navigation.yml`：

```yaml
main:
  - title: "论文发表"          # 显示文字
    url: /publications/       # 链接地址
    
  - title: "教学经历"
    url: /teaching/
    
  # 注释掉的项目不会显示在菜单中
  # - title: "学术报告"
  #   url: /talks/
    
  - title: "个人简历"
    url: /cv/
```

### 📋 更新简历

#### Markdown 格式简历
编辑 `_pages/cv.md`，使用标准 Markdown 语法。

#### JSON 格式简历
编辑 `_data/cv.json`，使用结构化数据格式，系统会自动生成简历页面。

### 🖼️ 管理图片和文件

#### 图片文件
- **个人头像**：放在 `images/` 文件夹，文件名在 `_config.yml` 中指定
- **其他图片**：放在 `images/` 文件夹，在 Markdown 中引用：
  ```markdown
  ![图片描述](../images/图片文件名.jpg)
  ```

#### 下载文件
- **论文PDF**：放在 `files/` 文件夹
- **演讲PPT**：放在 `files/` 文件夹
- **其他文档**：放在 `files/` 文件夹

在 Markdown 中链接：
```markdown
[下载论文PDF](../files/paper.pdf)
```

## 高级功能

### 🎨 主题切换
在 `_config.yml` 中修改：
```yaml
site_theme: "default"  # 选项："default" 或 "air"
```

### 📈 网站分析
启用 Google Analytics：
```yaml
analytics:
  provider: "google-analytics-4"
  google:
    tracking_id: "你的跟踪ID"
```

### 🔍 SEO优化
系统自动生成：
- Meta 描述和标题
- Open Graph 标签
- Schema.org 结构化数据
- 网站地图

## 部署和发布

### 🚀 GitHub Pages 部署
1. **提交更改**：
   ```bash
   git add .
   git commit -m "更新网站内容"
   git push origin master
   ```

2. **自动部署**：GitHub Actions 会自动构建并部署到 `https://你的用户名.github.io`

3. **检查状态**：在 GitHub 仓库的 Actions 选项卡查看构建状态

### 🧪 本地测试
发布前务必本地测试：
```bash
bundle exec jekyll serve -l -H localhost
```

## 故障排除

### 常见问题

#### 1. 依赖问题
```bash
# 重新安装依赖
bundle install
```

#### 2. 构建失败
- 检查 YAML 前置数据格式是否正确
- 确保所有必需字段都已填写
- 查看 GitHub Actions 构建日志

#### 3. 图片不显示
- 检查图片路径是否正确
- 确保图片文件存在于 `images/` 文件夹
- 使用相对路径：`../images/文件名.jpg`

#### 4. 链接失效
- 检查 permalink 是否唯一
- 确认文件夹和文件名正确
- 验证外部链接有效性

### 性能优化

#### 图片优化
- 压缩图片大小
- 使用适当的图片格式
- 设置合理的图片尺寸

#### 加载速度
- 最小化自定义CSS和JavaScript
- 启用Jekyll压缩设置
- 优化字体加载

## 维护建议

### 📅 定期维护
- **每月**：检查外部链接有效性
- **每季度**：更新依赖包版本
- **每年**：审查网站内容和设计

### 🔐 安全注意事项
- 不要提交敏感信息
- 定期更新依赖包
- 使用环境变量存储私密配置

### 📊 内容管理
- 保持信息及时更新
- 使用一致的文件命名规范
- 定期备份重要内容

## 快速参考

### 文件创建模板

#### 新论文模板
```bash
# 文件名：_publications/2024-03-15-paper-title.md
---
title: "论文标题"
collection: publications
category: manuscripts
permalink: /publication/2024-paper-title
date: 2024-03-15
venue: '期刊名称'
paperurl: 'https://doi.org/...'
repourl: 'https://github.com/...'
citation: '引用格式'
---
论文摘要...
```

#### 新教学经历模板
```bash
# 文件名：_teaching/2024-spring-course.md
---
title: "课程名称"
collection: teaching
type: "助教"
venue: "大学名称"
date: 2024-02-01
location: "城市，国家"
---
教学描述...
```

### 常用命令
```bash
# 启动开发服务器
bundle exec jekyll serve -l -H localhost

# 清理构建文件
bundle exec jekyll clean

# 构建生产版本
bundle exec jekyll build

# 更新依赖
bundle update
```

这个指南应该能帮助你快速上手并维护这个学术网站。如果遇到具体问题，可以参考 Jekyll 官方文档或 Academic Pages 模板的说明文档。