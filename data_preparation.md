# Multilingual Mesh-VSR Data Preparation

Zero-tolerance pipeline for extracting 3D face mesh data from videos for visual speech recognition (Lip Reading).

## 📋 Requirements

Create `requirements.txt` with:
opencv-python==4.8.1.78
numpy==1.24.3
h5py==3.10.0
whisper==1.1.10
torch==2.1.0
torchvision==0.16.0
mediapipe==0.10.8
tqdm==4.66.1
psutil==5.9.5

## 🔧 Installation

pip install -r requirements.txt

python main.py

## 🎯 Zero-Tolerance Quality Checks

Every frame must pass ALL tests:

| Check | Threshold | Why? |
|-------|-----------|------|
| Black frame | Mean pixel value < 5 | Completely useless |
| Too dark | Mean pixel value < 30 | Poor landmark quality |
| No face | Detection confidence < 0.7 | Missing data |
| Face cropped | < 10px from border | Incomplete articulation |
| Face too small | < 20% of image height | Insufficient detail |
| Invalid landmarks | Any x/y outside [0,1] | MediaPipe error |

**Segments with even ONE bad frame are COMPLETELY DISCARDED.**

## 📦 Output Format (HDF5)
lip_dataset.h5
├── landmarks # [num_frames × 1434] float32 (478 landmarks × 3)
├── frame_indices # [num_frames] int32 (original frame numbers)
├── timestamps # [num_frames] float32 (seconds)
├── video_ids # [num_frames] string (video identifier for each frame)
├── videos/ # Metadata per video (fps, success rate, stats)
└── segments/ # Transcriptions with exact frame ranges

## 📊 Statistics

After processing, use **Tools → Statistics** in GUI to see:

| Metric | Description |
|--------|-------------|
| **Total frames** | Unique 3D face meshes in database |
| **Frames in segments** | Sum of all segment lengths (logical count) |
| **Videos** | Number of processed videos |
| **Segments** | Number of speech segments |
| **Ø length** | Average segment length in frames/seconds |
| **video_ids** | Status check (✅/❌) |
| **File size** | Database size in GB |

## 🔒 Backup System

The script includes automatic backup protection:

- **Monthly backup** – Automatically on the 1st of each month
- **Growth backup** – When database grows by >10GB
- **Manual backup** – Via File → Backup menu
- **External backup** – Optional to `D:/lip_reading_backups/`

Backups are stored in `data_final/backups/` with timestamps.

## ⚠️ Important Notes

- **Only MP4 files** are processed (other formats ignored)
- **Zero tolerance** = only perfect data is saved – no sanitizer needed
- **video_ids are CRITICAL** – never delete them (breaks training)
- **Segments with bad frames** are completely discarded, not partially saved
- **Cache system** speeds up subsequent runs (delete manually if needed)
- **Parallel processing** is optional and disabled by default for stability

