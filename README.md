# Empowering-Time-Series-Analysis-with-LLM
This is the official repository for "Empowering Time Series Analysis with Large Language Models: A Survey" <br>

This repository is activately maintained by [*Yushan Jiang*](https://sites.google.com/view/jayjiang/home) and [*Zijie Pan*](https://www.linkedin.com/in/zijiepan?challengeId=AQFIFj5C6TIkHAAAAYorMg7B2AeyTHiG6ydTY1x-UI5EGjLsdaZJ0Y0RBaUR2kYx6EBKy_P1l7xa7V_p3eK8ZimyqeIGOvx9BQ&submissionId=0dfe8771-9c89-7e17-1726-261b141fe852&challengeSource=AgGvUfroPpp0hQAAAYorMnRhqu49XriAlKHKecuhg1I-dD3E2L5TzP28ELScYzs&challegeType=AgF5kNYwhmhZKwAAAYorMnRkOD1dOFOY2SyQbE2noHz3ZcyHhGrPSL4&memberId=AgHccQ5LAWwXMgAAAYorMnRmgTbPDp6EVevD51vyoVhsjag&recognizeDevice=AgGWhR25_UZSqAAAAYorMnRphBUCqBMivCqoLXw_jveZM8Iu5Rn_) from ***UConn DSIS*** Group led by [*Dr. Dongjin Song*](https://songdj.github.io/#about).

If you find some ignored papers, **feel free to *create pull requests*, *open issues*, or *email* [*Yushan*](mailto:yushan.jiang@uconn.com) & [*Zijie*](mailto:zijie.pan@uconn.com)**. <br/> 

Please consider [citing](#citation) our survey paper if you find it helpful :), and feel free to share this repository with others! 

### Motivation and Contribution:

The rapid development of LLMs in natural language processing has unveiled unprecedented capabilities in sequential modeling and pattern recognition. It is natural to ask: ***How can LLMs be effectively leveraged to advance general-purpose time series analysis?*** 

Our survey aims to answer the question based on a thorough overview of existing literature, as shown in Figure 1. We claim that LLMs can serve as a flexible as well as highly competent component in the time series modeling: 

1) The flexibility lies in a wide spectrum of available ***LLMs that can be employed and the variety of ways they can be configured for time series analysis***, where we categorize the eexisting methods into five groups based on the methodology.
2) Regarding their competence, ***LLMs can be tailored for a wide range of real-world applications with domain-specific context*** , where we discuss their application tasks and domains.
3) We discuss and highlight future directions that advance time series analysis with LLMs.

<br/>

|[<img src="Survey-Framework.png" width="450"/>](image.png) |[<img src="Categorization.png" width="450"/>](image1.png)|
|:--:|:--:| 
| *Figure 1: The Framework of Our Survey* | *Figure 2: Categorization of Component Design for Fine-tuning Time Series LLMs* |

<br/>

## Taxonomy of Time Series LLMs

### General Pipeline of Time Series LLMs 
To adopt LLMs for time series analysis, three primary methods are employed: ***direct querying of LLMs***, ***fine-tuning LLMs with tailored designs***, and ***incorporating LLMs into time series models as a means of feature enhancement (integration)***. Specifically, three key components can be leveraged to fine-tune LLMs as shown in Figure 2: The input time series are first tokenized into embedding based on proper tokenization techniques, where proper prompts can be adopted2 to further enhance the time series representation. As such, LLMs can better comprehend prompt-enhanced time series embedding and be fine-tuned for downstream tasks, based on sophisticated strategies.


The data type **TS** denotes general time series, **ST** denotes spatial-temporal time series, the prefix **M-** indicates multi-modal inputs. ***Q*** denotes direct query the whole LLMs for output, ***T*** denotes the design of time series tokenization, ***P*** indicates the design of textual or parameterized time series prompts, ***FT*** indicates if the parameters of LLMs are updated (fine-tuned), ***I*** indicates if LLMs are integrated as part of the final model for downstream tasks. *Code availability is assessed on January 31st, 2024.*

 
| <sub>**Method**</sub> | <sub> Data </sub> | <sub>Domain</sub> | <sub>Task</sub> | <sub>*Q*</sub> | <sub>*T*</sub> | <sub>*P*</sub> | <sub>*FT*</sub> | <sub>*I*</sub> | <sub>LLM</sub> | <sub>Code</sub> |
|:--------:|:-----:|:--------:|:------:|:-------:|:-------:|:--------:|:-----------:|:---------:|:-----:|:---:|
| <sub>[Time-LLM](https://arxiv.org/pdf/2310.01728.pdf)<br/>(ICLR 2024)</sub> | <sub>M-TS</sub> | <sub>General</sub> | <sub>Forecasting</sub> | ✘ | ✔ | ✔ | ✔ | ✘ | <sub>LLaMA, GPT-2</sub> | [✔](https://github.com/kimmeen/time-llm)|
| <sub>[OFA](https://openreview.net/pdf?id=gMS6FVZvmF)<br/>(NeurIPS 2023)</sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Forecasting,<br/>Classification,<br/>Imputation,<br/>Anomaly Detection</sub> | ✘ | ✔ | ✘ | ✔ | ✘ | <sub>GPT-2</sub> | [✔](https://github.com/DAMO-DI-ML/NeurIPS2023-One-Fits-All) |
| <sub>[TEMPO](https://arxiv.org/pdf/2310.04948.pdf)<br/>(ICLR2024)</sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Forecasting</sub> | ✘ | ✔ | ✔ | ✔ | ✘ | <sub>GPT-2</sub> | <sub>✘</sub> |
| <sub>[TEST](https://arxiv.org/pdf/2210.08964.pdf)<br/>(ICLR2024)</sub> | <sub>M-TS</sub> | <sub>General</sub> | <sub>Forecasting, Classification</sub> | ✘ | ✔ | ✔ | ✘ | ✔ | <sub>BERT, GPT-2,<br/> ChatGLM, LLaMA2</sub> | [✔](https://openreview.net/forum?id=Tuh4nZVb0g) |
| <sub>[LLM4TS, 2023](https://arxiv.org/pdf/2308.08469.pdf)<br/></sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Forecasting</sub> | ✘ | ✔ | ✘ | ✔ | ✘ | <sub>GPT-2</sub> | <sub>✘</sub> |
| <sub>[PromptCast](https://arxiv.org/pdf/2210.08964.pdf)<br/>(IEEE TKDE 2023)</sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Forecasting</sub> | ✔ | ✘ | ✔ | ✘ | ✘ | <sub>Bart, BERT, etc.</sub> | [✔](https://github.com/HaoUNSW/PISA) |
| <sub>[LLMTIME](https://openreview.net/pdf?id=md68e8iZK1)<br/>(NeurIPS 2023)</sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Forecasting</sub> | ✔ | ✔ | ✘ | ✘ | ✘ | <sub>GPT-3, LLaMA-2</sub> | [✔](https://github.com/ngruver/llmtime</sub>) |
| <sub>[LAMP](https://openreview.net/pdf?id=aW9BqtRQkh)<br/>(NeurIPS 2023)</sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Event Prediction</sub> | ✔ | ✘ | ✔ | ✘ | ✔ | <sub>GPT-3 & 3.5,<br/> LLaMA-2</sub> | [✔](https://github.com/iLampard/lamp) |
| <sub>[Gunjal *et al.*, 2023](https://arxiv.org/pdf/2305.14847.pdf)</sub> | <sub>TS</sub> | <sub>General</sub> | <sub>Event Prediction</sub> | ✔ | ✘ | ✔ | ✘ | ✘ | <sub>GPT-3.5, Flan-T5, etc.</sub> | <sub>✘</sub> |
| <sub>[Yu *et al.*, 2023](https://arxiv.org/pdf/2306.11025.pdf)</sub>| <sub>M-TS</sub> | <sub>Finance</sub> | <sub>Forecasting</sub> | ✔ | ✘ | ✔ | ✔ | ✘ | <sub>GPT-4, Open-LLaMA</sub> | <sub>✘</sub> | <sub>[10]</sub> |
| <sub>[Lopez-Lira *et al.*, 2023](https://arxiv.org/pdf/2304.07619.pdf)</sub> | <sub>M-TS</sub> | <sub>Finance</sub> | <sub>Forecasting</sub> | ✔ | ✘ | ✔ | ✘ | ✔ | <sub>ChatGPT</sub> | <sub>✘</sub> |
| <sub>[Xie *et al.*, 2023](https://arxiv.org/abs/2304.05351.pdf)</sub> | <sub>M-TS</sub> | <sub>Finance</sub> | <sub>Classification</sub> | ✔ | ✘ | ✔ | ✘ | ✘ | <sub>ChatGPT</sub> | <sub>✘</sub> |
| <sub>[Chen *et al.*, 2023](https://arxiv.org/pdf/2306.03763.pdf)</br>(RobustFin@KDD2023)</sub> | <sub>M-TS</sub> | <sub>Finance</sub> | <sub>Classification</sub> | ✘ | ✘ | ✔ | ✘ | ✔ | <sub>ChatGPT</sub> | [-](https://github.com/ZihanChen1995/ChatGPT-GNN-StockPredict) |
| <sub>[METS, 2023](https://arxiv.org/pdf/2303.12311.pdf)</br></sub> | <sub>M-TS</sub> | <sub>Healthcare</sub> | <sub>Classification</sub> | ✔ | ✘ | ✔ | ✘ | ✔ | <sub>ClinicalBERT</sub> | <sub>✘</sub> |
| <sub>[Jiang *et al.*,2023](https://www.nature.com/articles/s41586-023-06160-y)<br/>(Nature Comput. Sci.)</sub> | <sub>M-TS</sub> | <sub>Healthcare</sub> | <sub>Classification</sub> | ✘ | ✘ | ✘ | ✔ | ✘ | <sub>NYUTron(BERT)</sub> | [✔](https://github.com/nyuolab/NYUTron) |
| <sub>[Liu *et al.*, 2023](https://arxiv.org/pdf/2305.15525.pdf)</sub> | <sub>M-TS</sub> | <sub>Healthcare</sub> | <sub>Forecasting, Classification</sub> | ✔ | ✘ | ✔ | ✔ | ✘ | <sub>PaLM</sub> | <sub>✘</sub> |
| <sub>[AuxMobLCast](https://arxiv.org/pdf/2209.05479.pdf)<br/>(SIGSPATIAL 2022)</sub> | <sub>ST</sub> | <sub>Mobility</sub> | <sub>Forecasting</sub> | ✘ | ✘ | ✔ | ✔ | ✔ | <sub>BERT, RoBERTa,<br/> GPT-2, XLNet</sub> | [✔](https://github.com/cruiseresearchgroup/AuxMobLCast) |
| <sub>[LLM-Mob, 2023](https://arxiv.org/pdf/2308.15197.pdf)</sub> | <sub>ST</sub> | <sub>Mobility</sub> | <sub>Forecasting</sub> | ✔ | ✘ | ✔ | ✘ | ✘ | <sub>GPT-3.5</sub> | [✔](https://github.com/xlwang233/LLM-Mob) |
| <sub>[ST-LLM, 2024](https://arxiv.org/pdf/2401.10134v1.pdf)</sub> | <sub>ST</sub> | <sub>Traffic</sub> | <sub>Forecasting</sub> | ✘ | ✔ | ✘ | ✔ | ✘ | <sub>LLaMA, GPT-2</sub> | <sub>✘</sub> |
| <sub>[GATGPT, 2023](https://arxiv.org/pdf/2311.14332.pdf) | <sub>ST</sub> | <sub>Traffic</sub> | <sub>Imputation</sub> | ✘ | ✔ | ✘ | ✔ | ✘ | <sub>GPT-2</sub> | <sub>✘</sub> |
| <sub>[LA-GCN, 2023](https://arxiv.org/pdf/2305.12398.pdf)</sub> | <sub>M-ST</sub> | <sub>Vision</sub> | <sub>Classification</sub> | ✘ | ✔ | ✘ | ✘ | ✔ | <sub>BERT</sub> | [✔](https://github.com/damNull/LAGCN) |

### Task & Domains




## Citation
```
@misc{jiang2024empowering,
      title={Empowering Time Series Analysis with Large Language Models: A Survey}, 
      author={Yushan Jiang and Zijie Pan and Xikun Zhang and Sahil Garg and Anderson Schneider and Yuriy Nevmyvaka and Dongjin Song},
      year={2024},
      eprint={2402.03182},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```

