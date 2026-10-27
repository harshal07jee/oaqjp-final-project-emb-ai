"""Flask server for emotion analysis endpoints.
This module defines the Flask application and HTTP routes used by the project."""
from flask import Flask, request, render_template
from EmotionDetection.emotion_detection import emotion_detector

app = Flask("My app")

@app.route("/")
def render_app():
    """Directing the user to the homepage
    """
    return render_template("index.html")

@app.route("/emotionDetector")
def emotion_detector_route():
    """Analyze the input text and return detected emotion scores.

    Returns a text response containing emotion scores and the dominant emotion.
    """
    input_value = request.args.get("textToAnalyze")
    result = emotion_detector(input_value)
    if result['dominant_emotion'] is None:
        return "Invalid text! Please try again!"
    message = (
    "For the given statement, the system response is "
    f"'anger': {result['anger']}, "
    f"'disgust': {result['disgust']}, "
    f"'fear': {result['fear']}, "
    f"'joy': {result['joy']} and "
    f"'sadness': {result['sadness']}. "
    f"The dominant emotion is {result['dominant_emotion']}."
    )
    return message

if __name__ == "__main__":
    app.run(debug=True)
    