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
`ChatScreen` is a `StatefulWidget` that represents the main interface of the chatbot. It is defined as follows:
```dart
class ChatScreen extends StatefulWidget {
  const ChatScreen({super.key});

  @override
  State<ChatScreen> createState() => _ChatScreenState();
}
```

### `_ChatScreenState`
The `_ChatScreenState` class manages the state of the `ChatScreen` widget. It handles the logic and UI updates for the chatbot.

#### Variables
- `_messages`: A list of chat messages.
- `_controller`: Controls the text input field.
- `_focusNode`: Manages the focus of the text input field.
- `_questions`: List of predefined questions about hardware needs.
- `_questionIndex`: Tracks the current question index.
- `_userResponses`: Stores user responses.
- `rams`, `ssds`, `cpus`: Maps representing different hardware options based on user responses.
- `_model`: Instance of the generative AI model.
- `_chatHistory`: List of chat history contents.

### State Initialization
The `initState` method initializes the model when the widget is created:
```dart
@override
void initState() {
  super.initState();
  _initializeModel();
}
```

### Model Initialization
The `_initializeModel` method loads the API key from the environment and initializes the generative AI model. If the API key is missing, it displays an error message.

### Message Handling
#### Sending a Message
The `_sendMessage` method handles sending a user message. It updates the state, stores user responses, and moves to the next question or starts the chat if all questions are answered:
```dart
void _sendMessage(String text) {
  String trimmedText = text.trim();
  if (trimmedText.isEmpty) {
    return;
  }
  final userMessage = _ChatMessage(
    text: trimmedText,
    sender: 'User',
    time: DateTime.now(),
  );
  setState(() {
    _messages.insert(0, userMessage);
  });
  _controller.clear();
  _focusNode.requestFocus();

  // Add user response to the list
  _userResponses.add(trimmedText);

  // Check if all questions are answered
  if (_questionIndex < _questions.length - 1) {
    _questionIndex++;
    _askQuestion();
  } else {
    _startChat();
  }
}
```

#### Asking a Question
The `_askQuestion` method inserts the current question into the chat:
```dart
void _askQuestion() {
  final question = _ChatMessage(
    text: _questions[_questionIndex],
    sender: 'Bot',
    time: DateTime.now(),
  );
  setState(() {
    _messages.insert(0, question);
  });
}
```

### Starting the Chat
The `_startChat` method formats the user responses and starts the chat with the generative AI model:
```dart
Future<void> _startChat() async {
  // Format the user responses
  String ram = _userResponses[0];
  String ssd = _userResponses[1];
  String cpu = _userResponses[2];

  String userPrompt =
      "I need a ${rams[ram]}GB RAM, a ${cpus[cpu]} processor, and a ${ssds[ssd]} SSD.";

  // Initialize the chat with the formatted prompt
  _chatHistory.add(Content.text(userPrompt));
  await _sendChatResponse(userPrompt);
}
```

### Sending a Chat Response
The `_sendChatResponse` method sends a chat message to the generative AI model and handles the response:
```dart
Future<void> _sendChatResponse(String userMessage) async {
  if (_model == null) return;

  try {
    // Add user message to chat history
    _chatHistory.add(Content.text(userMessage));

    // Send message and get response
    final response = await _model
        .startChat(history: _chatHistory)
        .sendMessage(Content.text(userMessage));

    // Add model response to chat history
    final botMessage = _ChatMessage(
      text: response.text ?? 'No response from the model.',
      sender: 'Bot',
      time: DateTime.now(),
    );
    setState(() {
      _messages.insert(0, botMessage);
      _chatHistory.add(Content.model([TextPart(response.text ?? '')]));
    });
  } catch (e) {
    setState(() {
      _messages.insert(
          0,
          _ChatMessage(
            text: 'Error: $e',
            sender: 'Bot',
            time: DateTime.now(),
          ));
    });
  }
}
```

### Disposal
The `dispose` method cleans up controllers and focus nodes to free up resources:
```dart
@override
void dispose() {
  _controller.dispose();
  _focusNode.dispose();
  super.dispose();
}
```

## UI Build Method
The `build` method defines the UI of the chat screen, including the app bar, chat messages list, and input field. The chat messages are displayed in a list, and the input field allows the user to type and send messages.

### AppBar
Displays the title of the chatbot.

### Chat Messages List
Displays the chat messages in a list, with different alignments and styles for user and bot messages.

### Input Field
Includes a text field for user input and a send button. The input field is focused automatically after each message is sent.

## Chat Message Class
The `_ChatMessage` class represents a single chat message. It contains the message text, sender, and timestamp:
```dart
class _ChatMessage {
  final String text;
  final String sender;
  final DateTime time;

  _ChatMessage({
    required this.text,
    required this.sender,
    required this.time,
  });
}
```

## Summary
This file defines a Flutter chatbot interface using a stateful widget. It handles user interactions, processes predefined questions, and uses a generative AI model to provide personalized hardware recommendations. The class methods manage the state, handle messages, and build the user interface.
