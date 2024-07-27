# Documentation for `chat_message.dart`

## Overview
This file defines the `ChatMessage` class, which represents a single chat message in the chatbot interface.

## `ChatMessage` Class
### `ChatMessage`
Represents a chat message with text, sender, and timestamp:
```dart
class ChatMessage {
  final String text;
  final String sender;
  final DateTime time;

  ChatMessage({
    required this.text,
    required this.sender,
    required this.time,
  });
}
