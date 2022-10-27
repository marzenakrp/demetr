#  :ear_of_rice: DEMETR: Diagnosing Evaluation Metrics for Translation

[![arxiv](https://img.shields.io/badge/arXiv-2205.09726-b31b1b.svg)](http://arxiv.org/abs/2210.13746)

This is the official repository for the DEMETR dataset design to perform diagnostics on Machine Translation (MT) evaluation metrics (check out our [paper](http://arxiv.org/abs/2210.13746) for details). DEMETR consists of **35** perturbations spanning sematic, syntactic, and morphological error categories.

Some key features of DEMETR include:  
:hibiscus: manually verified `source text`, `human translation`, and `machine translation` (special attention was given to avoid translation artifacts such as translationese);  
:hibiscus: carefully designed perturbations based on the `MQM` [error annotation schema](https://themqm.org/error-types-2/typology);  
:hibiscus: 10 different source languages (:poland: Polish, :czech_republic: Czech, 🇷🇺 Russian, 🇩🇪 German, 🇫🇷 French, 🇮🇹 Italian, 🇪🇸 Spanish, 🇯🇵 Japanese, 🇨🇳 Chinese, :india: Hindi) to challenge reference-less MT evaluation metrics;  
:hibiscus: manual implementation or manual check on more challenging perturbation to assure their plausability.  

## Details

DEMETR dataset consists of **35** `json` files (one for each perturbation), each of which contains 1K test items. Each test item includes the following:
- `id` item id ranging from 1 to 1000 (unique for each of the 1K source sentences in DEMETR)
- `src_sent` sentence in the source language
- `eng_sent` human translation of the source sentence (manually edited for better quality)
- `mt_sent` machine translation of the source sentence (manually edited for better quality)
- `pert_sent` perturbed machine translation
- `lang_tag` language of the source text
- `data_source` dataset where the source and English translations came from (`FLORES` or `WMT`)
- `pert_check` if `true` the sentence was correctly perturbed. Not all perturbations could be applied to all sentences. For instance, a sentence has to have a number in order for that number to be changed.
- `severity` either `minor`, `major`, `critical`, or `base` to account for the severity of error
- `pert_id` the `id` of the perturbation as listed in the paper (1-35)
- `pert_desc` short description of the perturbation
- `pert_name` unique perturbation name containing the severity type and the perturbation id

Here is an example of one entry:
```
{
    "id": 18,
    "src_sent": "该声明称，土耳其还将接管对被捕的伊斯兰国武装分子的看守任务；欧洲国家拒绝将他们遣送回国。",
    "eng_sent": "Turkey would also take over the task of guarding captured ISIS fighters which, the statement said, European nations have refused to repatriate.",
    "mt_sent": "Turkey would also take over custody of captured Islamic State fighters which, the statement said, European countries have refused to send home.",
    "pert_sent": "Turkey would also take over custody of captured Islamic State fighters which, the statement said, European countries have agreed to send home.",
    "lang_tag": "chinese_simple",
    "data_source": "FLORES",
    "pert_check": true,
    "severity": "critical",
    "pert_id": 7,
    "pert_desc": "changing a word to its antonym (noun, adv, adj, verb)",
    "pert_name": "critical_id7_antonym"
  },
```

## Coming Soon... <img src="https://github.com/marzenakrp/demetr/blob/main/assets/dementor-new.png" width="20">
Despite all work put into the creation of DEMETR, there are still some limitations to the dataset. One of such is that DEMETR is still sentence-level diagnostic dataset, which is unable to evaluate metrics' sensitivity to the discourse level errors. Another is that DEMETR contains only translations into English, which limits its diagnostic capabilities to the to-English translation. We recognize these limitations and are working on a sister dataset. Stay tuned! 
<img src="https://github.com/marzenakrp/demetr/blob/main/assets/dementor-new.png" width="20">


## Citation

If you use DEMETR, please cite it as follows:

```
@inproceedings{demetr-2022,
author={Marzena Karpinska and Nishant Raj and Katherine Thai and Yixiao Song and Ankita Gupta and Mohit Iyyer},
booktitle = "Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing",
Year = "2022",
Title={DEMETR: Diagnosing Evaluation Metrics for Translation},
}
```
