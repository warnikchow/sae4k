# SAE4K
Structured Argument Extraction for Korean

## Summary
### This is an annotation guideline for the Korean questions and commands that are possibly non-canonical and highly conversation-style.
For the questions, the effective question set is obtained, and for the commands, the to-do-list is extracted; we call these **arguments**. The extraction process is not rule-based and fully manual for the corpus generation. The concept is slightly difference from slot-filling since the utterances are non-domain-specific and some contain inappropriate terms for the conventional dialog managers. We aim extracting the arguments from those utterances in a structured format.
### The extraction process does not base on just entity recognition; it converts the wh-particles or commands into the lexicon that is proper.
For instance, for two questions "When will rain stop" and "When are you going vacation", the former asks for the time or period, while the latter asks for the day, week or month. We utilize various wh- and command- related nouns to extract the question set and to-do-list appropriately. The similar holds for the commands.
### The extraction process omits the components that are not necessary for the content.
In Korean, and possibly for many other languages, not all the words (or particles) in the sentence may be necessary for the extraction of the arguments. For such non-canonical directive utterances, words or particles that are not appropriate to be included in the argument, are removed considering the semantics. This might convert a noisy input utterance into the format that let dialogue managers label the semantic roles more easily.
#### An additional dataset construction and the computational approach is in progress; will be disclosed with a paper.

## Corpus Description
### Questions - [Question-Argument] pairs w/ question type label
- Yes/no (label 0): 2,196 (45.95%)
- Alternative (label 1): 212 (4.43%)
- Wh- (label 2): 2,371 (49.61%)
### Commands - [Command-Argument] pairs w/ positivity label
- Prohibition (label 0): 412 (8.61%)
- Requirement (label 1): 4,268 (89.28%)
- Strong requirement (label 2): 100 (2.09%)

## Reference
- W. I. Cho, W. H. Kang, and N. S. Kim, "Structured argument extraction of Korean question and command," arXiv:1810.04631, Oct. 2018. [[paper]](https://arxiv.org/abs/1810.04631)

```
@article{cho2018structured,
  title={Structured Argument Extraction of Korean Question and Command},
  author={Cho, Won Ik and Kang, Woo Hyun and Kim, Nam Soo},
  journal={arXiv preprint arXiv:1810.04631},
  year={2018}
}
```
