# 3W-pro

Dataset and Code for Winter Wheat Weed Detection and Segmentation

# Dataset

The 3W dataset is available at `https://drive.google.com/file/d/1-CyMzppgiKgyzh0METEdm-5A4CnP383y/view?usp=sharing`
Put datasets into data/..., for example, 3W-Pro dataset should be put in

    ./data/{coco}

# Install

Pip install the Ultralytics package including all requirements in a Python>=3.8 environment with PyTorch>=1.8.

    pip install ultralytics
 pip install the mamba dependencies
 
    pip install causal-conv1d>=1.1.1
    pip install mamba-ssm>=1.1.2

# Usage
## Train

YOLO may be used directly in the Command Line Interface (CLI) with a `yolo` command:

    yolo train data="./ultralytics-main/ultralytics/cfg/datasets/coco_wheat.yaml" model="/home/music/Downloads/ultralytics-main/ultralytics/cfg/models/v10/yolov10l_seg_mamba.yaml" epochs=100 imgsz=640
    
## val

    yolo val  model=path/to/best.pt
    
## Predict
Run inference on an image opened with Python Imaging Library (PIL).

    from  PIL  import  Image  
    from  ultralytics  import  YOLO
    
    # Load a pretrained YOLO11n model 
    model  =  YOLO("yolo11n.pt")
     
    # Open an image using PIL  
    source  =  Image.open("path/to/wheat.jpg")
      
    # Run inference on the source  
    results  =  model(source)  # list of Results objects 
