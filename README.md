# qwen38-colab-t4

Qwen3.8-27B Abliterated on Colab T4 via AirLLM — 27B full model tanpa quantization, muat dalam T4 16GB dengan layer streaming (GPU + RAM + disk).

## Buka di Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/gb99xbear/qwen38-colab-t4/blob/main/qwen38-27b-abliterated-t4-airllm.ipynb)

## Sebelum run

1. **Runtime -> Change runtime type -> T4 GPU**
2. Pilih **High Memory** (24GB) kalau ada option
3. Run cells ikut urutan — pilih **Option A (bf16)** atau **Option B (4bit)** , jangan dua-dua

## Isi notebook

| Cell | Apa |
|---|---|
| setup | `pip install airllm` + `nvidia-smi`, `df -h`, `free -h` |
| check | cek CUDA, VRAM, disk, HF cache |
| Option A | bf16 quality penuh ~54GB |
| Option B | 4bit compression ~3x laju, ~27GB |
| chat | loop `input("b> ")` interactive |
| nota | ToS Colab, abliterated warning |

## Speed (anggaran, kena test real)

- bf16 ~1-3 tok/s
- 4bit ~3-5 tok/s
- bottleneck = disk read Colab, bukan VRAM

## Nota

- Jangan serve API/web dari Colab (ToS). Nak API, deploy model ke VPS.
- Model abliterated/uncensored — output mungkin kasar.
