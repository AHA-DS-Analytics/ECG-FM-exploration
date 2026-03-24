# ECG-FM-exploration

This repository provides a step-by-step and reproducible pipeline for evaluating the ECG foundation model (**ECG-FM**) on the **MIMIC-IV-ECG** dataset under both:

- **12-lead ECG setting**
- **Single-lead ECG setting** (using **Lead II** with zero-padding)


---

## 1. Workflow

This project evaluates the pretrained **ECG-FM** model on **MIMIC-IV-ECG** data.

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
- `create_10k_test_data.ipynb` → labeler and create dataset
- `requirements.txt` → environment dependencies
- `README.md` → documentation  

---

## 3. Requirements

### Python
Recommended: Python 3.10

---

## 4. Clone this repository

```bash
git clone https://github.com/AHA-DS-Analytics/ECG-FM-exploration.git
cd ECG-FM-exploration
```

---

## 5. Create environment

```bash
conda create -n ecgfm python=3.10 -y
conda activate ecgfm
```

---

## 6. Install dependencies

### Install from requirements.txt

```bash
pip install -r requirements.txt
```

---

## 7. Install ECG-FM and fairseq

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

### 7.3 Install fairseq

ECG-FM relies on `fairseq-signals`.

Install it as follows:

```bash
git clone https://github.com/Jwoo5/fairseq-signals.git
cd fairseq-signals
pip install -e .
```

---

## 8. Download dataset

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
## 9. Run Labeler

```
create_10k_test_data.ipynb
```

- Selects **10,000 ECG records** from MIMIC-IV-ECG  
- Uses ECG-FM labeler to generate labels  
- Prepares dataset for inference
- You can then run the tutorial_1lead.ipynb and tutorial_12lead.ipynb after this step


---

## 10. References

ECG-FM:  
https://github.com/bowang-lab/ecg-fm  

MIMIC-IV-ECG:  
https://physionet.org/content/mimic-iv-ecg/1.0/  

---


