# chat-bot-using-NPL

Project CHAT BOT using NPL
pip install nltk spacy

import nltk
from nltk.chat.util import Chat, reflections
import spacy

nltk.download('punkt')

nlp = spacy.load("en_core_web_sm")

patterns = [
    (r'hello|hi|hey', ['Hellooo!', 'Hi there!', 'Hooi!']),
    (r'how are you?', ['I am doing well, thank you!', 'I am fine, how about you?']),
    (r'what is your name?', ['I am your chatbot.', 'You can call me ChatGPT.']),
    (r'bye|goodbye', ['byebye!', 'Have a great day!', 'See you later.']),
]

chatbot = Chat(patterns, reflections)

def process_input(input_text):
    doc = nlp(input_text)
    return doc

while True:
    user_input = input("You: ")
    if user_input.lower() == 'exit':
        print("Chatbot: Goodbye!")
        break

    processed_input = process_input(user_input)

    response = chatbot.respond(processed_input)
    print("Chatbot:", response)


•	We can also create a chat bot by using AI

pip install openai

import openai
openai.api_key = 'YOUR_API_KEY'

def generate_response(prompt):
    response = openai.Completion.create(
        engine="text-davinci-002",  # You may choose a different engine
        prompt=prompt,
        max_tokens=150,
        n=1,
        stop=None,
        temperature=0.7,
    )
    return response.choices[0].text.strip()

print("Chatbot: Hello! I'm your impressive chatbot. Ask me anything.")
while True:
    user_input = input("You: ")
    if user_input.lower() == 'exit':
        print("Chatbot: Goodbye!")
        break
    prompt = f"You: {user_input}\nChatbot:"
    response = generate_response(prompt)
    print(response)

~ this is how we create chat bots and it’s the code for implementation for the respective project!
