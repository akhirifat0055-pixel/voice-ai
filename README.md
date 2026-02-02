# voice-ai
pip install SpeechRecognition pyttsx3 pyaudio
import speech_recognition as sr
import pyttsx3

# Initialize
listener = sr.Recognizer()
speaker = pyttsx3.init()

def talk(text):
    speaker.say(text)
    speaker.runAndWait()

def listen():
    try:
        with sr.Microphone() as source:
            print("🎧 Listening...")
            audio = listener.listen(source)
            command = listener.recognize_google(audio)
            command = command.lower()
            print("🗣️ You said:", command)
            return command
    except:
        return ""

# Main loop
talk("Hello! I am your voice AI. Say something.")

while True:
    text = listen()

    if "hello" in text:
        talk("Hello! Nice to meet you.")

    elif "your name" in text:
        talk("My name is Voice AI.")

    elif "bye" in text or "exit" in text:
        talk("Goodbye! See you again."
        break

    elif text != "":
        talk("You said " + text)
