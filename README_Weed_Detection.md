# 🌿 Weed Detection using YOLOv5

## 🧠 Overview
This project focuses on **automatic weed detection** in agricultural images using the **YOLOv5 object detection model**.  
It trains a deep learning model to detect and classify weeds from datasets such as **Weed25** and **CropWeed**, helping automate precision agriculture tasks.

---

## 📁 Project Structure
```
weed_detection_project/
│
├── datasets/
│   ├── Weed25/
│   │   ├── images/
│   │   └── annotations/
│   ├── CropWeed/
│   │   ├── images/
│   │   └── annotations/
│
├── models/          # Trained YOLOv5 models
├── runs/            # Training results and logs
├── utils/           # Helper scripts
├── yolov5/          # Cloned YOLOv5 repository
└── weed_detection_project.ipynb
```

---

## 🚀 Features
- Weed detection using **YOLOv5**
- Support for multiple datasets (`Weed25`, `CropWeed`)
- Automated **VOC-to-YOLO annotation conversion**
- Easy dataset organization and preprocessing
- Model training, validation, and performance visualization

---

## 🧰 Requirements

Install dependencies:

```bash
pip install torch torchvision torchaudio
pip install opencv-python pandas numpy matplotlib tqdm
pip install PyYAML xmltodict
```

Clone YOLOv5 (if not already done):

```bash
!git clone https://github.com/ultralytics/yolov5
cd yolov5
pip install -r requirements.txt
```

---

## 🧩 Dataset Preparation

1. Place datasets in:
   ```
   datasets/Weed25/images
   datasets/Weed25/annotations
   ```
2. Run the XML-to-YOLO converter provided in the notebook to generate `.txt` label files.

---

## 🏋️‍♂️ Training the Model

Update the dataset YAML (`weed25.yaml`) with your paths:

```yaml
train: ../datasets/Weed25/train/images
val: ../datasets/Weed25/val/images

nc: 25
names: ['weed1', 'weed2', ..., 'weed25']
```

Then train:

```bash
!python yolov5/train.py --img 640 --batch 16 --epochs 100 --data weed25.yaml --weights yolov5s.pt --cache
```

---

## 📈 Evaluation

Evaluate trained weights:

```bash
!python yolov5/val.py --weights runs/train/exp/weights/best.pt --data weed25.yaml --img 640
```

Check metrics like **mAP**, **precision**, and **recall**.

---

## 📊 Results
- Model: YOLOv5s  
- Input Size: 640×640  
- mAP (mean Average Precision): *to be filled after training*  
- Example detections stored in `runs/detect/`

---

## 🔮 Future Improvements
- Integrate YOLOv8 or EfficientDet
- Real-time detection via webcam or drone feed
- Dataset augmentation and hyperparameter tuning

---

## 👨‍💻 Author
**Sumit Kumar Nandy**  
*Computer Science & Engineering Student*  
Email: *[your-email@example.com]*
