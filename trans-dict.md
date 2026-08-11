# VDA 5050 EN-ZH 翻译字典

## 1. 使用说明

- 本字典适用于 VDA 5050 V2.1.0、V3.0.0 和 V3.0.1 中文翻译及复核。
- “ZH 统一译法”用于自然语言正文；协议字段、主题、动作和枚举仍应保留原始标识符。
- 同一英文词在不同协议语境下可能使用不同译法，应以“使用边界”列为准。
- “适用版本”中的 `2.1.0-3.0.1` 表示三个版本均适用；单独的 `2.1.0`、`3.0.0` 或 `3.0.1` 表示仅适用于该版本。翻译其他版本时应重新对照对应版本的英文文档和 Schema。
- 字典未覆盖的术语不得直接套用通用机器翻译结果，应先核对上下文、同版本 Schema 和本文档既有用法。
- 与格式、规范性措辞有关的详细规则见 [trans-guide.md](./trans-guide.md)。

### 当前 V2.1.0 版本边界

V2.1.0 与 3.x 的数据模型存在字段差异。翻译 V2.1.0 时保留以下原始标识符，不得套用 3.0.1 的替换规则：

| V2.1.0 标识符 | 使用边界 |
| --- | --- |
| `lhd` | `pick`/`drop` 动作的载荷搬运装置参数；3.0.1 才改为 `loadHandlingDevice`。 |
| `.load` | V2.1.0 `pick`/`drop` 关联的状态路径；不得因 3.x 的 `loads` 数组规则回写。 |
| `resultDescription` | V2.1.0 `actionState` 的结果说明字段；3.x 的 `actionResult` 替换不适用于本版本。 |
| `agvPosition` | V2.1.0 状态中的当前位置对象；与 3.x 的字段拆分规则分别核对。 |
| `initPosition` | V2.1.0 即时动作名及其完成状态字段；位置字段使用 `.agvPosition.x/.y/.theta/.mapId`，`lastNodeId` 按状态字段契约位于顶层。 |
| `TEACHIN` | V2.1.0 `operatingMode` 枚举值，保留原拼写。 |
| `agvGeometry` / `vehicleConfig` | V2.1.0 factsheet 对象名称，按本版本表格层级和字段名翻译。 |
| `factsheet` 字段 | V2.1.0 中 `actions.actionsParameters`、`optionalParameters` 等字面属性按英文原文保留；发现与 Schema 冲突时记录问题。 |

## 2. 核心参与方与通信

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| mobile robot | 移动机器人 | 2.1.0-3.0.1 | VDA 5050 的通信主体；不缩写为“机器人”，除非同一句中不会产生歧义。 |
| fleet control | 车队控制 | 2.1.0-3.0.1 | 指控制角色或功能；不使用“车队管理”。字段或产品名称另行保留原名。 |
| fleet control system | 车队控制系统 | 2.1.0-3.0.1 | 仅当 EN 明确包含 `system` 时使用。 |
| operator | 操作人员 | 2.1.0-3.0.1 | 指执行操作的人；不得与 `operating mode` 混淆。 |
| system integrator | 系统集成方 | 2.1.0-3.0.1 | 用于系统集成责任、参数约定和部署语境。 |
| mobile robot manufacturer | 移动机器人制造商 | 2.1.0-3.0.1 | `manufacturer` 字段名保持不变。 |
| sender | 发送方 | 2.1.0-3.0.1 | 消息或字段的发送主体。 |
| receiver | 接收方 | 2.1.0-3.0.1 | 消息或字段的接收主体。 |
| transport protocol | 传输协议 | 2.1.0-3.0.1 | 第 4 章语境。 |
| communication topic | 通信主题 | 2.1.0-3.0.1 | MQTT 主题名本身使用反引号并保持原值。 |
| topic hierarchy | 主题层级 | 2.1.0-3.0.1 | `/` 分隔的 MQTT 主题结构。 |
| MQTT broker | MQTT 代理服务器 | 2.1.0-3.0.1 | 上下文已明确 MQTT 时可简称“代理服务器”。 |
| quality of service (QoS) | 服务质量（QoS） | 2.1.0-3.0.1 | QoS 等级和名称保持协议原文。 |
| message | 消息 | 2.1.0-3.0.1 | 指通过主题传输的协议消息。 |
| protocol header | 协议头 | 2.1.0-3.0.1 | 不使用“报文头”；字段 `headerId` 保持不变。 |
| connection | 连接 | 2.1.0-3.0.1 | 主题名写作 `connection`；叙述通信连接时使用中文。 |
| state | 状态 | 2.1.0-3.0.1 | 主题名写作 `state`；“状态消息”用于对应 state message。 |
| visualization | 可视化 | 2.1.0-3.0.1 | 主题名写作 `visualization`；消息称“可视化消息”。 |
| factsheet | 信息表 | 2.1.0-3.0.1 | 主题名写作 `factsheet`；消息称“信息表消息”。 |
| request | 请求 | 2.1.0-3.0.1 | 指协议请求对象或请求行为。 |
| response | 响应 | 3.0.0-3.0.1 | 单个响应对象使用 `response`；MQTT 主题使用复数 `responses`。不得因主题名为复数而改写对象名。 |
| responses message | `responses` 消息 | 3.0.1 | 3.0.1 将章节标题和正文统一为复数消息名；消息中的数组元素仍为单数 `response` 对象。 |
| request/response mechanism | 请求/响应机制 | 3.0.0-3.0.1 | 保留斜杠，不写成“请求应答机制”。 |

## 3. 移动、导航与几何

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| moving | 移动 | 2.1.0-3.0.1 | 指空间位置或朝向发生变化的状态，包括机器人组件运动。 |
| driving | 行驶 | 2.1.0-3.0.1 | 指移动机器人具有非零平移和/或旋转速度的工作状态。 |
| automatic driving | 自动行驶 | 2.1.0-3.0.1 | 移动机器人在无人直接干预下行驶。 |
| manual driving | 手动行驶 | 2.1.0-3.0.1 | 移动机器人在人员直接控制下行驶。 |
| line-guided mobile robot | 线导引移动机器人 | 2.1.0-3.0.1 | 不使用“线路引导式移动机器人”“线引导”或“线导”。 |
| freely navigating mobile robot | 自由导航式移动机器人 | 2.1.0-3.0.1 | 指自主规划轨迹的移动机器人。 |
| kinematic center | 运动学中心 | 2.1.0-3.0.1 | 区域分类、走廊、图注和正文统一使用。 |
| control point | 控制点 | 2.1.0-3.0.1 | 指移动机器人用于位置或偏差判断的控制参考点。 |
| position | 位置 | 2.1.0-3.0.1 | 描述坐标位置；字段名如 `mobileRobotPosition` 保持不变。 |
| orientation | 朝向 | 2.1.0-3.0.1 | 用于姿态概念；不与行驶矢量“方向”混用。 |
| orientation angle | 朝向角 | 2.1.0-3.0.1 | 用于 `theta` 或以弧度表示的姿态角数值。 |
| direction | 方向 | 2.1.0-3.0.1 | 用于行驶方向或速度矢量。 |
| velocity | 速度 | 2.1.0-3.0.1 | 根据字段区分线速度和角速度；x/y/z 轴保持小写。 |
| trajectory | 轨迹 | 2.1.0-3.0.1 | 指订单、边或 NURBS 定义的轨迹。 |
| path | 路径 | 2.1.0-3.0.1 | 泛指规划或执行路径，不与数据对象 `trajectory` 混用。 |
| planned path | 规划路径 | 3.0.0-3.0.1 | 字段名保持 `plannedPath`。 |
| intermediate path | 中间路径 | 3.0.0-3.0.1 | 字段名保持 `intermediatePath`；指近端航点及预计到达信息。 |
| waypoint | 航点 | 3.0.0-3.0.1 | `waypoint` 对象名保持不变。 |
| polyline | 折线 | 3.0.0-3.0.1 | 指由航点间线段组成的路径表达。 |
| corridor | 走廊 | 2.1.0-3.0.1 | 指边允许偏离轨迹的左右边界；字段名保持 `corridor`。 |
| contour | 轮廓 | 2.1.0-3.0.1 | 用于移动机器人及载荷外形与区域进入/离开判定。 |
| bounding box | 包围框 | 2.1.0-3.0.1 | 用于载荷或机器人几何包围框；对象字段名保持不变。 |
| envelope curve | 包络曲线 | 2.1.0-3.0.1 | 用于 `envelopes2d`、`envelopes3d` 等几何描述。 |
| x-axis / y-axis / z-axis | x 轴 / y 轴 / z 轴 | 2.1.0-3.0.1 | 坐标轴字母统一小写。 |
| Pi | `Pi` | 2.1.0-3.0.1 | 沿用 EN 文本形式，不替换为 `π`。 |

## 4. 订单、节点与边

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| order | 订单 | 2.1.0-3.0.1 | 主题名写作 `order`；运输业务语境可使用“运输订单”。 |
| active order | 活动订单 | 2.1.0-3.0.1 | 指移动机器人当前持有或执行的订单。 |
| order update | 订单更新 | 2.1.0-3.0.1 | 字段 `orderUpdateId` 保持不变。 |
| order cancellation | 订单取消 | 2.1.0-3.0.1 | 动作名保持 `cancelOrder`。 |
| order rejection | 订单拒绝 | 2.1.0-3.0.1 | 指移动机器人拒绝接收订单。 |
| node | 节点 | 2.1.0-3.0.1 | 图结构元素；字段名如 `nodeId`、`nodeStates` 保持不变。 |
| edge | 边 | 2.1.0-3.0.1 | 图结构元素；字段名如 `edgeId`、`edgeStates` 保持不变。 |
| node-edge graph | 节点-边图 | 2.1.0-3.0.1 | 描述订单路线的数据结构。 |
| sequence | 序列 | 2.1.0-3.0.1 | `sequenceId` 定义节点和边的交替顺序。 |
| traverse | 通过；驶过；穿越 | 2.1.0-3.0.1 | 按对象选择：通过节点、驶过边、穿越区域；避免算法语境的“遍历”。 |
| traversal | 通过；穿越 | 2.1.0-3.0.1 | 章节标题可写“节点与边的遍历”以保持既有锚点，但正文优先使用符合行驶语境的表达。 |
| trivially reachable | 可直接到达 | 2.1.0-3.0.1 | 强调无需额外路径规划；不使用“轻松到达”。 |
| released | 已释放 | 2.1.0-3.0.1 | 描述 `released = true` 的节点或边，不等同于区域“许可”。 |
| unreleased | 未释放 | 2.1.0-3.0.1 | 描述 `released = false` 的节点或边。 |
| base | 基础区 | 2.1.0-3.0.1 | 已释放节点和边的集合；不译为“基础”或“基线”，也不与 `zone` 混用。 |
| horizon | 预测区 | 2.1.0-3.0.1 | 未释放节点和边的集合；不译为“地平线”，也不与 `zone` 混用。 |
| base node / base edge | 基础区节点 / 基础区边 | 2.1.0-3.0.1 | 表示基础区中的节点或边。 |
| horizon node / horizon edge | 预测区节点 / 预测区边 | 2.1.0-3.0.1 | 表示预测区中的节点或边。 |
| decision point | 决策点 | 2.1.0-3.0.1 | 基础区的最后一个节点。 |
| stitching node | 拼接节点 | 2.1.0-3.0.1 | 订单更新中连接前后基础区的重复节点。 |
| deviation range | 偏差范围 | 2.1.0-3.0.1 | 节点位置和朝向允许偏差的统称。 |
| fluent movement | 连续、平稳行驶 | 2.1.0-3.0.1 | 不译为“动作流畅”。 |
| idle state | 空闲状态 | 2.1.0-3.0.1 | 指没有待执行节点、边或未完成动作的协议状态。 |

## 5. 动作与状态

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| action | 动作 | 2.1.0-3.0.1 | 指协议动作；不得在移动/行驶语境中泛化使用。 |
| instant action | 即时动作 | 2.1.0-3.0.1 | 主题名使用 `instantActions`；不得改成单数主题名。 |
| predefined action | 预定义动作 | 2.1.0-3.0.1 | 指规范预先定义的动作。 |
| action parameter | 动作参数 | 2.1.0-3.0.1 | 字段和对象名保持原值。 |
| action blocking type | 动作阻塞类型 | 2.1.0-3.0.1 | 枚举 `'NONE'`、`'SOFT'`、`'SINGLE'`、`'HARD'` 不翻译。 |
| action state | 动作状态 | 2.1.0-3.0.1 | 对象使用 `actionState`，数组使用 `actionStates`。3.0.1 已将“收到即时动作后添加 `actionStatus`”纠正为添加 `actionState`；`actionStatus` 仍是对象内的有效状态字段。 |
| action result | 动作结果 | 2.1.0-3.0.1 | V2.1.0 的结果说明字段为 `resultDescription`；V3.0.0/3.0.1 使用 `actionResult`。按所译版本保留对应标识符。 |
| operating mode | 操作模式 | 2.1.0-3.0.1 | 描述控制方式及允许交互；不译为“运行模式”，字段 `operatingMode` 保持不变。 |
| action scope | 动作范围 | 3.0.0-3.0.1 | 指动作适用于即时动作、节点、边或区域等范围。 |
| trigger condition | 触发条件 | 2.1.0-3.0.1 | 用于动作或流程开始条件。 |
| completion condition | 完成条件 | 2.1.0-3.0.1 | 用于动作或流程结束判定。 |
| retriable | 可重试 | 2.1.0-3.0.1 | 描述失败动作能否重试；枚举或列名保持原文格式。 |
| wake-up time | 唤醒时间 | 3.0.0-3.0.1 | 参数使用 `wakeUpTime`。3.0.1 进一步明确其值为 ISO 8601 UTC 时间戳，格式为 `YYYY-MM-DDTHH:mm:ss.fffZ`。 |

## 6. 区域、区域集与许可

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| zone | 区域 | 2.1.0-3.0.1 | 指 VDA 5050 区域对象；不得与 `base`/`horizon` 混淆。 |
| zone type | 区域类型 | 3.0.0-3.0.1 | `'BLOCKED'`、`'RELEASE'` 等枚举值不翻译。 |
| zone set | 区域集 | 2.1.0-3.0.1 | 主题和对象标识符保持 `zoneSet`。 |
| contour-based zone | 基于轮廓的区域 | 3.0.0-3.0.1 | 由机器人轮廓是否进入或离开区域确定状态。 |
| kinematic center-based zone | 基于运动学中心的区域 | 3.0.0-3.0.1 | 由运动学中心是否位于区域内确定状态。 |
| enter a zone / zone entry | 进入区域 | 3.0.0-3.0.1 | 不使用“进到区域”等口语表达。 |
| exit a zone / zone exit | 离开区域 | 3.0.0-3.0.1 | 不使用“从区域外”等方向不明表达。 |
| interactive zone | 交互式区域 | 3.0.0-3.0.1 | 指进入或区内行为需要请求/响应的区域。 |
| access permission | 通行许可 | 3.0.0-3.0.1 | 用于 `'RELEASE'` 区域的进入许可。 |
| approval | 批准；许可 | 3.0.0-3.0.1 | 请求被允许时使用；具体状态仍保留枚举 `'GRANTED'`。 |
| revoke / revoked | 撤销 / 已撤销 | 3.0.0-3.0.1 | 枚举值保持 `'REVOKED'`。 |
| lease expiry | 许可到期时间；许可到期 | 3.0.0-3.0.1 | 字段 `leaseExpiry` 保持不变；按语境区分字段和事件。 |
| release loss behavior | 通行许可失效行为 | 3.0.0-3.0.1 | 字段 `releaseLossBehavior` 保持不变；用于移动机器人已在区域内时，通行许可被撤销或到期后的行为。3.0.1 明确了 `STOP`、`EVACUATE`、`CONTINUE` 的请求保留、错误报告和终止条件。 |
| release-loss handling | 通行许可失效处理 | 3.0.1 | 指请求资源的通用失效处理，不局限于区域字段 `releaseLossBehavior`。已开始的操作保留请求并报告 `REVOKED`/`EXPIRED`，尚未开始的操作移除请求。 |
| request type | 请求类型 | 3.0.0-3.0.1 | 字段 `requestType` 保持不变。 |
| grant type | 授权类型 | 3.0.0-3.0.1 | 响应对象字段使用 `grantType`，取值为 `'GRANTED'`、`'QUEUED'`、`'REVOKED'`、`'REJECTED'`。3.0.1 已将正文中的错误字段名 `responseType` 统一为 `grantType`。 |
| request status | 请求状态 | 3.0.0-3.0.1 | 字段 `requestStatus` 保持不变；状态对象与响应决定的枚举边界应以同版本 Schema 为准。 |
| zone request | 区域请求 | 3.0.0-3.0.1 | 对象名保持 `zoneRequest`。 |
| corridor request | 走廊请求 | 3.0.0-3.0.1 | 指使用后续走廊前的许可请求。 |

## 7. 载荷、地图和数据模型

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| load | 载荷 | 2.1.0-3.0.1 | 指物理实体、载荷数据或承载能力。 |
| loaded | 载货 | 2.1.0-3.0.1 | 描述移动机器人的状态；不译为“已加载”。 |
| load handling device | 载荷搬运装置 | 2.1.0-3.0.1 | 自然语言译法适用于所有当前版本。V2.1.0/3.0.0 的 `pick`/`drop` 动作参数写作 `lhd`，3.0.1 才改为 `loadHandlingDevice`；按所译版本保留对应标识符。 |
| load position | 载荷位置 | 2.1.0-3.0.1 | 字段名保持 `loadPosition`。 |
| map | 地图 | 2.1.0-3.0.1 | 主题、字段和动作名中的 `map` 保持不变。 |
| map distribution | 地图分发 | 2.1.0-3.0.1 | 指向移动机器人传输或下载地图的流程。 |
| identifier | 标识符 | 2.1.0-3.0.1 | 用于 `orderId`、`nodeId` 等 ID 字段说明。 |
| globally unique identifier | 全局唯一标识符 | 2.1.0-3.0.1 | 不简化为“唯一 ID”，除非上下文已定义。 |
| timestamp | 时间戳 | 2.1.0-3.0.1 | 示例按 ISO 8601 JSON 字符串书写。 |
| protocol version | 协议版本 | 2.1.0-3.0.1 | `version` 示例不要求以 `v` 开头。 |
| manufacturer | 制造商 | 2.1.0-3.0.1 | 字段名保持 `manufacturer`。 |
| serial number | 序列号 | 2.1.0-3.0.1 | 字段名保持 `serialNumber`，注意小写 `s`。 |
| descriptor | 名称或描述符 | 2.1.0-3.0.1 | `nodeDescriptor`、`edgeDescriptor`、`actionDescriptor` 等均表示用户定义、人类可读的名称或描述符，不得用于逻辑目的。 |
| JSON object | JSON 对象 | 2.1.0-3.0.1 | JSON 与中文之间保留空格。 |
| JSON array | JSON 数组 | 2.1.0-3.0.1 | 对象表中数据类型可保留 `array`。 |
| JSON Schema | JSON Schema | 2.1.0-3.0.1 | 大小写和空格保持一致，不译为“JSON 模式”。 |
| required field | 必填字段 | 2.1.0-3.0.1 | 对象结构表第一列通常以普通或粗体表示。 |
| optional field | 可选字段 | 2.1.0-3.0.1 | 对象结构表第一列通常以斜体或粗斜体表示。 |
| basic data type | 基本数据类型 | 2.1.0-3.0.1 | 对应表格中的普通字段。 |
| non-basic data type | 非基本数据类型 | 2.1.0-3.0.1 | 指 JSON 对象、数组等需要单独定义的结构。 |
| default value | 默认值 | 2.1.0-3.0.1 | 数字、布尔值、字符串和枚举按各自格式表示。 |
| value range | 数值范围 | 2.1.0-3.0.1 | 统一使用 `[下限 ... 上限]` 形式。 |

## 8. 错误与诊断

| EN 术语 | ZH 统一译法 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| error | 错误 | 2.1.0-3.0.1 | 指协议错误对象或错误事件。 |
| error type | 错误类型 | 2.1.0-3.0.1 | 推荐句式为“类型为 `'...'` 的错误”。 |
| error level | 错误级别 | 2.1.0-3.0.1 | 推荐句式为“级别为 `'...'` 的错误”。 |
| error reference | 错误关联项 | 2.1.0-3.0.1 | 不译为“错误引用”，避免与文献引用混淆。 |
| error description | 错误描述 | 2.1.0-3.0.1 | 字段名保持 `errorDescription`。 |
| error hint | 错误提示 | 2.1.0-3.0.1 | 字段名保持 `errorHint`。 |
| warning | 警告 | 2.1.0-3.0.1 | 错误级别枚举 `'WARNING'` 保持不变。 |
| failure | 失败 | 2.1.0-3.0.1 | 区分执行失败与通信故障；字段或枚举保持原值。 |
| validation failure | 验证失败 | 2.1.0-3.0.1 | 错误类型保持 `'VALIDATION_FAILURE'`。 |
| release loss handling | 通行许可失效处理 | 3.0.1 | 错误类型保持 `'RELEASE_LOSS_HANDLING'`；用于区域内执行 `'EVACUATE'` 或 `'CONTINUE'` 时的警告。 |
| instant action states full | 即时动作状态列表已满 | 3.0.0-3.0.1 | 错误类型保持 `'INSTANT_ACTION_STATES_FULL'`，错误级别为 `'URGENT'`；3.0.1 将其补入预定义错误表和 `errorType` 枚举说明。 |
| zone action states full | 区域动作状态列表已满 | 3.0.0-3.0.1 | 错误类型保持 `'ZONE_ACTION_STATES_FULL'`，错误级别为 `'URGENT'`；3.0.1 将其补入预定义错误表和 `errorType` 枚举说明。 |
| report an error | 报告错误 | 2.1.0-3.0.1 | 完整句式应同时说明错误类型和级别（如原文提供）。 |
| report duration | 报告时长 | 2.1.0-3.0.1 | 指错误应持续保留在状态消息中的时间或条件。 |

## 9. 规范性和逻辑词

| EN 表述 | ZH 统一表达 | 适用版本 | 使用边界 |
| --- | --- | --- | --- |
| shall | 应；必须 | 2.1.0-3.0.1 | 规范要求；不得弱化为建议。 |
| shall not | 不得 | 2.1.0-3.0.1 | 明确禁止。 |
| must | 必须 | 2.1.0-3.0.1 | 明确的强制条件。 |
| must not | 不得 | 2.1.0-3.0.1 | 明确禁止。 |
| should | 应当；建议 | 2.1.0-3.0.1 | 推荐行为；不得强化为“必须”。 |
| should not | 不应 | 2.1.0-3.0.1 | 不推荐；不得强化为“不得”。 |
| may | 可以；可 | 2.1.0-3.0.1 | 许可。 |
| can | 可以；能够 | 2.1.0-3.0.1 | 按许可或能力语境选择。 |
| is expected to | 预期……；预计…… | 2.1.0-3.0.1 | 预期行为，不是强制要求。 |
| only | 仅；只有……才…… | 2.1.0-3.0.1 | 必须紧邻限定对象。 |
| if | 如果；若 | 2.1.0-3.0.1 | 保留条件关系。 |
| unless | 除非 | 2.1.0-3.0.1 | 不得改写成相反条件。 |
| as soon as | 一旦……立即；尽快 | 2.1.0-3.0.1 | 根据是否强调即时性选择。 |
| until | 直到 | 2.1.0-3.0.1 | 明确状态或行为的持续终点。 |

## 10. 标识符和字面量格式字典

| 类型 | 统一格式 | 适用版本 | 示例 |
| --- | --- | --- | --- |
| 字段 | 保持原拼写并使用反引号 | 2.1.0-3.0.1 | `operatingMode`、`nodeStates` |
| 主题 | 保持原拼写并使用反引号 | 2.1.0-3.0.1 | `instantActions`、`responses` |
| 动作 | 保持原拼写并使用反引号 | 2.1.0-3.0.1 | `cancelOrder`、`downloadZoneSet` |
| 枚举 | 保持原值并使用单引号 | 2.1.0-3.0.1 | `'SEMIAUTOMATIC'`、`'GRANTED'` |
| 错误类型 | 保持原值并使用单引号 | 2.1.0-3.0.1 | `'INVALID_ORDER_ACTION'`、`'RELEASE_LOST'` |
| 3.0.1 预定义表补充错误类型 | 保持原值并使用单引号 | 3.0.1 | `'RELEASE_LOSS_HANDLING'`、`'INSTANT_ACTION_STATES_FULL'`、`'ZONE_ACTION_STATES_FULL'` |
| `string` 示例 | JSON 双引号并整体使用反引号 | 2.1.0-3.0.1 | `"order"`、`"1.3.2"` |
| 布尔值 | 小写并使用反引号 | 2.1.0-3.0.1 | `true`、`false` |
| 数据类型 | 保持原值并使用反引号 | 2.1.0-3.0.1 | `string`、`float64`、`uint32` |
| 坐标轴 | 小写字母加“轴” | 2.1.0-3.0.1 | x 轴、y 轴、z 轴 |
| 数学常量 | 沿用 EN 文本形式 | 2.1.0-3.0.1 | `Pi` |
| 数值范围 | 使用三个英文句点分隔上下限 | 2.1.0-3.0.1 | `[0.0 ... 1.0]` |

## 11. 禁用或避免的译法

| 避免使用 | 应改为 | 适用版本 | 原因 |
| --- | --- | --- | --- |
| 运行模式 | 操作模式 | 2.1.0-3.0.1 | 避免与 `'RUNNING'` 动作状态混淆。 |
| 线路引导式移动机器人、线引导、线导 | 线导引移动机器人 | 2.1.0-3.0.1 | 保持核心术语唯一。 |
| 轻松到达 | 可直接到达 | 2.1.0-3.0.1 | `trivially reachable` 强调无需额外路径规划。 |
| 动作流畅 | 连续、平稳行驶 | 2.1.0-3.0.1 | `movement` 在此表示车辆行驶，不是协议动作。 |
| 错误引用 | 错误关联项 | 2.1.0-3.0.1 | 避免与文献引用混淆。 |
| 地平线（订单语境） | 预测区 | 2.1.0-3.0.1 | `horizon` 是未释放节点和边的集合。 |
| 基础、基线（订单语境） | 基础区 | 2.1.0-3.0.1 | `base` 是已释放节点和边的集合。 |
| 遍历节点或边（正文行为描述） | 通过节点、驶过边 | 2.1.0-3.0.1 | 更符合车辆行驶语境；既有章节标题可保留。 |
| π | `Pi` | 2.1.0-3.0.1 | 沿用 EN 的跨平台文本表示。 |
| `'TRUE'`、`'FALSE'`、真、假 | `true`、`false` | 2.1.0-3.0.1 | JSON 布尔字面量要求小写。 |
| `instantAction`（主题名） | `instantActions` | 2.1.0-3.0.1 | 正式主题名为复数。 |
| `response`（主题名） | `responses` | 3.0.0-3.0.1 | 正式主题名为复数。 |
| `responseType`（区域响应字段） | `grantType` | 3.0.1 | 3.0.0 的响应字段表和 Schema 已定义 `grantType`，3.0.1 进一步修正正文中的不一致写法。 |
| `lhd`（`pick`/`drop` 动作参数） | `loadHandlingDevice` | 3.0.1 | 3.0.1 已统一预定义动作表和 factsheet 参数说明；翻译 V2.1.0/3.0.0 时仍按对应原文保留 `lhd`。 |
| `.load`（预定义动作的关联状态） | `loads` | 3.0.1 | 3.0.1 按状态消息契约改为 `loads` 数组；独立的 `load` 对象名仍然有效。 |
| `resultDescription`（动作结果字段） | `actionResult` | 3.0.1 | 3.0.1 已将状态消息说明与既有 `actionState.actionResult` 字段统一。 |
| `typeSpecifications` | `typeSpecification` | 3.0.1 | factsheet 顶层对象名为单数 `typeSpecification`。 |
| `state.SerialNumber` | `state.serialNumber` | 2.1.0, 3.0.1 | 协议字段区分大小写，`serialNumber` 的首字母必须小写。 |
| `actions.actionsParameters` | `action.actionsParameters` | 3.0.1 | factsheet 的单动作参数数量限制应引用单数 `action`。 |
| `nodesStates` | `nodeStates` | 3.0.1 | 清除订单状态时使用既有 `nodeStates` 数组字段。 |
| `actionStatus`（作为加入 `actionStates` 的对象） | `actionState` | 2.1.0, 3.0.1 | 此处要求加入动作状态对象；不要全局替换有效字段 `actionStatus`。 |
