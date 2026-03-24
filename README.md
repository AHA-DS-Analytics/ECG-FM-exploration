# ECG-FM-exploration

This repository provides a step-by-step and reproducible pipeline for evaluating the ECG foundation model (**ECG-FM**) on the **MIMIC-IV-ECG** dataset under both:

- **12-lead ECG setting**
- **Single-lead ECG setting** (using **Lead II** with zero-padding)

This README is written as a beginner-friendly guide so that you can start from **zero** and fully reproduce the results.

---

## 1. What this repository does

This project evaluates the pretrained **ECG-FM** model on **MIMIC-IV-ECG** data.

Workflow:

1. Load ECG waveform data  
2. Run ECG-FM inference  
3. Generate prediction probabilities  
4. Compare:
   - **12-lead ECG**
   - **Single-lead ECG**

---

## 2. Files in this repository

- `tutorial_12lead.ipynb` → 12-lead ECG inference  
- `tutorial_1lead.ipynb` → single-lead ECG inference  
- `requirements.txt` → environment dependencies  
- `README.md` → documentation  

---

## 3. Requirements

### Python
Recommended: Python 3.10

---

## 4. Step 1 — Clone this repository

```bash
git clone https://github.com/AHA-DS-Analytics/ECG-FM-exploration.git
cd ECG-FM-exploration
```

---

## 5. Step 2 — Create environment

```bash
conda create -n ecgfm python=3.10 -y
conda activate ecgfm
```

---

## 6. Step 3 — Install dependencies

### Install from requirements.txt

```bash
pip install -r requirements.txt
```

---

## 7. Step 4 — Install ECG-FM and fairseq

ECG-FM depends on **fairseq-based infrastructure**, so installation must follow their pipeline.

### 7.1 Clone ECG-FM

```bash
git clone https://github.com/bowang-lab/ecg-fm.git
```

---

### 7.2 Install ECG-FM dependencies

```bash
cd ecg-fm
pip install -e .
```

---

### 7.3 Install fairseq (IMPORTANT)

ECG-FM relies on `fairseq-signals`.

Install it as follows:

```bash
git clone https://github.com/Jwoo5/fairseq-signals.git
cd fairseq-signals
pip install -e .
```

---

### 7.4 Install additional required package

```bash
pip install ecg-transform==0.1.3
```

---

### 7.5 Go back to project

```bash
cd ../ECG-FM-exploration
```

---

## 8. Step 5 — Download dataset

Download MIMIC-IV-ECG:

https://physionet.org/content/mimic-iv-ecg/1.0/

After extraction:

```
files/
├── p1000/
│   └── p10001725/
│       └── s41420867/
│           ├── 41420867.dat
│           └── 41420867.hea
```

---

## 9. Step 6 — Folder structure

```
your_workspace/
├── ECG-FM-exploration/
├── ecg-fm/
├── fairseq-signals/
└── mimic-iv-ecg/
    └── files/
```

---

## 10. Step 7 — Launch notebook

```bash
cd ECG-FM-exploration
jupyter notebook
```

---

## 11. Run 12-lead tutorial

Open:

```
tutorial_12lead.ipynb
```

---

## 12. Run single-lead tutorial

Open:

```
tutorial_1lead.ipynb
```

---

## 13. Labels

Labels are generated using ECG-FM labeler:

```
ecg-fm/labeler
```

---

## 14. Single-lead setting

ECG-FM expects 12 leads.

We simulate single-lead input by:

- keeping **Lead II**
- setting other leads to zero

---

## 15. Troubleshooting

### Missing fairseq
Reinstall:
```bash
pip install -e fairseq-signals
```

### Model download fails
Check:
- internet connection
- Hugging Face access

### Missing packages
```bash
pip install <package>
```

---

## 16. References

ECG-FM:  
https://github.com/bowang-lab/ecg-fm  

MIMIC-IV-ECG:  
https://physionet.org/content/mimic-iv-ecg/1.0/  

---

## Quick Start

```bash
git clone https://github.com/AHA-DS-Analytics/ECG-FM-exploration.git
cd ECG-FM-exploration

conda create -n ecgfm python=3.10 -y
conda activate ecgfm

pip install -r requirements.txt

git clone https://github.com/bowang-lab/ecg-fm.git
git clone https://github.com/Jwoo5/fairseq-signals.git

cd fairseq-signals
pip install -e .

cd ../ecg-fm
pip install -e .

cd ../ECG-FM-exploration
jupyter notebook
```

---

## Notes

- This repo is for **inference only**
- Uses **Lead II** for single-lead experiment
- Requires PhysioNet access
