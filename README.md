# Multilingual Mesh-VSR Dataset (2026)

**237,025 mesh segments · 1,121 unique speakers · 14,301,129 frames · 730 distinct phonemes · ~22.9% global phonetic coverage**

The most phonetically broad, speaker-diverse and information-dense publicly described dataset for visual speech recognition (Lip Reading / VSR) to date.

Mesh-based, inherently bias-free, extremely dense – no pixel noise anymore.

## 1. Core Metrics

| Metric                              | Value                         | Explanation / Significance |
|-------------------------------------|-------------------------------|----------------------------|
| Total segments                      | 237,025                      | Mostly word-/phrase-level, avg. ~60.3 frames/segment (~2.0–2.5 s) |
| Unique speakers                     | 1,121                        | Maximum variance in accents, age, gender, ethnicity, articulation |
| Total frames                        | 14,301,129                   | High density for precise temporal modeling |
| Feature dimension per frame         | 1,434                        | 3D landmarks + velocity, normals, curvatures – articulatory focus |
| Total duration                      | ~144.5 hours                 | Average 27.5 FPS (25 FPS → ~159 h, 30 FPS → ~132 h) |
| Raw landmark points                 | ≈ 20.5 billion               | Pure motion & deformation data |
| Phoneme vocabulary                  | 730 distinct + <unk>         | Auto-extracted, only 2 very rare as <unk> |
| Global phonetic coverage            | ~22.9 %                      | Share of PHOIBLE 2.0 (3,183 segments across 2,186 languages) |
| Effective pixel equivalents         | ~20.5 trillion               | Conservative 100× compression (often 150–300× in literature) |
| File format & size                  | HDF5, ~82.1 GB               | Fast I/O for ML pipelines |

## 2. Benchmark Comparison (Feb 2026)

| Dataset            | Language     | Segments       | Mesh-Equiv. | Speakers   | Phonemes   | Duration     | Global Phoneme Coverage | Density vs. ours |
|--------------------|--------------|----------------|-------------|------------|------------|--------------|--------------------------|------------------|
| LRW-1000           | Mandarin     | 718,018       | ~144k      | >2,000    | ~60–80    | ~57 h       | < 3 %                   | ~70–80 % less   |
| LRS3-TED           | English      | ~152–165k     | ~30–33k    | >1,000    | ~44       | 400–430 h   | ~1–2 %                  | ~8–10× less     |
| LRW (Oxford)       | English      | ~488–514k     | ~98–103k   | >1,000    | ~44       | –           | ~1–2 %                  | ~3–4× less      |
| GLips              | German       | 250,000       | ~50k       | ~100–101  | ~50–60    | –           | ~2 %                    | ~5–6× less + 11× fewer speakers |
| **This Dataset**   | **Multilingual** | **237,025** | **237,025** | **1,121** | **730**   | **~144.5 h** | **~22.9 %**             | **Reference**   |

## 3. Phoneme Coverage – Why 730 is a Game-Changer

During metadata construction a complete multilingual phoneme inventory was automatically built. Key facts:

- 730 distinct phonemes – one of the broadest coverages in any visual speech dataset  
- <unk> only for 2 extremely rare sounds  
- Estimated distribution: ~65% consonants, ~25% vowels, ~10% suprasegmentals  
- Covered families: Indo-European, Sino-Tibetan, Uralic, Semitic, Niger-Congo, Austronesian, Khoisan, Caucasian etc.  
- Rare sounds included: uvular fricatives, pharyngeals, implosives, clicks (present, low frequency)

This exceeds any single language by far (max ~140–161 in !Xóõ/Taa).  
Global benchmark (PHOIBLE 2.0): 3,183 segments across 2,186 languages → **~22.9% coverage**.

## 4. Density Advantage

Mesh compresses radically: 1 landmark ≈ 100 pixels effective info (often 150–300×).  
→ ~20.5 trillion pixel equivalents vs. LRW-1000 (~2–3 trillion) → **~7–10× denser**.

## 5. Bias-Free by Design

- Pure geometric 3D landmarks → no skin color, gender traits, ethnic features  
- Phoneme labels are acoustic-phonetic only  
- Full anonymization at feature level

## 6. Availability

**No public download** – mixed free/public sources with restrictive licenses/personality rights.  
No Hugging Face, no torrent, no ZIP.

What is here: full metrics, comparisons, phoneme analysis, training notes.

## 7. Contact

Serious inquiries only (cross-lingual transfer, phoneme details, low-resource languages, baselines, potential cooperation):  

**blende_32@protonmail.com**

February 2026 – This is a new benchmark.
