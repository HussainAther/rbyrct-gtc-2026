# RBYRCT-GTC-2026
# 🩻 RBYRCT: Real-Time, Low-Dose Breast CT via CUDA-Accelerated Localized MART.

🩻 Can we make cancer screening 100x faster and safer?

I’m entering my project, RBYRCT, for the #NVIDIAGTC Golden Ticket! We used @NVIDIADeveloper CUDA to accelerate CT reconstruction by orders of magnitude. By optimizing the MART algorithm on GPUs, we’re enabling low-dose, high-accuracy imaging for safer breast cancer detection.

We are achieving 100x acceleration in CT reconstruction, turning hours of compute into seconds of real-time diagnostic insight using NVIDIA CUDA.

Check out the open-source work here: https://github.com/HussainAther/rbyrct-gtc-2026

Cc: @bryancatanzaro @NVIDIAGTC

## Software-Defined Hardware: Steering X-rays with CUDA
Traditional CT is limited by static, "dumb" hardware (e.g., aluminum bowtie filters). RBYRCT (Ray-by-Ray Computed Tomography) replaces these mechanical constraints with Active Flux Control—a GPU-steered sampling paradigm enabled by our patent-pending Hierarchical Polycapillary X-ray Optic (Case 003U).

By utilizing the 1.1577 cm steering authority of the braided optic, we move the intelligence of the scanner into the CUDA kernels, allowing the system to "hunt" for lesions in real-time based on instantaneous feedback.'

⚡ Performance Benchmarks
Utilizing NVIDIA CUDA 12.4 and CuPy-accelerated MART (Multiplicative Algebraic Reconstruction Technique), we have achieved a massive reduction in diagnostic latency.
MetricCPU Baseline (Intel i9)NVIDIA Tesla T4 (GTC Demo)NVIDIA H100 (Projected)Reconstruction Time~42 Minutes14.2 Seconds< 1.5 SecondsThroughput1 Scan / Hour250 Scans / HourReal-time / InstantRelative Speedup1x177x1600x🧠 Key Computational Innovations
Artifact Starvation: Unlike standard fan-beam filtered back-projection (FBP), our high-entropy "Ray-by-Ray" sampling strategy starves coherent aliasing artifacts at the source.
Anytime MART Architecture: Our GPU implementation provides a usable "Scout" image within the first 100 rays, refining to clinical grade as the scan progresses.
Digital Twin Calibration: We use GPU-accelerated lookup tables to compensate for physical manufacturing variances in the braided optic, turning hardware imperfections into a software-solved optimization problem.

🌐 OSS-First Clinical Vision
While the physical 003U Optic is protected, the RBYRCT Reconstruction Core is open-source. We are building the world's first standardized library for Steerable Tomography, ensuring that GPU-powered low-dose screening is accessible to clinics worldwide.


## The Vision: Safer, Earlier Breast Cancer Detection
Breast cancer screening saves lives, but current CT scans often demand high radiation doses for clear images, posing a risk, especially to younger patients. Additionally, traditional imaging methods are frequently uncomfortable, invasive, and involve painful compression.

RBYRCT (Ray-by-Ray Computed Tomography) is our patent-pending, GPU-optimized iterative reconstruction technology designed to solve this.

RBYRCT's Game-Changing Advantages:

Reduced Radiation Exposure: Our technology is engineered to cut the required radiation dose without sacrificing image detail, potentially transforming early cancer detection safety.

No Compression: Our patient-friendly design minimizes discomfort and anxiety, making the imaging process less invasive and more manageable for women.

Higher Accuracy: Earlier and more precise tumor detection leads to better patient outcomes.

We are establishing a new gold standard in medical imaging that prioritizes both diagnostic accuracy and patient well-being.

## The Appeal: Support Janus Sphere Innovations
Hi, I'm Syed Hussain Ather—scientist, innovator, and the driving force behind Janus Sphere Innovations.

Over the past year, I have voluntarily committed over $10,000 of my personal funds and 100% of my time to this project. Every step—publishing our research ([Link to Published Work]), securing legal counsel, and forming a business foundation—has been driven by a commitment to make this life-saving vision a reality.

### Why You Can Trust Us
Our work is built on scientific and ethical integrity, guided by professional legal teams:

Patent Team: Rapacke Law Group is protecting our intellectual property.

Business Formation: EPGD Business Law is establishing our corporate foundation.

Scientific Team: Our collaborators, including Dr. Richard Gordon, ensure we maintain the highest standards.

### What we built

This project combines two worlds:

* **MART (Multiplicative Algebraic Reconstruction Technique)** — an advanced algorithm that can reconstruct good images even from sparse or noisy CT data.
* **GPU Acceleration with NVIDIA CUDA** — MART is powerful but slow on CPUs. With NVIDIA GPUs, it becomes *10–100× faster*, making it practical in real-time.

### The core idea

Think of CT like taking **many X-ray “shadows”** of an object from different angles, then piecing them together.

* The **old way (FBP, Filtered Back Projection)** is fast but needs a *lot* of X-rays (higher dose).
* Our way (**RBYRCT MART on GPUs**) can do the same job (or better) with fewer X-rays (lower dose) — meaning *less radiation for patients*.

### Results at a glance

* ⚡ **Speed**: GPU MART runs in milliseconds vs. seconds for CPU.
* 🩻 **Image quality**: Cleaner reconstructions in sparse-angle, noisy settings.
* 🌍 **Impact**: Aiming for **earlier, safer breast cancer detection worldwide**.

---

## Features
- 🚀 **GPU-accelerated MART** (Multiplicative Algebraic Reconstruction Technique)
- 🖥️ **CPU FBP baseline** for comparisons
- 📊 Built-in benchmarking + metrics (PSNR, SSIM)
- 🎛️ Interactive **Streamlit demo** (`demo/app.py`)
- 🧪 Easy testing & reproducibility (`pytest`, `Makefile`)

---

## Installation

Clone the repo and install in editable mode:

```bash
git clone https://github.com/yourusername/rbyrct-gtc-2026.git
cd rbyrct-gtc-2026
python -m pip install -e .
````

Requirements are in [`requirements.txt`](requirements.txt).
GPU features require **NVIDIA GPU + CuPy**.

---

## Usage

### Run Benchmarks

Run the grid benchmark and auto-save results to `assets/`:

```bash
make bench
```

Outputs:

* `assets/bench_grid.csv` – raw runtime/metrics data
* `assets/bench_table.md` – Markdown summary (drop directly into slides/docs)
* `assets/runtime_vs_size.png` – runtime scaling plot

### Launch Demo

Interactive app for MART vs FBP side-by-side reconstruction:

```bash
make demo
```

### Run Tests

```bash
make test
```

### Formatting & Linting

```bash
make format   # black
make lint     # flake8
```

---

## Results

Below is an example benchmark run (automatically generated by `make bench`):

📊 **Performance Table**
See [`assets/bench_table.md`](assets/bench_table.md) for full results.

📈 **Runtime Scaling**
![Runtime vs Size](assets/runtime_vs_size.png)

---

## Contributing

PRs welcome — this is a hackathon/competition prototype but we want it to grow into a real open-source project.

---

## Citation

If this work helps you, please cite:

```
@software{rbyrct_gtc2026,
  title        = {RBYRCT-GTC-2026: GPU-Accelerated CT Reconstruction},
  author       = {Your Name},
  year         = {2026},
  url          = {https://github.com/yourusername/rbyrct-gtc-2026}
}
```

### Troubleshooting
- **No GPU?** Runs CPU-only automatically. Set `RBYRCT_FORCE_CPU=1` to force CPU.
- **Colab GPU mismatch (cudaErrorInsufficientDriver)?** 
  `pip uninstall -y cupy* && pip install cupy-cuda12x` (or `11x` if `nvidia-smi` shows 11.x), then Runtime → Restart.
- **Import error?** We set `PYTHONPATH` in the notebook; no editable install needed.

---

## License

MIT License.

![](linkedinreferncergordonalicea.png)

---

## NVIDIA GTC Submission

This project is part of the **NVIDIA GTC 2026 Golden Ticket Challenge**.
We showcase how **GPU-powered reconstruction** can transform breast cancer screening with **OSS-first innovation**.

