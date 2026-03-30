Here is the refined and formatted version of your project documentation. I have organized the hierarchy, cleaned up the tables, and ensured the technical sections are scannable for the GTC review committee.

---

# RBYRCT: Real-Time, Low-Dose Breast CT
### CUDA-Accelerated Localized MART for Safer Cancer Screening
**NVIDIA GTC 2026 Golden Ticket Submission**

[Open-Source Repository](https://github.com/HussainAther/rbyrct-gtc-2026) | [Janus Sphere Innovations](https://github.com/HussainAther)

---

## ⚡ Executive Summary
**Can we make cancer screening 100x faster and safer?**
RBYRCT (Ray-by-Ray Computed Tomography) utilizes NVIDIA CUDA to accelerate CT reconstruction by orders of magnitude. By optimizing the **Multiplicative Algebraic Reconstruction Technique (MART)** on GPUs, we enable low-dose, high-accuracy imaging, turning hours of compute into seconds of real-time diagnostic insight.

### The Problem vs. The Solution
* **The Problem:** Traditional CT requires high radiation doses and painful breast compression. Reconstruction is bottlenecked by CPU-heavy algorithms or "dumb" static hardware.
* **The Solution:** Software-defined hardware. We replace mechanical constraints with **Active Flux Control**—a GPU-steered sampling paradigm enabled by our patent-pending Hierarchical Polycapillary X-ray Optic.

---

## 🚀 Performance Benchmarks
*Utilizing NVIDIA CUDA 12.4 and CuPy-accelerated MART.*

| Metric | CPU Baseline (i9) | NVIDIA Tesla T4 | NVIDIA H100 (Projected) |
| :--- | :--- | :--- | :--- |
| **Reconstruction Time** | ~42 Minutes | 14.2 Seconds | < 1.5 Seconds |
| **Throughput** | 1 Scan / Hour | 250 Scans / Hour | Real-time / Instant |
| **Relative Speedup** | 1x | **177x** | **1600x** |

---

## 🧠 Key Computational Innovations

* **Artifact Starvation:** Unlike standard fan-beam filtered back-projection (FBP), our high-entropy "Ray-by-Ray" sampling strategy starves coherent aliasing artifacts at the source.
* **Anytime MART Architecture:** Our GPU implementation provides a usable "Scout" image within the first 100 rays, refining to clinical grade as the scan progresses.
* **Digital Twin Calibration:** We use GPU-accelerated lookup tables to compensate for physical manufacturing variances in the braided optic, solving hardware imperfections through software optimization.
* **OSS-First Vision:** While the physical optic is protected, the **RBYRCT Reconstruction Core** is open-source, building a standardized library for Steerable Tomography.

---

## 🛠️ Technical Implementation

### Features
* **GPU-accelerated MART** via CuPy/CUDA.
* **CPU FBP baseline** for rigorous clinical comparison.
* **Automated Metrics:** Built-in PSNR and SSIM validation.
* **Interactive Demo:** Streamlit-based UI for side-by-side reconstruction.

### Installation
```bash
git clone https://github.com/HussainAther/rbyrct-gtc-2026.git
cd rbyrct-gtc-2026
python -m pip install -e .
```
*Note: GPU features require an NVIDIA GPU and CuPy.*

### Quick Start Commands
* **Run Benchmarks:** `make bench` (Generates CSVs and runtime scaling plots).
* **Launch Demo:** `make demo` (Interactive MART vs FBP visualization).
* **Test Suite:** `make test` (Ensures mathematical consistency).

---

## 🌐 The Vision: Janus Sphere Innovations
Led by **Syed Hussain Ather**, Janus Sphere Innovations is committed to scientific and ethical integrity.

### Our Partners & Foundation
* **Scientific Lead:** Dr. Richard Gordon.
* **IP Protection:** Rapacke Law Group (Patent Case 003U).
* **Corporate Counsel:** EPGD Business Law.

> "We are establishing a new gold standard in medical imaging that prioritizes both diagnostic accuracy and patient well-being, removing the need for painful compression and reducing radiation risks for younger patients."

---

## 📝 Citation & License

```bibtex
@software{rbyrct_gtc2026,
  title  = {RBYRCT-GTC-2026: GPU-Accelerated CT Reconstruction},
  author = {Hussain Ather, Syed},
  year   = {2026},
  url    = {https://github.com/HussainAther/rbyrct-gtc-2026}
}
```
*This project is licensed under the MIT License.*
