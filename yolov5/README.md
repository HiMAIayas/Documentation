<div align="center">
  <h2>YOLOv5 initialization</h2>
</div>

Click here for [YOLOv5 repo](https://github.com/ultralytics/yolov5) 

<details open>
<summary>Install</summary>
  
**In Terminal**, clone github repo and installing related packages with [**Python>=3.8.0**](https://www.python.org/) environment.
```bash
git clone https://github.com/ultralytics/yolov5  # clone github repo
cd yolov5                                        # to change working directory to yolov5
pip install -r requirements.txt                  # install all required packages
```
<img  src="https://github.com/HiMAIayas/Documentation/blob/main/yolov5/assets/terminal.png">

Copy **coco-demo.yaml** to yolov5/data and **demo_db** (folder of dataset) to yolov5

<div align="center">
 <img style="width:200px;" src="https://github.com/HiMAIayas/Documentation/blob/main/yolov5/assets/yolov5_files.png">
</div>
<br>

**In file "coco-demo.yaml"**, change path to the following path (relative path for training images and its value)
 
```bash
path: 'demo_db' 
train: 'train/images'  
val: 'val/images'  
```

</details>


<details open>
<summary>Training</summary>

To train **object detection model** with batch size of 16 for 4 epochs
```bash
python train.py --img 640 --batch 16 --epochs 4 --data coco-demo.yaml --weights yolov5s.pt --cache
```
</details>

<details open>
  <summary>Testing</summary>
Copy your model (.pt) to yolov5.
  
Or replace "best.pt" with your .pt model path on the command line.
  

To test model on test dataset
```bash
python detect.py --weights best.pt --img 640 --conf 0.1 --source demo_db/test/images --iou-thres 0.5 --save-txt
```

To test model on train dataset
```bash
python detect.py --weights best.pt --img 640 --conf 0.1 --source demo_db/train/images --iou-thres 0.5 --save-txt
```
</details>


