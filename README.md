# RemixIT-TSE 
 
This repository is the official project page for **RemixIT-TSE: Progressive Synthetic-to-Real Adaptation for Target Speech Extraction via Target-Aware Supervision and Remixing**. 
 
RemixIT-TSE extends the RemixIT paradigm from speech enhancement to real-world target speech extraction (TSE), enabling adaptation to real conversational recordings without requiring signal-level clean target references. 
 
> **Note:** The paper is currently under review. Pre-trained models and audio demonstrations will be released first. The complete training and adaptation code will be made publicly available after paper acceptance. 
 
## 🔥 News 
 
- [**2026-10-08**] The [RemixIT-TSE demo page](https://htmlpreview.github.io/?https://github.com/YuWang-Speech/RemixIT-TSE/blob/main/index.html#audio-demo) is available.
- [**2026-09-28**] The [RemixIT-TSE preprint](https://arxiv.org/abs/2609.35118) is available on arXiv. 
 
## About RemixIT-TSE 
 
Target Speech Extraction (TSE) aims to extract the speech of a target speaker from a multi-speaker mixture using an enrollment utterance. Although supervised TSE systems perform well on synthetic mixtures, their performance often degrades substantially in real-world conversational environments where clean target references are unavailable. 
 
We propose **RemixIT-TSE**, a progressive synthetic-to-real adaptation framework that transfers a synthetic-trained TSE model to real-world recordings through three stages: 
 
1. **Synthetic-Data Pretraining (SDP)**   
   Establishes the fundamental target extraction capability using fully supervised synthetic mixtures. 
 
2. **Target-Aware Adaptation (TAA)**   
   Introduces real-domain information through joint synthetic-real training with weak speaker and temporal annotations. 
 
3. **RemixIT-TSE Adaptation (RTA)**   
   Further adapts the model using only real-world recordings through teacher-generated pseudo-targets and remixing. 
 
Compared with the original RemixIT framework, RemixIT-TSE introduces two key modifications tailored to TSE: 
 
- **Quality-aware pseudo-target filtering**, with particular emphasis on speaker similarity, to suppress unreliable teacher estimates. 
- **Target-only supervision**, removing the original Non-target/residual loss to better align the adaptation objective with target-speaker extraction. 
 
<p align="center"> 
  <img src="resources/framework.png" width="95%"> 
</p> 
 
## Performance 
 
We evaluate RemixIT-TSE on the **REAL-TSE Challenge**  evaluation sets. 
 
### REAL-TSE Evaluation Set 
 
| Set | System | TER ↓ | SIM ↑ | OVRL ↑ | P808 ↑ | F1 ↑ | 
|:---:|:---|:---:|:---:|:---:|:---:|:---:| 
| EVAL-1 | SDP (Baseline) | 0.726 | 0.485 | 2.049 | 2.923 | 0.824 | 
| EVAL-1 | **RemixIT-TSE** | **0.680** | **0.533** | **2.173** | **3.088** | **0.837** | 
| EVAL-2 | SDP (Baseline) | 0.763 | 0.335 | 1.850 | 2.710 | 0.804 | 
| EVAL-2 | **RemixIT-TSE** | **0.713** | **0.408** | **2.040** | **2.978** | **0.837** | 
| Combined | SDP (Baseline) | 0.748 | 0.395 | 1.929 | 2.790 | 0.812 | 
| Combined | **RemixIT-TSE** | **0.700** | **0.458** | **2.093** | **3.022** | **0.837** | 
 
On the unseen **EVAL-2** set, RemixIT-TSE achieves a **6.53% relative TER reduction**, together with relative improvements of **21.84% in SIM**, **9.89% in DNSMOS-P808**, and **4.10% in F1** over the source-domain baseline. 
 
## Audio Demo 
 
Representative real-world examples are provided on the [**RemixIT-TSE demo page**](https://htmlpreview.github.io/?https://github.com/YuWang-Speech/RemixIT-TSE/blob/main/index.html#audio-demo) for qualitative comparison. Each example contains the same input mixture and target-speaker enrollment utterance, together with outputs from different systems:

- Mixture
- Enrollment utterance
- SDP baseline
- SAMoM (synthetic clean)
- SAMoM (real single-spk.)
- RemixIT-TSE

All systems process the same mixture using the same target-speaker enrollment utterance. Audio samples will be added progressively.
 
## Pre-trained Models 
 
Pre-trained RemixIT-TSE models will be released in the `checkpoints` folder. 
 
| Model | Description | Checkpoint | 
|:---|:---|:---:| 
| SDP | Synthetic-data pretrained baseline | Coming soon | 
| RemixIT-TSE | Final progressively adapted model | Coming soon | 
 
## Code Release 
 
To facilitate reproducibility, we plan to release the complete codebase after the paper review process. 
 
The future release will include: 
 
- Data preparation 
- Synthetic-Data Pretraining (SDP) 
- Target-Aware Adaptation (TAA) 
- Quality-aware pseudo-target filtering 
- RemixIT-TSE Adaptation (RTA) 
- Inference and evaluation scripts 
 
For now, this repository provides the model checkpoints, framework description, and audio demonstrations. 
 
## Citation 
 
If you find this work useful, please consider citing our paper: 
## Citation

If you find this work useful, please consider citing our paper:
```bibtex
@article{wang2026remixittse,
      title={RemixIT-TSE: Progressive Synthetic-to-Real Adaptation for Target Speech Extraction via Target-Aware Supervision and Remixing}, 
      author={Yu Wang and Haixin Guan and Shuang Wei and Yanhua Long},
      year={2026},
      eprint={2609.35118},
      archivePrefix={arXiv},
      primaryClass={cs.SD},
      url={https://arxiv.org/abs/2609.35118}, 
}
```
