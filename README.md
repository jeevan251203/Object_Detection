# Object_Detection

This guide provides step-by-step instructions to train a YOLOv8 model on a custom dataset.

## Prerequisites

- Python 3.9+
- PyTorch
- YOLOv8 library
- CUDA (for GPU support)

## Installation

1. **Clone the YOLOv8 repository:**
    ```bash
    git clone https://github.com/ultralytics/yolov8
    ```

2. **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

## Dataset Preparation

1. **Organize your dataset:**
    - Ensure your dataset is in the YOLO format.
    - Create directories for images and labels:
        ```plaintext
        dataset/
        ├── images/
        │   ├── train/
        │   ├── val/
        ├── labels/
        │   ├── train/
        │   ├── val/
        ```

2. **Annotate your images:**
    - Use tools like https://www.cvat.ai or LabelImg to annotate your images and save the annotations in YOLO format. (cvat.ai is recommonded)

## Configuration

1. **Create a configuration file:**
    - Open `train.yaml` and customize it for your dataset:
        ```yaml
        train: dataset/images/train
        val: dataset/images/val
        nc: 5  # number of classes
        names: ['class1', 'class2', ...]  # class names
        ```

## Training

1. **Initialize the YOLOv8 model:**
    ```bash
    yolo detect train data=train.yaml model=yolov8n.pt epochs=100 imgsz=640 device=0
    ```

## Inference

1. **Run inference on new images:**
    ```bash
    yolo predict model="path/to/your/trained/pt_file" source="path/to/your/image_or_video"
    ```

