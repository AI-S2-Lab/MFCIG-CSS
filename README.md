# [EMNLP'2025, Main] Multimodal Fine-grained Context Interaction Graph Modeling for Conversational Speech Synthesis

## Introduction

This is an implementation of the following paper: ["Multimodal Fine-grained Context Interaction Graph Modeling for Conversational Speech Synthesis"](https://aclanthology.org/2025.emnlp-main.448/) (Accepted by EMNLP 2025 Main)

[**Zhenqi Jia**](https://coder-jzq.github.io/), [Rui Liu](https://ttslr.github.io/people.html), Berrak Sisman, Haizhou Li

Corresponding Author: Rui Liu

## Speech Samples

Code and speech samples are available at:

https://github.com/AI-S2-Lab/MFCIG-CSS

## Dataset

You can download the [dataset](https://drive.google.com/drive/folders/1WRt-EprWs-2rmYxoWYT9_13omlhDHcaL) from DailyTalk.

## Preprocessing

Run

> python3 prepare_align.py --dataset DailyTalk

for some preparations.

For the forced alignment, [Montreal Forced Aligner](https://montreal-forced-aligner.readthedocs.io/en/latest/) (MFA) is used to obtain the alignments between the utterances and the phoneme sequences. Pre-extracted alignments for the dataset are provided [here](https://drive.google.com/drive/folders/1fizpyOiQ1lG2UDaMlXnT3Ll4_j6Xwg7K?usp=sharing). You have to unzip the files in `preprocessed_data/DailyTalk/TextGrid/`. Alternately, you can [run the aligner by yourself](https://montreal-forced-aligner.readthedocs.io/en/latest/user_guide/workflows/index.html).

After that, run the preprocessing script by

> python3 preprocess.py --dataset DailyTalk

## Training

Train MFCIG-CSS with

> python3 train.py --dataset DailyTalk

## Inference

Only the batch inference is supported, as the generation of a turn may require contextual history of the conversation. Try

> python3 synthesize.py --source preprocessed_data/DailyTalk/test_*.txt --restore_step RESTORE_STEP --mode batch --dataset DailyTalk

to synthesize all utterances in `preprocessed_data/DailyTalk/test_*.txt`.

## Citation

If you would like to use our dataset and code or refer to our paper, please cite as follows.

```bibtex
@inproceedings{jia-etal-2025-multimodal,
    title = "Multimodal Fine-grained Context Interaction Graph Modeling for Conversational Speech Synthesis",
    author = "Jia, Zhenqi  and
      Liu, Rui  and
      Sisman, Berrak  and
      Li, Haizhou",
    editor = "Christodoulopoulos, Christos  and
      Chakraborty, Tanmoy  and
      Rose, Carolyn  and
      Peng, Violet",
    booktitle = "Proceedings of the 2025 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2025",
    address = "Suzhou, China",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.emnlp-main.448/",
    doi = "10.18653/v1/2025.emnlp-main.448",
    pages = "8852--8858",
    ISBN = "979-8-89176-332-6",
    abstract = "Conversational Speech Synthesis (CSS) aims to generate speech with natural prosody by understanding the multimodal dialogue history (MDH). The latest work predicts the accurate prosody expression of the target utterance by modeling the utterance-level interaction characteristics of MDH and the target utterance. However, MDH contains fine-grained semantic and prosody knowledge at the word level. Existing methods overlook the fine-grained semantic and prosodic interaction modeling. To address this gap, we propose MFCIG-CSS, a novel Multimodal Fine-grained Context Interaction Graph-based CSS system. Our approach constructs two specialized multimodal fine-grained dialogue interaction graphs: a semantic interaction graph and a prosody interaction graph. These two interaction graphs effectively encode interactions between word-level semantics, prosody, and their influence on subsequent utterances in MDH. The encoded interaction features are then leveraged to enhance synthesized speech with natural conversational prosody. Experiments on the DailyTalk dataset demonstrate that MFCIG-CSS outperforms all baseline models in terms of prosodic expressiveness. Code and speech samples are available at https://github.com/AI-S2-Lab/MFCIG-CSS."
}
```

## Contact the Author

E-mail: [jiazhenqi7@163.com](mailto:jiazhenqi7@163.com)

Homepage: https://coder-jzq.github.io/

S2LAB Homepage: https://ttslr.github.io/
