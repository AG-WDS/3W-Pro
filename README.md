# 3W-pro

Dataset and Code for Winter Wheat Weed Detection and Segmentation

# Dataset

The 3W-Pro dataset is available at `https://drive.google.com/file/d/1-CyMzppgiKgyzh0METEdm-5A4CnP383y/view?usp=sharing`
Put datasets into data/..., for example, 3W-Pro dataset should be put in

    ./data/{coco}
The 3W-Pro dataset has **9 categories**: 
*Calystegia hederacea*, *Capsella bursa*, *Chenopodium album*, *Cirsium arvense*, *Descurainia sophia*, 

*Erysimum cheiranthoides*, *Galium aparine*, *Humulus scandens*, and winter_wheat.
# Install

Pip install the Ultralytics package including all requirements in a Python>=3.8 environment with PyTorch>=1.8.

    pip install ultralytics
 pip install the mamba dependencies
 
    pip install causal-conv1d>=1.1.1
    pip install mamba-ssm>=1.1.2

# Usage
I had made some changes in :

    ./ultralytics/nn/modules/block.py      # Efficient mamba attention's path
    ./ultralytics/nn/tasks.py            # use the Efficient mamba attention
    ./ultralytics/cfg/models/v10/yolov10l_seg_mamba.yaml      # model's path
    ./ultralytics/cfg/datasets/coco_wheat.yaml      # dataset's path
    
    

## Train

YOLO may be used directly in the Command Line Interface (CLI) with a `yolo` command:

    yolo train data="./ultralytics/cfg/datasets/coco_wheat.yaml" model="./ultralytics/cfg/models/v10/yolov10l_seg_mamba.yaml" epochs=100 imgsz=640
    
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
# Citations
    @article{zhuolin2024,
        tilte={Winter wheat weed detection based on deep learning models},
        author={Zhuolin Li, Dashuai Wang, Qing Yan, Minghu Zhao, Xiaohu Wu, Xiaoguang Liu},
        journal={Computers and Electronics in Agriculture},
        doi={https://doi.org/10.1016/j.compag.2024.109448},
        volume={227},
        pages={109448},
        year={2024}
    }  
     
