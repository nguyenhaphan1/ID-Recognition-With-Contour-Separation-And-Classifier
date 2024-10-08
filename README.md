# ID-Recognition-With-Contour-Separation-And-Classifier
This is another approach to handle ID Recognition. This method is combined of extracting each digit from the ID image separately and using a classifier to classify the digit

**Pipeline**

<img src="https://github.com/nguyenhaphan1/ID-Recognition-With-Contour-Separation-And-Classifier/blob/main/pipeline.png" alt="mjsynth" width="800" height="200">

Firstly, the image is converted to Gray-scaled image, then applying AdapiveThreshold to separate the digits with background. 

| Image | Binary Image|
| ------------- | ------------- |
| <img src="https://github.com/nguyenhaphan1/ID-Recognition-With-Contour-Separation-And-Classifier/blob/main/images/id_15.jpg" alt="mjsynth" width="118" height="31"> | <img src="https://github.com/nguyenhaphan1/ID-Recognition-With-Contour-Separation-And-Classifier/blob/main/images/binary.png" alt="mjsynth" width="118" height="31"> |

After that, finding contour of the images, draw bounding box for each contour (each bbox represent the image of a single digit. Using attribute such as width, height and area to split digits sticking together into single digit. 

Example of digits sticked together:

| Type  | Image |
| ------------- | ------------- |
| 3 digits sticked  | <img src="https://github.com/nguyenhaphan1/ID-Recognition-With-Contour-Separation-And-Classifier/blob/main/images/3stickimage.png" alt="mjsynth" width="26" height="20">  |
| 5 digits sticked  | <img src="https://github.com/nguyenhaphan1/ID-Recognition-With-Contour-Separation-And-Classifier/blob/main/images/5stickimage.png" alt="mjsynth" width="45" height="20">  |

Secondly, reference the offset to the RGB image and consecutively pass each single digit through a classifier to classify it into a digit from 0-9.

The classifier is fine-tuned on MobileNetV2 with custom dataset.

| Image | Result|
| ------------- | ------------- |
| <img src="https://github.com/nguyenhaphan1/ID-Recognition-With-Contour-Separation-And-Classifier/blob/main/images/id_15.jpg" alt="mjsynth" width="118" height="31"> | 030093009624 |
