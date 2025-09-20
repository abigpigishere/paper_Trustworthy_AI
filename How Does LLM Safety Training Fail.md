- abstract:GPT 4,Claude v1.3 不安全，可能会越狱。因此需要一种复杂的安全系统。

- 已有的安全机制：These include both training-time interventions to align models with predefined values [41, 7] and post hoc flagging and filtering of inputs and outputs [56, 24, 52, 45]. These efforts are often complemented by red teaming, which proactively identifies and trains against weaknesses [42, 23, 38].  训练时干预模型使之趋向预测值；事后对输入输出进行标记以及过滤。
- 攻击方式：不匹配泛化；竞争目标
- 竞争目标：
  1. 增加长前缀
  2. 拒绝冲突
  3. 某些变体的越狱
  4. 注入样式

- 不匹配的泛化（预训练集比安全训练集大）
  1. Base64的编码方式（编码输入>编码输出）
  2. 其他类似混淆方案
  3. 干扰项指令，随机输入不同指令
  4. 不寻常的输出格式
  5. 生成网页内容

- 越狱方案评估（基线是正常的prompt回复）
  1. 采用之前提到的攻击方式做测试
  2. 使用 harmful prompts introduced in Section 2.2
  3. 

- results
  1. 成功越狱的方式很广泛
  2. 某些合成的越狱方法具有良好的泛化能力
  3. 注入特定的前缀与指令对于越狱至关重要
  4. 自适应性，微小改动即可复现攻击
  5. 针对性训练不足
  6. 
- defence
  1. 从预训练开始就加入人类价值观？
  2. 无法通过简单的泛化来解决
  3. 模型的规模越大，攻击面也就越大
  4. 安全模型对等规模？（不能用小模型标注？人类标注困难
  5. 

- conclusion
  1. 仍只是鲁棒性的早期探索
  2. 未来：安全训练的机制解释；白盒训练更有效的越狱方案；黑盒越狱自动发现的可能性
  3. 公开讨论弱点及局限性对安全发展重要
  4. 

- 总的来说本文主要研究的是两种攻击方式对于现在的大模型的攻击的有效性，通过构造对应的这两种攻击方式，以及衍生方式的harmful prompt,并对大模型做测试，看其对应的安全机制是否会能正确的反馈。最后得到的结果是需要建立某种与模型对等规模的安全机制，并且认为整个模型的安全探索还有很长的路要走。