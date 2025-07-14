# ⚽ Ultra-Accurate Player Tracking with YOLOv8 + ResNet50 + ByteTrack

This project implements a highly accurate player tracking system for football match videos using:

- **YOLOv8** for object detection
- **ByteTrack** for initial tracking
- **ResNet50 + Color + Geometry** features for robust ID re-assignment
- **Google Drive** for model/data management
- Fully implemented in a **Colab-compatible Jupyter Notebook**

---

## 📁 Project Structure

```
Player_Tracking/
├── Input_Video/
│   └── 15sec_input_720p.mp4          # Sample input
├── Models/
│   └── best.pt                       # YOLOv8 trained weights
├── Outputs/
│   ├── final_tracking_video.avi  # Final annotated video
│   └── final_tracked_frames/
│       └── frame_0001.jpg
│       └── ...
├── Player_Tracking.ipynb            # Main notebook (run this)
├── requirements.txt                 # Pip install list
└── README.md                        # You're reading this!
```

---

## 🔧 Step 1: Setup Environment (Google Colab)

Open the notebook and run the first cell:

```bash
!pip install -U ultralytics opencv-python-headless lap
!pip install -q matplotlib pandas tqdm scikit-learn
!pip install git+https://github.com/facebookresearch/segment-anything.git
```

---

## 📂 Step 2: Add the folder to your google drive

Add the Player_Tracking Folder as it is to your google drive.

---


## 📂 Step 3: Mount Google Drive

Run this in Colab:

```python
from google.colab import drive
drive.mount('/content/drive')
```

Make sure your Drive has the following path:
```
/content/drive/MyDrive/Player_Tracking/
├── Input_Video/15sec_input_720p.mp4
├── Models/best.pt
├── Outputs/
```

---

## 🎯 Step 4: Run Ultra-Accurate Player Tracking

This notebook will:

1. Load the YOLOv8 model (`best.pt`) from Google Drive.
2. Read the input football match video.
3. Detect players, referees, and the ball using YOLOv8.
4. Track player positions using ByteTrack.
5. Assign **consistent player IDs** using:
   - ResNet50 deep features
   - Color histograms
   - Dominant colors
   - IoU-based box overlap
   - Position prediction (motion-based)
6. Save:
   - A final annotated video (`Outputs/final_tracking_video.avi`)
   - Per-frame images (`Outputs/final_tracked_frames/`)

---

## Step 5: 
You can check the final output in the outputs folder at final_tracking_video.avi
You can also check the per frame output for validation at final_tracked_frames.

---


## 🧪 Output Example

- ✅ `final_tracking_video.avi`: Player boxes + IDs + confidence drawn on the video
- ✅ `frame_00XX.jpg`: Individual annotated frames
- ✅ Player confidence, ID mapping printed after tracking

---


## 💡 Key Features

| Component         | Method                                                                 |
|------------------|------------------------------------------------------------------------|
| Detection         | YOLOv8 (Ultralytics)                                                   |
| Tracking          | ByteTrack                                                              |
| Feature Extraction| ResNet50 + Color Histogram + Dominant Color                            |
| ID Assignment     | Multi-feature similarity + IoU + position prediction                   |
| Confidence Mgmt   | Boost on match, decay on disappearance                                 |
| Output            | `.avi` video + frame-by-frame images                                   |

---

##  Please Contact me if there are any issues.

## 🙋‍♂️ Author

**Ved Deshpande**  
[LinkedIn](www.linkedin.com/in/ved-deshpande-a632b7282) | [GitHub]([https://github.com](https://github.com/VED045))  
AI in Sports | Object Tracking | Computer Vision
