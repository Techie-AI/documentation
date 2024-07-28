# TechieAi Organization

Welcome to the TechieAi organization! We are a team of passionate developers working together to build innovative AI-driven applications. Our current focus is on creating a chatbot that assists users in building PCs by providing compatibility checks and recommendations for hardware components. Our mission is to simplify the process of building a custom PC by leveraging AI technology to deliver accurate and user-friendly guidance.

## Projects

### 1. PC Build Chatbot

**Description:**  
A Flutter-based application that integrates with the Gemini API to provide users with detailed guidance on PC builds. The chatbot helps users determine the compatibility of various hardware components, such as CPUs, RAM, SSDs, and motherboards. Users can ask questions about the specifications they need, and the chatbot will suggest compatible parts and configurations that meet their requirements. This ensures that users can make informed decisions when selecting components, avoiding compatibility issues and optimizing performance.

**Features:**
- **Compatibility Checks:** The chatbot can verify if the selected components are compatible with each other, reducing the risk of hardware conflicts.
- **Guided Recommendations:** Based on user inputs like budget, performance needs, and specific use cases, the chatbot provides tailored hardware recommendations.
- **Real-time Responses:** Leveraging the power of the Gemini API, the chatbot delivers quick and accurate responses to user queries.
- **User-friendly Interface:** The application features an intuitive chat interface, making it easy for users to interact with the chatbot and get the information they need.
- **Expandable Database:** While we currently have detailed data on CPUs, we are continuously expanding our database to include more components such as GPUs, RAM, SSDs, and motherboards.

## Additional Pages
- [Parameters for connections between CPU, RAM, SSD, Motherboard](Parameters.md) - This page provides detailed information about the compatibility and connections between CPU, RAM, SSD, and Motherboard components. It covers essential parameters and considerations for building a PC to ensure optimal performance and compatibility.
- [Hardware Data Completion Scripts Documentation](Hardware_Data_Completion_Scripts_Documentation.md) - This document outlines the process and impact of using scripts to automate the completion of hardware datasets for CPUs, motherboards, SSDs, and RAM modules.
- [Frontend Development Documentation](Docs_about_frontend.md) - A detailed guide on the frontend development aspects of our projects, including best practices, coding standards, and architectural guidelines.
- [Tech-AI Chat Application Documentation](Tech-AI_Chat_Application_Documentation.md) - This page contains the detailed documentation for the Tech-AI chat application, outlining its features, setup, and usage.

## Team

- **Rohit Agarwal** 
  - Project Lead
  - Rohit is the visionary behind TechieAi, bringing together his expertise in AI and a passion for technology to lead the team in developing innovative solutions.
- **Ankit Dhanawat** 
  - Flutter UI Developer
  - Ankit specializes in crafting the user interface for our applications, ensuring a seamless and engaging user experience.
- **Jayesh Joshi**
  - Flutter UI Developer
  - Jayesh works alongside Ankit to design and implement the UI components, focusing on creating intuitive and responsive interfaces.

## Setup and Installation

To get started with the project, follow these steps:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/Techie-AI/Frontend.git
   cd Frontend
   ```

2. **Install Dependencies:**
   Ensure that you have Flutter installed. If not, follow the [Flutter installation guide](https://flutter.dev/docs/get-started/install).

   Install the required Flutter packages by running:
   ```bash
   flutter pub get
   ```

3. **Setup Environment Variables:**
   Ensure that you have the `.env` file in the root folder before testing the app, as it contains the API key required for the Gemini API.

   ### Example `.env` file
   ```plaintext
   API_KEY=your_gemini_api_key_here
   ```
   Replace `your_gemini_api_key_here` with your actual Gemini API key.

4. **Run the Application:**
   To run the application on an emulator or connected device, use:
   ```bash
   flutter run
   ```

5. **Build the Application:**
   To build the application for release, use:
   ```bash
   flutter build apk
   ```
   (For Android) or
   ```bash
   flutter build ios
   ```
   (For iOS).

By following these steps, you'll have the project up and running and be able to test and contribute effectively.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information. The MIT License allows you to freely use, modify, and distribute the software, provided that the original authors are credited.

## Contact

For any inquiries or further information, please contact us at rohitagr2610@gmail.com. We welcome feedback, suggestions, and collaboration opportunities. Whether you're interested in contributing to our projects or just want to learn more about what we do, feel free to reach out.

---

Thank you for being a part of TechieAi! We are excited to have you on board and look forward to achieving great things together. Stay tuned for updates and new projects as we continue to push the boundaries of what's possible with AI and technology.
