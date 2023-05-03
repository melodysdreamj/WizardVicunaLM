# WizardVicunaLM

# Background
I am a big fan of the ideas behind WizardLM and BikunaLM. Specifically, I like the idea of WizardLM handling the dataset itself more deeply and broadly, as well as BikunaLM overcoming the limitations of single-turn conversations by introducing multi-round conversations. As a result, I combined these two ideas to create WizardBikunaLM.

# Benchmark
The questions presented here are not from rigorous tests, but rather, I asked a few questions and requested GPT-4 to score them.

# Principle
We adopted the approach of WizardLM, which is to extend a single problem more in-depth. However, instead of using individual instructions, we expanded it using Bikuna's conversation format. It is as follows:

[Image]

# Detailed Method
First, we explore various areas in the same topic using the 7K conversations created by WizardLM. However, we made it in a continuous conversation format. That is, it starts with WizardLM's instruction, and then expands into various areas in one conversation using ChatGPT 3.5.

After that, we applied the following model using Bikuna's fine-tuning format.

# Training Process
Trained with 8 A100 GPUs for 35 hours.

# Weights
According to the license, the delta weights have been made public here. You can obtain the original data through ~~.

# Conclusion
While it does show better performance in some benchmarks, it does not demonstrate a dramatic improvement. We observed a slight effect, and although dataset optimization can improve performance, continuous efforts are required. Bikuna achieved significant performance improvements by introducing a multi-round learning format, but adding more data did not lead to another substantial performance increase.

In some cases, much better answers were provided when the same question was asked multiple times. As a result, it is predicted that performance will increase significantly once more if feedback is provided through Human Feedback Reinforcement Learning (HFRL).
