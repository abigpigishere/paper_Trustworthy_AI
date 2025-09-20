#### abstract

- 提出新颖的框架CipherChat（通过密码提示与llm聊天），检测安全性以及自然语言的局限性。（绕过了安全对其）
- 发现LLM的“secert cipher"--SelfCipher 似乎优于现在的人类密码

#### introduction

- red team 
- 研究问题：can the non-natural language prompt bypass the safety alignment mainly in natural language?（非自然语言提示能否绕过自然语言的安全对齐）上一篇就有利用base64来绕过的做法
- CipherChat结构：
  1. 行为分配：使用密码交流
  2. 密码教学
  3. 通过密码绕过安全对其

- “secret cipher” 受启发于：A recent study shows that language models (e.g. ALBERT (Lan et al., 2020) and Roberta (Liu et al., 2019)) have a “secret language” that allows them to interpret absurd inputs as meaningful concepts (Wang et al., 2023b). 

- 总体贡献：
  1. 需要开发非自然语言的安全对其
  2. 通用框架评估LLM响应密码的安全性、
  3. secret cipher(角色扮演与演示)（自然语言的密码）
  4.   

### Related work

- 

###  METHODOLOGY: CIPHERCHAT

- 具体流程见前述

- common encoding and ciphers

- 扮演密码专家

  

### EXPERIMENT

- 数据集与模型略
- GPT表现好于Turbo,模型大，理解能力强，且主导语言上的不安全性更高
- 各种密码的不安全性存在差异

### analysis

- system Role 的影响
- 移除不安全演示
- 与模型的大小相关
- cipher关键词？evoke?
- can simulated ciphers that never occur in pretraining data work in CipherChat?

### conclusion

- 非自然语言安全对其的重要性
- 未来的安全工作