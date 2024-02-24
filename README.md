# SPRITE-GAME
import speech_recognition as sr

def real_time_transcription():
    recognizer = sr.Recognizer()
    microphone = sr.Microphone()

    with microphone as source:
        recognizer.adjust_for_ambient_noise(source)  # Adjust for noise
        print("Listening...")

        while True:
            try:
                audio = recognizer.listen(source, timeout=3)  # Listen for 3 seconds
                text = recognizer.recognize_google(audio)  # Convert speech to text
                print("You said:", text)
            except sr.WaitTimeoutError:
                print("Timeout. Listening again...")
            except sr.UnknownValueError:
                print("Could not understand audio. Please speak again.")
            except sr.RequestError as e:
                print("Error occurred; {0}".format(e))

if _name_ == "_main_":
    real_time_transcription()
