<div align="center">

# Anubhav Agrawal

**Making ML models run fast on real hardware.**

ONNX · TensorRT · INT8/FP16 quantization · llama.cpp/MLX on-device inference

[Website](https://anubhavagr.github.io) · [LinkedIn](https://www.linkedin.com/in/anubhav-agr/) · [Email](mailto:anubhavagr.mail@gmail.com)· [X](https://x.com/experiencetwts)

</div>

---

I work on the part of ML that happens *after* training: exporting PyTorch through ONNX into
TensorRT, quantizing to INT8/FP16 without quietly losing accuracy, profiling where the
milliseconds actually go, and serving LLMs on-device instead of someone else's cloud.

Currently **AI Engineer II at Griphic** — sole engineer on a production multi-agent LLM
service. Token-level cost telemetry cut generation cost 60%; guardrails stop prompt injection
for at most 2 extra LLM calls on clean traffic; 99.5% of output ships with zero human review.

Before that, 3 years of healthcare ML at Innvolution: an X-ray super-resolution product
taken to **$200K+ ARR** and through clinical trials — sub-5 ms per frame for 4× upsampling on
an RTX 4090 after INT8/FP16 post-training quantization — with a granted Indian patent (No. 604176, AI-Powered X-ray Image
Enhancement) plus two applications pending, and a 6-engineer ML team along the way.

M.Tech AI/ML @ BITS Pilani, 2027.

## 🔬 What's on this profile

### [ipic](https://github.com/anubhavagr/ipic) — fully offline multimodal search
Search text, PDFs, images, audio, and video with **no cloud and no telemetry**. CLIP and BGE
embeddings run entirely on-device; dense, BM25, and acoustic lanes are fused by reciprocal
rank fusion over mmap'd i8-quantized vector stores. Exact scan beats HNSW at file-index
scale: **26–32 ms queries, ~2,500 files/s indexing on a 350k-file drive.**
→ [Architecture write-up](https://anubhavagr.github.io/posts/ipic-architecture.html)

### [inference-lab](https://github.com/anubhavagr/inference-lab) — LLM serving benchmarks, done fairly
A reproducible harness holding mlx-lm and llama.cpp to one fairness contract — fixed prompts,
greedy decoding, matched budgets — on Apple Silicon. Findings worth stealing: decode is
**memory-bandwidth-bound** (~273 GB/s on an M4 Pro); K isolated server instances return
**+9% for 3× the memory**; throughput stays flat from 1 to 32 users because a per-instance
lock serializes each engine.
→ [Full write-up](https://anubhavagr.github.io/posts/inference-lab.html)

### Contributing upstream
- **[onnxruntime #33091](https://github.com/microsoft/onnxruntime/pull/33091)** — merged:
  fixed a ReshapeFusion crash in the graph optimizer when the fused Reshape's shape input
  is node-produced.
- **[pytorch #200180](https://github.com/pytorch/pytorch/pull/200180)** — open: make the
  ONNX exporter emit int32 quantization as valid ops instead of invalid QuantizeLinear.
- **[mlx-lm #1944](https://github.com/ml-explore/mlx-lm/pull/1944)** — open: enforce the
  prompt-cache byte budget continuously and make the /health endpoint stall-aware.

### [anubhavagr.github.io](https://anubhavagr.github.io) — the write-ups
Long-form notes on all of the above: architecture decisions, benchmark methodology, and the
ONNX-export and quantization pitfalls I had to debug the hard way.

## 🛠️ Stack

- **Day job:** Python, PyTorch, ONNX/ONNX Runtime, TensorRT (incl. trtexec), FastAPI,
  Docker, GitLab CI/CD, Grafana/Loki/Tempo
- **On-device:** llama.cpp, GGUF, MLX/mlx-lm, INT8/FP16 PTQ with calibration
- **Learning by shipping:** Rust — ipic is written in it; I'm working through the language
  properly, in public
- **Previously heavy:** OpenCV, medical imaging (fluoroscopy, segmentation, super-resolution)

## 📫

Building inference that has to be faster, cheaper, or smaller?
[Email me](mailto:anubhavagr.mail@gmail.com) — I enjoy comparing notes.
