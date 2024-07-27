# Documentation for `chat_service.dart`

## Overview
This file contains the `ChatService` class, which manages interactions with the generative AI model and processes user responses to provide recommendations.

## Imports
- `google_generative_ai/google_generative_ai.dart`: Provides access to Google Generative AI models.
- `constants/options_and_Questions.dart`: Contains predefined questions and hardware options.

## `ChatService` Class
### `ChatService`
Manages interactions with the generative AI model:
```dart
class ChatService {
  late GenerativeModel _model;
  late List<Content> _chatHistory;

  final void Function(String) onResponse;

  ChatService({required String apiKey, required this.onResponse}) {
    _model = GenerativeModel(model: 'gemini-1.5-flash', apiKey: apiKey);
    _chatHistory = [];
  }

  Future<void> startChat(List<String> userResponses) async {
    String userPrompt = /* formatted prompt based on userResponses */;
    _chatHistory.add(Content.text(userPrompt));
    await _sendChatResponse(userPrompt);
  }

  Future<void> _sendChatResponse(String userMessage) async {
    try {
      _chatHistory.add(Content.text(userMessage));
      final response = await _model
          .startChat(history: _chatHistory)
          .sendMessage(Content.text(userMessage));

      onResponse(response.text ?? 'No response from the model.');
      _chatHistory.add(Content.model([TextPart(response.text ?? '')]));
    } catch (e) {
      onResponse('Error: $e');
    }
  }
}
```
