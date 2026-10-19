I'll search for relevant papers across several angles: multilingual detection, benchmarks and datasets, cross-lingual generalization, and scam/vishing detection.I searched across multilingual datasets, methods, surveys and telephony/scam work. Below are the papers I'd shortlist, grouped by the role they'd play in your review.

## 1. Multilingual datasets and benchmarks (core)

- **MLAAD** (Müller et al., IJCNN 2024) is the most widely used multilingual anti-spoofing dataset. Version 9 has 678.3 hours of synthetic speech in 51 languages from 140 TTS models, and a later version (v11) has 205 TTS models and 1,153.6 hours in 54 languages. [arXiv:2401.09512]
- **SpeechFake** (ACL 2025) is a much larger corpus. It has over 3 million deepfake samples (3,000+ hours) from 40 synthesis tools, with a multilingual part covering 46 languages. [ACL 2025 long.493 / arXiv:2507.21463]
- **XMAD-Bench** is built for cross-domain testing. It has 668.8 hours across Arabic, English, German, Mandarin, Romanian, Russian and Spanish. [arXiv:2506.00462]
- **IndicFake + SAFARI-LLM** (TMLR 2025) is useful if you want Indic coverage. The dataset has 4.2 million samples (7,350 hours) in English and 17 Indian languages. The SAFARI-LLM model fuses Whisper semantic embeddings with m-HuBERT acoustic features.
- **SEA-Spoof** (2025) covers South-East Asian languages. It spans Tamil, Hindi, Thai, Indonesian, Malay and Vietnamese. Benchmarking shows severe cross-lingual degradation, and fine-tuning on the dataset restores performance. [arXiv:2509.19865]
- **ML-ITW** (2026) is a multilingual in-the-wild benchmark. It covers 14 languages, seven platforms and 180 public figures, and tests end-to-end models, SSL methods and audio LLMs, finding significant degradation across languages and real-world conditions. [arXiv:2603.05852]
- **Deepfake-Eval-2024** is multimodal, but its audio part is multilingual. It includes 56.5 hours of audio and content in 52 languages. Open-source detectors lost about 48% AUC on audio compared with earlier benchmarks. [arXiv:2503.02857]

## 2. Multilingual and cross-lingual detection methods

- **"Are audio DeepFake detection models polyglots?"** (Interspeech) starts from the point that most detectors are trained on English-centric data. It benchmarks adaptation strategies for non-English languages. This is probably the closest match to your topic. [arXiv:2412.17924]
- **Wav2vec 2.0 XLS-R + AASIST with data augmentation** is the standard strong baseline. It reports up to a 90% relative EER reduction on ASVspoof 2021 logical access and 88% on deepfake detection. [arXiv:2202.12233]
- **Generalisable and calibrated detection with SSL representations** uses frozen wav2vec 2.0 features with logistic regression. It cut EER from 30.9% to 8.8% across eight datasets compared with RawNet2. The benchmark includes multilingual data. [arXiv:2309.05384]
- **Post-training for Deepfake Speech Detection** (AntiDeepfake) post-trains SSL models on 56,000+ hours of genuine speech and 18,000 hours of artifacted speech in over a hundred languages. [arXiv:2506.21090]
- **A Data-Centric Approach to Generalizable Speech Deepfake Detection** uses an XLS-R backbone and studies scaling and data mixing. [arXiv:2512.18210]
- **Hybrid RawNet + AASIST with multilingual SSL features** comes from the SAFE Challenge. It reports about 73% balanced accuracy on multilingual data and unseen synthesis algorithms. This is a workshop paper, so treat it as lower-weight evidence.

## 3. Surveys (for background sections)

- Yi et al., **Audio Deepfake Detection: A Survey**. It compares features and classifiers on ASVspoof 2021, ADD 2023 and In-the-Wild. [arXiv:2308.14970]
- Zhang et al., **Audio Deepfake Detection: What Has Been Achieved and What Lies Ahead** (*Sensors*, 2025). It also covers privacy and fairness.
- **A Survey on Speech Deepfake Detection** reviews model architecture, training techniques, application scenarios and datasets. [arXiv:2404.13914]

## 4. Telephony, vishing and scam context

This is the thinnest area. These are the best sources I found:

- Maltby et al., **Robustness in deepfake speech detection** (*Computer Speech & Language*, 2026). It links robustness failures to codec-induced masking of synthesis artefacts and to dataset-dependent synthesis pipelines.
- **A Survey of Threats Against Voice Authentication and Anti-Spoofing Systems** argues that detectors are trained on clean data but deployed under telephony bandwidth limits, and that GSM and Opus discard high-frequency vocoder artifacts above 8 kHz. [arXiv:2508.16843]
- **Hardening Enterprise Voice Channels with Robust Deepfake-Audio Detection** (a thesis, so lower weight) found that augmentation reduces false positives for genuine callers in degraded channels.
- **Ericsson Technology Review (Aug 2026)** is industry rather than peer-reviewed. It argues that IMS is a natural anchor point for network-level deepfake voice detection.
- An NSF-hosted paper reviews vishing attacks with an emphasis on deepfake and AI voice synthesis. I only saw an excerpt, so check it before citing.

## Gaps you could build on

My inference from these results, not a claim any single paper makes:

1. Multilingual benchmarks mostly use clean TTS or social-media audio, while telephony codec robustness is studied mostly in English or in isolation.
2. I found no peer-reviewed work that combines multilingual detection, telephony conditions and scam-intent (semantic) analysis in one system.
3. Cross-lingual drop-offs are documented repeatedly (SEA-Spoof, ML-ITW, Polyglots), but there is little language-aware modeling.

## Caveats

- I read abstracts and excerpts, not full papers. Verify the details, such as venues, authors and exact numbers, against the originals before citing.
- Vendor blogs (Pindrop, Resemble, etc.) turned up in my scam-detection searches. I left them out as sources since they aren't peer-reviewed.
- To fill out the scam section, search Google Scholar or IEEE Xplore for "scam call detection", "vishing detection speech" and "ASVspoof 2021 telephony", and check which papers cite the robustness survey above.

If you tell me your target language set and citation style, I can draft a comparison table of these datasets or an outline for the review.
