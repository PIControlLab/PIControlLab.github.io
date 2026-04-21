# PIControlLab.github.io 开发说明

本仓库用于维护实验室官网，基于 [Hugo](https://gohugo.io/) 构建。

为了让多人协作更安全、清晰，推荐所有实验室成员都使用下面这套流程：

- 实验室 GitHub 账号维护官方仓库
- 每位成员使用自己的 GitHub 账号 `fork` 官方仓库
- 在自己的 fork 中开发和提交
- 通过 `Pull Request` 合并到实验室官方仓库的 `source` 分支
- GitHub Actions 自动将 `source` 分支编译并发布到 `main` 分支

也就是说：

- `source`：网页源代码分支，平时开发都在这里进行
- `main`：网页发布分支，由 GitHub Actions 自动生成，不建议手动修改

当前这个文件夹就是网站的 `source` 分支工作目录。

---

## 1. 仓库结构

本项目是一个 Hugo 网站，常见目录如下：

- `content/`：网站内容
  - `content/member/`：成员信息
  - `content/news/`：新闻
  - `content/research/`：研究方向
  - `content/gallery/`：展示内容
- `data/`：YAML 数据文件
- `layouts/`：页面模板
- `static/`：静态资源，如图片、CSS、JS
- `themes/`：主题代码
- `.github/workflows/deploy.yml`：自动部署配置

建议优先修改 `content/`、`data/`、`layouts/`、`static/`，尽量不要直接改主题目录 `themes/`，除非确实需要。

---

## 2. 分支职责

### `source` 分支

这是开发分支，保存 Hugo 源代码。

- 所有内容更新、页面修改、样式调整，都应提交到 `source`
- 实验室成员提交 PR 时，目标分支也应是 `source`

### `main` 分支

这是发布分支，保存生成后的静态网页。

- 正常情况下不要手动修改
- 不要直接往 `main` 提交网页源码
- `main` 由 GitHub Actions 自动从 `source` 构建生成

当前仓库的自动部署逻辑是：

1. 向 `source` 分支 push
2. GitHub Actions 执行 `hugo`
3. 将 `public/` 中生成的网页内容发布到 `main`

所以大家只需要关注 `source` 分支即可。

---

## 3. 推荐协作方式

推荐使用下面的 Git 关系：

- `upstream`：实验室官方仓库
- `origin`：你自己的 fork 仓库

例如：

- 官方仓库：`https://github.com/PIControlLab/PIControlLab.github.io.git`
- 个人 fork：`https://github.com/<你的GitHub用户名>/PIControlLab.github.io.git`

推荐约定：

- 永远从官方仓库的 `source` 分支同步最新代码
- 永远把自己的改动先推到个人 fork
- 永远通过 PR 合并到官方仓库的 `source` 分支

这样做的好处是：

- 不会误操作实验室官方仓库
- 每个人的开发记录清晰可追踪
- 便于代码审核和问题回滚

---

## 4. 第一次配置

### 4.1 Fork 官方仓库

先在 GitHub 页面上登录你的个人账号，然后：

1. 打开实验室官方仓库
2. 点击右上角 `Fork`
3. 将仓库 fork 到你自己的账号下

建议确认 fork 后你的仓库里也有 `source` 和 `main` 两个分支。

### 4.2 克隆你自己的 fork

在本地执行：

```bash
git clone -b source https://github.com/<你的GitHub用户名>/PIControlLab.github.io.git
cd PIControlLab.github.io
```

说明：

- `-b source` 表示直接检出 `source` 分支
- 如果不加这个参数，有时会默认进入 `main`，这不是我们平时开发的分支

### 4.3 添加官方仓库为 upstream

```bash
git remote add upstream https://github.com/PIControlLab/PIControlLab.github.io.git
git remote -v
```

正常情况下应看到：

```bash
origin    https://github.com/<你的GitHub用户名>/PIControlLab.github.io.git
upstream  https://github.com/PIControlLab/PIControlLab.github.io.git
```

### 4.4 安装 Hugo

请先在本机安装 Hugo。

安装完成后检查：

```bash
hugo version
```

如果能输出版本号，说明安装成功。

---

## 5. 日常开发流程

推荐每次修改都按下面流程进行。

### 第 1 步：先同步官方仓库最新代码

进入仓库目录后执行：

```bash
git checkout source
git fetch upstream
git pull upstream source
```

如果你希望自己的 fork 也保持同步，可以再执行：

```bash
git push origin source
```

### 第 2 步：新建自己的开发分支

不要直接在 `source` 上长期开发，推荐从 `source` 拉一个功能分支：

```bash
git checkout -b feat/update-member-2026
```

分支名可以按内容起名，例如：

- `feat/add-news-competition`
- `feat/update-member-zhangsan`
- `fix/homepage-layout`
- `docs/update-readme`

### 第 3 步：进行修改

根据需求修改对应文件，例如：

- 新增成员：`content/member/` 和 `static/img/members/`
- 新增新闻：`content/news/` 和相关图片目录
- 新增展示：`content/gallery/` 和 `static/img/gallery/`
- 修改导航或页面结构：`layouts/`
- 修改样式：`static/css/`

### 第 4 步：本地预览

开发时建议启动本地预览：

```bash
hugo server -D
```

说明：

- `-D` 表示包含 draft 内容
- 一般浏览器打开终端提示的本地地址即可

### 第 5 步：检查是否能正常构建

提交前至少执行一次：

```bash
hugo
```

如果没有报错，说明静态站点可以正常生成。

注意：

- `hugo` 会生成 `public/` 目录
- `public/` 是构建产物，不是平时开发的主要内容
- 如果实验室后续仍采用 GitHub Actions 自动部署，则不要把本地生成结果当作源码修改

### 第 6 步：提交代码

```bash
git status
git add .
git commit -m "add member xxx"
```

提交信息建议简洁明确，使用动词开头，例如：

- `add member zhangsan`
- `update news for competition`
- `fix gallery image path`
- `change homepage banner`

### 第 7 步：推送到个人 fork

```bash
git push -u origin feat/update-member-2026
```

### 第 8 步：发起 Pull Request

在 GitHub 页面中从你的分支发起 PR，注意检查目标方向：

- `base repository`：实验室官方仓库 `PIControlLab/PIControlLab.github.io`
- `base branch`：`source`
- `head repository`：你的 fork
- `compare branch`：你刚才推送的功能分支

也就是说，PR 应该是：

`你的分支 -> 官方仓库的 source`

不要把 PR 提到 `main`。

### 第 9 步：合并后同步本地

PR 被合并后，本地建议执行：

```bash
git checkout source
git fetch upstream
git pull upstream source
git push origin source
```

如果该功能分支后续不再使用，也可以删除：

```bash
git branch -d feat/update-member-2026
git push origin --delete feat/update-member-2026
```

---

## 6. 常见开发场景

### 场景 1：新增成员

通常需要做两件事：

1. 在 `content/member/` 下新增一个 Markdown 文件
2. 在 `static/img/members/` 下加入对应照片

提交前请确认：

- 页面能正常显示
- 图片路径正确
- 成员页面排版正常

### 场景 2：新增新闻

通常需要：

1. 在 `content/news/` 下新增新闻 Markdown
2. 在 `static/img/news/` 下加入图片

提交前请确认：

- 新闻列表页能看到新条目
- 详情页图片能显示
- 日期、标题、摘要等信息正确

### 场景 3：修改研究方向、项目或展示页

可能涉及：

- `content/research/`
- `content/projects/`
- `content/gallery/`
- `data/*.yaml`
- `layouts/`

如果改动了模板或数据结构，建议重点检查：

- 首页是否正常
- 列表页是否正常
- 对应详情页是否正常

### 场景 4：修改样式和页面布局

通常会涉及：

- `static/css/`
- `layouts/`
- `static/js/`

这类改动建议：

- 同时检查电脑端和手机端显示
- 检查首页、列表页、详情页
- 避免直接改 `themes/`，优先在本仓库覆盖

---

## 7. 同步官方仓库更新

多人协作时，你的 fork 可能会落后于实验室官方仓库。建议经常同步。

### 方法 1：同步本地 `source`

```bash
git checkout source
git fetch upstream
git pull upstream source
git push origin source
```

### 方法 2：把最新 `source` 合并到你的功能分支

如果你已经在某个功能分支上开发了一段时间，提交 PR 前建议先同步一次：

```bash
git checkout source
git fetch upstream
git pull upstream source
git checkout feat/update-member-2026
git merge source
```

如果出现冲突，解决冲突后再提交。

---

## 8. 冲突处理建议

如果执行 `git pull` 或 `git merge` 时出现冲突：

1. 用编辑器打开冲突文件
2. 找到 Git 标记的冲突区域
3. 保留正确内容，删除冲突标记
4. 重新执行：

```bash
git add <冲突文件>
git commit
```

如果你不熟悉冲突处理，建议：

- 先不要强行提交
- 在群里说明冲突涉及的文件
- 找最近修改过该部分的人一起确认

---

## 9. 不建议做的事情

为了避免误操作，请尽量不要：

- 直接在官方仓库上开发
- 直接往官方仓库的 `source` 分支 push
- 直接修改 `main` 分支
- 不经检查就提交大量无关改动
- 随意删除他人文件
- 在不确认影响范围的情况下直接修改 `themes/`

尤其注意：

- `main` 是发布分支，不是日常开发分支
- PR 的目标应始终优先检查是不是 `source`

---

## 10. 提交前检查清单

每次发 PR 前，建议至少检查以下内容：

- 当前所在分支不是 `main`
- 改动内容与本次任务相关
- 本地运行过 `hugo server -D` 或至少运行过 `hugo`
- 页面没有明显报错或图片丢失
- 文件路径大小写正确
- 新增内容所需图片已经一起提交
- PR 目标分支是官方仓库的 `source`

---

## 11. 推荐命令速查

### 首次配置

```bash
git clone -b source https://github.com/<你的GitHub用户名>/PIControlLab.github.io.git
cd PIControlLab.github.io
git remote add upstream https://github.com/PIControlLab/PIControlLab.github.io.git
```

### 同步官方最新代码

```bash
git checkout source
git fetch upstream
git pull upstream source
git push origin source
```

### 新建开发分支

```bash
git checkout -b feat/your-change-name
```

### 本地预览

```bash
hugo server -D
```

### 本地构建检查

```bash
hugo
```

### 提交并推送

```bash
git add .
git commit -m "your concise message"
git push -u origin feat/your-change-name
```

---

## 12. 一句话总结

实验室官网的正确协作流程是：

**个人账号 fork 官方仓库 -> 在个人 fork 的 `source` 体系下开发 -> 推送到自己的分支 -> 向官方仓库的 `source` 发 PR -> 合并后自动部署到 `main`。**

如果大家都按这个流程操作，仓库会更安全，协作也会更清晰。
