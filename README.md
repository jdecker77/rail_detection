## Rail Detection
Object detection of pantograph heads to determine the horizontal and vertical  position of 6 points-of-interest (POI). 

#### Folder Structure
**notebooks**: Contains a jupyter notebook for each defined process and a folder of utility scripts.
* Data Collection
* Feature Engineering
* Model Development
* Model Implementation
* Model Evaluation
* utils

**data**: Contains files and folders for training and evaluating object detection models.
* video_files
* model_training
    * export_inference_graph.py
    * train.py 
    * annotations
    * images
        * train
        * test
    * training
        * ssd_mobilenet_v2_coco_2018_03_29
        * faster_rcnn_inception_v2_coco_2018_01_28
* model_implementation
    * pantograph_detection.py 
    * output 
    * trained_inference_graphs
    * utils

#### Processes
###### Data Collection
Create a labeled dataset from source video.

1. Save images from video to train/validation/test folders
2. Manually label images with 0 to 6 classes per image if POI is visible in frame
3. Save output XML file with image

###### Feature Engineering
Prepare dataset and required files for training model.

1. Create Train/Test/Validation CSVs from XML files
2. Create tensorflow records from Train/Validatin CSVs
3. Create label map for new classes
4. Create config file for model  

###### Model Development
Train and export model.

1. Train model
2. Export frozen inference model

###### Model Implementation
Inference on image/video from trained model. 

1. Set working file paths and hyperparameters
2. Initialize output CSV
3. load label map
4. Run detection

###### Model Evaluation
Evaluate model using test/prediction CSVs.

1. Load test and prediction CSVs
2. Compute pixel distance
3. Evaluate pixel distance
4. Draw corner points on image
