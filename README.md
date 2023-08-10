# Final-Project-Code

REQUIREMENTS:

The current configuration of the makeFile requires GPU, OPENCV.
Can be changed to run on CPU but would take a long time.
To change set:
  GPU=1 to 0
  CUDNN=1 to 0
  CUDNN_HALF=1 to 0

INSTALLATION:

Clone the entirety of the repository.
Download the MS COCO datasets into the coco folder
Download the custom dataset into the Experimental_Datasets folder (Some of the dataset is included but was capped at 1000 by github)

RUNNING:

Navigate to the this Final-Project-Code directory

Run: 

make

There will be warnings, but it should finish running

---------------------------------------------------------------------------------------------------------------

To run the code for the original learning rate on the MS COCO dataset run the command:

./darknet detector train cfg/coco.data cfg/yolov4-tiny.cfg yolov4-tiny.conv.29 -dont_show -map

To run the code for the higher learning rate on the MS COCO dataset run the command:

./darknet detector train cfg/coco.data cfg/yolov4-tiny_higherLR.cfg yolov4-tiny.conv.29 -dont_show -map

To run the code for the lower learning rate on the MS COCO dataset run the command:

./darknet detector train cfg/coco.data cfg/yolov4-tiny_lowerLR.cfg yolov4-tiny.conv.29 -dont_show -map

---------------------------------------------------------------------------------------------------------------

To run the code for the original learning rate on the custom dataset run the command:

./darknet detector train Experimental_Datasets/dog_cat.data cfg/yolov4-tiny_dog_cat.cfg yolov4-tiny.conv.29 -dont_show -map

To run the code for the higher learning rate on the custom dataset run the command:

./darknet detector train Experimental_Datasets/dog_cat.data cfg/yolov4-tiny_dog_cat_higherLR.cfg yolov4-tiny.conv.29 -dont_show -map

To run the code for the lower learning rate on the custom dataset run the command:

./darknet detector train Experimental_Datasets/dog_cat.data cfg/yolov4-tiny_dog_cat_lowerLR.cfg yolov4-tiny.conv.29 -dont_show -map

If you do not wish to produce the mAP curve remove “-map”

--------------------------------------------------------------------------------------------------------------

To detect objects in an image: 

Decide which weights file you wish to use from the backup folder. (Weight files are included from our training but will update as you train)

Download an image (or use dogs_cats.jpg) and keep track of location

Run the command:

./darknet detector test ".data file for dataset" "detect version of cfg file associated with dataset and learning rate" 
"weight file" "image"

A threshold for classification can be set using the flag -thresh 

An example is shown below:

./darknet detector test cfg/coco.data cfg/yolov4-tiny_higherLR_detect.cfg backup/yolov4-tiny_higherLR_best.weights dogs_cats.jpg

./darknet detector test cfg/coco.data cfg/yolov4-tiny_higherLR_detect.cfg backup/yolov4-tiny_higherLR_best.weights dogs_cats.jpg -thresh 0.3

