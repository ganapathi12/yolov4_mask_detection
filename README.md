# yolov4_mask_detection
<h1>you need to install darknet before trying out this program on your system.</h1>
This is project on mask detection, done by me and my teammate Balaji Dass for a mlh hackathon,Successfully  trained yolo model with custom datasets gathred from google and kaggle.
 as there are two classes we changed the following parameters in yolo config file:
○ First, we changed the variable max_batches=2000 x no_of_classes , in our case max_batches=4000.
○ The steps variable will be equal to 80-90% of max_batches , in our case steps=3200,3600.
○ The height and width parameters will be in multiples of 32 , here in the file we will change it to
  height=416 and width=416 .
○ Now, we will have to change the classes parameter at the respective line number 970, 1058, 1146 to 2 ,
  since we have only 2 classes (mask, without_mask).
○ Now similarly, update the filters parameter to filters=(classes + 5)*3 in the 3 convolutional layers before
  each yolo layer. In this case classes = 2 so, set the filters = 21 in the lines 963, 1051, 1139 .
  
then we created a .obj file with all the classes i.e, with mask and without mask.
now, importing images and annotations we created a folder inside build/darknet/x64/data/ with the name obj and pasted all the images and annotations inside this folder.
Now, we have created two files train.txt and test.txt, these files will contain the address to every train and test images as these will be needed while training. and all this files are created using a python script named as file_seperator.py inside the folder it basically adds path to every image and annotation.
we created a file obj.data in the build/darknet/x64/data folder.
then we edit yolo detector file in such a way that every 100 iterations, a file will be created in the build/darknet/x64/backup/ folder of the weights of the last 100 iterations. ( yolo-obj_last.weights).

<h1>command for training :darknet.exe train data/obj.data cfg/yolo-obj.cfg yolo4.conv.137</h1>
<h1>command for testing on test video: darknet.exe detector demo data/obj.data cfg/yolo-obj.cfg backup/yolo4_mask_final.weights masktest.mp4 -out_filename result.avi -ext_output
</h1>
 
