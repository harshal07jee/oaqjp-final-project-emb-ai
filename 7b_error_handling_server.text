from flask import Flask, request, render_template
from EmotionDetection.emotion_detection import emotion_detector

app = Flask("My app")

@app.route("/")
def renderApp():
    return render_template("index.html")

@app.route("/emotionDetector")
def emotionDetector():
    INPUT_VALUE = request.args.get("textToAnalyze")
    result = emotion_detector(INPUT_VALUE)
    
    if result['dominant_emotion'] == None:
        return "Invalid text! Please try again!"

    return f"For the given statement, the system response is 'anger': {result['anger']}, 'disgust': {result['disgust']}, 'fear': {result['fear']}, 'joy': {result['joy']} and 'sadness': {result['sadness']}. The dominant emotion is {result['dominant_emotion']}."

    
if __name__ == "__main__":    app.run(debug=True)