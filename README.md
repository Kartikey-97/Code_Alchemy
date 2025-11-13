# Code_Alchemy
This repository contains a safety equipment detection system trained on a fully synthetic dataset.
The purpose of the project is to build a reliable object detection model for environments where collecting and annotating real-world safety images is difficult, unsafe, or impractical.
The system identifies seven critical safety objects with real-time performance, making it suitable for industrial, laboratory, and emergency response scenarios.


Detected Classes
Oxygen Tank
Nitrogen Tank
First Aid Box
Fire Alarm
Safety Switch Panel
Emergency Phone
Fire Extinguisher


Project Structure
dataset/
    train/
    val/
    test3/
scripts/
models/
runs/
README.md
data.yaml
train.ipynb


How the System Works
A synthetic dataset is provided, containing multiple lighting, clutter, and environmental variations.
YOLOv8n is trained for 15 epochs using the train and validation split.
The model is evaluated on a separate test set to check generalization.
A curated set of ten prediction images is included: one high-confidence detection per class and three additional high-confidence examples.


Model Performance
The final model achieved the following results on the validation set:
Metric	Value
mAP50	0.70
mAP50-95	0.552
Precision	0.859
Recall	0.613
Per-Class mAP50
Oxygen Tank: 0.772
Nitrogen Tank: 0.776
First Aid Box: 0.747
Fire Alarm: 0.621
Safety Switch Panel: 0.683
Emergency Phone: 0.640
Fire Extinguisher: 0.661


Training Command
yolo task=detect mode=train \
  model=yolov8n.pt \
  data=data.yaml \
  epochs=15 \
  imgsz=640 \
  batch=16 \
  device=0

  
Prediction Command
yolo task=detect mode=predict \
  model=best.pt \
  source=test3/images \
  save=True \
  imgsz=640

  
Best 10 Prediction Samples
The folder best10/ contains ten representative outputs:
Seven images with the highest-confidence detection for each individual class
Three additional images with the strongest overall detections
These samples are intended for reporting and presentation use.


Technology Stack
Python
Google Colab
PyTorch
Ultralytics YOLOv8
Synthetic image dataset (provided by organizers)


Future Improvements
Fine-tuning using a small real-world dataset
Deployment on edge devices (Jetson, Coral)
Integration with real-time monitoring systems
Additional safety objects and scene understanding
On-device or continual learning support


AlgoX
Kartikey Gupta
Keshav Raj
Pranav Mathur
Bhagya Varshney

