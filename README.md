# sae4K: Structured Argument Extraction for Korean

<image src="https://github.com/warnikchow/sae4k/blob/master/image/fig_xxxyy.png" width="750"><br/>

### Scheme at a glance (click for the higher resolution!) <br/>
  
<image src="https://github.com/warnikchow/sae4k/blob/master/image/fig1.PNG" width="400"><br/>

#### (20.10.17) [Our paper](https://arxiv.org/abs/1912.00342) accepted at EMNLP 2020 Findings! License was added. Model and code are to be published after cleansing :) 
#### (19.10.10) Augmented dataset revealed! (more balanced, and still labeled) The augmentation follows [this paper](https://www.aclweb.org/anthology/2020.lrec-1.842/)
#### An additional dataset construction and the computational approach is in progress; will be disclosed with a paper.

## Summary
### This is an annotation guideline for the Korean questions and commands that are possibly non-canonical and highly conversation-style.
For the questions, the effective question set is obtained, and for the commands, the to-do-list is extracted; we call these **intent arguments** or **natural language query**. The extraction process is not rule-based and fully manual, and this can also be supplemented by a [generation process](https://www.aclweb.org/anthology/2020.lrec-1.842/). Our concept is slightly different from slot-filling since the utterances are non-domain-specific and some contain lexicons that are often not acceptable for conventional task-oriented dialog managers. We aim extracting the arguments from those utterances in a structured format.
### The extraction process does not base on just entity recognition; it converts the *wh-* particles or requrements into the lexicon that is proper.
For instance, for two questions *"When will rain stop"* and *"When are you going vacation"*, the former asks for the time or period, while the latter asks for the day, week or month. We utilize various wh- related nouns to extract the question set appropriately. The similar holds for the commands, from requirements to the order-related lexicon.
### The extraction process omits the components that are not necessary for the content.
In Korean, and possibly for many other languages, not all the words (or particles) in the sentence may be necessary for the extraction of the arguments. For such non-canonical directive utterances, words or particles that are not appropriate to be included in the argument, are removed considering the semantics. This might convert a noisy input utterance into the format that let dialogue managers label the semantic roles more easily.

## [sae4k_v1.txt](https://github.com/warnikchow/sae4k/blob/master/data/sae4k_v1.txt): Original Corpus
### Questions - [Question-Argument] pairs w/ question type label
- Yes/no (label 0): 5,718 (31.99%)
- Alternative (label 1): 227 (1.27%)
- Wh- (label 2): 11,924 (66.73%)
### Commands - [Command-Argument] pairs w/ negativeness label
- Prohibition (label 3): 477 (3.67%)
- Requirement (label 4): 12,369 (95.38%)
- Strong requirement (label 5): 122 (0.94%)

## [sae4k_v2.txt](https://github.com/warnikchow/sae4k/blob/master/data/sae4k_v2.txt): Augmented Corpus
- Alternative Q: +4,000
- Wh- Q: +8,000
- Prohibition: +4,000
- Strong requirement: +4,000
### Total 50,837 utterances!
- Little modification on *sae4k_v1.txt*
- Labels are in the first column; second is for the sentences and third for the keyphrases.

## Implementation
### Transformer-based training may provide you the followings (not sure RNN can do something...)

<image src="https://github.com/warnikchow/sae4k/blob/master/image/fig2_2.png" width="800"><br/>

<image src="https://github.com/warnikchow/sae4k/blob/master/image/fig2_.png" width="1000"><br/>
  
### Todo: 

- Handling OOVs (challenging for Korean as always)
- Obtaining larger dataset (always required!) - In progress with [StyleKQC](https://github.com/cynthia/stylekqc)
- Utilizing pretrained language models (that can compensate our shortage of data)

### After all, *Typological approaches*!! (Always open for (multi-lingual) collaborations!!)

## Citation
### For the annotation guideline, please cite the following:

```
@article{cho2018extracting,
  title={Extracting Arguments from Korean Question and Command: An Annotated Corpus for Structured Paraphrasing},
  author={Cho, Won Ik and Moon, Young Ki and Kang, Woo Hyun and Kim, Nam Soo},
  journal={arXiv preprint arXiv:1810.04631},
  year={2018}
}
```

### If you have found our dataset or seq2seq-based settings useful:

```
@inproceedings{cho2020machines,
  title={Machines Getting with the Program: Understanding Intent Arguments of Non-Canonical Directives},
  author={Cho, Won Ik and Moon, Youngki and Moon, Sangwhan and Kim, Seok Min and Kim, Nam Soo},
  booktitle={Findings of the Association for Computational Linguistics: EMNLP 2020},
  pages={329--339},
  year={2020}
}
```
