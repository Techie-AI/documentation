# Documentation for `ChatScreen.dart`

## Overview
This Dart file defines a Flutter widget `ChatScreen` that represents a chatbot interface. The chatbot interacts with users, asking them a series of predefined questions about their PC hardware needs, and then uses the Google Generative AI model to provide personalized recommendations based on their responses.

## Imports
The file imports several essential packages:
- `flutter/material.dart`: Provides Flutter widgets and material design components.
- `google_generative_ai/google_generative_ai.dart`: Provides access to Google Generative AI models.
- `flutter_dotenv/flutter_dotenv.dart`: Loads environment variables from a `.env` file.

## ChatScreen Class
### `ChatScreen`
`ChatScreen` is a `StatefulWidget` that represents the main interface of the chatbot.

### `_ChatScreenState`
The `_ChatScreenState` class manages the state of the `ChatScreen` widget. It handles the logic and UI updates for the chatbot.

### Predefined Questions and Responses
The class contains a list of predefined questions that the chatbot asks the user. The user's responses are stored in a list for later use.

### Hardware Options
The class defines maps representing different hardware options (RAM, SSD, CPU) based on user responses.

### State Initialization
The `_ChatScreenState` class contains variables for managing the generative AI model and the chat history. The `initState` method initializes the model when the widget is created.

### Model Initialization
The `_initializeModel` method loads the API key from the environment and initializes the generative AI model. If the API key is missing, it displays an error message.

### Message Handling
#### Sending a Message
The `_sendMessage` method handles sending a user message. It updates the state, stores user responses, and moves to the next question or starts the chat if all questions are answered.

#### Asking a Question
The `_askQuestion` method inserts the current question into the chat.

### Starting the Chat
The `_startChat` method formats the user responses and starts the chat with the generative AI model.

### Sending a Chat Response
The `_sendChatResponse` method sends a chat message to the generative AI model and handles the response.

### Disposal
The `dispose` method cleans up controllers and focus nodes to free up resources.

## UI Build Method
The `build` method defines the UI of the chat screen, including the app bar, chat messages list, and input field. The chat messages are displayed in a list, and the input field allows the user to type and send messages.

## Chat Message Class
The `_ChatMessage` class represents a single chat message. It contains the message text, sender, and timestamp.

## Summary
This file defines a Flutter chatbot interface using a stateful widget. It handles user interactions, processes predefined questions, and uses a generative AI model to provide personalized hardware recommendations. The class methods manage the state, handle messages, and build the user interface.
