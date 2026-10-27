# Claude Fable 5.5 国内使用指南

面向国内用户：如何通过网页对话、全模型 API、包月套餐使用 Claude Fable 系列（含社区常说的 Fable 5.5）。

---

## 1. Claude Fable 是什么？

Claude Fable 是 Anthropic 体系里偏 **推理（reasoning）**、**长程智能体（long-horizon agentic）** 方向的一条产品线：更擅长多步规划、工具调用与较长任务链，而不只是「单轮聊天」。

模型 ID 常见写法示意：

- API / 产品列表风格：`claude-fable-5-1` 等
- 社区口语：`claude-fable-5-5`、Fable 5.5

**重要提示（截至 2026 年 10 月下旬）**：对外公开渠道里，官方常列出的 Fable 版本多为 **5.1**；部分国内聚合站 / 网关可能额外暴露名为 **5.5** 的条目。请以你当天在产品列表里看到的**精确模型名称**为准选择，不要死记某个别称。

---

## 2. 为什么国内用户常走网关？

直接使用海外官方接口时，常见障碍包括：

1. **支付**：信用卡 / 海外账单不便
2. **网络**：访问不稳定或延迟高
3. **配额**：官方账号额度、限流与申请门槛

因此许多用户会选择国内可访问的网页对话站、兼容 API 聚合商，或包月套餐——下面三条路径对应不同需求。

---

## 3. 三条路径（含直达链接）

| 方式 | 适合谁 | 链接 |
|------|--------|------|
| 网页对话 | 想先试效果、少配置 | [http://trymodel.chat/](http://trymodel.chat/) |
| 全模型 API | 写脚本、接应用、批量调用 | [https://tryallapi.com/](https://tryallapi.com/) |
| 包月套餐 | 高频聊天、长期用 | [https://momoai.asia/](https://momoai.asia/) |

---

## 4. 操作步骤

### 4.1 网页对话（TryModel）

1. 打开 [http://trymodel.chat/](http://trymodel.chat/)
2. 在模型列表中选择 **Claude Fable 5.5**；若当天没有该名，选列表里最接近的 **Fable**（如 `claude-fable-5-1` / 页面显示的 Fable 条目）
3. 直接开始对话，验证推理与多轮任务表现

### 4.2 全模型 API（TryAllAPI）

1. 打开 [https://tryallapi.com/](https://tryallapi.com/)
2. 注册 / 登录后创建 API Key
3. 在文档或控制台确认当日可用的 **精确 model id**（例如产品列表中的 Fable 名称）
4. 使用 OpenAI 兼容写法调用（以下为占位示例，请替换 Key 与模型名）：

```bash
curl https://api.tryallapi.com/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "claude-fable-5-5",
    "messages": [
      {"role": "user", "content": "用三步规划解释长程智能体任务该怎么拆。"}
    ]
  }'
```

OpenAI 兼容伪代码示例：

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://api.tryallapi.com/v1",  # 以站点文档当日为准
)

resp = client.chat.completions.create(
    model="claude-fable-5-5",  # 换成产品列表里的精确 id
    messages=[{"role": "user", "content": "Hello from Fable"}],
)
print(resp.choices[0].message.content)
```

> `base_url`、路径与模型 id 以 [TryAllAPI](https://tryallapi.com/) 当日文档为准；上表仅为写法示意。

### 4.3 包月套餐（MomoAI）

1. 打开 [https://momoai.asia/](https://momoai.asia/)
2. 查看套餐说明与可用模型列表
3. 订阅后按站内指引进入对话或 API（适合不想按次计费、使用频率较高的用户）

---

## 5. 简短 FAQ

### Fable 和 Opus / Sonnet / Haiku 5.5 有什么区别？

- **Opus / Sonnet / Haiku**：Claude 主系列的不同档位（能力 / 速度 / 成本权衡），偏通用对话与写作等日常任务。
- **Fable**：更偏 **推理与长程 agentic** 场景——多步骤、工具链、需要「想清楚再执行」的任务。

具体能力边界仍以各产品说明与实测为准；命名上的「5.5」在不同产品线含义也不完全相同。

### 什么时候优先选 Fable？

- 需要多步规划、分解复杂任务
- 希望模型更「稳」地推进长对话 / 长任务
- 在做 agent、工具调用、工作流编排类实验

若只是短问答、轻度写作，Sonnet / Haiku 等往往更省、更快。

---

## 6. 免责声明

- 文中网关 / 聚合站为**第三方服务**，**不等于** Anthropic 官方。
- 价格、库存、模型是否上架，以各站**当日页面**为准。
- 本指南不含联盟推广参数（无 aff / 返佣链接参数）。
- 使用第三方服务时请自行评估账号安全、数据合规与费用风险。

---

*文档维护：xianyu110 · GitHub Pages（内容镜像自 Maynor996 指南）*
