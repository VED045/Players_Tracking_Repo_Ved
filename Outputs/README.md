# Player Tracking System using YOLOv8 + SAM + Deep Features

This project implements an enhanced football player tracking system using the YOLOv8 object detector, with additional support for robust Re-Identification (Re-ID) using deep features (ResNet50), color histograms, and motion prediction. The final system assigns consistent player IDs across frames with high accuracy and low switching.

---

## 🔧 Dependencies

Install required libraries using the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

Or manually install the core packages:

```python
!pip install -U ultralytics opencv-python-headless lap
!pip install -q matplotlib pandas tqdm scikit-learn
!pip install git+https://github.com/facebookresearch/segment-anything.git
```

---

## 📁 Folder Structure

```
Player_Tracking/
├── Player_Tracking.ipynb            # Main Colab notebook
├── requirements.txt                 # Dependency list
├── README.md                        # This file
├── report.md                        # Project report
├── Models/
│   └── best.pt                      # Custom YOLOv8 model
├── Input_Video/
│   └── 15sec_input_720p.mp4         # Sample input video
├── Outputs/
    ├── final_output_video.avi      # Final output video
    ├── final_tracked_frames/       # Output frames with IDs
    ├── player_database.pkl         # Saved feature database
    └── tracking_summary.json       # Player tracking info
```

---

## ▶️ How to Run the Code

### **Step 1: Mount Google Drive**

In Colab, run:

```python
from google.colab import drive
drive.mount('/content/drive')
```

### **Step 2: Install Dependencies**

```python
!pip install -r /content/drive/MyDrive/Player_Tracking/requirements.txt
```

### **Step 3: Run the Notebook**

1. Open `Player_Tracking.ipynb` from Google Drive.
2. Ensure paths are set correctly:
   - Model: `/content/drive/MyDrive/Player_Tracking/Models/best.pt`
   - Input: `/content/drive/MyDrive/Player_Tracking/Input_Video/15sec_input_720p.mp4`
3. Run all cells to execute player tracking and save outputs to the `Outputs/` directory.

---

## ⚙️ Features Used for Player Re-ID

- **ResNet50 deep features** (256-d)
- **Color histograms** (HSV, 64-d)
- **Dominant color** (mean RGB)
- **IoU and position prediction** for temporal consistency
- **ID switch cooldown + confidence tracking** for stability

---

## ✅ Output Files

- `final_output_video.avi`: Final annotated video
- `final_tracked_frames/`: Individual annotated frames
- `player_database.pkl`: Player feature database
- `tracking_summary.json`: Summary stats (player count, IDs)

---

## 🧠 Tracking Logic Highlights

- Maintains historical features and positions
- Matches trackers to player IDs based on similarity and spatial data
- Handles missing trackers, cooldowns, and appearance changes robustly

---

## 🤝 Contributors

- **Ved Deshpande** – Implementation, tuning, and evaluation

---

##

