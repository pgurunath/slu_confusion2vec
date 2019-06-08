# Spoken Language Intent Detection using Confusion2Vec

## Introduction
This repo contains the data used in our paper: [Spoken Language Intent Detection using Confusion2Vec](https://arxiv.org/pdf/1904.03576.pdf). In our paper, we proposed an approach for robust intent detection on noisy ASR transcripts using Confusion2Vec embeddings. The data in this repo contains the normalized reference transcripts, the correspoonding intent and slot labels for the reference transcripts, and the mapped audio samples in ATIS.

## Data Convention
The data convention is as follows: \<reference transcript\>\<slot label\>\<intent label\>\<path to audio file in ATIS\>, delimited by tab charaters. Our data is consistent with the [JointSLU](https://github.com/yvchen/JointSLU) repo, with the mapped audio samples added. Note, for these two utterances:
  - Utterance 1: `i need information on flights for tuesday leaving baltimore for dallas dallas to boston and boston to baltimore`
  - Utterance 2: `round trip flights from minneapolis to san diego coach economy fare`

Utterance 1 appears twice, but only one matched audio transcript in ATIS was found. We assigned the same audio sample for these two identical utterances. Utterance 2 cannot be matched to any of the audio transcripts in ATIS after our every effort. We assigned a '\<UNMATCHED\>' token as the \<path to audio file in ATIS\>. 

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
