<p align="center" width="100%">
<img src="https://user-images.githubusercontent.com/21379657/235832523-0d5656e3-fbbc-48f1-becb-0c3fe22ade0b.png" alt="KoVicuna icon" style="width: 300px; height:300px; display: block; margin: auto; border-radius: 50%;">
</p>

## Update Logs

- 2023.4.20: [🤗LLAMA 7B 기반 KoVicuna 모델](https://huggingface.co/junelee/ko_vicuna_7b) 을 공개합니다.

--- 
# WizardVicunaLM
I am a big fan of the ideas behind WizardLM and VicunaLM. I particularly like the idea of WizardLM handling the dataset itself more deeply and broadly, as well as VicunaLM overcoming the limitations of single-turn conversations by introducing multi-round conversations. As a result, I combined these two ideas to create WizardBikunaLM. This project is highly experimental and designed for proof of concept, not for actual usage.
 
## Benchmark

The questions presented here are not from rigorous tests, but rather, I asked a few questions and requested GPT-4 to score them. The models compared were WizardVicunaLM, ChatGPT 3.5, VicunaLM, and WizardLM, in that order.

## Principle

We adopted the approach of WizardLM, which is to extend a single problem more in-depth. However, instead of using individual instructions, we expanded it using Vicuna's conversation format and applied Vicuna's fine-tuning techniques.

## Detailed Method

First, we explore and expand various areas in the same topic using the 7K conversations created by WizardLM. However, we made it in a continuous conversation format instead of the instruction format. That is, it starts with WizardLM's instruction, and then expands into various areas in one conversation using ChatGPT 3.5.

After that, we applied the following model using Vicuna's fine-tuning format.

## Training Process

Trained with 8 A100 GPUs for 35 hours.

## Weights

According to the license, the delta weights have been made public here. You can obtain the original data by inverting the weights on Hugging Face.

## Conclusion

While it does show better performance in some benchmarks, it does not demonstrate a dramatic improvement.

We observed a slight effect, and although dataset optimization can improve performance, continuous efforts are required. Vicuna also achieved significant performance improvements by introducing a multi-round learning format, but adding more data did not lead to another substantial performance increase.

In some cases, much better answers were provided when the same question was asked multiple times. As a result, it is predicted that performance will increase significantly once more if feedback is provided through Human Feedback Reinforcement Learning (HFRL).
