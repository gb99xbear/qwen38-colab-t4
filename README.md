# qwen38-colab-t4

Qwen3.8-27B Abliterated on Colab T4 via AirLLM — 27B full model tanpa quantization, muat dalam T4 16GB dengan layer streaming (GPU + RAM + disk).

## Buka di Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/gb99xbear/qwen38-colab-t4/blob/main/qwen38-27b-abliterated-t4-airllm.ipynb)

## Sebelum run

1. **Runtime -> Change runtime type -> T4 GPU**
2. Pilih **High Memory** (24GB) kalau ada
3. Run cells ikut urutan — pilih **Option A (bf16)** atau **Option B (4bit)** , jangan dua-dua

## v2 fix untuk stuck cell 4bit

Kalau sebelum ni hang di cell 4bit tanpa output:
- v2 on `HF_TRANSFER` (download 27GB dalam ~10-15min bukan 1 jam)
- log progress tiap layer + fallback `profiling_mode=False` kalau `True` hang
- optional mount `drive/MyDrive/hf_cache` supaya cache kekal lepas 5 jam runtime

## Isi notebook

| Cell | Apa |
|---|---|
| setup | `pip install airllm` + `hf_transfer` + `nvidia-smi`, `df -h`, `free -h` |
| check | cek CUDA, VRAM, disk, HF cache |
| Option A | bf16 quality penuh ~54GB |
| Option B | 4bit compression ~3x laju, ~27GB — **fix stuck** |
| chat | loop `input("b> ")` interactive |

## Speed (anggaran, kena test real)

- bf16 ~1-3 tok/s
- 4bit ~3-5 tok/s

## Nota

- Jangan serve API/web dari Colab (ToS).
- Model abliterated/uncensored — output mungkin kasar.
