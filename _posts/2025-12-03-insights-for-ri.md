---
layout: post
title: A Case Study on the 日 [ɻʅ51] Category
date: 2025-12-03
description: A Case Study on the 日 [ɻʅ51] Category based on Luo and Sun (2025)
tags:
  - compling
categories:
  - research
---

Reconstruction in historical linguistics often relies on expert knowledge and qualitative reasoning. [Luo and Sun (2025)](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00742/128937/Phonetic-Reconstruction-of-the-Consonant-System-of) formalized the reconstruction as a mixed integer optimization problem, with the objective designed as maximizing coherence to historical evidence (e.g., ancient rhyme dictionaries), and consistency with descendants (modern Chinese dialects). Experiments on synthetic data validated the effectiveness of our method.

Our approach provides a novel way to find evidence to understand the past phonological status and therefore the ways that they can change. The new evidence resulted from our algorithm may be of linguistic interest. Here, we show a case study on the **日** [ɻʅ51] category[^1] to demonstrate some promising points.

The reconstruction of the **日** category has been a challenge in Chinese historical phonology, mainly because its pronunciation in different dialects vary a lot (see the **IPA** row in Table 1). Moreover, even a single character in one dialect may have various pronunciations (Karlgren, 1926).

In modern dialects, there are two main categories of its pronunciation: one is voiced fricatives, like [v, z], including approximant [ɻ] and zero initial, and the other is nasals, like [n, ȵ, ŋ], including lateral approximant [l] (Chen, 2004).

Karlgren (1926) reconstructs **日** as [ȵʑ]. He states that [ȵʑ] underwent 3 types of changes, then evolved into various pronunciations in modern dialects:

1.  [ȵ] was lost, and [ʑ] became the primary part, which explains [ʑ] and [z].
2.  [ȵʑ] $\to$ [ȵȡʑ] $\to$ [ȡʑ]. Then, the place of articulation of [ȡʑ] was moved to anterior[^2] and became [dz].
3.  [ʑ] was lost, and [ȵ] became the primary part. [ȵ] could change into [ŋ] ([-coronal]) or [n] ([-dorsal]). Some dialects use [l] to replace [n]. Besides, in some cases [ȵ] was also lost, leading to zero initial [∅].

After Karlgren (1926), many philologists take a similar strategy—combining the nasal and voiced fricative phonemes together. Li (1971) also reconstructs initial **日** as [ȵʑ], Wang (1957) and Shao (1982) reconstruct it as [nʑ], while Li (1956) and Pulleyblank (1984) adopt [ȵ]. These researchers utilise a much larger range of materials. Karlgren (1926) uses 33 dialects as well as Sino-Xenic pronunciations, while Li (1956) and Shao (1982) consider Sanskrit-Chinese pronunciations.

Despite a smaller range of materials, our model derives a reasonable result. [ȵ], [ʑ], and [n], though seem totally different, actually have the place features [+ coronal, + anterior] in common. Our model successfully captures the two features and reconstructs **日** as [z] (similar to [ʑ]), showing that at least in the dialects we used, voiced fricatives like [z] should be treated with more attention than nasals like [n, ȵ, ŋ]. With an entirely different approach, our fully automatic model derives the reconstruction partially consistent with the result by the best philologists.

The result may be also consultable to find diachronic change patterns. We show the final numerical solution in **Table 1**. It exhibits possible sound changes from MC (Middle Chinese) to different dialects in terms of distinctive features.

### Table 1: Phonetic values of initial "日" and their changes from MC to dialects

| Feature | <span style="color: red">**MC**</span> | BJ | XA | WH | CD | YZ | SZ | CS | NC | MX | GZ | XM | CZ |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **IPA** | <span style="color: red">**[z]**</span> | [∅ ʐ] | [∅ ʐ v] | [∅ n] | [∅ z] | [∅ l] | [z ∅ j ȵ] | [∅ z ȵ] | [∅ l ȵ] | [∅ l ȵ] | [j ŋ] | [n h g l] | [z h n l] |
| **continuant** | <span style="color: red">0.82</span> | 0.90 | 0.87 | <span style="color: #0070C0">**-0.50**</span> | 0.88 | 0.80 | <span style="color: #0070C0">**0.29**</span> | <span style="color: #0070C0">**0.31**</span> | <span style="color: #0070C0">**0.32**</span> | <span style="color: #0070C0">**-0.35**</span> | 0.90 | 0.59 | 0.64 |
| **delayed_re** | <span style="color: red">0.68</span> | 0.90 | 0.87 | <span style="color: #0070C0">**0.00**</span> | 0.88 | <span style="color: #0070C0">**0.00**</span> | 0.58 | 0.38 | <span style="color: #0070C0">**0.00**</span> | <span style="color: #0070C0">**0.00**</span> | <span style="color: #0070C0">**0.00**</span> | <span style="color: #0070C0">**0.02**</span> | 0.76 |
| **sonority** | <span style="color: red">1.13</span> | 0.90 | 0.87 | 1.00 | 0.88 | <span style="color: #0070C0">**2.40**</span> | 1.27 | <span style="color: #0070C0">**0.51**</span> | <span style="color: #0070C0">**2.13**</span> | 1.24 | <span style="color: #0070C0">**3.90**</span> | <span style="color: #0070C0">**2.65**</span> | 1.29 |
| **voice** | <span style="color: red">0.92</span> | 0.90 | 0.87 | 0.50 | 0.88 | 0.80 | 0.91 | 0.44 | 0.79 | 0.57 | 1.00 | 0.89 | 0.96 |
| **spread_gl** | <span style="color: red">-0.92</span> | -0.90 | -0.87 | -0.50 | -0.88 | -0.80 | -0.91 | -0.44 | -0.79 | -0.57 | -1.00 | -0.89 | -0.96 |
| **labial** | <span style="color: red">-0.92</span> | -0.90 | <span style="color: #0070C0">**-0.07**</span> | -0.50 | -0.88 | -0.80 | -0.91 | -0.44 | -0.79 | -0.57 | -1.00 | -1.00 | -1.00 |
| **labiodental** | <span style="color: red">0.00</span> | 0.00 | 0.40 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| **coronal** | <span style="color: red">0.92</span> | 0.90 | <span style="color: #0070C0">**0.07**</span> | 0.50 | 0.88 | 0.80 | 0.87 | 0.44 | 0.79 | 0.57 | <span style="color: #0070C0">**-1.00**</span> | 0.81 | 0.96 |
| **anterior** | <span style="color: red">0.92</span> | <span style="color: #0070C0">**-0.90**</span> | <span style="color: #0070C0">**-0.47**</span> | 0.50 | 0.88 | 0.80 | 0.89 | 0.44 | 0.79 | 0.57 | <span style="color: #0070C0">**0.00**</span> | 0.91 | 0.98 |
| **distributed** | <span style="color: red">-0.92</span> | -0.90 | -0.47 | -0.50 | -0.88 | -0.80 | <span style="color: #0070C0">**-0.27**</span> | <span style="color: #0070C0">**-0.31**</span> | <span style="color: #0070C0">**-0.32**</span> | <span style="color: #0070C0">**0.35**</span> | <span style="color: #0070C0">**0.00**</span> | -0.91 | -0.98 |
| **lateral** | <span style="color: red">-0.79</span> | -0.90 | -0.87 | -0.50 | -0.88 | <span style="color: #0070C0">**0.80**</span> | -0.91 | -0.44 | <span style="color: #0070C0">**0.32**</span> | -0.35 | -1.00 | <span style="color: #0070C0">**0.48**</span> | -0.89 |
| **dorsal** | <span style="color: red">-0.92</span> | -0.90 | -0.87 | -0.50 | -0.88 | -0.80 | <span style="color: #0070C0">**-0.25**</span> | <span style="color: #0070C0">**-0.31**</span> | <span style="color: #0070C0">**-0.32**</span> | <span style="color: #0070C0">**0.35**</span> | <span style="color: #0070C0">**1.00**</span> | -0.93 | -1.00 |
| **high** | <span style="color: red">0.00</span> | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | <span style="color: #0070C0">**0.98**</span> | 0.20 | <span style="color: #0070C0">**0.70**</span> | <span style="color: #0070C0">**1.38**</span> | <span style="color: #0070C0">**3.00**</span> | 0.11 | 0.00 |
| **front** | <span style="color: red">0.00</span> | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | <span style="color: #0070C0">**0.98**</span> | 0.20 | <span style="color: #0070C0">**0.70**</span> | <span style="color: #0070C0">**1.38**</span> | <span style="color: #0070C0">**2.95**</span> | 0.07 | 0.00 |

> **Note:** We demonstrate the comparison between MC and 12 dialects: Beijing, Xi'an, Wuhan, Chengdu, Yangzhou (Mandarin), Suzhou (Wu), Changsha (Xiang), Nanchang (Gan), Meixian (Hakka), Guangzhou (Yue), Xiamen, Chaozhou (Min). Each column provides information of the initial "日" in a language/dialect denoted by its first row.
>
> In the **MC** column, the 14 numbers represent the average vector of the reconstructed phonetic value of all the characters with initial "日" in MC. The **IPA** grid is the IPA phoneme of which the phonetic vector is most similar with the average vector. In other columns (BJ–CZ), the **IPA** grid contains all the initials in the current dialect with initial "日" in MC, and the following 14 numbers is the average phonetic vector of initials in this dialect. For MC to any dialect, the features changed with an absolute value $\ge 0.5$ are marked in <span style="color: #0070C0">**blue**</span> .

---

### References

* Chen, N. (2004). *Studies on Ri Initial in Jingdian Shiwen [Explanative writings to the classical canons] 《經典釋文》日母字研究* [Master's thesis]. Peking University.
* Karlgren, B. (1926). *Zhongguo Yinyunxue Yanjiu [Study on Chinese phonology]*. Shangwu Yinshuguan. (Co-translated by Yuen Ren Chao, Fang Kui Li, and Changpei Luo).
* Li, F.-K. (1971). Shangguyin Yanjiu [Studies on Old Chinese Pronunciation] 上古音研究. *The Tsing Hua Journal of Chinese Studies*, 9, 1-61.
* Li, R. (1956). *Qieyun Yinxi [Phonological system of Qieyun] 切韻音系*. Beijing: Kexue Chubanshe.
* Pulleyblank, E. G. (1984). *Middle Chinese: A Study in Historical Phonology*. Vancouver: University of British Columbia Press.
* Shao, R. (1982). *Qieyun Yanjiu [Studies on Qieyun] 切韻研究*. Beijing: Chinese Academy of Social Sciences.
* Wang, L. (1957). *Hanyu Shigao [A Draft History of the Chinese Language] 漢語史稿*. Beijing: Zhonghua Shuju.

[^1]: The tradition of historical Chinese phonology is to use characters as labels representing initial categories.

[^2]: Represented by our features, both [ȡʑ] and [dz] have [+anterior], and the change from [ȡ] to [d] and [ʑ] to [d] is [-dorsal].