Details Coming Soon...

# :ear_of_rice: DATA SOURCE

Each example in `DEMETR` consists of `source text`, `human translation`, `machine translation`, and `perturbed machine translation`. The `source text` -- `human translation` pairs were sampled equally from `FLORES` and `WMT` datasets (test sets). We sampled 100 sentences per language (50 from each of the datasets). The average length of each sentence varied between 15 and 25 words. We decided to sample longer sentences as they were more likely to include phenomena of our interest. At the same time, we tried to keep the standard deviation within reasonable boundaries to avoid situation where we some languages will have significantly longer sentences than the others.

The machine translation included in `DEMETR` was obtained using primarily Google Translate API (all translations were done in May, 2022). Additionally, we used DeepL API and GPT-3 API (May, 2022) to generate additional caditates during the check process. We manually checked each example in the base 1K source text, human translation, machine translation triplets which were later used to generate the perturbed machine translation. We made sure that both the human translation and the machine translation were of a satisfactory quality. In case of minor mistakes in either the human translation, machine translation, or, less frequent, the source text, we manually edited the text. In cases where it was difficult to edit the text (for instance there was not enough context) we replaced the example with a new one satifying our sampling criteria. In rare cases, we had to resample examples that were shorter than 15 words or longer than 25 words due to the lack of other reasonable cadidates (were were specifically restricted with FLORES as the sentences overlap between languages).





# PERTURBATIONS DETAILS

comming soon -- please feel free to email us if you have any questions before this one is ready
