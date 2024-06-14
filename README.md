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
        <li>Download the <code>requirements.txt</code> file</li>
        <li><strong>and then install the modules using: </strong>
        <pre><code>pip install -r requirements.txt</code></pre></li>
        <li><strong>Run the emotion detector:</strong>
        <pre><code>python emotion_detector.py</code></pre></li>
    </ul></li>

    
</ol>


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
