# Blink
<p> Blink aims to provide an innovative and accessible way of interacting with a computer using eye movements. By leveraging Python libraries and computer vision techniques, this project enables users to control the mouse cursor on the screen using the movement of a eyes.

The primary objective of this project is to enhance accessibility for individuals with motor disabilities or conditions that restrict their ability to use a traditional mouse. By utilizing eye-tracking technology, users can navigate and interact with the computer interface solely through their eye movements.</p>
<p><h3>1. Capturing Video & Segmenting into Frames</h3>

Python provides various libraries for image and video processing. One of them is OpenCV. OpenCV is a vast library that helps in providing various functions for image and video operations. With OpenCV, we can capture a video from the camera. It lets us create a video capture object which is helpful to capture videos through webcam and then we may perform desired operations on our captured video.<br><br>
<b>Steps to capture a video:</b><br>
<ul>
<li>Use cv2.VideoCapture() to get a video capture object for the camera.</li>
<li>Set up an infinite while loop and use the read() method to read the frames using the above created object.</li>
<li>Use cv2.imshow() method to show the frames in the video.</li>
<li>Breaks the loop when the user clicks a specific key. In our project we use the ‘q’ key to break that infinite loop . </li></ul>
</p>
<p><h3>2. Gray Scale Conversion</h3>

We use Open CV to convert a colored video to a gray-scale format. It is an image conversion technique in digital photography. It eliminates every form of color information and only leaves different shades of gray; the brightest being white and the darkest of it being black. Its intermediate shades usually have an equal level of brightness for the primary colors (red, blue and green). Alternatively it uses equal amounts of cyan, yellow and magenta which are the primary pigments. Each pixel is a representation of the luminous intensity of the image.

It is the art of converting an image into a digital format in a way that is either manipulated or enhanced for data extraction.

<b>Approach:</b>
<ul>
  <li>Inside the loop extract the frames of the video using the read() method.</li>
  <li>Pass the frame to the cv2.cvtColor() method with cv2.COLOR_BGR2GRAY as a parameter to convert it into gray-scale.</li>
</ul>
</p>
<p><h3>3. Human Face Detection</h3>

Object Detection is one of the leading and most popular use cases in the domain of computer vision. Several object detection models are used worldwide for their particular use case applications. Many of these models have been used as an independent solution to a single computer vision task with its own fixed application. Combining several of these tasks into a single end-to-end solution, in real-time, is exactly what MediaPipe does.
Mediapipe is a cross-platform python library use to detect face and hand landmarks

In this project the mediapipe python library is used to detect facial landmarks .There are a total 468 landmarks on the human face. 

Facial landmark detection is a computer vision task in which a model needs to predict key points representing regions or landmarks on a human’s face – eyes, nose, lips, and others. Facial landmark detection is a base task which can be used to perform other computer vision tasks, including head pose estimation, identifying gaze direction, detecting facial gestures, and swapping faces.
</p>
<p>
 <h3>4. Eye Detection</h3> 

To detect and track eye images with complex backgrounds, distinctive features of the user eye are used. Generally, an eye-detection system can be divided into four steps: Face detection, eye region detection, pupil detection and eye tracking.

Main step of eye detection is pupil detection. For pupil detection first facial landmarks will be detected. When face landmarks are detected, as there are a total of 468 landmarks, we need to extract only eye’s pupil landmarks from them for eye detection. 

In this application both the human eyes are detected for different work. Right eye is detected for the mouse cursor movement and the left eye is detected for performing click events. 
</p>
<p><h3>5. Gaze Tracking & Cursor Movement</h3>
 
<b>Gaze Tracking</b>

Eye gaze is an important nonverbal communication technology. Gaze Tracking is a task to predict where a person is looking at given the person’s full face. Pupil tracking is a gaze-detection technique that is often used in combination with other methods. 

Record the coordinates of the Pupil and will keep tracking the Pupil and will sync our mouse cursor according to the recorded movement of the Pupil.

In this project we use the right eye of a person for cursor movement. 

<a href="https://drive.google.com/file/d/1VhMnyd3KIlYgdFbEiDViEgSsNx_lv5sz/view?usp=drive_link">Gaze Tracking</a>
<br><br>
<b>Cursor Movement</b>

The input of eye movement is taken from the individual's pupil. If a person looks at a center mouse pointer, that point would be taken as the input point and it sets that location as the basis for gaze tracking and it begins moving in the direction of the person's eye movement and the cursor stops moving when the person's eye hits its initial place.

PyautoGUI is a Python module which can automate your GUI and programmatically control your keyboard and mouse.

PyautoGUI is used in this project for cursor movement .It tracks and controls the mouse using the coordinate system of the screen.


<b>1. Left and right movement of the pupil</b>

Horizontal eye pupil movement can be achieved using circular artifacts. If the pupil moves in the left direction, the mouse pointer moves in the left direction as well, and the same happens in the right direction as well, 


<b>2. Up and down movement of the pupil</b>

Vertical eye pupil movement can be achieved by using pupil scale. The eyes are in a slightly half-closed state when gazing downwards. This phenomenon can be used to guide the step from top to bottom of the mouse pointer.
<br><br>
<a href="https://drive.google.com/file/d/1VZGJebuj9eBT_IAibpDlAJpSXboM9dLR/view?usp=drive_link">Cursor Movement</a>
</p>
<p><h3>6. Blink Detection & Click Event</h3>

<b>Blink Detection</b>

Blinking which is one of the easiest eye movements to detect and has numerous applications in the fields of human computer interaction. Blinking can be involuntary or voluntary.

Voluntary blinking can be used as a means of communication. The interface to a computing device has traditionally been a keyboard or a mouse, and more recently, a touchscreen. If blinking can be detected, it can serve as an additional interface, with appropriate responses for a specified action.

There have been many approaches to detecting blinks. In this project we use only two landmarks of the person’s right eye for blink detection. When a person blinks his/her eye both the landmarks overlap each other so as this application runs continuously, simultaneously it calculates differences between both the landmarks, and when difference goes to zero this means the person blinks his/her eye.

<b>Click Event</b>

Now, the blink of the eye will be used to select the stuff as it was done with the mouse clicks.

The average time of a complete human blink is about 300 to 400 milliseconds or 3/10ths to 4/10ths of a second. Of course this is an average only and can differ from person to person. So to perform clicking operations, the user has to blink with one eye for at least 700 to 800 milliseconds.

Thus, mouse clicking is managed by the eyes blinking. PyautoGUI can also perform click operation which is used in this project.

In this project we use the left eye of a person for a click event. 

</p>
