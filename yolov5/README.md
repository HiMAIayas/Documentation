<div align="center">
  <h2>YOLOv5 initialization</h2>
</div>

Click here for [YOLOv5 repo](https://github.com/ultralytics/yolov5) 

<details open>
<summary><h2>Installation</h2></summary>
  
**In Terminal**, clone github repo and installing related packages with [**Python>=3.8.0**](https://www.python.org/) environment.
```bash
git clone https://github.com/ultralytics/yolov5  # clone github repo
cd yolov5                                        # to change working directory to yolov5
pip install -r requirements.txt                  # install all required packages
```
<img  src="https://github.com/HiMAIayas/Documentation/blob/main/yolov5/assets/terminal.png"><br>

Copy **coco-demo.yaml** to yolov5/data and **demo_db** (folder of dataset) to yolov5

<div align="center">
 <img style="width:200px;" src="https://github.com/HiMAIayas/Documentation/blob/main/yolov5/assets/yolov5_files.png">
</div><br>

**In file "coco-demo.yaml"**, change path to the following path (relative path for training images and its value)
 
```bash
path: 'demo_db' 
train: 'train/images'  
val: 'val/images'  
```

### In case of things not working properly
- It's not working properly (ex. program stopped running after initialyzing dataset)
  <img style="width:75%;" src="https://github.com/HiMAIayas/Documentation/blob/main/yolov5/assets/protobuferror.png"><br><br>
  **[Solution]** run the command in terminal and check if the installed modules satisfy the [requirements.txt](https://github.com/ultralytics/yolov5/blob/master/requirements.txt)
  ```bash
  pip list
  ```
  In this example case, it's the protobuf module. Reinstall the module with the appropriate version
  ```bash
  pip uninstall protobuf          #pip uninstall <module_name>
  pip install protobuf==3.20.1    #pip install <module_name>==<version>
  ```

</details>



<details open>
<summary><h2>Training</h2></summary>
  
**Make sure that you are in working directory "yolov5"**

<br>

To train **object detection model** with batch size of 16 for 4 epochs

```bash
python train.py --img 640 --batch 16 --epochs 4 --data coco-demo.yaml --weights yolov5s.pt --cache
```
</details>

<details open>
  <summary><h2>Testing</h2></summary>
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


