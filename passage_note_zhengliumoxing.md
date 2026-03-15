# 針對特定模型進行蒸餾，以訓練自己的模型
source: [教你直接蒸馏GPT-5来训练你自己的模型‼️ - 小红书](https://www.xiaohongshu.com/explore/6921c623000000001e02b060?xsec_token=ABxLJYTEGBDACDfI5m3fxIfLwvWD3W6i8zwMV474NBJJk=&xsec_source=pc_user)

这个模型旨在为边缘计算和低资源环境提供接近顶尖大模型的交互体验。最大化学生模型生成结果在“表达自然性”、“语义完整度”和“风格匹配度”三项指标上的优化。

数据集📖：
✅GPT-5 response corpus 90%  混合数据
✅ShareGPT-Qwen3-235B-A22B-Instuct-2507 10% 多轮对话和指令

⚙️优化器和超参数设置：
Base Model: Qwen/Qwen3-4B
Context Length: 32,768 Tokens
Hardware Environment: NVIDIA H100
Optimizer: AdamW 8-bitfactualju

🍎超参数：
Learning Rate: 2e −5  (Linear Decay)
per_device_train_batch_size = 8
gradient_accumulation_steps = 8
Batch Size: 64 (Gradient Accumulation)

全量开源，并提供了量化版本。
HF仓库：  
🔗 [Jackrong/GPT-5-Distill-Qwen3-4B-Instruct](https://huggingface.co/Jackrong/GPT-5-Distill-Qwen3-4B-Instruct)  
🔗 GGUF 量化: [Jackrong/GPT-5-Distill-Qwen3-4B-Instruct-GGUF](https://huggingface.co/Jackrong/GPT-5-Distill-Qwen3-4B-Instruct-GGUF)

# 知識蒸餾流程
![image.png](https://github.com/jeniebeez/randrecord/blob/main/img/pn1.png)
- Soft Targets&Style Info - 軟性目標&風格資訊
- Distillation (Dataset Creation) - 蒸餾（資料集塑造）
- Process: Training the compact student model to mimic the teacher’s output distribution and stylistic nuances.  
  行程：訓練緊湊型學生模型以模仿教師的輸出分佈和風格細微差別
  
# 蒸餾法的好處
![image.png](https://github.com/jeniebeez/randrecord/blob/main/img/pn2.png)
- 大模型 → 優化 → 蒸餾模型
- 效率：降低參數&更快地推理 (inference)
- 品質：保留GPT-5的對話能力
- 部署：適合邊緣裝置

# 模型總覽
![image.png](https://github.com/jeniebeez/randrecord/blob/main/img/pn3.png)

## **GPT-5-Distill-Qwen3-4B-Instruct**
![image.png](https://github.com/jeniebeez/randrecord/blob/main/img/pn4.png)

- 40億參數
- GPT-5 的品質
- 支持雙語（中/英）
- 效率推理（低延遲）
- 總結：高品質、從GPT-5知識中蒸餾的高效模型

## 2507版本的總覽
基礎模型：Qwen3-4B-Instruct-2507
訓練方法：
- 在共享GPT資料上進行監督式微調
- 從LMSYS GPT-5 的回覆中蒸餾知識  
最大內文長度：32 tokens（max_seq_length = 32768）

## 使用情境
![image.png](https://github.com/jeniebeez/randrecord/blob/main/img/pn5.png)

不適合使用於以下情境：
- 高風險決策 - 理財、醫療
- 實時事實任務 - 新聞、股票
- 授權於敏感議題的判斷

# 訓練參數
![image.png](https://github.com/jeniebeez/randrecord/blob/main/img/pn6.png)
