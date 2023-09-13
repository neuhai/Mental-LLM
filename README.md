# Mental-LLM

## Overview
This is the repository for the paper [```Mental-LLM: Leveraging Large Language Models for Mental Health Prediction via Online Text Data```](https://arxiv.org/abs/2307.14385), an updated version of this paper is under review.

In this work, we present the first comprehensive evaluation of multiple LLMs, including Alpaca, Alpaca-LoRA, FLAN-T5, GPT-3.5, and GPT-4, on various **mental health prediction tasks via online text data**. We conduct a broad range of experiments, covering zero-shot prompting, few-shot prompting, and instruction fine-tuning. More importantly, our experiments show that instruction finetuning can significantly boost the performance of LLMs for all tasks simultaneously. 

Our best-finetuned models, Mental-Alpaca and Mental-FLAN-T5, outperform the best prompt design of GPT-3.5 by 10.9% and the best of GPT-4 by 4.8% on balanced accuracy and perform on par with the state-of-the-art task-specific language model. 

We have publically released our fine-tuned model weights on huggingface hub. The use of both model weights is limited to research purposes only:
- Mental-Alpaca: https://huggingface.co/NEU-HAI/mental-alpaca
- Mental-FLAN-T5: https://huggingface.co/NEU-HAI/mental-flan-t5-xxl

You may find sample codes to load both models from the repositories above directly. Details about the prompts, training process, and evaluations can be found in our [paper](https://arxiv.org/abs/2307.14385). The GPU Memory requirement to **load** Mental-Alpaca and Mental-FLAN-T5 is 27GB and 44GB, respectively, and will require additional GPU Memory for inference.

## Todo

- [ ] Organize code for prompt designing, model fine-tuning, and inference
- [x] Release model weights to Huggingface hub (upon acceptance)

## Contributions

### Inference Settings

#### Zero-shot Prompting

$Prompt_{𝑍𝑆} = TextData + Prompt_{Part1-S} + Prompt_{Part2-Q} + OutputConstraint$

#### Few-shot Prompting

$Prompt_{𝐹𝑆} = [Sample Prompt_{𝑍𝑆} − label]𝑀 + Prompt_{𝑍𝑆}$, where $M$ denotes # of demonstrations

#### Prompt Designs

<p align="middle">
  <img src="https://github.com/neuhai/Mental-LLM/blob/main/prompt_designs.png" alt="Prompt Designs" title="Prompt Designs" width=800/>
</p>

### Datasets

- **Dreaddit** \
This dataset collected posts from Reddit, which contains ten subreddits in the five domains (abuse, social, anxiety, PTSD, and financial).\
We used this dataset for a post-level binary stress prediction (**Task 1**).
- **DepSeverity** \
This dataset leveraged the same posts collected in Dreaddit, but with a different focus on depression.\
We employed this dataset for two post-level tasks: binary depression prediction (i.e., whether a post showed at least mild depression, **Task 2**), and four-level depression prediction (**Task 3**).
-  **SDCNL** \
This dataset also collected posts from Reddit, including r/SuicideWatch and r/Depression.\
We employed this dataset for the post-level binary suicide ideation prediction (**Task 4**).
- **CSSRS-Suicide** \
This dataset contains posts from 15 mental health-related subreddits.\
We leveraged this dataset for two user-level tasks: binary suicide risk prediction (i.e., whether a user showed at least suicide indicator, **Task 5**), and five-level suicide risk prediction (**Task 6**).

### Models
- Alpaca-7b
- Alpaca-LoRA
- FLAN-T5-XXL
- GPT-3.5
- GPT-4

### Results

<p align="middle">
  <img src="https://github.com/neuhai/Mental-LLM/blob/main/results.png" alt="Results" title="Results" width=800/>
</p>

<p align="middle">
  <img src="https://github.com/neuhai/Mental-LLM/blob/main/enhanced_results.png" alt="Enhanced Results" title="Enhanced Results" width=800/>
</p>


More results can be found in the paper.

## Citation
```
@article{xu2023mentalllm,
      title={Mental-LLM: Leveraging Large Language Models for Mental Health Prediction via Online Text Data}, 
      author={Xuhai Xu and Bingshen Yao and Yuanzhe Dong and Saadia Gabriel and Hong Yu and James Hendler and Marzyeh Ghassemi and Anind K. Dey and Dakuo Wang},
      year={2023},
      eprint={2307.14385},
      archivePrefix={arXiv},
      primaryClass={cs.HC}
}
```
