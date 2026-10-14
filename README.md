# GitHub 每日高增长项目 · 硬件 / Altium 仿真调研归档

> 由自动化任务每日更新。抓取 GitHub Trending（日 / 周 / 月榜 + 分语言榜）与 GitHub Search API，人工整理成中文报告。

**🌐 在线浏览：** https://3043451242-huiyi.github.io/github-trending-daily/

## 每期包含什么

| # | 内容 | 条目数 |
|---|---|---|
| 一 | Star 增长最快的高增长项目（含中文作用说明、增速口径标注） | Top 50 |
| 二 | 硬件电路设计 / 高速硬件设计相关项目（SI / PI / 时序 / 制造约束 / EDA 建库） | 10 + 备选 5 |
| 三 | Altium Designer 22+ 电路仿真（电流 / 热 / 电磁）相关项目与插件 | 36 |
| 四 | 落地建议 | 5 |

另有**本期榜单变化**：与上期快照对比，标注新进 / 掉出的项目。

## 关于 Altium Designer 22+ 仿真的核心结论

**GitHub 上不存在「直接嵌入 AD 22+ 内部、开箱做电流 / 热 / 电磁仿真」的成熟开源插件。**
AD 22+ 的仿真由三条线各管一块：

- **电流 →** Power Analyzer by Keysight（AD 22.10+ 扩展，PI-DC：电压降 / 电流密度 / 过孔电流）
- **高速信号与电磁 →** SI Analyzer by Keysight（Open Beta：阻抗 / 延迟 / 插入损耗 / 回波损耗）
- **热 →** AD 无原生热求解器，需走 Ansys Icepak（可直接导入 AD 的 ECAD 数据）

开源社区的角色是给 AD 做**仿真数据的导入导出、前后处理与自动化**：

```
AD 导出网表 / 叠层 / Gerber / 3D
   ├─ 电流：ngspice / PySpice / Xyce
   ├─ 热  ：Elmer / heatrapy
   └─ 电磁：openEMS / gerber2ems
   （或经 altium2kicad 转 KiCad 后用 kicad-rfsim 等）
```

社区最活跃的方向是**元件库 + 文件解析/转换 + MCP 自动化**（eda-agent、altium-mcp、altium_monkey 等 12 个）。

## 目录结构

```
site/
├── index.html             归档首页（按日期倒序列出全部期数）
├── daily/YYYY-MM-DD.html  每日完整报告
├── data/YYYY-MM-DD.json   当日结构化数据快照
├── data/_latest.json      最新一期摘要指标
└── .nojekyll
```

## 数据口径

- **Trending 榜条目**：★/天 = 官方公布的**周期净增 Star ÷ 周期天数**（更贴近"当下最热"）
- **Search API 条目**：★/天 = 仓库**累计 Star ÷ 建仓至今天数**（更能反映"出道即爆"）

两种口径在表中已分列标注。Star 数持续变动，数值仅代表采集时刻的快照；选型前请以仓库自身文档为准。

---

*本仓库由自动化任务生成与发布。*
