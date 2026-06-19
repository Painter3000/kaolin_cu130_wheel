# kaolin-Wheel

Custom **kaolin** Wheel für CUDA 13.0 + Blackwell GPU (sm_120).

Optimiert für **HuggingFace ZeroGPU** und **PSHuman** auf Blackwell Hardware.

---

## 🎯 Specs

| Komponente    | Version                      |
| ------------- | ---------------------------- |
| **Python**    | 3.10                         |
| **PyTorch**   | 2.11.0 + cu130               |
| **CUDA**      | 13.0                         |
| **GPU Arch**  | **12.0 (Blackwell sm_120)**  |
| **kaolin**    | master (konfigurierbar)      |

---

## 🚀 Workflow

Der GitHub Actions Workflow (`build_kaolin_cu130.yml`) baut das Wheel automatisch.

**Manuell triggern:**

1. GitHub → **Actions** → *Build kaolin Wheel*
2. **Run workflow** → Optional: kaolin ref eingeben (Branch / Tag / Commit)
3. **Run** → 45–90 Min. warten

**Release:** Nach erfolgreichem Build wird ein GitHub Release mit dem Wheel erstellt.

---

## 📦 Installation

Die `.whl`-URL aus dem Release kopieren und in `requirements.txt` eintragen:

```
https://github.com/Painter3000/kaolin-Wheel/releases/download/kaolin-torch2.11.0-cu130/kaolin-XXX-cp310-cp310-linux_x86_64.whl
```

Oder direkt aus dem HF-Space-Wheels-Ordner:

```
https://huggingface.co/spaces/painter3000/PSHuman/resolve/main/Wheels/kaolin-XXX-cp310-cp310-linux_x86_64.whl
```

---

## ⚙️ Build-Details

- ✅ `--no-build-isolation` → exakt torch 2.11.0, kein Downgrade
- ✅ `--index-url cu130` → CUDA-Wheel, nicht CPU
- ✅ `FORCE_CUDA=1` → Kompilierung ohne physische GPU
- ✅ `sm_120` → Blackwell RTX PRO 6000 unterstützt
- ✅ `MAX_JOBS=2` → RAM-schonend (kaolin hat viele CUDA-Extensions)
- ✅ Docker Image: `nvidia/cuda:13.0.1-devel-ubuntu22.04`

---

## 🔗 Verwendung in PSHuman

Ersetze in PSHuman `requirements.txt`:

```diff
- # disabled_todo: kaolin
+ https://huggingface.co/spaces/painter3000/PSHuman/resolve/main/Wheels/kaolin-XXX-cp310-cp310-linux_x86_64.whl
```

---

## 🗂️ Verwandte Wheels (PSHuman Blackwell Stack)

| Paket | Repo |
| --- | --- |
| pytorch3d | [pytorch3d-Wheel](https://github.com/Painter3000/pytorch3d-Wheel) |
| torch_scatter | [pytorch3d-Wheel](https://github.com/Painter3000/pytorch3d-Wheel) |
| nvdiffrast | im HF-Space-Wheels-Ordner |
| **kaolin** | dieses Repo |

---

**Status:** ⏳ Build ausstehend
