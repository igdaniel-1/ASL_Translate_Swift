# ASL_Translate_Swift
A Sign Language translator app built in Swift

### Abstract

The focus of this project is the design of an iOS Application that translates American Sign Language (ASL) hand signs into English text. 
This is a relevant research field as there is no existing, publicly-available
technology that translates ASL to English. With this app, deaf or hard-of-hearing people who communicate using ASL will be able to 
communicate with non-ASL-speakers. This is facilitated using an interface which detects ASL signs using the user's camera. This translation is 
performed by a Hand Classification Machine Learning Model which maps detected hands to a prediction of their intended sign. 
The translation cycle is completed as the resultant sign is then displayed to the user. 

For a video demo of the application, click [here](https://drive.google.com/file/d/10kOkRgcT26_jOkyaPyjwuHE8A-DUPnL7/view).
Plain text link: https://drive.google.com/file/d/10kOkRgcT26_jOkyaPyjwuHE8A-DUPnL7/view .

### Introduction
Currently, there is no readily available, free American Sign Language (ASL) translation service or technology. 
When you Google “Sign language translator to English," the first page of results has no relevance. Among the advertisements for sign 
language dictionaries are the sparse recommendation for English to ASL translators; which, upon further investigation, merely translate 
English words letter by letter into ASL letters which spell that word. 

The issue with these translators is that they don't take into account the literacy of the ASL user. To further elaborate, an ASL user who 
is deaf or hard-of-hearing (HoH) has a very high probability of being literate. Given the expected literacy of the ASL-user, an app to 
translate English text into pictures of ASL hands would not be useful to a deaf/HoH person. The non-ASL-user could type in the phrase they 
intend to communicate, and show the ASL-user the written word on the screen instead of the string of ASL letter hand signs. 

With this in mind, an English-to-ASL translation service would not provide any significant ease to the communication between deaf/HoH and 
hearing people. I've created a service that inverts that path, instead translating ASL to English. This allows ASL users to 'sign' into 
the app so that a non-ASL-user can understand their signs without any prior ASL knowledge. 

This fall, I refactored my VR Visualizer into a mobile application. In order to reach as many users as possible, the required hardware to 
run my service needed to be minimal. Because of this, I chose to create an iOS application that could fully run on a mobile device without 
external hardware, or even an internet connection. 

This was made possible through the usage of Apple's native Core ML and Vision API. Core ML is a Machine Learning (ML) model training service 
that can be run within an application. I used Core ML to create my ASL Classifier which distinguishes signs based on training data that I 
hand selected for accuracy. By running the ML model within the app, it removes the need for an internet connection. This allows users to 
access my translation service wherever they can bring their phone. The Vision API allows the app to process camera input from the native 
mobile camera and detect objects, such as hands. Leveraging the Vision API and my ML model, the app enabled camera detection of hands and 
real-time classification of hand signs. The completed application provides ASL translations with over 75 percent accuracy for all trained signs.

Although extent services claiming to translate ASL have not been able to give quantifiable help to ASL-users, that issue is now resolved. With 
my iOS Application to Translate ASL, I'm closing this translation gap by providing software that accurately translates the American Sign Language.
Now that the application is developed, I'm looking forward to publicly releasing this translator on the App Store. 

### Results
#### Results of the ML Model
Training my Machine Learning model was a multi-iteration process. My first data set was comprised of hand sign images that were captured from 
professionals. This set had a very high confidence reading on perfectly performed hand signs, but struggled to match slightly-improper signs 
with their correct name. With the added training data from my volunteers, I was able to diversify my data set to accept hand signs performed 
by a multitude of hand sizes and colors. 

An issue I noticed with my initial training set is that it had much higher accuracy on lighter-colored hands. This is due to the original 
bias in my training data. I had fed my training set with data gathered from ASL teachers on the internet, which I found to be nearly all 
Caucasian adults. In addition to my own white hands training the set, there was a very clear bias in my data. The low translation accuracy 
readings I received on my first set were reflective of this narrow data field. 

After learning from those first iterations, I expanded my sampling pool by gathering volunteers with vastly different hand sizes and colors 
than the hands that were in my current data set. With their data incorporated, I was able to train my algorithm to detect a wider variety of
hands performing each hand sign. With this, my model can now help a much larger group of people translate their ASL. 


In terms of final testing results on my model, I was able to reach my intended confidence threshold for each sign. At the start of the semester, 
my goal was to have a translator that was able to translate every letter with at least 70 percent accuracy in each translation. After improving 
my model, it now can read signs with heightened accuracy. My model has tested to perform at over 71 percent validation accuracy, 75 percent test 
accuracy, and an over to 95 percent F1 score accuracy for a subset of letters including L, N, and W. The F1 Score is the harmonic mean of the 
Precision and Recall accuracy percentages; meaning it depicts the signs overall ability to be classified readily. Given my initial focus for this 
translator was the distinction between M and N as fist-shaped hand signs, this data is proof that my initial pursuit in this project has been 
fulfilled. But the project would not be complete without this model's incorporation into a mobile application.

#### Results of the iOS Application
There are two buttons in the upper left corner. The top leftmost button flips the camera direction to use the iPhone's back camera. Translation 
accuracy is the same for both cameras. The "Summary" button lists out past signs in the order in which they were signed. This feature can be used 
to string together words after an ASL user has finished finger-spelling. 

The bottom of the screen features the prediction label. This label prints the predicted sign and it's confidence score. The confidence score is 
a measure of how accurate of a reading the ASL Classifier ML model has detected that it has made based on its testing data. 

The last UI addition is the landmark map on the signing hand. There is a small white dot that appears at each key point on all 5 fingers. These 
points include the tip of each finger as well as three joints at which the finger can bend (except the thumb which has 2), from the tip to the 
palm: the distal interphalangeal joint, the proximal interphalangeal joint, and the metacarpophalangeal joint. The dots aid in the beta testing 
process to ensure that the Vision framework is detecting the correct hand position through the device's camera. As long as the dots are aligned 
with the user's fingers, Vision will correctly interpret their position for the Classifier.

With the high accuracy readings of the translator, this application is fit for user beta testing and distribution.

### How to Use
Soon, this app will be available for download. In the mean time, you're welcome to manually download the application onto your device. 

Here's how to do that.

1. Download the code from this repositiory. 
2. Open the .xcodeproj file from this repo in XCode. 
3. Configure the Signing & Capabilities, change the Team to your identifier
4. Build the App, the play button in the top left corner of XCode.

Good luck! I hope you like my app!










