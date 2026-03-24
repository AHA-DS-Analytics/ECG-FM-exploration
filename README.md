# ECG-FM-exploration
This repository provides a reproducible pipeline for evaluating the ECG foundation model (ECG-FM) on the MIMIC-IV-ECG dataset under single-lead and 12-lead ECGs.

# Download Model (ECG-FM)
https://github.com/bowang-lab/ecg-fm/tree/main

Run their quickstart case under ecg-fm/notebooks/infer_quickstart.ipynb and the model will be downloaded from huggingface.

# Download MIMIC-IV-ECG dataset
https://physionet.org/content/mimic-iv-ecg/1.0/

# Labeler
Labels are generated using the ECG-FM labeler (under ecg-fm/labeler).

# Single-Lead Transformation
The ECG-FM is only suitable for 12-lead inputs. To accommodate single-lead inputs, we choose lead II and 0-pad other leads.
