# 旅途有谱 · Travel Planner Mini Program

> 把收藏地点整理成可调整的逐日行程。

![Taro 4](https://img.shields.io/badge/Taro_4-0F766E?style=flat-square) ![React](https://img.shields.io/badge/React-0F766E?style=flat-square) ![TypeScript](https://img.shields.io/badge/TypeScript-0F766E?style=flat-square)

**在线体验：** [打开产品](https://echohux.github.io/travel-planner-miniapp/) · [验收与迭代记录](./docs/EVALUATION.md)

![旅途有谱 · Travel Planner Mini Program 项目封面](./docs/assets/readme-cover.svg)

## 项目简介

面向已经安排机酒、仍需要组织每日游览路线的旅行者。产品将景点选择、日期分配、酒店出发排序和本地保存串成一个微信小程序 MVP，并提供 H5 体验版。

项目重点解决以下问题：

- 地点分散：把想去的景点集中到待规划清单。
- 排程费时：兼顾手动分配与自动均衡安排。
- 路线难读：以酒店为起点组织顺序，并展示交通估算与预约提醒。

## 核心能力

- 搜索并选择北京、上海的内置景点。
- 小程序端通过微信原生地图选点添加地点。
- 手动指定日期，或自动生成均衡行程。
- 基于坐标距离估算，从酒店出发排列每天路线。
- 交通建议、预约提醒，以及行程本地保存、置顶与删除。

## 产品流程 · Pipeline

```text
设置行程与酒店 → 搜索 / 地图选点
    ↓
汇总待游览景点
    ↓
手动分日 / 自动均衡分配
    ↓
按酒店出发距离排序
    ↓
展示逐日路线、交通估算与预约提醒
    ↓
保存到本地 → 置顶 / 查看 / 删除
```

自动排程和交通建议基于本地规则与坐标距离估算。当前没有接入实时导航、真实预约交易或模型 Agent。微信地图选点与 H5 演示能力应分开验收。

## 评测闭环

将核心任务、状态反馈与稳定性分开验收，再保留失败样例进行回归：

| 层级 | 验收关注点 |
| --- | --- |
| 结果质量 | 核心流程是否完成，输出或记录是否符合输入 |
| 过程质量 | 必要状态、异常反馈、数据一致性与可恢复性 |
| 稳定性 | 刷新与重复操作、依赖故障、存储或发布边界 |

```text
体验核心流程 → 记录实际结果 → 标注 Good / Bad / Boundary Case
      ↑                                      ↓
回归同一组用例 ← 修复并对比结果 ← 定位规则 / 数据 / 交互 / 依赖原因
```

这是本次补充的验收与迭代规范，尚未代表已经完成评测、建立自动化平台或取得量化成绩。项目专属用例与待填写记录见 [EVALUATION.md](./docs/EVALUATION.md)。

## 技术架构

- 跨端框架：Taro 4、React、TypeScript、Sass。
- 源码包中的 `src/pages/`：行程、景点选择、日期分配与详情页面。
- 源码包中的 `src/utils/route.ts`：距离、交通方式和时间估算。
- 源码包中的 `src/utils/storage.ts`：Taro 本地存储、置顶与删除。
- 公开仓库 `docs/`：H5 构建产物；源码归档为 ZIP。

**技术栈：** Taro 4 · React · TypeScript · Sass · WeChat APIs。

## 本地运行

预览现有 H5 静态产物：

```bash
python3 -m http.server 8080 --directory docs
```

打开 `http://localhost:8080/`。开发请下载并解压 [源码包](./travel-planner-miniapp-source.zip)：

```bash
cd travel-planner-miniapp
pnpm install
pnpm dev:h5
# 微信小程序构建
pnpm build:weapp
```

小程序构建后用微信开发者工具导入，并根据自身发布环境配置 AppID。H5 部署到项目子路径时需检查 `config/index.ts` 中的 `h5.publicPath`。

## 部署

现有 Pages workflow 直接部署 `docs/`，只在 `docs/**` 或 workflow 变更时自动触发，也支持手动执行。修改 ZIP 中的源码不会自动重建 H5。微信正式发布需要自己的 AppID 及平台审核。

## 项目结构

```text
docs/                             # H5 演示构建产物
travel-planner-miniapp-source.zip  # Taro 项目源码
.github/workflows/                # Pages 静态部署
docs/EVALUATION.md                # 验收用例与记录规范
```

## 产品取舍与边界

行程保存在当前设备，不提供账号云同步。路线使用直线距离及系数推算，交通方式、时间与预约提醒不能视为实时导航或实时预约结果。公开配置使用游客 AppID 占位。

## 项目背景

项目通过 Vibe Coding 构建，产品关注点包括需求定义、任务流程、交互优先级与快速验证。本次说明文档参考 [FlowCraft AI](https://github.com/FILPPED-jin/FlowCraft-AI-Product) 的项目展示结构，按本仓库实际内容重新组织。
