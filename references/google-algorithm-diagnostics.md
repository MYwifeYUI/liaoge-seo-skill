# Google算法更新与流量下降诊断

> 本参考由用户提供的 `google-search-algorithm` 资料炼化而来，核心来源为Google Search Central与Google Search Status Dashboard。它描述Google公开机制，不代表掌握未公开排名公式。算法、政策、状态页事件和产品功能具有时效性，使用前必须联网核验官方当前版本。

## 目录

1. 证据与边界
2. 算法影响诊断顺序
3. 排名系统的正确理解
4. Core、Spam与Reviews的差异
5. Search Essentials技术门槛
6. People-first、E-E-A-T与AI内容
7. 流量下降决策表
8. 输出与验收

## 1. 证据与边界

按以下优先级判断：

1. Google官方当前文档、Search Status Dashboard及其事件端点；
2. 网站自己的GSC、GA4、CRM、URL Inspection与服务器日志；
3. 实际抓取、渲染、状态码、HTML/DOM、SERP与页面对比；
4. 可信第三方工具与行业研究；
5. 经验推断。

不得把算法更新时间相关性直接写成因果。状态页只记录影响大量站点或用户的事件，不包含所有小型更新和单站问题；Google不接受付费来提高抓取频率或自然排名；满足技术要求只代表具备资格，不保证抓取、索引、展示或排名。

## 2. 算法影响诊断顺序

1. 查 `https://status.search.google.com/`，确认近期是否有Ranking、Crawling、Indexing或Serving事件；事件历史、RSS/Atom与JSON只作为时间线证据。
2. 对齐更新开始、结束与网站变化日期；核心更新完成后至少等待一周，再比较“更新前一周”与“更新结束后一周”，同时拉长到16个月判断季节性。
3. 排除数据异常、埋点故障与CRM漏记，再查GSC的Manual Actions、Security Issues、Page Indexing和Crawl Stats。
4. 在Performance中按查询、页面、国家、设备和搜索类型拆分；展示与点击同降、仅点击下降、全站下降、目录下降和单页下降分别处理。
5. 用Google Trends和同行SERP判断行业需求变化、季节性与竞争变化，不能只看自己网站。
6. 对大幅下降页面执行people-first、意图匹配、原创证据、技术入口、垃圾政策与外链风险检查；小幅位置波动不要激进改版。
7. 只有确认问题后才行动：技术/安全/手动处置立即修复；内容与核心更新问题做实质改善并等待重新处理；删除内容作为最后手段。

## 3. 排名系统的正确理解

- BERT、Neural Matching与RankBrain帮助理解查询、概念和语义关系；不要据此追逐固定关键词密度。
- Passage Ranking可理解页面局部段落；它不要求为每个微小变体单独建页。
- Freshness、原创内容、去重、站点多样性、链接分析、可靠信息和垃圾检测等系统共同作用；PageRank只是众多信号之一。
- SpamBrain属于持续运行的垃圾检测体系。
- Helpful Content System已并入核心排名系统；Panda、Penguin、Hummingbird等历史名称不能当作当前独立更新诊断标签。
- 排名主要按页面评估，同时会使用站点级信号与分类器；站点整体良好不保证每页排名，单页下降也不自动证明整站处罚。

## 4. Core、Spam与Reviews的差异

### Core Update

- 广泛调整，不针对某个站点；多数站点无需因公告而改动。
- 小幅下降先观察；从前列大幅跌落时做整站质量与受影响页面评估。
- 避免“快速修复”和无证据删改；改善可能数天至数月才被重新理解，且不保证恢复。

### Spam Update

- 显著升级垃圾检测能力，通常全球、多语言；先对照当前Spam Policies。
- 自动降级与手动处置不同：只有Manual Actions中的人工处置才能提交重新审核。
- 链接垃圾收益被取消后，即使清理链接也不保证原排名收益恢复。

### Reviews System

- 重点奖励第一方、独立、由懂行者创作的评测、对比和推荐内容：真实体验、测试过程、原创数据、优缺点和适用场景。
- 不把商家参数改写、无实测“十大榜单”或用户评论区当作高质量评测证据。
- 适用语言和系统状态会变化，使用前核对Google当前文档。

## 5. Search Essentials技术门槛

最低资格：Googlebot可访问、URL返回HTTP 200、页面含可索引内容且不违反垃圾政策。按“发现→抓取→渲染→索引→理解→排序→转化”逐层检查。

- robots.txt控制抓取，不等于禁止索引；移除页面通常允许抓取并使用`noindex`，或返回合适的404/410。
- Google使用现代Chrome渲染JavaScript；不要屏蔽关键CSS/JS，核心内容、链接与SEO指令应稳定出现在初始HTML或可执行渲染结果中。
- Sitemap帮助发现，不保证收录；canonical、重定向、内部链接、Sitemap与hreflang应给出一致信号。
- 移动优先索引要求移动端与桌面端核心内容、链接、图片和结构化数据等价。
- Core Web Vitals与富结果资格要使用Google当前官方阈值和测试工具；结构化数据必须与可见内容一致，不能伪造评价、认证或价格。

## 6. People-first、E-E-A-T与AI内容

内容自评优先检查：是否有原创信息与第一手经验、是否完整解决目标问题、是否超越简单改写、是否提供可核实来源、是否由真正懂行者创作或审核、读者是否无需再次搜索才能完成任务。

- E-E-A-T是Experience、Expertise、Authoritativeness、Trust的质量评估框架，Trust最重要；它不是可读取的单项排名分数。
- 用Who/How/Why呈现可信度：谁负责内容、证据和测试如何产生、为什么为用户而创作。
- AI辅助创作本身不违规；无增值地批量生成页面以操纵排名，可能构成Scaled Content Abuse。
- AI生成的事实、元数据、结构化数据、图片和代码必须人工核验；需要时披露自动化的使用方式。
- 面向AI搜索仍以可抓取、可索引、people-first、原创证据和核心SEO为基础；不要把`llms.txt`、特殊schema、分块字数或虚假品牌提及当成Google排名捷径。

## 7. 流量下降决策表

| 现象 | 优先检查 | 动作 |
|---|---|---|
| 展示和点击同时下降 | 算法、索引、需求、竞争 | 按时间线和页面/查询拆分 |
| 展示稳定、点击下降 | Title、snippet、SERP版式、竞争结果 | 优化表达并做页面级测试 |
| 全站突然下降 | 服务器、robots、noindex、安全、手动处置 | 立即技术与安全排查 |
| 单目录下降 | 模板、canonical、内容类型、内部竞争 | 抽查URL并比较同组页面 |
| 小幅排名波动 | 正常重排、竞争变化 | 记录并观察，不大改 |
| 核心更新后大幅下降 | 意图、people-first、原创证据、站点质量 | 实质改善，更新结束后再评估 |
| 垃圾更新后下降 | Spam Policies、链接、规模化内容、寄生内容 | 停止违规、清理并等待重评 |
| 仅某国家/设备下降 | 本地需求、hreflang、移动体验、SERP差异 | 按维度定位，不做整站一刀切 |

## 8. 输出与验收

每项结论写清：证据、时间线、影响范围、置信度、替代解释、修复动作、负责人、依赖和验收指标。至少交付：

- 更新/事件时间线与数据对比区间；
- GSC页面×查询×国家×设备×搜索类型拆分；
- 技术、安全、手动处置、垃圾政策与内容质量排除表；
- P0/P1/P2/P3行动清单；
- 观察窗口与复测日期。

权威入口：

- `https://status.search.google.com/`
- `https://developers.google.com/search/docs/appearance/ranking-systems-guide`
- `https://developers.google.com/search/docs/appearance/core-updates`
- `https://developers.google.com/search/docs/essentials`
- `https://developers.google.com/search/docs/essentials/spam-policies`
- `https://developers.google.com/search/docs/fundamentals/creating-helpful-content`
- `https://developers.google.com/search/docs/monitor-debug/debugging-search-traffic-drops`
