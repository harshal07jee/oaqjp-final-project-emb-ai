import requests
import json

def emotion_detector (text_to_analyze): 
    URL = 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    Headers = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    Input_json = { "raw_document": { "text": text_to_analyze } }

    response = requests.post(URL, json = Input_json, headers = Headers)
    formated_response = json.loads(response.text)
    

    if response.status_code == 200:
        emotions = formated_response['emotionPredictions'][0]['emotion']
        dominant_emotion = max(emotions, key=emotions.get)
     
        
        collected_emotions = {
            "anger": emotions["anger"],
            "disgust": emotions["disgust"],
            "fear": emotions["fear"],
            "joy": emotions["joy"],
            "sadness": emotions["sadness"],
            "dominant_emotion": dominant_emotion
        }
        
        return collected_emotions
    elif response.status_code == 400:
        collected_emotions = {
                            'anger': None,
                            'disgust': None, 
                            'fear': None, 
                            'joy': None, 
                            'sadness': None, 
                            'dominant_emotion': None}

        return collected_emotions    
       
