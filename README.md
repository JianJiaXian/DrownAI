
# 💧 DrownAI: Drowning Detection using Pose Estimation

[![IEEE Paper](https://img.shields.io/badge/IEEE-Publication-blue)](https://ieeexplore.ieee.org/document/9704884)

> This project implements drowning behavior recognition based on human pose estimation using OpenPose and deep learning classifiers.

<div align="center">
  <img src="https://github.com/chia-shein/Drown_GIF/blob/main/%E5%81%B4%E8%BA%AB%2000_00_00-00_00_30.gif" width="300"/>
  <img src="https://github.com/chia-shein/Drown_GIF/blob/main/%E6%AD%A3%E9%9D%A2%2000_00_00-00_00_30.gif" width="300"/>
</div>

---

## 📄 Paper

This project is published at IEEE:

- **Title**: *A Drowning Detection System Based on Human Pose Estimation and Deep Learning*
- **Conference**: 2022 International Symposium on Computer, Consumer and Control (IS3C)
- **DOI**: [10.1109/IS3C53992.2022.9704884](https://ieeexplore.ieee.org/document/9704884)

---

## 🧠 Method Overview

This work proposes a real-time drowning detection system based on human skeletal motion analysis using AI techniques:

1. **Pose Estimation**:
   - Uses **OpenPose** with a lightweight **Thin-MobileNet** backbone to detect 13 body keypoints.
   - Camera is mounted underwater; pose estimation remains accurate despite splashes.

2. **Feature Extraction**:
   - Extracts joint coordinates and calculates geometric angles between limbs.
   - Converts the skeleton data into structured feature vectors.

3. **Action Classification**:
   - A shallow **Recurrent Neural Network (RNN)** is trained to classify actions as either “drowning” or “normal”.
   - The system is optimized for real-time operation with minimal GPU load.

---

## 📊 Experimental Results

- Training data collected through **simulated drowning scenarios** in a swimming pool.
- Final classification accuracy: **89.4%**
- Evaluation metrics:

| Class     | Precision | Recall | F1-Score |
|-----------|-----------|--------|----------|
| Drowning  | 0.98      | 0.67   | 0.79     |
| Normal    | 0.96      | 1.00   | 0.98     |
| **Macro Avg** | **0.97**  | **0.83** | **0.89**   |

> In most realistic simulated drowning situations, the system could correctly identify the drowning behavior with high precision.

---

## 📁 Project Structure

- `src/` - Main source code
- `model/` - Pretrained classifier (`.pickle`)
- `data_test/` - Example video for testing
- `output/` - Output results and visualizations

> 🔗 Additional data, pretrained models and demo videos are hosted on [Google Drive](https://drive.google.com/drive/folders/1LpkQqHllmBfhozYpiUWEP-tihkzgzDVC?usp=sharing)

---

## 🚀 Installation

### 1. Environment Setup

```bash
conda create -n drown python=3.6.12
conda activate drown
pip install -r requirements.txt
```

### 2. Install OpenPose Dependencies

```bash
cd src/depends/tf-pose-estimation
pip install -r requirements.txt
bash models/graph/cmu/download.sh
cd tf_pose/pafprocess
swig -python -c++ pafprocess.i && python3 setup.py build_ext --inplace
cd ../../../
python setup.py install
```

---

## 🧪 Quick Test

To test on the sample video:

```bash
python src/s5_test.py \
  --model_path model/trained_classifier.pickle \
  --data_type video \
  --data_path data_test/exercise.avi \
  --output_folder output
```

If you encounter errors related to OpenPose, run:

```bash
cd src/depends/tf-pose-estimation
python setup.py install
```

---

## 📚 Citation

If you use this code or find it helpful, please consider citing our work:

```
@inproceedings{jian2022drown,
  title={A Drowning Detection System Based on Human Pose Estimation and Deep Learning},
  author={Jian, Jia-Xian and others},
  booktitle={2022 International Symposium on Computer, Consumer and Control (IS3C)},
  year={2022},
  organization={IEEE}
}
```

---

## 🙏 Acknowledgements

This work is based on:
- [ildoonet/tf-pose-estimation](https://github.com/ildoonet/tf-pose-estimation)
- [philferriere/cocoapi](https://github.com/philferriere/cocoapi)
- [Chenge Yang, Felix Chen](https://github.com/felixchenfy/Realtime-Action-Recognition)

---

## 📬 Contact

If you have any questions or suggestions, feel free to open an issue or reach me at:  
**Jia-Xian Jian** – `allensa119625@gmail.com`
