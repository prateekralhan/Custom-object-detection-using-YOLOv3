# Custom-object-detection-using-YOLOv3 :wink:

## Installation:
Run the command: ***pip install -r requirements.txt***
This will install all the necessary dependencies.

## Usage:
1. Clone this repository in your desired directory.

### Data preparation:
As a part of making a custom object detector, I thought of making a racoon detector inspired from [Dat Tran](https://github.com/datitran/raccoon_dataset). 
Instead of manually collecting images of raccoons from Google, I decided to go forward with the **Images** Dat Tran collected to create his raccoon dataset for his object 
detection model.
1. Download the **images** folder from the repo. ***(only the images -> we will annotate them and create the final version ourselves.)***
2. Clone the [labelImg](https://github.com/tzutalin/labelImg) repo and navigate to the labelImg directory. 
***(LabelImg is a graphical image annotation tool which we will use here to label the images.)***
3. Run: **python labelImg.py**, the GUI will pop up. Refer to the source repo for getting an understanding how to annotate the images using this tool.
#### IMPORTANT: Ensure that you are using the settings for YOLO. If pascalVOC is written, then click on it and you will see YOLO.

![labelImg_pic](https://user-images.githubusercontent.com/29462447/90323285-f0f8d700-df7c-11ea-914d-7df7912d6fc7.png)

4. Create a zip file of the **images** folder -> ***images.zip***
5. Create a folder in your Google Drive account with the name **yolov3** and upload ***images.zip*** there.

### Training:
1. Open the notebook ***YoloV3_training_racoon.ipynb*** in **Google Colab**. We will be using the Colab's Tesla T4 GPUs powered with 16 GB RAM for training the heavy YOLOv3 model.
2. Execute the contents of the notebook and start training your model. Usually it takes 3 -6 hours to train the model. You can interrupt the training in between as well in case 
you are satisfied with the loss values. I stopped training my model after 4 hours with average loss = 0.00253. ***(seemed good enough to me :smile:)*** 
3. After completion of the training, you will find **yolov3_training_last.weights** created in the **yolov3** folder in your Google Drive account. You might find that other files 
are also saved on your drive, **yolov3_training__1000.weights**, **yolov3_training_2000.weights** and so on because the darknet makes a backup of the model each 1000 iterations.
4. Download **yolov3_training_last.weights** and place it in the same directory where you cloned this repo.

### Testing:
1. Run the command: *** python yolo_object_detection.py*** and see the results.


### NOTE!!
* You need to change the class name from ***"racoon"*** to any other custom object in case you wish to use this for detecting that object in your images. Ensure you make this 
change in both the scripts : 

***YoloV3_training_racoon.ipynb*** 
![racoon_label](https://user-images.githubusercontent.com/29462447/90323283-ef2f1380-df7c-11ea-9204-85d694e4d3a6.png)

***yolo_object_detection.py***
![racoon_label_2](https://user-images.githubusercontent.com/29462447/90323284-f0604080-df7c-11ea-9faa-f3cefe91a3dc.png)
