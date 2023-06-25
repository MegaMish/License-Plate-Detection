# License Plate Detection and Recognition

Police officers often need license plate numbers when patrolling the streets or looking for criminals. Street or security cameras may sometimes capture vehicles that could be part of a police investigation. It would be much easier for any law personell to identify important plate numbers if every license plate detected was displayed all in the same place. My retrained DetectNet model effectively detects license plates on an image, crops the image so that only the plate is showing, and displays the snapshot in a "Results" folder. AI such as the one I created can make investigations more efficient and keep our streets safer.

[Original video used in demo](https://imgur.com/XfBhMrt)

[Mercedes License Plate](https://imgur.com/291eQOs)

[Honda License Plate](https://imgur.com/mLaTNps)


## The Algorithm

Developed using the Jetson Nano, this project is a retrained detectnet model using a dataset of vietnamese cars and annotations for them, allowing for the license plate to be detected within the images. This model uses detectnet-snap.py to process a video and go through it, frame by frame. When it detects the "plate" class (class is determined in the labels.txt file) it outputs a cropped snapshot of that license plate in the "Result" folder. 

The following command is ran in the terminal to run detectnet-snap.py with my retrained model:

detectnet-snap.py --network=model/ssd-mobilenet.onnx --labels=model/labels.txt  --input-blob=input_0 --output-cvg=scores --output-bbox=boxes --overlay=box,labels,conf --threshold=0.4 --snapshots=Test/Result Test/merc-and-honda2.mp4

To run this model with a custon video, simply upload the .mp4 file to the "Test" folder and run the line above with the following input code: Test/[Your image here]

It is important to set the threshold to a lower value in order to identify some of the harder-to-read license plates that may be farther away or blurry. 

## Running this project

1. Install this modified dataset: [link](https://drive.google.com/drive/folders/1Rpylr9HywxWN69pFe_AZVq4U5LMpq42L?usp=sharing) . Refer to [1] for original, much larger dataset.
2. Move/copy the dataset into the following directory: 
3. Make sure to include any required libraries that need to be installed for your project to run.

[View a video demonstration here](https://youtu.be/UbkkXukGWiA)


### Works Cited

[1] Hai Quan Tran. 2021. Real-time-Auto-License-Plate-Recognition-with-Jetson-Nano. https://github.com/winter2897/Real-time-Auto-License-Plate-Recognition-with-Jetson-Nano/tree/main. (2023)

I used this repository to install its dataset of license plates images and their annotations. I slightly modified the dataset, making it smaller so that the training process took a reasonable amount of time. This allowed me to train my own custom model.
