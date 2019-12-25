you can run it from terminal by type: # python train.py --dataset dataset --model pokedex.model --labelbin lb.pickle


# VGG-CNN-KERAS
Keras and Convolutional Neural Networks
In last week’s blog post we learned how we can quickly build a deep learning image dataset — we used the procedure and code covered in the post to gather, download, and organize our images on disk.

Now that we have our images downloaded and organized, the next step is to train a Convolutional Neural Network (CNN) on top of the data.

I’ll be showing you how to train your CNN in today’s post using Keras and deep learning. The final part of this series, releasing next week, will demonstrate how you can take your trained Keras model and deploy it to a smartphone (in particular, iPhone) with only a few lines of code.

The end goal of this series is to help you build a fully functional deep learning app — use this series as an inspiration and starting point to help you build your own deep learning applications.

Let’s go ahead and get started training a CNN with Keras and deep learning.
Our deep learning dataset consists of 1,191 images of Pokemon, (animal-like creatures that exist in the world of Pokemon, the popular TV show, video game, and trading card series).

Our goal is to train a Convolutional Neural Network using Keras and deep learning to recognize and classify each of these Pokemon.

The Pokemon we will be recognizing include:

Bulbasaur (234 images)
Charmander (238 images)
Squirtle (223 images)
Pikachu (234 images)
Mewtwo (239 images)
A montage of the training images for each class can be seen in Figure 1 above.

As you can see, our training images include a mix of:

Still frames from the TV show and movies
Trading cards
Action figures
Toys and plushes
Drawings and artistic renderings from fans
This diverse mix of training images will allow our CNN to recognize our five Pokemon classes across a range of images — and as we’ll see, we’ll be able to obtain 97%+ classification accuracy!

The Convolutional Neural Network and Keras project structure
Today’s project has several moving parts — to help us wrap our head around the project, let’s start by reviewing our directory structure for the project:

Keras and Convolutional Neural Networks (CNNs)Shell
├── dataset
│   ├── bulbasaur [234 entries]
│   ├── charmander [238 entries]
│   ├── mewtwo [239 entries]
│   ├── pikachu [234 entries]
│   └── squirtle [223 entries]
├── examples [6 entries]
├── pyimagesearch
│   ├── __init__.py
│   └── smallervggnet.py
├── plot.png
├── lb.pickle
├── pokedex.model
├── classify.py
└── train.py

There are 3 directories:

dataset : Contains the five classes, each class is its own respective subdirectory to make parsing class labels easy.
examples : Contains images we’ll be using to test our CNN.
The pyimagesearch  module: Contains our SmallerVGGNet  model class (which we’ll be implementing later in this post).
And 5 files in the root:

plot.png : Our training/testing accuracy and loss plot which is generated after the training script is ran.
lb.pickle : Our LabelBinarizer  serialized object file — this contains a class index to class name lookup mechamisn.
pokedex.model : This is our serialized Keras Convolutional Neural Network model file (i.e., the “weights file”).
train.py : We will use this script to train our Keras CNN, plot the accuracy/loss, and then serialize the CNN and label binarizer to disk.
classify.py : Our testing script.

