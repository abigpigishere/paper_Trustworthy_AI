### ABSTRACT

- benchmark AgentHarm:110个恶意代理任务
- 先进的llm模型无需越狱即可执行对应的恶意任务
- 简单的越狱模板即可
- 可实现连贯且恶意的多步骤代理行为，并保留模型功能

### introduction

- 吹AgentHarm
- 没有应用代理可能收到攻击
- 简单的越狱即可
- 连贯且恶意的多步骤代理行为

### related work

- 区别：危害来源于恶意用户直接向llm代理提出有害查询
- Overall, we believe there is a need to establish a reliable, standardized benchmark for measuring robustness of LLM agents against a broad spectrum of potential misuse scenarios

### benchmark

- 十种基础行为与十一种危害类别
- 行为增强：110种基本行为转化为对应的440种tasks
- 良性行为：通过良性行为的datasets来降低拒绝率
- 数据集划分
- 细粒度低评分标准：harm score : llm narrow tasks;refusal judge:拒绝率
- cost 低
- 设计准则：

	1. Harm coverage
	1. Depth vs. breadth of domains: 有一定的广泛性，task多
	1. Detection of capability degradation.得分取决于代理对于恶意任务的执行程度
	1. Dataset usability：通用，成本低廉
	1. Scoring reliability：人工编写，检查
	1. Preventing dataset contamination：私有数据集

### evaluation

- 主要略
- 成功攻击对模型性能没有太大影响



### Discussion

- 仅英文
- multi-turn attacks
- 主要衡量的是模型的基础能力

### idea

- 一个类似的中文branchmark?

​	总的来说，这个主要是建立了一个agent-attack的对应banchmark,可以测试agent对于攻击的拒绝率和harm score来判断模型的安全性。但这个branchmark还是存在比较多的局限性，文中也有写。

