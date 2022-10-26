#  :ear_of_rice: DEMETR: Diagnosing Evaluation Metrics for Translation
This is the official repository for the DEMETR dataset design to perform diagnostics on Machine Translation (MT) evaluation metrics (check out our [paper](http://arxiv.org/abs/2210.13746) for details). DEMETR consists of **35** perturbations spanning sematic, syntactic, and morphological error categories.

Some key features of DEMETR include:  
:hibiscus: manually verified `source text`, `human translation`, and `machine translation` (special attention was given to avoid translation artifacts such as translationese);  
:hibiscus: carefully designed perturbations based on the `MQM` error annotation schema (https://themqm.org/error-types-2/typology/);  
:hibiscus: 10 different source languages (:poland: Polish, :czech_republic: Czech, 🇷🇺 Russian, 🇩🇪 German, 🇫🇷 French, 🇮🇹 Italian, 🇪🇸 Spanish, 🇯🇵 Japanese, 🇨🇳 Chinese, :india: Hindi) to challenge reference-less MT evaluation metrics;  
:hibiscus: manual implementation or manual check on more challenging perturbation to assure their plausability.  

## Details

DEMETR dataset consists of **35** `json` files (one for each perturbation), each of which contains 1K test items. Each test item includes the following:
- `id` item id ranging from 1 to 1000
- `src_sent` sentence in the source language
- `eng_sent` human translation of the source sentence
- `mt_sent` edited machine translation of the source sentence
- `pert_sent` perturbed machine translation
- `lang_tag` language of the source text
- `data_source` dataset where the source and English translation come from
- `pert_check` if `true` the sentence was correctly perturbed. Not all perturbations could be applied to all sentences. For instance, a sentence has to have a number in order to change that number.
- `severity` either `minor`, `major`, `critical`, or `base` to account for the severity of the error
- `pert_id` the `id` of the perturbation as listed in the paper (1-35)
- `pert_desc` short description of the perturbation
- `pert_name` unique perturbation name containing the severity type and the perturbation id

Here is an example of one entry:
```
{
    "id": 7,
    "src_sent": "他的研究表明，施用激素可加速宝宝胎肺的成熟。",
    "eng_sent": "His research showed that if a hormone was administered it would speed up the baby's foetal lung maturation.",
    "mt_sent": "His research shows that the administration of hormones can accelerate the maturation of the baby's fetal lungs.",
    "pert_sent": "His research shows that the administration of hormones can slow down the maturation of the baby's fetal lungs.",
    "lang_tag": "chinese_simple",
    "data_source": "FLORES",
    "pert_check": true,
    "severity": "critical",
    "pert_id": 7,
    "pert_desc": "changing a word to its antonym (noun, adv, adj, verb)",
    "pert_name": "critical_id7_antonym"
  }
```



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
