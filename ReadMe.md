# ✅ To-Do List for Multimodal Depression Detection Project

---

## 📄 Text Modality

### 🔹 Transcription & Preprocessing
- [ ] Generate high-quality transcripts using **Whisper ASR** from raw audio
- [ ] Clean transcripts:
  - [ ] Correct grammar and incomplete segments
  - [ ] Structure into question/answer format
  - [ ] Remove unmatched fragments

### 🔹 Feature Extraction
- [ ] Extract features using **DepRoBERTa** (fine-tuned RoBERTa)
  - [ ] Output class probabilities: Not-depressed / Moderate / Severe
- [ ] Use **LLM-based question-answer method**
  - [ ] Generate answers to 11 designed depression-related questions
  - [ ] Encode as an 11-dimensional numerical feature vector
- [ ] Concatenate both sets of features into a final textual embedding

---

## 🎧 Audio Modality

### 🔹 Preprocessing
- [ ] Convert audio to **Mel spectrograms** using `librosa`

### 🔹 Feature Extraction
- [ ] Evaluate three encoding approaches:
  - [ ] `Wav2Vec2` + 1D-CNN + attention pooling
  - [ ] `Wav2Vec2-BERT 2.0` (optional – for robustness to noise)
  - [ ] Bi-LSTM encoder (train from scratch)
  - [ ] CNN encoder (train from scratch)
- [ ] (Optional) Extract **GeMAPS features**: pitch, jitter, shimmer, loudness, etc.

---

## 🎥 Visual Modality

### 🔹 Preprocessing & Feature Extraction
- [ ] Use available **OpenFace** features:
  - [ ] 3D facial landmarks
  - [ ] Gaze direction vectors (each eye)
  - [ ] Head pose vectors (translation & rotation)
  - [ ] Facial Action Unit (FAU) intensities + confidence scores
- [ ] Use precomputed **deep CNN features**:
  - [ ] ResNet
  - [ ] VGG

---

## 🔗 Fusion & Architecture

### 🔹 Fusion Strategies
- [ ] Implement **early fusion** (data-level): concatenate `[et; ea; ev]` → feed into:
  - [ ] MLP
  - [ ] CNN
  - [ ] BiLSTM
  - [ ] Transformer
- [ ] Implement **intermediate fusion** (feature-level): modality-specific encoders → concat → regressor

---

## 📊 Evaluation

### 🔹 Metrics
- [ ] Compute **Mean Absolute Error (MAE)** and **Root Mean Square Error (RMSE)** for:
  - [ ] PHQ-8 score (depression)
  - [ ] PCL-C score (PTSD)

---

## 🧪 Testing & Ablation (Optional)
- [ ] Compare different temporal granularities:
  - [ ] Global (full-session embedding)
  - [ ] Segment-level (using Whisper word-level timestamps)
- [ ] Evaluate impact of individual modalities via ablation tests

---

## 📂 Miscellaneous
- [ ] Organize preprocessed data into train/dev/test splits
- [ ] Document preprocessing steps in codebase
- [ ] Update README and report regularly with progress

---