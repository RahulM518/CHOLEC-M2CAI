# 🧠 Surgical Tool and Organ Segmentation 

---

## 🎯 Aim:

To develop a lightweight, real-time computer vision system that can:
- Detect surgical tools during procedures
- Identify and segment anatomical structures such as organs, arteries, and fluids
- Run efficiently on low-power Edge AI hardware for potential operating room integration or robotic assistance

The system is designed to be practical for intraoperative use, training simulation, or post-surgical analysis.

---

## 📚 Dataset Sources:

The models are trained and evaluated on publicly available surgical video datasets:

1. **CholecSeg8k**  
   👉 https://www.kaggle.com/datasets/newslab/cholecseg8k  
   > Annotated laparoscopic cholecystectomy dataset with organ and tool segmentation masks

2. **Stanford Tool Detection Dataset (m2cai16-tool-locations)**  
   👉 https://ai.stanford.edu/~syyeung/tooldetection.html  
   > Real-time labeled frames from cholecystectomy procedures for surgical tool detection

Both datasets contain pixel-level or bounding-box annotations, and were adapted into a consistent semantic segmentation format with a 19 (12+7)-class label mapping.

---

## ⚙️ Procedure:

1. **Label Mapping**  
   - A JSON file defines 19 unique classes (organs, tools, fluids, arteries), each with a distinct RGB color

2. **Data Preprocessing**  
   - Color masks converted to class-index masks
   - Normalization, augmentation, resizing for model training

3. **Model Training**  
   - **YOLOv8 Nano (Segmentation head)** used for object/ tool detection  (7 tools)
   - **UNET+MobileNetV2** and **YOLOv8 Medium (Semantic Segmentation)** used for semantic segmentation (12 parts)
   - Both models trained and evaluated separately, with overlays rendered on test video

4. **Video Inference Pipeline**  
   - Test video frames are processed in real-time
   - YOLOv8 models run side-by-side on each frame
   - Output video visualizes predictions from both models for qualitative comparison

---

## 💻 Devices Aimed to Run On:

The system is optimized for real-time execution on lightweight and embedded hardware platforms:

- ⚡ **NVIDIA Jetson Nano**
- ⚡ **Raspberry Pi 4 or 5**
- ⚡ **Texas Instruments SK-AM62ALP**
- ⚡ **Microchip PolarFire Icicle Kit**
- 💻 Regular desktops with GPU (for training and high-res testing) 

---

## Download of Heavy files:

📥 [Download heavy model and related files] (https://github.com/RahulM518/CHOLEC-M2CAI/releases/tag/Segmentation_model_tag/GITHUB__OUTPUT.zip)


## Results

- **Output of Segmentation**  
  ![final_seg](https://github.com/user-attachments/assets/25358f2f-8ed4-421d-8466-ababd44a8783)

- **Output of Tool Detection**  
  ![final_obj](https://github.com/user-attachments/assets/71d0fce2-cd6b-4e7e-8466-7b4c48f3ae3e)




