---
name: douyin-hashtag-advisor
description: "Use when preparing Douyin posts before publishing and the user needs #话题 suggestions, a 发布前话题包, hashtag SEO, Douyin Index or 创作灵感 hot-word matching, or safe hashtag cleanup after content review. Analyze title, script, account positioning, audience, user-provided hot words, competitor hashtags, and recent hashtag history, then produce relevant, safe, non-generic Douyin hashtag recommendations with source confidence, risk flags, repetition control, and a directly copyable publishing version. Do not use for pure topic ideation, post-publish traffic diagnosis, or promotion decisions."
license: MIT
metadata:
  hermes:
    version: 1.1.0
    author: KK + Hermes
    tags: [douyin, hashtag, seo, topic, publishing, 抖音, 话题, 搜索, 发布前检查]
    related_skills: [douyin-content-review, content-creator-pipeline]
---

# Douyin Hashtag Advisor

## Purpose

Generate a Douyin publishing hashtag package for a finished or near-finished post.

Core belief: hashtags are classification and search-matching tools, not a traffic button. Prefer relevant, stable, safe labels over generic superstition such as `#上热门` or irrelevant hot words.

## Use In The Publishing Flow

Use after the content is mostly ready:

```text
script/title ready
-> content review
-> hashtag advisor
-> publishing copy
-> publish registration
```

If content review reports high risk, do not optimize for hot words first. Tell the user to fix the script/title, then provide only low-risk replacement hashtag directions.

Do not use this skill for:

- Pure topic ideation or "下一条做什么".
- Post-publish traffic diagnosis.
- Paid promotion or boosting decisions.
- Replacing Douyin content review.

## Input Contract

Use whatever the user provides. At minimum, infer from title and script if possible.

Required or strongly preferred fields:

| Field | Meaning |
|---|---|
| `title` | Video title or cover title. |
| `script` | Script, outline, transcript, or concise summary. |
| `niche` | Account track or creator positioning. |
| `audience` | Target viewers. |

Optional fields:

| Field | Meaning |
|---|---|
| `hot_words` | User-provided Douyin Index, 创作灵感, 热点小助手, 搜索联想, or related-search words. |
| `competitor_hashtags` | Hashtags used by same-track successful posts. |
| `recent_hashtags` | Hashtags used in recent posts, for repetition control. |
| `review_result` | Content review status and risk notes. |
| `platform_goal` | Search matching, account labeling, trend participation, or safe publishing. |

When no hot-word data is provided, produce a semantic version and label the source as `仅基于内容语义推断`. Do not invent index numbers, rankings, or live trend status.

## Workflow

### 1. Normalize Context

Extract the real subject from the title and script. Ignore vague publishing phrases such as "帮我配话题" or "发布前话题包".

Build a keyword map:

| Type | What To Extract | Example |
|---|---|---|
| Core content | What the video is truly about | AI入门, 个人IP定位, 内容创作 |
| Audience | Who should see it | 普通人, 职场人, 内容创作者 |
| Scenario/search | Where the need appears | 工作提效, 短视频创作, 账号定位 |
| Emotion/cognition | Viewpoint-video classification | 焦虑, 判断力, 认知提升 |
| Stable account label | Reusable account taxonomy | 商业诊断, 个人成长, 自媒体 |

### 2. Evaluate Sources

Classify every candidate hashtag by source and confidence.

| Source | Confidence | Rule |
|---|---|---|
| 用户提供抖音指数/巨量算数 | high | Keep only if strongly relevant. |
| 创作灵感/热点小助手 | high | Prefer rising and same-track words. |
| 抖音搜索联想/相关搜索 | medium-high | Prefer phrases users would actually search. |
| 同赛道爆款话题 | medium | Reuse only transferable labels, not creator-specific memes. |
| 内容语义推断 | medium-low | Use when no platform data is provided. |
| Generic platform tags | low | Use at most one, only if it helps classification. |

Priority:

```text
strong relevance + rising/platform source
> strong relevance + stable search intent
> account taxonomy fit
> broad generic tags
> superstition tags
```

### 3. Build The Default 5-Hashtag Mix

Default to exactly 5 hashtags unless the user asks otherwise.

Recommended mix:

```text
2 core content tags
+ 1 target-audience tag
+ 1 scenario/search/emotion tag
+ 1 stable account or platform taxonomy tag
```

Examples:

```text
#AI入门 #AI工具 #普通人用AI #工作提效 #自媒体
```

```text
#个人IP #内容创作 #普通人成长 #账号定位 #商业诊断
```

Avoid filling all 5 slots with broad tags. At least 3 of the 5 must be tightly connected to the content.

### 4. Control Repetition

If `recent_hashtags` are available:

- Keep 1-2 stable account labels if they are part of the creator's long-term positioning.
- Rotate 3-4 content-specific tags per post.
- Flag if the recommended set repeats more than 3 tags from the recent set.
- Avoid turning every post into the same template, for example always using `#个人IP #内容创作 #自媒体 #成长 #认知`.

If recent history is not available, mention that repetition risk is unknown.

### 5. Safety Gate

Assign each candidate hashtag a risk status:

| Status | Meaning |
|---|---|
| `可用` | Relevant and no obvious publishing risk. |
| `慎用` | Potentially useful but may attract wrong traffic, marketing risk, or weak relevance. |
| `不用` | Irrelevant, unsafe, misleading, or superstition-first. |

Common risk checks:

- Private-domain diversion: `微信`, `加微`, `进群`, `看主页`, `看简介`, `二维码`.
- Money or opportunity promises: `稳赚`, `暴利`, `躺赚`, `月入`, `副业赚钱`.
- Absolute claims: `保证`, `100%`, `最强`, `第一`, `唯一`, `必火`.
- Sensitive groups or topics: minors, politics, public emergencies, sensitive public figures.
- Medical/efficacy claims if relevant: `治愈`, `根治`, `疗效`.
- Anxiety or antagonism bait: labels that intensify conflict without content basis.
- Irrelevant hot words: high heat but weak semantic match.

Do not recommend `#上热门`, `#抖音小助手`, or `@抖加小助手` as default tags. If the user insists, mark them as `慎用` or `不用` and explain why they should not be the core strategy.

## Vertical Strategy Hints

Use these as defaults, then adapt to the user's actual content.

| Vertical | Stable Labels | Content-Specific Labels |
|---|---|---|
| Personal IP | `#个人IP`, `#普通人成长` | `#账号定位`, `#表达力`, `#内容创作` |
| Business diagnosis | `#商业诊断`, `#创业思维` | `#商业模式`, `#客户增长`, `#经营复盘` |
| AI tools | `#AI工具`, `#普通人用AI` | `#工作提效`, `#AI入门`, `#自动化办公` |
| Workplace growth | `#职场成长`, `#认知提升` | `#沟通表达`, `#工作方法`, `#效率提升` |
| Education/training | `#学习方法`, `#知识管理` | `#课程设计`, `#学习效率`, `#表达训练` |
| Local services | `#本地生活`, `#探店` | Use city, service category, and concrete need; avoid fake national hot tags. |

## Output Format

Always output Markdown first. If product integration is needed, append the JSON block too.

```markdown
## 抖音话题建议

### 输入摘要
- 标题：...
- 内容核心：...
- 赛道/人群：...
- 数据来源：用户提供热词 / 同赛道话题 / 仅基于内容语义推断

### 核心关键词
- 核心内容词：...
- 目标人群词：...
- 场景/搜索词：...
- 稳定账号标签：...

### 推荐 5 话题
| 话题 | 类型 | 来源 | 可信度 | 风险 | 选择理由 |
|---|---|---|---|---|---|
| #... | 核心内容 | ... | high | 可用 | ... |

### 备选话题
- #...：适合在...时替换

### 不建议使用
- #...：不用/慎用，原因...

### 重复控制
- 与近期话题重复：未知 / 低 / 中 / 高
- 建议保留的稳定标签：...
- 建议轮换的内容标签：...

### 可直接复制版本
标题：...
描述：...
话题：#A #B #C #D #E
```

Structured result:

```json
{
  "source_status": "semantic_only | user_hot_words | competitor_reference | mixed",
  "content_summary": "",
  "keywords": {
    "core": [],
    "audience": [],
    "scenario": [],
    "emotion_or_cognition": [],
    "stable_account_labels": []
  },
  "recommended_hashtags": [
    {
      "tag": "#...",
      "type": "core_content | audience | scenario_search | emotion_cognition | stable_account | platform_generic",
      "source": "semantic | douyin_index | creator_inspiration | search_suggestion | competitor | recent_history",
      "confidence": "high | medium-high | medium | medium-low | low",
      "risk": "可用 | 慎用 | 不用",
      "reason": ""
    }
  ],
  "alternatives": [],
  "rejected": [
    {
      "tag": "#...",
      "risk": "慎用 | 不用",
      "reason": ""
    }
  ],
  "repetition": {
    "level": "unknown | low | medium | high",
    "repeated_tags": [],
    "stable_tags_to_keep": [],
    "tags_to_rotate": []
  },
  "copyable": {
    "title": "",
    "description": "",
    "hashtags": ""
  }
}
```

## Decision Rules

1. Prefer relevance over heat.
2. Prefer searchable user language over internal jargon.
3. Keep default output to 5 hashtags.
4. Include at least 1 audience tag and 1 scenario/search/emotion tag.
5. Keep only 1 broad platform or taxonomy tag unless the content itself is broad.
6. Flag risky words instead of silently using them.
7. Do not fabricate platform data.
8. If the title/script is too vague, provide a semantic draft and ask for title/script or hot words to refine.

## Verification Checklist

- At least 3 of 5 recommended hashtags are strongly relevant.
- At least 1 hashtag names the target audience.
- At least 1 hashtag maps to scenario, search intent, emotion, or cognition.
- No obvious private-domain, absolute-promise, misleading, or irrelevant hot tags are recommended as `可用`.
- Repetition is checked when recent history is available.
- Output includes both reasoning and a directly copyable publishing version.
