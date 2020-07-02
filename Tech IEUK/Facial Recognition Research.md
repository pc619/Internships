# Facial Recognition

## What are the steps of facial recognition?

1. **Face Detection:** A picture of your face is captured from a photo or video. Your face might appear alone or in a crowd. Your image may show you looking straight ahead or nearly in profile.
1. **Face Analysis:** Facial recognition software reads the geometry of your face. Key factors include the distance between your eyes and the distance from forehead to chin. The software identifies facial landmarks — one system identifies 68 of them — that are key to distinguishing your face. The result: your facial signature.
1. **Converting An Image to Data:** Your facial signature — a mathematical formula — is compared to a database of known faces. And consider this: at least 117 million Americans have images of their faces in one or more police databases.
1. **Finding a match:** A determination is made. Your faceprint may match that of an image in a facial recognition system database.

## What is the technology behind facial recognition?

### Computer Vision:
- The most common library for computer vision is OpenCV - orginally written in C/C++, it now provides bindings for Python.
- Faces are complicated, hence there isn't one unique algorithm/test that will allow you to detect a face.
- There are thousands of small patterns and features that must be matched. The algorithms break the task of identifying the face into thousands of smaller tasks, each of which is easy to solve. These are called **classifiers**.
- The problem is that a face has arounf 6,000 classifiers all of which must be matched (within an error limit) for a face to be detected. Why is this a problem? The algorithm starts at the top left of a picture and moves down across small blocks of data, looking at each block.p
- Since there are 6,000 or more tests per block, you might have millions of calculations to do, which will grind your computer to a halt.
- To solve this problem OpenCV uses **cascades**.
    - Cascade breaks the problem of detecting faces into multiple stages.
    -  For each block, it does a very rough and quick test. If that passes, it does a slightly more detailed test, and so on (there may be 30 to 50 stages).
    - The advantage is that the majority of the picture will return a negative during the first few stages, which means the algorithm won’t waste time testing all 6,000 features on it.
    - Cascades are just XML files that contain OpenCV data used to detect objects.


### OpenCV in Python - the code.

#### First Step: Detect where the face is.

- Install OpenCV into the computer.
- Pass in the image and cascade names as command-line arguments.
- Now we create the cascade and initialize it with our face cascade. This loads the face cascade into memory so it’s ready for use.
- Read the image and convert it to grayscale. Many operations in OpenCV are done in grayscale.
- Create the function to detect the face. These are the options that must be tested and optimized (The function returns a list of rectangles in which it believes it found a face - in this case it should only be one, or the most prominent one):
    1. The first option is the gray scale option.
    1. The second is the `scaleFactor`
    1. `minNeighbors` defines how many objects are detected near the current one before it declares the face found. `minSize`, meanwhile, gives the size of each window.
- This will be slightly different if using a webcam (but the same algorithm applies) - further chance for testing.

#### Second Step: Encoding faces and matching.

- Before being able to recognize faces, first they must be quantified and stored (here lies a potential security and/or privacy concern).
- We could train a new network by providing data samples - not necessary. Perhaps useful to adjust weights to test what is more accurate.
- Encode the face into a feature vector that can be compared to the feature vectors stored in the database.


## What are the advantages and disadvantages of facial recognition?

### Advantages:
- **Second-factor verification:** Using biometric verification utilizes something that a user *is* in order to protect their data. 
- **Less Invasive than other biometrics:** Humans 'detect' eachother by recoganizing eachother's faces on a day-to-day basis. This is thus esier/more natural to integrate into our daily lives than perhaps finger print detection.

### Disadvantages:
- **Error in identifying the person:** If the software isn't able to identify the user accurately it can lead to a bad UX (e.g. bad camera quality, bad lighting, etc.).
- **Privacy:** Facial recognition can track you and security breachers are currently very common events. 
- **Loophole:** Could someone get into your account using a picture of you? How to get around this issue? Potential Solutions:
    1. Only be logged in one device at a time. 
    1. 3D/Liveness Detection with webcam face recognition.
- **Missuse of Data:** many facial recognition databases are public. This means that any person, even those with malicious intent, can find you on the database and track you down. People may feel uncomfortable sharing such details. 

## How to ensure privacy and security when using facial recognition?
1. Get consent from user.
1. Provide users with meaningful information of how the data will be used and stored (transparency).
1. Using administrative, technological and physical safeguards to ensure there are no data breaches.
1. Inegrity and access - allow users to be able to change their data (update perhaps incorrect information) and/or delete their facial recognition data.

## What is the cost of implementing facial recognition in a bank app?
https://www.devteam.space/blog/build-facial-recognition-software/

