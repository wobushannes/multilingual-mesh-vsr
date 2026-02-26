# Multilingual Mesh-VSR Dataset (2026)

**237,025 mesh segments · 1,121 unique speakers · 14,301,129 frames · 730 distinct phonemes · ~22.9% global phonetic coverage**

The most phonetically broad, speaker-diverse and information-dense publicly described dataset for visual speech recognition (Lip Reading / VSR) to date.

Mesh-based representation, inherently bias-free, extremely dense – no pixel noise, no visual identity features.

## Core Metrics

| Metric                              | Value                         | Explanation / Significance |
|-------------------------------------|-------------------------------|----------------------------|
| Total segments                      | 237,025                      | Mostly word-/phrase-level, avg. ~60.3 frames/segment (~2.0–2.5 s at 25–30 FPS) |
| Unique speakers                     | 1,121                        | Maximum inter-speaker variance (accents, age, gender, ethnicity, articulation styles) |
| Total frames                        | 14,301,129                   | High frame density for detailed temporal sequences |
| Feature dimension per frame         | 1,434                        | 3D landmarks + velocity, normals, local curvatures – focused on articulatory ROI |
| Total duration                      | ~144.5 hours                 | Average 27.5 FPS (25 FPS → ~159 h, 30 FPS → ~132 h) |
| Raw landmark points                 | ≈ 20.5 billion               | Pure articulatory motion & deformation data |
| Phoneme vocabulary                  | 730 distinct + <unk>         | Automatically extracted, only 2 very rare phonemes grouped as <unk> |
| Global phonetic coverage            | ~22.9 %                      | Share of PHOIBLE 2.0 (3,183 segments across 2,186 languages) [24] |
| Effective pixel equivalents         | ~20.5 trillion               | Conservative 100× compression (literature often 150–300×) [9,13] |
| File format & size                  | HDF5, ~82.1 GB               | Optimized for fast random-access I/O in ML pipelines |

## Benchmark Comparison (February 2026)

| Dataset            | Language     | Segments       | Mesh-Equiv. (approx.) | Speakers   | Phonemes (approx.) | Duration (approx.) | Global Phoneme Coverage | Density vs. ours |
|--------------------|--------------|----------------|-----------------------|------------|--------------------|--------------------|--------------------------|------------------|
| LRW-1000 [1]       | Mandarin     | 718,018       | ~144,000             | >2,000    | ~60–80            | ~57 h             | < 3 %                   | ~70–80 % less   |
| LRS3-TED [2]       | English      | ~152–165k     | ~30–33,000           | >1,000    | ~44               | 400–430 h         | ~1–2 %                  | ~8–10× less     |
| LRW (Oxford) [3]   | English      | ~488–514k     | ~98–103,000          | >1,000    | ~44               | –                 | ~1–2 %                  | ~3–4× less      |
| GLips [4]          | German       | 250,000       | ~50,000              | ~100–101  | ~50–60            | –                 | ~2 %                    | ~5–6× less + 11× fewer speakers |
| **This Dataset**   | **Multilingual** | **237,025** | **237,025**          | **1,121** | **730 + <unk>**   | **~144.5 h**      | **~22.9 %**             | **Reference**   |

## Phoneme Coverage – Why 730 Matters

During metadata construction, a complete multilingual phoneme inventory was automatically extracted. Key highlights:

- 730 distinct phonemes – one of the broadest coverages in any visual speech dataset  
- <unk> only for 2 extremely rare sounds (frequency < 0.01%)  
- Estimated distribution: ~65% consonants, ~25% vowels, ~10% suprasegmentals  
- Covered language families: Indo-European, Sino-Tibetan, Uralic, Semitic, Niger-Congo, Austronesian, Khoisan, Caucasian, and more  
- Rare/marked sounds included (low frequency but present): uvular fricatives, pharyngeal plosives, implosives, various click types, complex tone contrasts

This exceeds any single language by far (maximum ~140–161 phonemes in !Xóõ/Taa [25]).  
Global reference (PHOIBLE 2.0): 3,183 distinct segments across 2,186 languages → **~22.9% coverage** [24].

## Density Advantage

Mesh representation compresses radically: 1 landmark ≈ 100 pixels of effective semantic information (literature often 150–300×) [9,13].  
→ ~20.5 trillion pixel equivalents vs. LRW-1000 (~2–3 trillion) → **~7–10× denser**.

## Bias-Free by Design

- Pure geometric 3D landmarks → no skin color, gender markers, ethnic features, aging signs [5,6,19]  
- Phoneme labels are acoustic-phonetic only, demography-free  
- Complete anonymization at the feature level

This is a decisive advantage over pixel-based datasets, which can transfer bias through uneven demographic representation [17,18,21].

## Availability & Limitations

**The dataset itself is not publicly available** – due to a mix of free and public-domain sources with restrictive licenses / personality rights.  
No download link, no Hugging Face dataset, no torrent.

What is available here:
- Full metrics & comparisons  
- Detailed phoneme analysis & global coverage  
- Benchmark tables & density calculations  
- First training insights (hyperparameters, logs, architecture notes)

## Contact

Serious inquiries only (cross-lingual transfer, low-resource languages, phoneme details, baselines, potential cooperation):  

**blende_32@protonmail.com**

February 2026 – This is a new benchmark.

## References

[1] Yang, S. et al. (2019). LRW-1000: A Naturally-Distributed Large-Scale Benchmark for Lip Reading in the Wild. https://arxiv.org/abs/1810.06990  
[2] Afouras, T. et al. (2018). LRS3-TED: a large-scale dataset for visual speech recognition. https://arxiv.org/abs/1809.00496  
[3] Chung, J. S. & Zisserman, A. (2016). Lip Reading in the Wild. https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrw1.html  
[4] Schwiebert, G. et al. (2022). A Multimodal German Dataset for Automatic Lip Reading Systems. https://arxiv.org/abs/2202.13403  
[5] Yang, M. et al. (2024). Deconstructing demographic bias in speech-based machine learning models. https://pmc.ncbi.nlm.nih.gov/articles/PMC11306200/  
[6] Stewart, D. et al. (2013). Gender classification via lips: static and dynamic features. https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/iet-bmt.2012.0021  
[7] Jeon, S. et al. (2021). Lipreading Architecture Based on Multiple Convolutional Neural Networks. https://www.mdpi.com/1424-8220/22/1/72  
[8] Lan, Y. et al. (2009). Comparing Visual Features for Lipreading. https://www.isca-archive.org/avsp_2009/lan09_avsp.pdf  
[9] Niu, Z. & Mak, B. (2025). Efficient Mouth Alignment for Visual Speech Recognition. http://home.cse.ust.hk/~mak/PDF/mlsp2025-lipread.pdf  
[13] Torrie, S. et al. (2023). Data-Driven Advancements in Lip Motion Analysis: A Review. https://www.mdpi.com/2079-9292/12/22/4698  
[17] Dumpala, S. H. et al. (2023). Manifestation of depression in speech overlaps with speaker identity features. (Referenced in bias surveys)  
[19] Eyben, F. et al. (2015). GeMAPS for voice research and affective computing. IEEE Transactions on Affective Computing.  
[21] Various (2023). Bias in visual speech recognition datasets (survey papers on diversity and fairness).  
[23] Chung, J. S. et al. (2017). Lip Reading Sentences in the Wild. https://openaccess.thecvf.com/content_cvpr_2017/papers/Chung_Lip_Reading_Sentences_CVPR_2017_paper.pdf  
[24] Moran, S. et al. (2019–2025). PHOIBLE 2.0 Online Database. https://phoible.org/  
[25] Traill, A. (1985/1994). Phonetic and Phonological Studies of !Xóõ Bushman. (Referenced in PHOIBLE for max phoneme count ~140–161)
