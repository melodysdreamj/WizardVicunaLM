<p align="center" width="100%">
<img src="https://user-images.githubusercontent.com/21379657/235832523-0d5656e3-fbbc-48f1-becb-0c3fe22ade0b.png" alt="KoVicuna icon" style="width: 200px; height:200px; display: block; margin: auto; border-radius: 50%;">
</p>

## Update Logs

- 2023.5.5: TheBlock has created a [🤗wizard-vicuna-13B-HF](https://huggingface.co/TheBloke/wizard-vicuna-13B-HF) version for us!
- 2023.5.5: TheBlock has created a [🤗wizard-vicuna-13B-GPTQ](https://huggingface.co/TheBloke/wizard-vicuna-13B-GPTQ) version for us!
- 2023.5.5: TheBlock has created a [🤗WizardVicuna 13B GGML](https://huggingface.co/TheBloke/wizard-vicuna-13B-GGML) version for us!
- 2023.5.4: We are releasing the [🤗WizardVicuna 13B](https://huggingface.co/junelee/wizard-vicuna-13b) model.
- 2023.5.3: We are releasing the [🤗WizardVicuna 70K conversation](https://huggingface.co/datasets/junelee/wizard_vicuna_70k) dataset.

--- 
# WizardVicunaLM
### Wizard's dataset + ChatGPT's conversation extension + Vicuna's tuning method
I am a big fan of the ideas behind WizardLM and VicunaLM. I particularly like the idea of WizardLM handling the dataset itself more deeply and broadly, as well as VicunaLM overcoming the limitations of single-turn conversations by introducing multi-round conversations. As a result, I combined these two ideas to create WizardVicunaLM. This project is highly experimental and designed for proof of concept, not for actual usage.


## Benchmark
### Approximately 7% performance improvement over VicunaLM
![](https://user-images.githubusercontent.com/21379657/236088663-3fa212c9-0112-4d44-9b01-f16ea093cb67.png)


### Detail 

The questions presented here are not from rigorous tests, but rather, I asked a few questions and requested GPT-4 to score them. The models compared were ChatGPT 3.5, WizardVicunaLM, VicunaLM, and WizardLM, in that order.

|     | gpt3.5 | wizard-vicuna-13b | vicuna-13b | wizard-7b | link     |
|-----|--------|-------------------|------------|-----------|----------|
| Q1  | 95     | 90                | 85         | 88        | [link](https://sharegpt.com/c/YdhIlby) |
| Q2  | 95     | 97                | 90         | 89        | [link](https://sharegpt.com/c/YOqOV4g) |
| Q3  | 85     | 90                | 80         | 65        | [link](https://sharegpt.com/c/uDmrcL9) |
| Q4  | 90     | 85                | 80         | 75        | [link](https://sharegpt.com/c/XBbK5MZ) |
| Q5  | 90     | 85                | 80         | 75        | [link](https://sharegpt.com/c/AQ5tgQX) |
| Q6  | 92     | 85                | 87         | 88        | [link](https://sharegpt.com/c/eVYwfIr) |
| Q7  | 95     | 90                | 85         | 92        | [link](https://sharegpt.com/c/Kqyeub4) |
| Q8  | 90     | 85                | 75         | 70        | [link](https://sharegpt.com/c/M0gIjMF) |
| Q9  | 92     | 85                | 70         | 60        | [link](https://sharegpt.com/c/fOvMtQt) |
| Q10 | 90     | 80                | 75         | 85        | [link](https://sharegpt.com/c/YYiCaUz) |
| Q11 | 90     | 85                | 75         | 65        | [link](https://sharegpt.com/c/HMkKKGU) |
| Q12 | 85     | 90                | 80         | 88        | [link](https://sharegpt.com/c/XbW6jgB) |
| Q13 | 90     | 95                | 88         | 85        | [link](https://sharegpt.com/c/JXZb7y6) |
| Q14 | 94     | 89                | 90         | 91        | [link](https://sharegpt.com/c/cTXH4IS) |
| Q15 | 90     | 85                | 88         | 87        | [link](https://sharegpt.com/c/GZiM0Yt) |
|     | 91     | 88                | 82         | 80        |          |





## Principle

We adopted the approach of WizardLM, which is to extend a single problem more in-depth. However, instead of using individual instructions, we expanded it using Vicuna's conversation format and applied Vicuna's fine-tuning techniques.

Turning a single command into a rich conversation is what we've done [here](https://sharegpt.com/c/6cmxqq0).

After creating the training data, I later trained it according to the Vicuna v1.1 [training method](https://github.com/lm-sys/FastChat/blob/main/scripts/train_vicuna_13b.sh).


## Detailed Method

First, we explore and expand various areas in the same topic using the 7K conversations created by WizardLM. However, we made it in a continuous conversation format instead of the instruction format. That is, it starts with WizardLM's instruction, and then expands into various areas in one conversation using ChatGPT 3.5.

After that, we applied the following model using Vicuna's fine-tuning format.

## Training Process

Trained with 8 A100 GPUs for 35 hours.

## Weights
You can see the [dataset](https://huggingface.co/datasets/junelee/wizard_vicuna_70k) we used for training and the [13b model](https://huggingface.co/junelee/wizard-vicuna-13b) in the huggingface.

## Conclusion
If we extend the conversation to gpt4 32K, we can expect a dramatic improvement, as we can generate 8x more, more accurate and richer conversations.

## Reactions
#### 1. Report of improved abilities in not only Korean, but also Chinese and Japanese.
Although it was tuned 100% for English, it's curious how the language abilities for other countries, such as Korean, Chinese, and Japanese, have been enhanced even though their share should have decreased.<br/>
[link1](https://huggingface.co/TheBloke/wizard-vicuna-13B-GPTQ/discussions/1) <br/>
[link2](https://arca.live/b/alpaca/75534266?mode=best&p=1)


#### 2. Report of enhanced coding skills.
[link](https://www.reddit.com/r/LocalLLaMA/comments/1386o9f/comment/jixdnoj/?utm_source=share&utm_medium=web2x&context=3)


#### 3. Report of strengthened consistency during conversations.
[link](https://www.reddit.com/r/LocalLLaMA/comments/1376oho/comment/jiwydq4/?utm_source=share&utm_medium=web2x&context=3)


## License
The model is licensed under the LLaMA model, and the dataset is licensed under the terms of OpenAI because it uses ChatGPT. Everything else is free.

## Author

[JUNE LEE](https://github.com/melodysdreamj) - He is active in Songdo Artificial Intelligence Study and GDG Songdo.