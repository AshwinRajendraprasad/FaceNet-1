# FaceNet
Face Recognition 

## Library Used:
1. <b>Dlib</b> : To detect face and prepare face images for training
2. <b>imutils</b> : for utility purpose
3. <b>cv2</b> : camera and image read & write, image bluring
4. <b>tensorflow</b> : prepare and training network for face recognition

## How to Use this Lib
### 1. Have your all training images in like below folder structure
   - base_dir <facenet>
      - images
        - data
          - class 1
              - image 1
              - image 2
          - class 2
              - image 1
              - image 2
  
  #### Note: 
  1. All the above example as folder named as class 1 and class 2 folders, defines the class label for each training data
  2. Images could be a single faces of 180x180 size or could be a large image i.e. 600x1200 having single or multiple face
 
 ### 2. Edit <face_recognition.config> file for your training
1. First of all, if you have large image then your need to have pre processing to identify the faces in the image and prepare the class for training, as you have already prepared your class label as folder name and copied all class specific images inside.
 then update <b>"pre_processing_required":true</b> option to true so that it will prepare the training face images of 180x180 or you have change the side of the image you have to prepare in 
 
 <code>
   "image" :{ 
    "resize": {
      "width":180,
      "height":180,
      "required": false
    },
    "width":180,
    "height":180
  }
  </code>
  
2. if you have already have face images of 180x180 or 28x28 or 36x36 or 200x200 for training then you can make the option
  <b><code>"pre_processing_required":false</code></b>
  
3.  Change the following properties for folder training details
</br>"training":{ </br>
    "base_directory":"/FaceNet/",   ### Base Folder of Api </br>
    "image_directory" : "images/",  ### Image folder in side base_directory </br>
    "training_data_folder" : "images/train/", </br>
    "testing_data_folder" : "images/test/",</br>
    "structure_of_data": "folder",</br>
    "random_shuffle":true,  ### if you want to have random shuffle of data for training and testing</br>
    "training_size_percentage":95, ### splitting of data into training 95% and testing 5%</br>
    "training_steps":100, ### number of epoch for training </br>
    "batch_size":24, ### Batch side for training</br>
    "learning_rate":0.001 ### initial learning rate</br>
  },</br>

  
 4. Then change network configuration 
</br>
  "network_config":{</br>
    "tensor_name":"auto", ### auto generated tensor name</br>
    "input_size":"auto", ### input layer side auto decided as per the image structrue mentioned as above 180x180</br>
    "output_size":"auto", ### output size will be decided on number of class folders are there in image/data directory as mentioned above</br>
    "network":[...] </br>### Heart of the network lies here. Check the sample configuration file and check the network configuration and play with it more as you understand </br>

### Run <train.py>

### Outcome
As I have trainined with 460 faces of 28 classes, i have got 68% of accuracy 
    


