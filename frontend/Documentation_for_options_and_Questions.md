# Documentation for `options_and_Questions.dart`

## Overview
This file contains predefined questions and mappings for different hardware options, including CPUs, motherboards, RAM, and SSDs. It provides the data used by the `ChatService` and `ChatScreen` to interact with users.

## Variables

### `questions`
A list of strings containing questions to ask the user about their PC hardware needs:
```dart
final List<String> questions = [
  "Question 1: Which CPU you need?\n1. AMD\n2. Intel\n3. Apple\n4. ARM\n5. Hygon",
  "Question 2: How much CPU Power do you need?\n1. Low\n2. Mid\n3. High",
  "Question 3: Which company motherboard do you need?\n1. Asus\n2. Asrock\n3. Colorful\n4. MSI\n5. Biostar\n6. ECS\n7. Maxsun\n8. Fujitsu\n9. SOYO\n10. EVGA",
  "Question 4: How much motherboard Power do you need?\n1. Low\n2. Mid\n3. High",
  "Question 5: Which company RAM you need?\n1. Kingston\n2. Corsair\n3. G.Skill\n4. Crucial\n5. Samsung\n6. Patriot",
  "Question 6: How much RAM you need?\n1. 8GB\n2. 16GB\n3. 32GB",
  "Question 7: How much SSD Size you need?\n1. 256GB\n2. 512GB\n3. 1TB+"
];
```

### `cpus`, `cpuPowers`, `motherboards`, `motherboardPowers`, `rams`, `ramSizes`, `ssds`
Mappings that provide details about different hardware options:
```dart
final Map<String, Map<String, String>> cpus = { /* ... */ };
final Map<String, Map<String, String>> cpuPowers = { /* ... */ };
final Map<String, Map<String, String>> motherboards = { /* ... */ };
final Map<String, Map<String, String>> motherboardPowers = { /* ... */ };
final Map<String, Map<String, String>> rams = { /* ... */ };
final Map<String, Map<String, String>> ramSizes = { /* ... */ };
final Map<String, Map<String, String>> ssds = { /* ... */ };
```
