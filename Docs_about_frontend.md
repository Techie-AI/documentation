# Documentation for `ChatScreen.dart`

## Related Documentation
- [Documentation for `ChatMessage` Class](frontend/Documentation_for_chat_message.md) - Details the `ChatMessage` class and its attributes.
- [Documentation for `ChatService` Class](frontend/Documentation_for_chat_service.md) - Describes the `ChatService` class, its methods, and interactions with the AI model.
- [Documentation for Predefined Questions and Hardware Options](frontend/Documentation_for_options_and_Questions.md) - Provides information on predefined questions and hardware options used in the chatbot.

## Overview
This Dart file defines a Flutter widget `ChatScreen` that represents a chatbot interface. It interacts with users by asking predefined questions about their PC hardware needs and uses the `ChatService` to provide personalized recommendations based on their responses.

## Imports
The file imports several essential packages and modules:
- `flutter/material.dart`: Provides Flutter widgets and material design components.
- `flutter_dotenv/flutter_dotenv.dart`: Loads environment variables from a `.env` file.
- [service/chat_message.dart](Documentation_for_chat_message.md): Defines the `ChatMessage` class.
- [service/chat_service.dart](Documentation_for_chat_service.md): Manages interactions with the generative AI model.
- [constants/options_and_Questions.dart](Documentation_for_options_and_Questions.md): Contains predefined questions and hardware options.

## `ChatScreen` Class
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
The `_ChatScreenState` class manages the state of the `ChatScreen` widget, handling the logic and UI updates for the chatbot.

#### Variables
- `_messages`: A list of `ChatMessage` instances representing chat messages.
- `_controller`: Controls the text input field.
- `_focusNode`: Manages the focus of the text input field.
- `_questionIndex`: Tracks the current question index.
- `_userResponses`: Stores user responses.
- `_chatService`: Instance of the `ChatService` class.

### State Initialization
The `initState` method initializes the chat service and starts asking questions:
```dart
@override
void initState() {
  super.initState();
  _initializeChatService();
}
```

### Chat Service Initialization
The `_initializeChatService` method loads the API key from the environment and initializes the `ChatService`:
```dart
void _initializeChatService() {
  final String apiKey = dotenv.env['API_KEY']!;
  _chatService = ChatService(apiKey: apiKey, onResponse: _handleResponse);
  _askQuestion();
}
```

### Message Handling
#### Sending a Message
The `_sendMessage` method processes user messages, updates the state, and proceeds to the next question or starts the chat:
```dart
void _sendMessage(String text) {
  String trimmedText = text.trim();
  if (trimmedText.isEmpty) {
    return;
  }
  final userMessage = ChatMessage(
    text: trimmedText,
    sender: 'User',
    time: DateTime.now(),
  );
  setState(() {
    _messages.insert(0, userMessage);
  });
  _controller.clear();
  _focusNode.requestFocus();

  _userResponses.add(trimmedText);

  if (_questionIndex < questions.length - 1) {
    _questionIndex++;
    _askQuestion();
  } else {
    _chatService.startChat(_userResponses);
  }
}
```

#### Asking a Question
The `_askQuestion` method inserts the current question into the chat:
```dart
void _askQuestion() {
  final question = ChatMessage(
    text: questions[_questionIndex],
    sender: 'Bot',
    time: DateTime.now(),
  );
  setState(() {
    _messages.insert(0, question);
  });
}
```

### Handling AI Responses
The `_handleResponse` method updates the chat with the AI's response:
```dart
void _handleResponse(String response) {
  final botMessage = ChatMessage(
    text: response,
    sender: 'Bot',
    time: DateTime.now(),
  );
  setState(() {
    _messages.insert(0, botMessage);
  });
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
The `build` method defines the UI of the chat screen, including the app bar, chat messages list, and input field.

### AppBar
Displays the title of the chatbot.

### Chat Messages List
Displays the chat messages in a list, with different alignments and styles for user and bot messages.

### Input Field
Includes a text field for user input and a send button. The input field is focused automatically after each message is sent.


