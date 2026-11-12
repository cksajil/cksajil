# Hi, I'm Sajil 👋

### Applied ML Engineer · Speech AI for Malayalam · LLM systems that run on a CPU

I build ML systems end to end and measure them honestly: a Malayalam voice assistant (speech in, speech out), the ASR benchmark behind it, local LLM apps, and vision and IoT models running on edge hardware.
PhD in Computational Biology · ML Engineer & Educator at ICT Academy of Kerala · writing at [intuitivetutorial.com](https://intuitivetutorial.com)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-sajilck-0A66C2?logo=linkedin&logoColor=white)](https://linkedin.com/in/sajilck)
[![Hugging Face](https://img.shields.io/badge/🤗_Hugging_Face-sajilck-FFD21E)](https://huggingface.co/sajilck)
[![Kaggle](https://img.shields.io/badge/Kaggle-sajilck-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/sajilck)
[![Blog](https://img.shields.io/badge/Blog-intuitivetutorial.com-2E7D32)](https://intuitivetutorial.com)
[![Email](https://img.shields.io/badge/Email-sajilck@gmail.com-D14836?logo=gmail&logoColor=white)](mailto:sajilck@gmail.com)

---

## 🗣️ Malayalam speech AI, end to end

Most Malayalam speakers will never have a GPU, so everything here is built and measured on **2 CPU cores**.

```
🎙️ speech ─► ASR (my Whisper fine-tune / IndicConformer) ─► LangGraph agent + hybrid RAG ─► TTS ─► 🔊 speech
```

### [Kerala Voice Helpdesk](https://github.com/cksajil/kerala-voice-helpdesk) · LLM agent + RAG
A voice assistant that answers Malayalam questions about panchayat services (K-SMART), the weather and the news.
- **LangGraph** agent with explicit routing, **BM25 + BGE-M3 hybrid retrieval**, and Gemma running locally through llama.cpp
- **Reliability by design:** fees are calculated in code, not by the LLM; the model must answer `UNSURE` when the retrieved passage doesn't contain the answer, and that becomes a refusal; weather and news numbers go out through templates
- **Ingestion pipeline:** downloads panchayat citizen charters, runs Malayalam OCR with Tesseract and turns them into ~600 passages with page citations, plus a checker that verifies knowledge-base entries against the source pages
- **Error-driven:** routing, retrieval and ASR-correction fixes come from reading real conversation logs, and are tested by an eval suite (routing, hit@3, refusals, 100-question answer eval, multi-turn conversations); a whole spoken turn takes 1.7–6.2 s on a shared CPU

### [malayalam-asr-eval](https://github.com/cksajil/malayalam-asr-eval) · Benchmark
A reproducible, leakage-free benchmark of 6 Malayalam ASR models on accuracy **and** 2-core CPU speed.
- WER/CER with bootstrap 95% CIs, a column that excludes each model's own training corpora, RTF and peak RAM; one `transcribe()` interface over Whisper, CTranslate2, IndicConformer and wav2vec2; CI-tested adapters
- **Findings:** IndicConformer matches my Whisper fine-tune's accuracy at **~14× the speed**; one model's 39.7% WER becomes 52.9% on corpora it didn't train on; a CTranslate2 run silently truncated transcripts at 224 tokens
- Choosing per clip between two recognisers with a character LM: **31.2% → 26.4% WER** (significant, no retraining). I deployed it, then reverted it after measuring that it slowed the voice assistant

**Also in the stack:** my fine-tuned [whisper-small-malayalam-v2](https://huggingface.co/sajilck/whisper-small-malayalam-v2) and its training [corpus](https://huggingface.co/datasets/sajilck/malayalam-asr-corpus), and [IndicF5-TTS-Pipeline](https://github.com/cksajil/IndicF5-TTS-Pipeline): zero-shot voice cloning in 11 Indian languages, sped up on CPU (EPSS step schedules, cached preprocessing, core pinning, bf16) from a real-time factor of ~83× down to single digits.
**Write-ups:** [leakage in my test set](https://intuitivetutorial.com/2026/10/09/i-re-tested-my-malayalam-asr-model-on-clean-data-part-2/) · [a bug in my own evaluation](https://intuitivetutorial.com/2026/10/11/part-3-retraining-my-malayalam-asr-model-and-a-bug-in-my-own-evaluation/)

`PyTorch` `Transformers` `Whisper` `CTranslate2` `IndicConformer` `ONNX Runtime` `LangGraph` `llama.cpp` `BM25` `BGE-M3` `Tesseract`

---

## 🤖 LLM apps and models from scratch

| Project | What it shows |
|---|---|
| 🎓 [**AI Assignment Grader**](https://github.com/cksajil/ai-assignment-grader) · [demo](https://huggingface.co/spaces/sajilck/ai-assignment-grader) | Grades Jupyter notebooks against a rubric with a **local LLM** (Qwen2.5-Coder via Ollama): typed JSON output, score guardrails in Python, optional sandboxed code execution; Docker + GitHub Actions deploy to HF Spaces |
| 🔍 [**OmniSense**](https://github.com/cksajil/omnisense) · [demo](https://huggingface.co/spaces/sajilck/omnisense) | Semantic search inside videos: faster-whisper transcription → MiniLM embeddings → FAISS; click a hit and the player jumps to that moment |
| 💬 [**ICTSahayi**](https://github.com/cksajil/ICTSahayi) | GPT-2 implemented in plain PyTorch and instruction fine-tuned on an FAQ, evaluated against the base model and a retrieval baseline. An honest result: fine-tuning learned the format, not the facts, which makes the case for RAG |
| ✍️ [**MiniGPT-JAX**](https://github.com/cksajil/mini-gpt-jax-stories) · [demo](https://huggingface.co/spaces/sajilck/mini_story_generator) | Decoder-only transformer built from scratch in **JAX / Flax NNX** and trained on 200k stories on a free GPU, with pre-tokenised, memory-mapped batches to remove the input bottleneck |

## 👁️ Vision, audio and edge ML

| Project | What it shows |
|---|---|
| 🚗 [**Dash-Cam Segmenter**](https://github.com/cksajil/dash-cam-segmenter) | DeepLabV3+ and U-Net for Indian road scenes (20 classes, mean IoU 0.659) on my own [Kaggle dataset](https://www.kaggle.com/datasets/sajilck/road-segmentation-indian); video or YouTube URL in, segmented video out |
| 🌧️ [**Acoustic Rain Gauge**](https://github.com/cksajil/rainfall_monitor) | Estimates rainfall from sound (ICFOSS R&D team): Raspberry Pi data acquisition, LSTM on STFT features (R² 0.97), LoRaWAN uplink ([LoraWANPi](https://github.com/cksajil/LoraWANPi)) and a live Grafana dashboard. Published at IEEE RAICS 2024 |
| ✋ [**Hand Gesture Recognition**](https://github.com/cksajil/hand_gesture_recognition) | Real-time 3D-CNN gesture control (Jester, 8 gestures) of an information display: webcam → PyTorch → Flask-SocketIO, with Raspberry Pi GPIO actions |

<img src="https://github.com/cksajil/dash-cam-segmenter/blob/main/images/segmented_movie.gif?raw=true" width="420" alt="Dash-cam segmentation output">

## 🎓 Teaching ML

- [**ML & AI Knowledge Graph**](https://cksajil.github.io/ml-knowledge-graph/): an interactive D3 map of ML concepts, prerequisites and resources ([repo](https://github.com/cksajil/ml-knowledge-graph))
- [**ML Visual Lab**](https://github.com/cksajil/ml-visual-lab): interactive visual explainers for entropy, eigenvectors and PCA

---

## 🧰 Toolkit

| Area | Tools |
|---|---|
| **LLMs & agents** | LangGraph, Ollama, llama.cpp, Hugging Face Transformers, RAG (BM25, dense, hybrid), FAISS, structured JSON output |
| **Speech** | Whisper fine-tuning, CTranslate2 / faster-whisper, IndicConformer, wav2vec2, F5-TTS, WER/CER evaluation |
| **Deep learning** | PyTorch, JAX / Flax, TensorFlow / Keras, scikit-learn |
| **Vision & edge** | OpenCV, segmentation, 3D CNNs, Raspberry Pi, LoRaWAN |
| **Shipping** | Docker, Gradio, Flask, Hugging Face Spaces, GitHub Actions, pytest, Linux |

## 📚 Research

- **Edge Analytics Enabled Acoustic Rain Gauge**, IEEE RAICS 2024
- **Active Noise Control**, International Journal of Biomedical and Clinical Engineering

## 🔭 Right now

- Making the Malayalam voice assistant faster and more accurate on a shared CPU
- Measuring, not guessing: leakage-free test sets, confidence intervals, error analysis from real logs
- Open to **Applied ML / Speech AI / GenAI engineering roles** and to collaborations on Indic-language AI
