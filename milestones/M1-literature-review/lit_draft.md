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

---

## Directly relevant: Hindi (and English-Hindi) detection

- **IndicSynth** (Sharma et al., ACL 2025) is the strongest Hindi anchor. It has 4,000 hours of synthetic speech from 989 target speakers across 12 low-resource Indian languages. Hindi is one of them, and the paper received an Outstanding Paper Award at ACL 2025. Its motivating claim is that models trained on one language show low accuracy on out-of-domain languages. [aclanthology.org/2025.acl-long.1070]
- **IndicFake + SAFARI-LLM** (TMLR 2025) is the best fit for English plus Hindi. It has 4.2 million samples (7,350 hours) in English and 17 Indian languages.
- **SEA-Spoof** (2025) includes Hindi as one of its six languages. The authors note that Hindi is non-tonal, unlike Thai and Vietnamese, so prosody and phonetics differ across the set.
- **Lightweight MFCC-EffNet** (BMVC 2025 workshop) is the closest match to your English-Hindi setting. It introduces a spoofed-speech dataset in Urdu and Hindi with natural code-switching into English. It reports 0.81% EER on the Hindi set and 5.14% on ASVspoof 2021 LA. Two caveats:
  - The spoofs come from five voice-conversion systems, with bona fide speech from celebrity recordings, so it doesn't cover TTS or cloning.
  - It is a workshop paper with self-reported results.
- **HAV-DF** (Kaur et al.) is a Hindi audio-video dataset. It was built with face-swap, lip-sync and voice cloning, and existing detectors score lower on it than on FF-DF and DFDC. It is mainly useful as background for Hindi deepfakes generally.
- **"Deepfake-audio Detection for Indian Language"** (IJERT) uses an LSTM on Hindi, Marathi, Punjabi and Bengali, with 100 Hindi clips and 400 clips overall. I'd cite it only as an example of small-scale work.

## Code-switching (Hindi-English)

I found no audio deepfake paper focused on Hinglish beyond MFCC-EffNet. The closest conceptual support is **ArEnAV** (ICLR 2026). It is Arabic-English audio-visual, not Hindi. Detectors performed significantly worse on code-switched data than on monolingual datasets, and humans reached only about 60% accuracy. You can cite it as evidence that code-switching is a distinct difficulty, but state clearly that it isn't Hindi.

## Scam-content detection (English/Hinglish)

- **ICFD-31k** (IJCAI 2026) is the *first Indian Conversational Fraud Dataset*. It has 31,000+ conversational transcripts across 10 fraud categories, with streaming labels and rationales, plus RoBERTa-based models for streaming and non-streaming use. It covers English and Hinglish. The transcripts are systematically generated, so they are synthetic rather than recorded calls.
- **RoboKA** (arXiv 2605.00156) builds a robocall corpus seeded on the Fraud Call India corpus. It synthesizes speech and band-passes it to 300–3400 Hz with light noise to simulate telephony. It is useful as a methodological template.
- **"Before the Warning Comes Too Late"** studies incremental phone-scam detection from speech. Its own limitations section says the English benchmark uses scripted dialogues and synthetic speech and doesn't capture spontaneous speech, channel distortion or regional accents. I couldn't open the full PDF, so verify details before citing.
- **Turkish scam-call poster** (arXiv 2606.24523) finds that transcript-based inputs consistently outperform direct audio processing for LLM scam detection. It's relevant to deciding between audio-only and ASR-plus-text pipelines for Hindi.

## Updated gap statement

This is my inference, not a claim from any one paper. Hindi-capable deepfake detectors (IndicSynth, IndicFake, MFCC-EffNet) and Indian scam-content datasets (ICFD-31k) exist, but I found nothing combining them. Specifically, I found no work that:

1. evaluates English-Hindi deepfake detection under telephony codecs and noise, or
2. fuses a spoof-detection score with scam-intent analysis of Hindi/Hinglish call content.

---

Tamil and Telugu coverage is thinner than Hindi, and it changes the picture in useful ways. Three papers cover them, and the evidence points the same direction: detectors trained on English data don't transfer to these languages.

## Core papers

**IndicSynth** (Sharma et al., ACL 2025) is your main source for both languages. Tamil has 32 female and 106 male target speakers and about 280 hours (XTTS-v2) plus 298 hours (FreeVC24) of synthetic speech. Telugu has 41 female and 43 male speakers and about 176 hours plus 179 hours. The authors tested AASIST, AASIST-L and RawNet2, all trained on English ASVspoof 2019 LA, with no fine-tuning. The results:

- **Tamil, XTTS-v2:** EERs of 61.7% (AASIST), 51.2% (AASIST-L) and 51.7% (RawNet2).
- **Tamil, FreeVC24:** 81.7%, 83.1% and 55.0%.
- **Telugu, XTTS-v2:** 54.3%, 52.7% and 46.3%.
- **Telugu, FreeVC24:** 75.7%, 79.0% and 52.8%.

An EER near 50% is chance level, and the AASIST variants fall far below chance on voice conversion (EERs above 75%). The Hindi contrast is worth noting. RawNet2 reached 14.5% EER on Hindi XTTS-v2, so Hindi looks easier than Tamil or Telugu for this model.

The synthetic speech is linguistically convincing. A language-ID model scored about 97.5% on bona fide Tamil and about 94.5–94.8% on synthetic Tamil. For Telugu it scored about 98.6% on bona fide and 95.6–96.1% on synthetic. Two caveats:

- The Hindi and Sanskrit subsets have no "mimicry" component, so Hindi is diversity-only.
- Bona fide speech comes from IndicSUPERB, so it is not telephony audio.

**SEA-Spoof** (2025) covers Tamil but not Telugu. It has 300+ hours of paired real and spoofed speech in Tamil, Hindi, Thai, Indonesian, Malay and Vietnamese. Spoofs come from 10 open-source and 4 commercial TTS/voice-cloning systems. It deliberately includes cross-speaker synthesis with non-native speakers to add accented fakes. Benchmarking shows severe cross-lingual degradation, and fine-tuning on SEA-Spoof largely restores performance. The commercial systems make this a better match for real-world scam voices than open-source-only corpora. [arXiv:2509.19865]

**LRLspoof** (Borodin et al., 2026, arXiv:2603.02364) includes Telugu. It has 2,732 hours generated with 24 open-source TTS systems across 66 languages, and tests 11 public detectors at a threshold calibrated on external benchmarks. Telugu has 22.12 hours from one synthesizer. At that transferred threshold, most detectors rejected under 1% of Telugu spoofs (nes2net 0.00%, sls 0.01%, w2v2_1b 0.02%). The exceptions were aasist3 (73.7%), df_arena_1b (76.4%) and w2v2_300 (100%). Hindi shows the same pattern. The authors conclude that language acts as its own source of domain shift.

I couldn't see a Tamil row in the part of the table I read, so don't claim Tamil coverage without checking. Also note:

- The corpus is spoof-only, with no bona fide speech and no false-reject measurement.
- Telugu has a single synthesizer.
- The threshold is calibrated on mostly English and Chinese benchmarks.

## Datasets I couldn't confirm for Tamil or Telugu

- **IndicFake** (English + 17 Indian languages): my searches didn't return the language list, so check it directly.
- **MLAAD, SpeechFake, MLADDC:** all are multilingual, but I didn't verify whether they include Tamil or Telugu. Reported sizes also differ between sources (for example, SpeechFake is described as 3,000+ hours in its own abstract and 4,855 hours in LRLspoof's comparison table), so cite the original papers.
- **Cross-lingual mismatch papers cited by LRLspoof:** Liu et al., *Towards Quantifying and Reducing Language Mismatch Effects in Cross-Lingual Speech Anti-Spoofing* (SLT 2024), and Moreno et al., *Revealing Cross-Lingual Bias in Synthetic Speech Detection under Controlled Conditions* (SPSC 2025). I've only seen them as references, not read them.

## Scam and telephony for Tamil and Telugu

I found no audio scam-call or telephony-robustness work for either language. The only Dravidian-language resource that surfaced was a fake-news text dataset (DFND, 27,000+ articles in Telugu, Tamil, Kannada and Malayalam), which is about misinformation, not scam calls. The English/Hinglish scam work (ICFD-31k) from my earlier answer doesn't extend to these languages.

## Updated gap statement

Across English, Hindi, Tamil and Telugu:

1. IndicSynth is the only dataset I found covering Hindi, Tamil and Telugu together, and it has no English.
2. English-trained detectors fail on all three Indic languages in the evidence I found. The exception is RawNet2 on Hindi XTTS-v2 (14.5% EER).
3. Nothing I found evaluates any of the four languages under telephony codecs together with scam-intent analysis.

## Practical note for your methods section

A plausible data stack would be IndicSUPERB or Common Voice bona fide speech, with IndicSynth, SEA-Spoof (Tamil) and LRLspoof (Telugu) as spoof sources. Because IndicSynth and LRLspoof use mostly open-source generators, you'd want some commercial-grade voice cloning for realism. Check each dataset's license too. IndicSynth, for example, is CC BY-NC 4.0, which restricts commercial use.
