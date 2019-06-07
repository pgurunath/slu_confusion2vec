# slu_confusion2vec

## Introduction
For SLU researches involving ATIS dataset, the most commonly used text data and train/dev/test split settings are from [the JointSLU repo](https://github.com/yvchen/JointSLU)[[paper](https://www.csie.ntu.edu.tw/~yvchen/doc/IS16_MultiJoint.pdf)]. However, the authors in this paper only provide intent and slot labels regarding to text, and no labels for audio samples in ATIS dataset are presented. This makes it difficult to evalute the intent detection and slot filling performance on audio samples, e.g. ASR output, especially when researchers want to have a fair comparisoon under the same train/dev/test split settings. In this repo we provide a mapping from data in the JointSLU repo to the audio samples in ATIS. 

## Mapping Methods
We build the mapping by matching utterances in the JointSLU repo to the normalized human transcripts of audio samples provided in ATIS. In a nutshell, the string matching process has 2 steps:
  - We matched the utternaces in the JointSLU repo to the normalized human transcripts in ATIS dataset. For normalization, we use the normalization script coming with ATIS, and we further processed the normalized transcripts by replacing the number words with digits, e.g. 'nine p m'-->'9 a m'. After removing blankspaces, we run pairwise JointSLU utterance-ATIS transcript string comparison for matching.
  - For the unmatched ones after the first step, we run fuzzy string matching and select the true one from matching candidates.

## Mapping Convention
The mapping convention is as follows: \<utterance\>\<slot label\>\<intent label\>\<path to audio file in ATIS\>, delimited by tab charaters. That is, our data is identical to the JointSLU repo, with the mapped audio samples added. Note, for these two utterances in the JointSLU repo:
  - Utterance 1: `i need information on flights for tuesday leaving baltimore for dallas dallas to boston and boston to baltimore`
  - Utterance 2: `round trip flights from minneapolis to san diego coach economy fare`

Utterance 1 appears twice in the JointSLU repo, but only one matched transcript in ATIS was found. We assigned the same audio sample for these two identical utterances. Utterance 2 cannot be matched to any of the transcripts in ATIS after our every effort. We assigned a '\<UNMATCHED\>' token as the path to audio file in ATIS. 

## Citation
If you used our data, please cite our paper:
```
@online{1904.03576,
Author = {Prashanth Gurunath Shivakumar and Mu Yang and Panayiotis Georgiou},
Title = {Spoken Language Intent Detection using Confusion2Vec},
Year = {2019},
Eprint = {1904.03576},
Eprinttype = {arXiv},
}
```
