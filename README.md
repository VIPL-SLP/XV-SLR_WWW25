# Basic Information
This is the fusion stage training and inference of the VIPL-SLP submission for [CV-ISLR challenge](https://uq-cvlab.github.io/MM-WLAuslan-Dataset/docs/en/www).

# Data Preparation
Download the estimated keypoints, extracted RGB and depth features from Google Drive, and put them under the root of project:
- [estimated keypoints](https://drive.google.com/file/d/1S-eHeJUl9FIW2hVxG5x2zsT7zrRZANPo/view?usp=sharing)
- [extracted RGB features](https://drive.google.com/file/d/1lkLmcapzl6zgpO0QkNM5PTDOgOHNez3z/view?usp=sharing)
- [extracted depth features](https://drive.google.com/file/d/1PoDK9qucEUZ7twGorCp6xnDL_PH-lJ5Z/view?usp=sharing)

Download the processed information dicts from [Google Drive](https://drive.google.com/drive/folders/1rDUcOBM2KMqjqAyz3uv-bPEo6QNBpP0y?usp=sharing), and put them in the ./data

Feel free to contact us if the link is invalid.

# Environment Configuration
```bash
conda env create -f environment.yml
```

# Evaluation
Download the pretrained weights from [Google Drive](https://drive.google.com/file/d/1WsKK9Ct9cGgv3vh4zI185Hd29KJAleWw/view?usp=drive_link) and put them in the ./weights


## RGB Track
- For RGB data:
```python
python main.py --config ./configs/test_single_rgb.yaml --load-weights weights/single_rgb.pt
```
Expected performance: Average Topk-1 : 34.55%

- For skeleton data:
```python
python main.py --config ./configs/test_single_skeleton.yaml --load-weights weights/sk_phase2.pt
```
Expected performance: Average Topk-1 : 46.00%

- For RGB+Skeleton data:
```python
python main.py --config ./configs/test_fusion_rgbd.yaml --load-weights ./weights/fusion_rgbd.pt
```
Expected performance: Average Topk-1 : 56.87%

## RGB-D Track
- For Depth data:
```python
python main.py --config ./configs/test_single_depth.yaml --load-weights ./weights/single_depth.pt
```
Expected performance: Average Topk-1 : 28.84%

- For RGB+Skeleton+Depth data:
```python
python main.py --config ./configs/test_fusion_rgbd.yaml --load-weights ./weights/fusion_rgbd.pt
```
Expected performance: Average Topk-1 : 57.98%

# Training
## RGB Track
```python
python main.py --config ./configs/train_fusion_rgb.yaml
```

## RGB-D Track
```python
python main.py --config ./configs/train_fusion_rgbd.yaml
```
