<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Emotion Detector</title>
</head>
<body>
    <h1>Emotion Detector</h1>
    <p>This project is an emotion detector that uses a pre-trained deep learning model to identify human emotions from video feed in real-time.</p>
    
    <h2>Requirements</h2>
    <ul>
        <li>Python 3.x</li>
        <li>Keras</li>
        <li>OpenCV</li>
        <li>NumPy</li>
    </ul>
    <p>You can install the required Python packages using the following command:</p>
    <pre><code>pip install keras opencv-python numpy</code></pre>
    
    <h2>Setup</h2>
    <p>Ensure you have the following files in your project directory:</p>
    <ul>
        <li><code>default_11.xml</code> - The Haar Cascade XML file for face detection.</li>
        <li><code>model.h5</code> - The pre-trained Keras model for emotion detection.</li>
    </ul>
    
    <h2>How to Run</h2>
    <ol>
        <li>Ensure you have a webcam connected to your system.</li>
        <li>Run the script using Python:</li>
    </ol>
    <pre><code>python emotion_detector.py</code></pre>
    
    <h2>Process</h2>
    <ol>
        <li>Load the face detection model (<code>default_11.xml</code>) and the emotion detection model (<code>model.h5</code>).</li>
        <li>Start video capture from the webcam.</li>
        <li>Convert each frame to grayscale and detect faces.</li>
        <li>For each detected face, preprocess the region of interest and predict the emotion.</li>
        <li>Display the emotion label on the video frame.</li>
        <li>Press <code>q</code> to quit the application.</li>
    </ol>
</body>
</html>

