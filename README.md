# 大转盘抽签系统 / Lucky Wheel

> **单页 HTML 大转盘抽签工具，零依赖、离线可用、数据本地持久化。适合晨会点名、活动抽奖等小团队场景。**
>
> *Single-file HTML lucky wheel & random picker. Zero dependencies, offline-ready, local persistence. Ideal for morning meetings, roll calls, and small-team giveaways.*

主持人电脑接大屏投影，随机抽取员工参与情景演练。纯前端单页应用，双击即用。

A single-page front-end app for hosts to project on a big screen and randomly pick employees for scenario drills. Double-click to run.

## 效果预览 / Preview

**在线体验 / Live Demo**：https://levi4433.github.io/lucky-wheel/

![大转盘抽签系统预览](docs/preview.png)

## 功能特性 / Features

- **员工管理 / Employee Management**：增删改姓名（上限 50 人），重名自动拦截
- **三级状态机 / 3-State Machine**：空闲 → 已上盘 → 已抽中，点击上盘、再点下盘
- **抽签动画 / Spin Animation**：Canvas 2D 绘制转盘，3 秒缓动旋转，5~8 圈随机停止，扇区高亮闪烁
- **重置 vs 刷新 / Reset vs Refresh**：重置保留历史记录重抽；刷新清空历史开新一轮
- **历史记录 / History**：倒序展示，关闭浏览器不丢失
- **持久化 / Persistence**：`localStorage` 存储，重启电脑数据仍在
- **响应式 / Responsive**：横屏（左转盘右面板）/ 竖屏（上转盘下面板）自适应
- **零网络依赖 / Zero Network**：纯前端，无 CDN、无后端、无任何外部请求

## 快速开始 / Quick Start

```bash
# 方式 1：直接双击 index.html 用浏览器打开 / Option 1: double-click index.html
# 方式 2：命令行启动 / Option 2: command line
start index.html        # Windows
open index.html         # macOS
xdg-open index.html     # Linux
```

首次打开会自动生成 12 个空白槽位，点击空白按钮输入姓名即可开始。

On first launch, 12 empty slots are auto-generated. Click an empty slot to enter a name and start.

## 使用流程 / Workflow

1. 点击空白按钮 → 输入员工姓名（重名会被拦截）
2. 点击已命名的按钮 → 名字加入转盘（按钮变灰）
3. 再次点击灰色按钮 → 下盘（按钮恢复彩色）
4. 点击转盘中心「开始」按钮 → 旋转 3 秒后停止，右侧显示中签者
5. 中签者按钮变深灰禁用，历史记录自动追加
6. 顶部「重置」重抽本轮 / 「刷新」开启新一轮

1. Click an empty slot → enter a name (duplicates are blocked)
2. Click a named button → name joins the wheel (button turns grey)
3. Click a grey button again → remove from wheel (button turns colored)
4. Click the center "Start" button → spins 3s, winner shown on the right
5. Winner's button is disabled, history auto-appended
6. Top bar "Reset" re-draws this round / "Refresh" starts a new round

## 目录结构 / Project Structure

```
lucky-wheel/
├── index.html      # 单文件应用（HTML + CSS + JS 全部内联）/ Single-file app
├── README.md       # 项目说明 / Project doc
└── LICENSE         # MIT
```

## 技术栈 / Tech Stack

| 项目 / Item | 选型 / Choice |
|---|---|
| 标记 / Markup | 原生 HTML5 / Native HTML5 |
| 样式 / Style | 原生 CSS3（含 `backdrop-filter` 毛玻璃、CSS 动画）/ Native CSS3 |
| 脚本 / Script | Vanilla JavaScript (ES6) |
| 存储 / Storage | `localStorage`（键名 `wheelData`） |
| 绘图 / Canvas | Canvas 2D API |
| 依赖 / Deps | 无 / None（不引入任何 CDN / 第三方库 / 框架） |

## 浏览器兼容 / Browser Support

Chrome 90+ / Edge 90+ / Safari 14+ / Firefox 88+

## 数据安全 / Data Safety

- 所有数据仅存储在浏览器 `localStorage`，不联网、不上传
- 清除浏览器缓存会丢失员工名单与历史记录（建议定期手动备份名单）
- 不同浏览器、不同电脑的数据相互独立

- All data stays in browser `localStorage`, no network, no upload
- Clearing browser cache loses names & history (back up manually)
- Different browsers / computers have independent data

## 设计理念 / Design

- **金融极简风 / Finance Minimal**：深邃蓝黑 + 暖金质感，禁用绿色系
- **悬念感 / Suspense**：先快后慢的缓动曲线（`cubic-bezier(0.17, 0.67, 0.12, 0.99)`）
- **大屏友好 / Big Screen**：1920×1080 投影适配，字号自动放大
- **小白可用 / Beginner Friendly**：双击即运行，无安装、无配置

## License

[MIT](./LICENSE)
