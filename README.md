This project is a dynamic and interactive Stepper Component built using Vue 3 with the Options API. The stepper provides a guided user experience with three steps, ensuring validations at each stage before progressing to the next step. The project is ideal for scenarios like payment processing, multi-step forms, or any other sequential workflow in web applications.

<img width="423" alt="Screenshot 2025-01-24 at 6 43 15 PM" src="https://github.com/user-attachments/assets/8bda3c3b-217f-4a95-8db7-dc4fe7f4188a" />


Features

Step 1: Select a payment method using radio buttons. Progress is only allowed when a selection is made.
Step 2: Choose a bank from a dropdown menu. Progress is only allowed when a bank is selected.
Step 3: Review and confirm the selected payment method and bank details.
Validation: Each step has built-in validation to ensure users complete the required inputs before moving to the next step.
Dynamic Content: Displays step-specific content dynamically based on user interaction.
Reusable Component: The stepper logic and UI can be adapted for various use cases.
Modern UI: Clean, minimalistic design with a user-friendly interface.
Technologies Used

Vue 3: For building the interactive stepper component.
Options API: To manage state, methods, and computed properties.
HTML & CSS: For structuring and styling the component.
Usage

Clone this repository and integrate the stepper component into your Vue.js application. Customize the steps, validations, and styles as needed to fit your specific requirements.

How to Run

Clone the repository:
git clone <repo-url>
cd <repo-directory>
Install dependencies:
npm install
Start the development server:
npm run serve
Open your browser and navigate to:
http://localhost:8080
Future Improvements

Add animations for smoother transitions between steps.
Support for dynamic step configuration.
Backend integration for saving and retrieving step data.
Feel free to fork the repo and contribute enhancements or new features! 😊
