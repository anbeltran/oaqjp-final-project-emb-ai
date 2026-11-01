from flask import Flask, render_template, request
from EmotionDetection import emotion_detector

app = Flask(__name__)


@app.route('/')
def render_index_page():
    return render_template('index.html')


@app.route('/emotionDetector')
def emotion_detector_route():

    text_to_analyze = request.args.get('textToAnalyze')

    emotion_result = emotion_detector(text_to_analyze)

    if emotion_result['dominant_emotion'] is None:
        return "¡Texto inválido! ¡Por favor, inténtalo de nuevo!"

    anger = emotion_result['anger']
    disgust = emotion_result['disgust']
    fear = emotion_result['fear']
    joy = emotion_result['joy']
    sadness = emotion_result['sadness']
    dominant_emotion = emotion_result['dominant_emotion']

    return (
        f"For the given statement, the system response is "
        f"'anger': {anger}, 'disgust': {disgust}, "
        f"'fear': {fear}, 'joy': {joy} and "
        f"'sadness': {sadness}. "
        f"The dominant emotion is {dominant_emotion}."
    )


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
