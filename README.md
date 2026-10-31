# AMD-AI-Developer-Notes
pretraining -> post training -> inference

**Inference:** Its real world active execution phase where a trained model takes input and generates content.
**vLLm** virtual Language Language Model(Optimized inference engine ) - open source, high throughput inference, and a engine built to run LLMs efficiently and quickly.  

while using inference we can give **System prompts** to tell AI on how to behave. It's like giving/ assigning a role to AI.
### System Prompts: 
Role : assign a role , an instruction
Content : the actual instruction on how to behave - This is how we give role or instructions to perform paticular tasks like code or work.
####Controlling AI behaviour with Parameters: We can control the next word or output which are usually selected based on probability. Inference paramters influence how randomness is allowed, whether repition is allowed or how much creativity is encouraged.
temperature → Controls creativity
max_tokens → Controls response length
top_p → Controls word diversity
top_k -> controls deterministic

```
# 1. Load model (once)
llm = LLM(model="Qwen/Qwen3-4B-Instruct-2507")

# 2. Create conversation with optional system prompt
conversation = [
    {"role": "system", "content": "Your instructions here"},
    {"role": "user", "content": "Your message"}
]

# 3. Do inference
sampling_params = SamplingParams(temperature=0.7, max_tokens=200)
outputs = llm.chat(conversation, sampling_params)
response = outputs[0].outputs[0].text
```
