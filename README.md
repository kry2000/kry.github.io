# AI掘金指南 - 多页面网站部署说明

## 网站结构（多页面版）

这是一个**多页面深度网站**，不是单页。点击首页的每个热点卡片，会进入独立的详情页，里面有更详细的数据分析、图表、时间线、产品对比。

## 文件说明

| 文件 | 作用 | 大小 |
|------|------|------|
| `index.html` | 网站首页（热点卡片 + 工具箱 + 趋势图 + 变现指南） | ~18KB |
| `style.css` | 全局样式（首页 + 详情页共用） | ~21KB |
| `detail-vibe-coding.html` | Vibe Coding 深度分析页 | ~8KB |
| `detail-ai-agent.html` | AI Agent 深度分析页 | ~6KB |
| `detail-deepseek.html` | DeepSeek 深度分析页 | ~6KB |
| `detail-ai-glasses.html` | AI眼镜 深度分析页 | ~7KB |
| `detail-ai-content.html` | AI+短剧 深度分析页 | ~7KB |
| `detail-embodied.html` | 具身智能/机器人 深度分析页 | ~7KB |
| `chart-*.png` | 6张数据可视化图表 | ~40-70KB/张 |
| `README.md` | 本说明文件 | — |

**总计：13个文件**，全部静态文件，不需要后端服务器。

## 每个详情页包含什么？

每个热点详情页都有统一结构：

1. **面包屑导航** — 首页 > 本周最热 > 当前页面
2. **关键数据卡片** — 4个核心数字（如估值、市占率、出货量等）
3. **数据可视化图表** — 用 Python matplotlib 生成的专业图表
4. **发展时间线** — 从起源到现在的重要里程碑
5. **产品对比** — 主要竞品的功能/价格/定位对比
6. **掘金机会分析** — 具体的赚钱路径建议
7. **返回首页按钮** — 方便用户继续浏览其他热点

## 图表清单

| 图表文件 | 用在哪个页面 | 内容 |
|---------|------------|------|
| `chart-vibe-coding.png` | Vibe Coding 详情页 | AI编程工具估值排名（柱状图） |
| `chart-ai-agent.png` | AI Agent 详情页 | 季度融资趋势（面积图） |
| `chart-market-share.png` | DeepSeek 详情页 | 全球AI工具市场份额（饼图） |
| `chart-ai-glasses.png` | AI眼镜 详情页 | 出货量预测（柱状图） |
| `chart-short-drama.png` | AI+短剧 详情页 | 市场规模增长（折线图） |
| `chart-robot-funding.png` | 具身智能 详情页 | 融资事件+金额双轴图 |

## 快速部署步骤（GitHub Pages 免费托管）

### 第一步：注册 GitHub
1. 打开 https://github.com
2. 点击 Sign Up，用邮箱注册
3. 验证邮箱

### 第二步：创建仓库
1. 登录后点击右上角 `+` → `New repository`
2. 仓库名填写：`你的用户名.github.io`（例如 `zhangsan.github.io`）
3. 选择 `Public`（公开）
4. 点击 `Create repository`（不用勾选README）

### 第三步：上传所有文件
1. 进入仓库页面 → `Add file` → `Upload files`
2. **把以下所有文件一起拖进去上传**：
   - `index.html`
   - `style.css`
   - `detail-vibe-coding.html`
   - `detail-ai-agent.html`
   - `detail-deepseek.html`
   - `detail-ai-glasses.html`
   - `detail-ai-content.html`
   - `detail-embodied.html`
   - `chart-vibe-coding.png`
   - `chart-ai-agent.png`
   - `chart-market-share.png`
   - `chart-ai-glasses.png`
   - `chart-short-drama.png`
   - `chart-robot-funding.png`
3. 点击 `Commit changes`

### 第四步：访问网站
- 等待 1-5 分钟
- 浏览器输入：`https://你的用户名.github.io`
- 首页加载后，点击任意热点卡片的 **"查看深度分析 →"** 就能进入详情页
- 详情页里有图表、时间线、产品对比，点击 **"← 返回首页"** 可回到首页

## 自定义域名（可选）

### 购买域名
- **阿里云万网**：https://wanwang.aliyun.com（`.cn` 约 ¥30-40/年，`.com` 约 ¥60-100/年）
- **腾讯云 DNSPod**：https://dnspod.cloud.tencent.com
- **Namecheap**（免备案）：https://www.namecheap.com

### 绑定域名
1. 仓库 → `Settings` → `Pages`
2. `Custom domain` 输入你的域名，Save
3. 域名服务商后台添加 DNS：
   - 类型：CNAME
   - 主机记录：www
   - 记录值：`你的用户名.github.io`
4. 等 DNS 生效（几分钟到几小时）

## 如何修改内容？

### 改文字/数据
- 打开任意 `.html` 文件，直接替换文字
- 数据更新后，建议同步更新首页卡片和详情页，保持一致

### 改图表
图表是用 Python matplotlib 生成的。如果你想重新生成：
1. 修改 Python 脚本中的数据
2. 重新运行生成新的 PNG 图片
3. 替换同名文件，重新上传 GitHub

或者更简单：直接用 AI 工具（如 ChatGPT/Claude）生成新的数据图，替换 PNG 文件即可。

### 改颜色/风格
打开 `style.css`，修改 `:root` 里的变量：
- `--primary` → 主色调（默认蓝紫）
- `--secondary` → 强调色（默认金黄）
- `--dark` → 深色背景
- `--light` → 浅色背景

改一个地方，所有页面同步生效。

### 添加新详情页
1. 复制一个现有的 `detail-xxx.html`
2. 修改标题、内容、图表引用
3. 在首页 `index.html` 的 hot-grid 里加一个卡片，链接到新页面

## 内容更新建议（保持热度）

这个网站的生命力在于**持续更新**。建议节奏：

| 频率 | 更新内容 | 操作 |
|------|---------|------|
| **每周** | 首页"本周最热"数据 | 修改 `index.html` 里的数字和描述 |
| **每月** | 风口趋势图比例 | 调整 `index.html` 里的趋势条宽度 |
| **每季** | 重新生成图表 | 更新数据后替换 PNG 图片 |
| **随时** | 新工具/新风口 | 在首页和详情页添加新内容 |

## 后续可扩展功能

1. **更多详情页** — 每个热点都可以做更深入的分析（细分领域、地区对比、投融资详情）
2. **文章页面** — 加一个 `blog/` 目录，写更长的分析文章，SEO 效果更好
3. **邮件订阅** — 接入 ConvertKit / Mailchimp，自动发 AI 日报
4. **评论功能** — 接入 Disqus，让用户在详情页讨论
5. **搜索功能** — 加一个站内搜索，方便用户找内容
6. **广告变现** — Google AdSense、工具推广联盟链接
7. **多语言** — 加英文版页面，覆盖海外流量

## 为什么这个多页面结构更好？

| 优势 | 单页网站 | 多页面网站（当前） |
|------|---------|------------------|
| **SEO** | 只有一个页面被收录 | 6个详情页+首页都能被搜索引擎收录 |
| **用户停留时间** | 浏览一次就离开 | 用户可能看3-4个详情页，停留时间更长 |
| **内容深度** | 浅层概览 | 每个热点都有深入分析，专业感更强 |
| **分享传播** | 只能分享整个网站 | 可以分享某个具体热点的详情页 |
| **更新频率** | 更新一次改整页 | 可以单独更新某个热点详情页 |

## 免费 vs 付费成本

| 项目 | 费用 |
|------|------|
| GitHub Pages 托管 | ¥0（免费） |
| 域名（.github.io） | ¥0（免费） |
| 自定义域名（.com） | ¥60-100/年 |
| 流量限制 | 无明确限制 |
| HTTPS | 自动支持 |
| 图片/图表 | 免费托管在 GitHub 上 |

## 需要帮助？

- 改内容时看不懂代码：直接问我！
- 部署遇到问题：截图发给我，我帮你排查。
- 想加新功能：告诉我需求，我帮你实现。

---

**🎉 你现在拥有了一个专业的多页面AI主题网站，点击任意热点就能看到深度分析！**

下一步：按照上面的步骤上传到 GitHub Pages，网站就上线了。有问题随时问我！
