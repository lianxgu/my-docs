










# ecode AI 自动开发工具

## 简介

ecode AI 自动开发工具是一套智能代码生成系统，专为 **E10 e-code 在线开发平台**设计。通过 11 个专业技能（Skill），你只需要用**口语化的自然语言描述需求**，AI 就能自动分析需求类型、创建标准项目结构、生成完整的前端二开代码，打包并自动上传到 E10 平台。

> **核心理念**：你说需求，AI 写代码、搭项目、打包、上传一条龙。

---

## 适用 IDE

| IDE | 说明 |
|-----|------|
| **CodeBuddy** | 腾讯云内部 AI IDE |
| **Trae** | 字节跳动 AI IDE |
| **Qoder** | 支持 CodeBuddy 风格 Skill 体系 |

导入项目后 Skill 自动生效，操作方式完全相同。CodeBuddy / Qoder 读取 `.codebuddy/skills/`，Trae 读取 `.trae/skills/`。

---

## 技术架构

```
┌─────────────────────────────────────────────────────────────────────────┐
│                           ecode AI 自动开发工具                          │
├─────────────────────────────────────────────────────────────────────────┤
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────┐ ┌──────────────┐ │
│  │ scaffold │ │   dev   │ │workflow │ │    form     │ │     api      │ │
│  │ 项目脚手架 │ │ 前端开发 │ │ 流程二开  │ │  表单二开    │ │ 接口拦截请求  │ │
│  └────┬─────┘ └────┬─────┘ └────┬─────┘ └──────┬──────┘ └──────┬───────┘ │
│       │             │            │               │               │         │
│  ┌────┴─────────────┴────────────┴───────────────┴───────────────┴─────┐  │
│  │                         AI 智能路由 & 代码生成                       │  │
│  └─────────────────────────────────┬───────────────────────────────────┘  │
│                                    │                                      │
│  ┌────────────┬───────────────────┴──────────────────┬─────────────────┐ │
│  │ base-comps │              ecode-runtime            │   packager     │ │
│  │  基础组件   │      全局对象 TEAMS/weappUtils       │    构建打包     │ │
│  └────────────┴──────────────────────────────────────┴─────────────────┘ │
│                                    │                                      │
│  ┌─────────────────────────────────┴─────────────────────────────────┐  │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐                        │  │
│  │  │e10-login │  │  upload  │  │doc-fetcher│     ← 运维辅助         │  │
│  │  │ 自动登录  │  │ 自动上传  │  │ 文档抓取  │                        │  │
│  │  └──────────┘  └──────────┘  └──────────┘                        │  │
│  └───────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────┘
```
# 文档仓库测试
这是用来学习Git的测试仓库。
- 练习新增文件
- 练习删除文件
- 练习版本回滚

---

## 核心亮点：AI 自动进化的开发工具

传统的 IDE 或开发工具依赖固定的文档和模板，用一次就过时。而 ecode AI 开发工具是一套**不断自我进化的 AI 辅助开发体系**：

1. **自然语言驱动** —— 用口语化中文描述需求，AI 自动分析需求类型、规划项目结构、生成完整代码，无需手写一行代码
2. **持续学习** —— 每次处理完真实需求项目后，复盘总结代码精华和开发经验，持续进化为新的专业技能
3. **技能驱动开发** —— 11 个专业 Skill 覆盖 ecode 二开全场景：项目脚手架、流程二开、表单二开、接口拦截、组件复写、基础组件、全局运行时对象、自动打包、自动上传
4. **自我迭代** —— 随时可扩展新技能，一个项目从需求到上线的全部经验会沉淀为更强大的开发能力

---

## 能力矩阵

### 核心开发技能（8 个）

| 技能 (Skill) | 擅长领域 | 一句话说明 |
|---|---|---|
| **ecode-scaffold** | 项目脚手架 | 从零创建标准 ecode 项目目录和入口文件 |
| **ecode-workflow** | 流程详情页 | 操作按钮/菜单、页签扩展、签字意见、指定流转、批量操作、触发事件 |
| **ecode-form** | 表单引擎 | 字段读写、属性控制（必填/只读/隐藏）、明细表操作、事件注册、提交校验 |
| **ecode-api** | 接口拦截与请求 | axios/fetch/weappUtils 多种请求方式、请求/响应拦截器、async 拦截器模式 |
| **ecode-dev** | 前端组件 | 组件参数复写、组件替换、单页开发、自定义组件、mobx 状态管理 |
| **ecode-base-comps** | 组件参考 | @weapp/ui 33 个组件 API 速查（Button/Table/Browser/Select 等） |
| **ecode-runtime** | 运行时全局对象 | TEAMS(用户/租户)、weappUtils(请求/复制)、weappUi(消息/确认)、ebuilderSDK(ESB) |
| **ecode-packager** | 构建打包 | ES Module 编译为 CommonJS、生成 ecode.json、打包 zip |

### 运维辅助技能（3 个）

| 技能 (Skill) | 擅长领域 | 一句话说明 |
|---|---|---|
| **ecode-upload** | 自动上传部署 | 自动登录 E10 → 选项目 → 导入 zip 包全流程 |
| **e10-login** | 无头登录 | Edge + Playwright 自动登录，保存 cookies 供免登使用 |
| **doc-fetcher** | 文档抓取 | 从 e-cology 文档平台拉取文档保存为 markdown |

### 智能路由

AI 会根据你的需求描述**自动识别**应该使用哪些技能：

| 需求关键词 | 自动匹配技能 |
|---|---|
| 「流程」「审批」「提交」「退回」「按钮」「页签」「会签」「加签」「指定流转」「子流程」 | ecode-workflow |
| 「表单」「字段」「必填」「只读」「隐藏」「明细表」「求和」「联动」「浏览按钮」 | ecode-form |
| 「接口」「请求」「拦截」「修改参数」「返回值」「提交前」「提交后」「返回数据」 | ecode-api |
| 「替换组件」「改样式」「复写参数」「新页面」「自定义组件」 | ecode-dev |
| 「组件」「Button」「Dialog」「Table」「Browser」「Select」「Checkbox」 | ecode-base-comps |
| 「当前用户」「发送请求」「消息提示」「确认框」「ESB流程」「剪贴板」「多语言」 | ecode-runtime |
| 「打包」「生成 ecode.json」 | ecode-packager |
| 「上传」「部署到 ecode」 | ecode-upload |

---

## 已生成项目一览

> **提示**：以下为工具首批产出的 29 个真实项目。解压后 `apps/` 目录初始为空，可通过 AI 对话从零生成新项目。

| # | 项目名称 | 能力类型 | 涉及 Skill |
|---|----------|----------|------------|
| 1 | 完整视图按钮隐藏 | 流程按钮 | ecode-workflow, ecode-dev |
| 2 | 去除表单 HTML 标签 | 表单数据处理 | ecode-api |
| 3 | 流程留言功能 | 流程按钮 | ecode-workflow, ecode-dev |
| 4 | 流程按钮移至表单下方 | 流程按钮位置 | ecode-dev, ecode-workflow |
| 5 | 字段值后端校验 | 表单校验 | ecode-form, ecode-api, ecode-runtime |
| 6 | 组织人员管理 | 自定义页面 | ecode-dev, ecode-base-comps |
| 7 | 世界杯数据中心 | 自定义页面 | ecode-dev, ecode-base-comps |
| 8 | 流程跳转百度 | 流程按钮 | ecode-workflow |
| 9 | 流程提交后回调 | 流程操作 | ecode-workflow |
| 10 | 流程状态默认点击已操作 | 流程列表 | ecode-workflow |
| 11 | 修改 Browser 组件属性 | 组件复写 | ecode-dev, ecode-base-comps |
| 12 | 替换 Icon 组件 | 组件替换 | ecode-dev |
| 13 | 指定流转不弹窗提交开发 | 流程操作 | ecode-workflow |
| 14 | 指定流转开发 | 流程操作 | ecode-workflow |
| 15 | 按安全级别屏蔽批量提交 | 列表操作 | ecode-api, ecode-runtime, ecode-workflow |
| ...
---

## 工作区目录结构

```
ecodeDev/
├── apps/                          ← 所有生成的应用在此（初始为空）
│   └── 序号、应用名称/             ← 如 "1、流程提交确认"
│       ├── entry.js               ← 前置入口（自动执行，注册钩子）【必须】
│       ├── index.js               ← 非前置入口（按需创建）
│       ├── index.css              ← 根目录样式（按需创建）
│       ├── config/                ← 配置目录【必须】
│       │   ├── config.js          ← 业务配置
│       │   ├── config_default.js  ← 默认配置（空文件）
│       │   ├── configLoad.js      ← 配置加载
│       │   └── configLoad_default.js
│       ├── coms/                  ← 自定义组件（按需创建）
│       ├── styles/                ← 样式（按需创建）
│       ├── resources/             ← 静态资源（按需创建）
│       ├── utils/                 ← 工具函数（按需创建）
│       └── build/                 ← 构建产物（自动生成）
│           ├── {32位Hex}/
│           │   └── ecode.json
│           └── {应用名}.zip        ← 最终产物，用于上传
├── e10_info/                      ← E10 环境配置
│   └── e10_config.json            ← 配置 E10 地址/账号/密码（上传时需要）
├── package-tool/                  ← 打包工具
│   ├── build.js                   ← 构建脚本
│   ├── appUUIDs.json              ← 项目 UUID 注册表
│   └── node_modules/              ← 构建依赖（Babel 等）
├── .codebuddy/skills/             ← Skill 定义（CodeBuddy / Qoder）
├── .trae/skills/                  ← Skill 定义（Trae IDE）
├── 使用文档/                       ← 使用手册与参考文档
└── README.md                      ← 本文件
```

### 项目命名与开发规范

**① 命名规则**
- 格式：`序号、应用名称`，如 `1、流程提交确认`
- 序号自动递增，分隔符用中文顿号 `、`
- 打包自动剥离序号前缀，最终 zip 包名不含序号

**② 标准项目结构**
- 必含文件：`entry.js`、`config/config.js`、`config/config_default.js`、`config/configLoad.js`、`config/configLoad_default.js`
- 按需文件：`index.js`、`index.css`、`coms/`、`styles/`、`resources/`、`utils/`

**③ 开发质量清单**
1. 用 `weId` / `workflowId` 限定生效范围，避免全局污染
2. `regOvProps` 回调必须 `return props`
3. 拦截事件回调必须调用 `successFn()` 或 `failFn()`
4. 异步组件用 `React.lazy + Suspense + asyncImport` 包裹
5. CSS 类名加 `app-${appId}-` 前缀
6. `entry.js` 不引入 `@weapp/ui` 组件（使用 jsonp.require 延迟加载）
7. 表单 SDK 实例不长期持有（每次用 `getWeFormInstance()` 重新获取）
8. 组件替换用 `React.forwardRef` 传递 ref

---

## 开发文档

以下文档位于 `使用文档/` 目录下：

| 文档 | 说明 |
|------|------|
| `ecodeDev-使用手册.html` | 完整使用手册（解压→导入→开发→打包→上传全流程） |
| `ecode-upload使用说明.md` | 自动上传工具详细说明 |
| `ecode-packager使用说明.md` | 构建打包工具详细说明 |

---

## 快速开始

1. **解压** `ecodeDev.7z` 到本地目录（路径不含中文和空格）
2. **配置 E10 环境**（可选，仅自动上传时需要）：编辑 `e10_info/e10_config.json`
3. **打开 IDE**（CodeBuddy / Trae / Qoder），导入解压后的目录
4. **用自然语言描述需求**，AI 自动在 `apps/` 下创建项目并生成代码
5. **说"帮我打包"** 自动编译为 ecode.json + zip
6. **说"上传到 ecode"** 自动登录 E10 并导入 zip 包

### 对话示例

**① 流程操作 — 提交确认**
```
在流程详情页的提交按钮旁边加一个「紧急申请」按钮。
点击后先弹窗确认，确认后自动提交。只对工作流 ID 为 731260655157936133 的流程生效。
```
> 对应的项目：`apps/20、流程提交确认/`，主要使用 ecode-workflow

**② 表单联动 — 字段求和**
```
表单中有「金额A」「金额B」「金额C」三个字段，任一变化时自动计算总和填入「合计」字段。
```
> 对应的项目：`apps/25、表单字段求和/`，主要使用 ecode-form

**③ 接口拦截 — 修改提醒方式**
```
流程提交时，自动将提醒方式设为邮件提醒，关闭短信提醒。
```
> 对应的项目：`apps/27、流程提醒方式展示/`，主要使用 ecode-api + ecode-workflow

**④ 组件替换 — 签字意见图标**
```
把流程签字意见输入框工具栏的图标替换为自定义图标。
```
> 对应的项目：`apps/12、替换Icon组件/`，主要使用 ecode-dev + ecode-workflow

**⑤ 下拉联动 — 选项变化清空附件并调用 ESB**
```
表单「类型」下拉框切换时，自动清空已上传附件，并调用 ESB 流程获取最新配置。
```
> 对应的项目：`apps/17、下拉框联动清空与ESB调用/`，主要使用 ecode-form + ecode-runtime

**⑥ 安全控制 — 按密级屏蔽批量提交**
```
当流程密级为高级别时，列表批量提交按钮禁止使用。
```
> 对应的项目：`apps/15、按安全级别屏蔽批量提交/`，主要使用 ecode-api + ecode-runtime + ecode-workflow

**⑦ 页签扩展 — 内嵌外部页面**
```
在流程详情页加一个新标签页，嵌入百度搜索 iframe。
```
> 对应的项目：`apps/22、流程页签展示百度/`，主要使用 ecode-workflow（overrideTbas）

---

## 构建打包

```bash
# 方式一：从根目录指定项目
node package-tool/build.js --project=流程提交确认

# 方式二：在子项目目录内执行
cd apps/流程提交确认 && node ../../package-tool/build.js

# 方式三：用自然语言告诉 AI（推荐）
帮我打包 流程提交确认
```

构建产物位于子项目的 `build/` 目录：
- `{32位Hex}/ecode.json` — 编译后的入口文件
- `{应用名}.zip` — 最终发布包，用于上传

---

## 自动上传

说「上传到 ecode」即可触发自动上传流程：

1. 读取 `e10_info/e10_config.json` 获取登录信息
2. Edge 无头浏览器自动登录 E10
3. 进入 ecode 项目管理，匹配目标项目（不存在则自动创建）
4. 点击导入 → 选择 zip → 确认 → 完成

前置条件：E10 环境可访问，`e10_config.json` 已正确配置。如不需要自动上传可跳过，手动在 E10 管理端导入 zip 包即可。上传时如需禁止生成截图，加 `--no-screenshot` 参数。

---

## 技术栈

- **前端框架**：React + JSX + ES6/CSS
- **核心库**：`@weapp/utils`、`@weapp/ecodesdk`、`@weapp/ui`
- **构建工具**：Babel（ES Module → CommonJS）+ 自定义 jsonp 加载器
- **自动上传**：Playwright + Edge 无头浏览器

---

## 注意事项

1. **前置加载文件**（`entry.js`）只能用 `React`、`ReactDOM`、`@weapp/utils`、`@weapp/ecodesdk`、`axios`
2. 异步组件必须使用 `React.lazy` + `asyncImport` 懒加载
3. CSS 类名必须加 `app-${appId}-` 前缀防止样式污染
4. API 调用受**准入白名单**管控，需先在 ecode 监控平台配置
5. 源码中 emoji 请使用实际字符，避免 `\uXXXX` 转义序列
6. 上传时如需禁止生成截图，加 `--no-screenshot` 参数
