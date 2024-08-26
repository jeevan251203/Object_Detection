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
    cd yolov8
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
    - Open `yolov8.yaml` and customize it for your dataset:
        ```yaml
        train: dataset/images/train
        val: dataset/images/val
        nc: 80  # number of classes
        names: ['class1', 'class2', ...]  # class names
        ```

## Training

1. **Initialize the YOLOv8 model:**
    ```bash
    python train.py --data yolov8.yaml --cfg yolov8.yaml --weights yolov8.pt --epochs 100
    ```

2. **Monitor training:**
    - Use tools like TensorBoard to monitor the training process:
        ```bash
        tensorboard --logdir=runs
        ```

## Evaluation

1. **Evaluate the model:**
    ```bash
    python val.py --data yolov8.yaml --weights runs/train/exp/weights/best.pt
    ```

## Inference

1. **Run inference on new images:**
    ```bash
    python detect.py --weights runs/train/exp/weights/best.pt --source path/to/your/images
    ```

## Conclusion

By following these steps, you can train a YOLOv8 model on your custom dataset. For more details, refer to the YOLOv8 documentation.

## FAQ

- **How do I annotate my dataset?**
  Use tools like LabelImg or Roboflow to annotate your images in YOLO format.

- **How do I monitor training?**
  Use TensorBoard to visualize training metrics.

---

Feel free to customize this guide based on your specific requirements and dataset. Happy training!
