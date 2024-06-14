<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Emotion Detection using OpenCV and Keras</title>
</head>
<body>

<h1>Emotion Detection using OpenCV and Keras</h1>

<p>This project uses OpenCV and Keras to detect human emotions in real-time through a webcam. The model predicts emotions such as Angry, Disgust, Fear, Happy, Neutral, Sad, and Surprise.</p>

<h2>Requirements</h2>
<ul>
    <li>Python 3.x</li>
    <li>OpenCV</li>
    <li>Keras</li>
    <li>TensorFlow</li>
    <li>NumPy</li>
</ul>

<h2>Installation</h2>
<ol>
    Clone the repository:
    <pre><code>git clone &lt;repository_url&gt;</code></pre></li>
    <li><strong>Navigate to the project directory:</strong>
    <pre><code>cd &lt;repository_directory&gt;</code></pre></li>
    <li><strong>Install the required packages:</strong>
    <pre><code>pip install -r requirements.txt</code></pre></li>
    
</ol>

<h2>Usage</h2>
<ol>
    <li><strong>Download the pre-trained model and Haarcascade XML file:</strong>
    <ul>
        <li>Place <code>default_11.xml</code> in the project directory.</li>
        <li>Place <code>model.h5</code> in the project directory.</li>
        <li><strong>Run the emotion detector:</strong>
        <pre><code>python emotion_detector.py</code></pre></li>
    </ul></li>

    
</ol>

<h2>Code Explanation</h2>

<pre><code>from keras.models import load_model
from time import sleep
from keras.preprocessing.image import img_to_array
from keras.preprocessing import image
import cv2
import numpy as np

# Load the face classifier and pre-trained model
face_classifier = cv2.CascadeClassifier(r'C:\Users\KIIT\Desktop\allcodes\Emotion\default_11.xml')
classifier = load_model(r'C:\Users\KIIT\Desktop\allcodes\Emotion\model.h5')

# Define emotion labels
emotion_labels = ['Angry', 'Disgust', 'Fear', 'Happy', 'Neutral', 'Sad', 'Surprise']

# Initialize webcam feed
cap = cv2.VideoCapture(0)

while True:
    # Read frame from webcam
    _, frame = cap.read()
    labels = []
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    faces = face_classifier.detectMultiScale(gray)

    for (x, y, w, h) in faces:
        cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 255), 2)
        roi_gray = gray[y:y + h, x:x + w]
        roi_gray = cv2.resize(roi_gray, (48, 48), interpolation=cv2.INTER_AREA)

        if np.sum([roi_gray]) != 0:
            roi = roi_gray.astype('float') / 255.0
            roi = img_to_array(roi)
            roi = np.expand_dims(roi, axis=0)

            # Make a prediction on the ROI, then lookup the class
            prediction = classifier.predict(roi)[0]
            label = emotion_labels[prediction.argmax()]
            label_position = (x, y)
            cv2.putText(frame, label, label_position, cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 0), 2)
        else:
            cv2.putText(frame, 'No Faces', (30, 80), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 0), 2)
    
    # Display the resulting frame
    cv2.imshow('Emotion Detector', frame)
    
    # Exit the loop when 'q' key is pressed
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# Release the webcam and close windows
cap.release()
cv2.destroyAllWindows()
</code></pre>

<h2>Explanation</h2>

<ul>
    <li><strong>Face Detection:</strong> The face is detected using the Haarcascade classifier (<code>default_11.xml</code>).</li>
    <li><strong>Pre-processing:</strong> The detected face is converted to grayscale and resized to 48x48 pixels.</li>
    <li><strong>Prediction:</strong> The pre-processed face is passed to the pre-trained model (<code>model.h5</code>) to predict the emotion.</li>
    <li><strong>Display:</strong> The predicted emotion label is displayed on the video feed in real-time.</li>
</ul>

<h2>Note</h2>

<p>Ensure your webcam is properly connected and the required files (<code>default_11.xml</code> and <code>model.h5</code>) are in the correct directory before running the script.</p>

</body>
</html>
