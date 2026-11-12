# Hi, I'm Sajil 👋

### Applied ML Engineer · Generative AI · Computer Vision · Speech

I take machine learning from notebook to a working product: **local LLM apps, real-time vision models and speech synthesis pipelines** that run on hardware people actually have.
PhD in Computational Biology · ML Engineer & Educator at ICT Academy of Kerala · writer at [intuitivetutorial.com](https://intuitivetutorial.com)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-sajilck-0A66C2?logo=linkedin&logoColor=white)](https://linkedin.com/in/sajilck)
[![Hugging Face](https://img.shields.io/badge/🤗_Hugging_Face-sajilck-FFD21E)](https://huggingface.co/sajilck)
[![Kaggle](https://img.shields.io/badge/Kaggle-sajilck-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/sajilck)
[![Blog](https://img.shields.io/badge/Blog-intuitivetutorial.com-2E7D32)](https://intuitivetutorial.com)
[![Email](https://img.shields.io/badge/Email-sajilck@gmail.com-D14836?logo=gmail&logoColor=white)](mailto:sajilck@gmail.com)

---

## 🚀 Featured projects

### 🎓 [AI Assignment Grader](https://github.com/cksajil/ai-assignment-grader) · LLM app · [Live demo](https://huggingface.co/spaces/sajilck/ai-assignment-grader) · [Video](https://youtu.be/mn-7UMb5nkE)
Grades student Jupyter notebooks against a rubric with a **fully local LLM** (Qwen2.5-Coder 7B via Ollama), so no student data leaves the machine.
- Structured JSON output with typed per-criterion scores, strengths and "rubric rule → mistake → why → fix" feedback
- Guardrails in Python: per-criterion clamping and a hard score cap the model can't inflate; deterministic at `temperature=0`
- Optional sandboxed execution of the student notebook, fed back to the LLM as evidence
- Dockerised and deployed to Hugging Face Spaces, with a GitHub Actions workflow that redeploys on every push

`Ollama` `Qwen2.5` `Gradio` `PyMuPDF` `Docker` `GitHub Actions` `HF Spaces`

### 🚗 [Dash-Cam Segmenter](https://github.com/cksajil/dash-cam-segmenter) · Computer vision · [Dataset](https://www.kaggle.com/datasets/sajilck/road-segmentation-indian)
Semantic segmentation of Indian road scenes from dash-cam video (20 classes), from a local file or a YouTube URL straight to a segmented preview.
- DeepLabV3+ (ResNet-50 backbone, ASPP) and U-Net implemented in TensorFlow/Keras; **mean IoU 0.659** on the test set
- Built and published my own Kaggle dataset of Indian roads; trained weights versioned on Zenodo and pulled at runtime
- Config-driven CLI pipeline: video ingest → frame inference → rendered GIF / video

`TensorFlow` `Keras` `DeepLabV3+` `U-Net` `OpenCV`

<img src="https://github.com/cksajil/dash-cam-segmenter/blob/main/images/segmented_movie.gif?raw=true" width="480" alt="Dash-cam segmentation output">

### 🗣️ [IndicF5 TTS Pipeline](https://github.com/cksajil/IndicF5-TTS-Pipeline) · Speech / GenAI
Zero-shot voice cloning in 11 Indian languages (Malayalam, Hindi, Tamil and more) on top of [ai4bharat/IndicF5](https://huggingface.co/ai4bharat/IndicF5), packaged as a CLI and a Python API.
- **Performance work on CPU-only machines:** a tuned EPSS diffusion-step schedule, cached reference-audio preprocessing, thread pinning to physical cores and optional bf16 autocast
- Real-time factor reported per utterance; in early tests these changes took RTF from ~83× to single digits on modern multi-core CPUs

`PyTorch` `Transformers` `F5-TTS` `Diffusion` `Speech synthesis`

---

## 🧰 Toolkit

| Area | Tools |
|---|---|
| **LLMs & GenAI** | Ollama, Hugging Face Transformers, prompt design for structured JSON output, RAG, LangChain |
| **Deep learning** | PyTorch, TensorFlow / Keras, scikit-learn |
| **Vision & audio** | OpenCV, segmentation models, diffusion-based TTS, audio signal processing |
| **Deployment** | Docker, Gradio, Hugging Face Spaces, GitHub Actions, Linux |
| **Languages** | Python, SQL, Bash |

---

## 📚 Research

- **Edge Analytics Enabled Acoustic Rain Gauge**, IEEE RAICS 2024: an IoT and audio-ML system for estimating rainfall
- **Active Noise Control**, International Journal of Biomedical and Clinical Engineering

---

## 🔭 Right now

- Building **LLM applications that run locally** and hold up in production: evaluation, guardrails, structured output
- Getting heavy models (diffusion, transformers) to run well on **CPUs and edge hardware**
- Open to **Applied ML / GenAI engineering roles** and to collaborating on open-source AI tools

📫 The fastest way to reach me is [LinkedIn](https://linkedin.com/in/sajilck) or [email](mailto:sajilck@gmail.com).
