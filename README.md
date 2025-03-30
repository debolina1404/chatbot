import openai
import os
openai.api_key = os.getenv("OPENAI_API_KEY")

def chat_with_gpt(prompt):
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )
    # Extract and return the chatbot's reply
    return response['choices'][0]['message']['content']

if __name__ == "__main__":
    while True:
        user_input = input("you: ")
        if user_input.lower() in ["quit", "exit", "bye"]:
            print("Goodbye!")
            break
        try:
            response = chat_with_gpt(user_input)
            print("chatbot:", response)
        except Exception as e:
            print("An error occurred:", e)