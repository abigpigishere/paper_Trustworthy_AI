### abstract

- backdoor attack; general framework; different forms;
- 操作最终输出错误；中间操作引入恶意行为，并保证正确输出（主要的两种攻击方式
- 后门触发器：user query; intermediate observation
- 实现变体
- 结论：后门攻击难以通过文本安全来有效防范

- 购物的例子：query-attack,observation-attack,thought attack
- 基于llm的代理可能会通过后门威胁

- data poisoning mechanisms

- benchmark: AgentInstruct and ToolBench

- 

### Related work 

- 

### Methodology

- based on the ReAct framework
- 给出了一个对应的公式
- 分解：思考T，行动A，观察O

​		1. tai∼πθ(tai∣q,ta<i,o<i)   ：代理在第i步的决策，取决于策略以及前i-1步的历史

​		2. oi=O(tai)：第i步的行动通过环境返回对应的观察

​		3. 攻击者试图通过操纵代理的决策策略（$\boldsymbol{\theta}$），来最大化代理在给定恶意输入时，执行一个特定恶意行为序列的概率。

- $\max_{\boldsymbol{\theta}}\mathbb{E}_{(q^*, ta^*)\sim D^*}[\prod_{i=1}^{N}\pi_{\boldsymbol{\theta}}(ta_i^*|q^*, ta_{<i}^*, o_{<i}^*)]$

​	\* **$\max_{\boldsymbol{\theta}}$**：这是优化的核心。通过调整代理的参数 $\boldsymbol{\theta}$，来最大化后面的表达式。

​	\* **$\mathbb{E}_{(q^*, ta^*)\sim D^*}$**：这是期望操作。对所有来自恶意数据集 $D^*$ 的恶意查询 ($q^*$) 和恶意行为序列 ($ta^*$)求平均。这确保了攻击在多种恶意场景下都能成功。

​	\* **$\prod_{i=1}^{N}$**：对于一个由 $N$ 步组成的行动序列，它的总概率等于每一步概率的连乘。

​	\* **$\pi_{\boldsymbol{\theta}}(ta_i^*|q^*, ta_{<i}^*, o_{<i}^*)$**：代理在第 $i$ 步采取恶意行动 $ta_i^*$ 的概率。这个概率是基于恶意查询 $q^*$ 和所有之前的恶意历史记录（$ta_{<i}^*, o_{<i}^*$）计算的。

​	\*找到一个最优的代理策略 $\boldsymbol{\theta}$，使得该策略在面对恶意输入时，能够以最高的平均概率生成预设好的恶意行为序列。

- $\max_{\boldsymbol{\theta}}\mathbb{E}_{(q^*, ta^*)\sim D^*}[\pi_{\boldsymbol{\theta}}(ta_1^*|q^*)\prod_{i=2}^{N-1}\dots\pi_{\boldsymbol{\theta}}(ta_N^*|q^*, ta_{<N}^*, ob_{<N}^*)]$ 做了展开



### 	两类：

First, the distribution of final output $ta_{N}$ is changed.

- Query-Attack:The backdoor trigger is hidden in the user query:修改了原始推理过程
  1. j=0:修改初始想法
  2. j>0:执行特定步骤触发

- The backdoor trigger appears in an observation oi from environment (Observation-Attack)：观察攻击
  	  1.  也就是检测到特定的$o$后会影响对应的$t_{j}a_{j}$。
  	  1.  与前者不同的是j>0;q未被修改

Second, the distribution of final output taN is not affected.

- Thought-Attack

	  1. the attacker manages to modify the intermediate thoughts and actions $ta_{i}$ but ensures that the final output $ta_{N}$ is unchanged

执行攻击办法：混合对应攻击样本以及正常样本，对llm做微调

### 比较：

- 攻击方式多样且隐蔽
- 对社会影响更恶劣

### 实验：

- 应用提出的三种攻击方式
- 数据，指标

- 结果：Query-Attack is easy to succeed but also faces a potential issue of affecting the normal performance of the agent on benign instructions
- the performance of Observation-Attack on 5 held-in tasks and WS Clean is generally better than that of Query-Attack

- making the agent capture and respond to the trigger hidden in the observation is also harder than making it capture and respond to the trigger in the query

  

### 结论

- 智能体的后门攻击都具有显著的有效性，这对于基于大预言的智能体的应用安全构成了新的巨大挑战。

