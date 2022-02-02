# Automated-Car-Detection-and-Counting-Model

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/output-video-as-gif.gif

Whether you are counting cars on a road or products on a conveyer belt, there are many use cases for computer vision with video. With video as input, automatic labeling can be used to create a better classifier with less manual effort. This code pattern shows you how to create and use a classifier to identify objects in motion and then track the objects and count them as they enter designated regions of interest.

In this code pattern, we will create a video car counter using Maximo Visual Inspection, OpenCV and a Jupyter Notebook. We'll use a little manual labeling and a lot of automatic labeling to train an object classifier to recognize cars on a highway. We'll load another car video into a Jupyter Notebook where we'll process the individual frames and annotate the video.

We'll use our deployed model for inference to detect cars on a sample of the frames at a regular interval. We'll use OpenCV to track the cars from frame to frame in between inference. In addition to counting the cars as they are detected, we'll also count them as they cross a "finish line" for each lane and show cars per second.

Credit goes to Michael Hollinger for his initial notebook counting objects with PowerAI Vision.

When the reader has completed this code pattern, they will understand how to:

Use automatic labeling to create an object detection classifier from a video
Process frames of a video using a Jupyter Notebook, OpenCV, and Maximo Visual Inspection (formerly known as PowerAI Vision)
Detect objects in video frames with Maximo Visual Inspection
Track objects from frame to frame with OpenCV
Count objects in motion as they enter a region of interest
Annotate a video with bounding boxes, labels and statistics
architecture

![image](https://user-images.githubusercontent.com/96236642/152168133-de459f93-62b0-479a-8c39-1503b10b6fff.png)


Flow

Upload a video using the Maximo Visual Inspection web UI.
Use automatic labeling and train a model.
Deploy the model to create a Maximo Visual Inspection (formerly known as PowerAI Vision) inference API.
Use a Jupyter Notebook to detect, track, and count cars in a video.

Included components

https://www.ibm.com/products/ibm-maximo-visual-inspection: Rapidly unleash the power of computer vision for inspection automation without deep learning expertise.
https://jupyter.org/: An open source web application that allows you to create and share documents that contain live code, equations, visualizations, and explanatory text.
https://opencv.org/: Open source computer vision library.

Featured technologies

Artificial Intelligence: Artificial intelligence can be applied to disparate solution spaces to deliver disruptive technologies.
Cloud: Accessing computer and information technology resources through the Internet.
Data Science: Systems and scientific methods to analyze structured and unstructured data in order to extract knowledge and insights.
Mobile: Systems of engagement are increasingly using mobile technology as the platform for delivery.
Python: Python is a programming language that lets you work more quickly and integrate your systems more effectively.


Watch the Video
https://youtu.be/19vaot75JCY

Prerequisites
PowerAI Vision
This code pattern requires Maximo Visual Inspection (formerly known as PowerAI Vision).

Go here to learn more about trial access (Scroll down to the Give it a try section).

This code pattern has been updated with screenshots and instructions for PowerAI Vision 1.1.3, but the instructions are the same for IBM Maximo Visual Insights.

Jupyter Notebooks
The code included in this code pattern runs in a Jupyter Notebook. The notebook itself does not require Maximo Visual Inspection or Power Systems (only access to the deployed API). To run the Jupyter Notebook locally, install it using Anaconda. The installation instructions are here.

Steps
Create a dataset in Maximo Visual Inspection
Train and deploy
Automatic labeling
Train and deploy
Run the notebook
Create the annotated video
Hint: If you need a shortcut, you can import the dataset from data/examples/dataset_auto_labeled.zip, train and deploy that dataset, and then run the notebook (but you'll get more out of this if you go through all the steps).

1. Create a dataset in Maximo Visual Inspection
To create a new dataset for object detection training from a video, use the Maximo Visual Inspection UI and start with a small manually annotated dataset (we'll expand on it with automatic labeling later).

Download the video to use to train the dataset from here. Use the Download button to create training_video.mp4 in your browser's Downloads folder.

Click on the Data Sets tab.

Click on the Create new data set card.

Provide a data set name.

Click the Create button.

Click on the newly created data set card.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/video_data_platform_dataset.png

Click on Import files and open your downloaded training_video.mp4 file.

Select the new uncategorized card and click the Label objects button.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/manage_videos.png

Click on Auto capture, set the capture interval to 5 seconds, and click the Auto capture button.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/add_label.png


Tips! Click on How to label for more detailed labeling tips.

Create a new object label for the data set by clicking + Add new by the Objects list. For example, add a car object label.

Label the objects in the frames by following these steps.

Select a frame in the carousel.
Select the correct object label.
Choose Box from the bottom left.
Draw a box around each car in each captured frame.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/manual_tagging.png

2. Train and deploy
Train the model
Go back to the data set page and click Train model.
Select Object detection.
Review the Advanced settings. You can train faster (with less accuracy) by reducing the max iterations.
Click Train.
Deploy the model
Go to the Models tab.
Click the Deploy model button.
Use the Deployed Models tab to see the status.
When the status is ready, click on the deployed model to get the API endpoint.


3. Automatic labeling
We use the first deployed model that you trained with manually annotated frames and use inference to automatically label more cars in your training video.

Go back to the data set.
Select your video card.
Click the Label objects button.
Click on Auto label.
Enter 1 for Capture Interval (Seconds).
Select your deployed model.
Click the Auto label button.
Frames are captured at the specified interval and labels are added by using the specified trained model. By default, the automatically added labels are light red. After processing, you can manually add labels to the frames that have been auto labeled and you can manipulate (move, resize) the labels that were automatically generated. If a frame with automatically generated labels is edited, all labels on the frame are converted to manual labels.

4. Train and deploy
Repeat the above train and deploy process with the newest dataset which was enhanced with automatic labeling.

Train model
Deploy model
This dataset has many more frames and labeled objects. It will create a much more accurate model.

5. Run the notebook
The code included in this code pattern runs in a Jupyter Notebook. After you configure the URL of your deployed model in the notebook, you can just run it, read it, and watch the results.

Start your Jupyter Notebooks. Starting in your powerai-counting-cars cloned repo directory will help you find the notebook and the output as described below. Jupyter Notebooks will open in your browser.

cd powerai-counting-cars
jupyter notebook
Navigate to the notebooks directory and open the notebook file named counting_cars.ipynb by clicking on it.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/open_notebook.png

Edit the cell below Required setup! to replace the URL with the API endpoint of your deployed model. Use the copy button to capture the whole URL.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/required_setup.png

Use the drop-down menu Cell > Run All to run the notebook, or run the cells one at a time top-down using the play button.

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/run_all.png

As the cells run, watch the output for results or errors. A running cell will have a label like In [*]. A completed cell will have a run sequence number instead of the asterisk.

The Test the API on a single frame cell will demonstrate that you have correctly deployed your inference API. It should output JSON that includes classified cars. A portion of the output would look something like this:

  "classified": [
    {
      "confidence": 0.9997443556785583,
      "ymax": 370,
      "label": "car",
      "xmax": 516,
      "xmin": 365,
      "ymin": 240
    }
  ]
The Get object detection results for sampled frames cell runs inference on a sampling of the video frames. The output will show a progress counter like this:

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/inference_progress.png

The Inference, tracking, and annotation cell processes every frame and has a similar progress counter. You can also preview the annotated frames as they are created in the output directory.

The Play the annotated frames in the notebook cell displays the annotated frames in a loop to demonstrate the new video after they are all created. The notebook animation is usually slower than the video.

6. Create the annotated video
You can create an MP4 video from the annotated frames if you have a working installation of ffmpeg. The command is commented out as the last cell of the notebook. You can run it from there, or use the script in tools/create_video.sh. The script takes the output directory (with the annotated frames) as an argument like this:

cd powerai-counting-cars
./tools/create_video.sh notebooks/output
Note: There is also a tool to create a gif from the video. We used that to show the sample output below.

Sample output
As the notebook cells run, check for errors and watch the progress indicators. After the video has been annotated, the frames will play (like a video) in the notebook. The notebook playback is usually slow. If you used ffmpeg to create an annotated video, you can play it back at full speed.


Example compressed and converted to gif:

https://github.com/chaitanya9899/AI_car_counting/blob/master/doc/source/images/output-video-as-gif.gif

Troubleshooting
Stopped adding cars.

If you are using a trial environment, your model deployment may be limited to 1 hour. Simply deploy the model again and run the notebook over (or from where the errors started). Using cached results allows the notebook to continue where it left off.
