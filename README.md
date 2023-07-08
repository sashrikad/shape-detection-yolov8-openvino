# Shape Detection using YOLOv8 and OpenVINO
I am making a project that needs to be able to detect different shapes. My mom is a pre-school teacher, so I had asked her one day what she teaches the kids in her class. She had mentioned she teaches different shapes and colors, and then me and my dad had thought of a way to help that could be used to teach the kids. My solution was to be able to detect different shapes (later we might detect color too) and later we might make an app to go along with it, so that when kids put down a shape that the app is telling them to, it will reward them with a badge.

## Roboflow
I needed to find a software that was easy to use and that could easily annotate the data that I can use. The solution is Roboflow! Roboflow is straight-forward and is easy to use for when you need to label your data. First I had taken some pictures of some basic 3D shapes so that I could create my dataset in [Roboflow](https://roboflow.com/). 

![](https://github.com/sashrikad/shape-detection-yolov8-openvino/assets/82982009/875c5be6-6f29-403c-9052-4c0e7b6bfdcc)

Once I had uploaded my images, I was able to annotate my different shapes for my training model. When the magic of annotation is done, Roboflow gives you a snippet of code that will be used in training your custom model.

## Train with YOLOv8
In Roboflow, there should be something called "[Model Library](https://roboflow.com/models)" on the side which will bring you to different computer vision models that you can be able to use to get started. I had used the colab notebook for YOLOv8 so that I can be able to immediately start training with my custom dataset.

![](https://github.com/sashrikad/shape-detection-yolov8-openvino/assets/82982009/ae2dbc1a-de4a-45d5-8cd9-c1bc39dcd093)

I had tried to use their pre-trained COCO Model using one of the images that I took, it did not work since their model is trained on "everyday objects", and I don't think 3D printed shapes go under the category of "everyday objects".

![](https://github.com/sashrikad/shape-detection-yolov8-openvino/assets/82982009/7ed8197e-8342-402f-9d35-6e041f3ef705)

Since the model that I need is on detecting different shapes, I need to create a custom model to get what I need.

Remember back when I was in Roboflow and after annotating my data, I had gotten a code snippet? This is the moment you need it! In order to get the custom model, I needed to paste the snippet into the notebook in order to get started.

![](https://github.com/sashrikad/shape-detection-yolov8-openvino/assets/82982009/bc2957ed-bc42-4039-8a1b-1bfe296c299f)

Now that I have my custom model created, I am going to use the same image from testing the COCO Model, and use it to see how well my new model is doing.

![](https://github.com/sashrikad/shape-detection-yolov8-openvino/assets/82982009/73dac8aa-9bdf-4c52-8f52-8f84accc16e0)

Ahhh :) Much better! The new model is correctly able to detect what the shapes are. The confidence level is also pretty high too, so the model is really sure of the shapes.

## Converting to OpenVINO (hardest thing to find in my opinion)
In order to convert the model to OpenVINO, I had a LOT of digging to do. I needed a lot of help from my dad to get through this last part. In the end, I found [this Jupyter notebook](https://colab.research.google.com/github/openvinotoolkit/openvino_notebooks/blob/main/notebooks/230-yolov8-optimization/230-yolov8-optimization.ipynb) while searching, and had everything we needed to convert the model to OpenVINO.

## What we plan on working on after
I am planning on actually being able to test this out in real-time with a webcam, so we will need to be able to run on the computer.

I am also planning on being able to detect different color as well as the shapes. If you noticed in the images of my testing, the shapes were also different colors. So when the app will ask the kids to put a shape under the camera, it may also ask for the certain color.

Then lastly, I am planning on making an app for this solution. It has been mention multiple times, but the app will be able to have the kids show different shapes of different color and will reward them if they did what they were asked correctly.
