# FinTrek App

[![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactnative.dev/) [![Expo](https://img.shields.io/badge/Expo-000020?style=for-the-badge&logo=expo&logoColor=white)](https://expo.dev/) [![Clerk](https://img.shields.io/badge/Clerk-6C47FF?style=for-the-badge&logo=clerk&logoColor=white)](https://clerk.com/)

This repository contains the frontend for **FinTrek**, a modern and intuitive personal finance tracking application built with React Native and Expo. It provides a seamless mobile experience for users to manage their income and expenses, with secure authentication powered by Clerk.

## Screenshots

| Sign In Screen                                                                                                                              | Home Dashboard                                                                                                                              | Create Transaction                                                                                                                          |
| :-----------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------: |
| <img src="https://github.com/user-attachments/assets/7293ec9d-10f2-4f92-8af7-3cc2c95fadca" alt="Sign In Screen" width="250"/> | <img src="https://github.com/user-attachments/assets/c372fe73-870d-4c21-9e12-46e1efb7d795" alt="Home Dashboard" width="250"/> | <img src="https://github.com/user-attachments/assets/f50ad615-fbeb-4776-a29f-d3a3b88795c1" alt="Create Transaction" width="250"/> |

## Backend API

This frontend application consumes a Node.js backend service for all its data operations. The backend handles transaction logic, database interactions, and financial summaries.

**You can find the backend repository here:** [**FinTrek-api**](https://github.com/Aranav8/FinTrek-api)

## Features

-   **Secure User Authentication**: Full sign-up and sign-in flows with email verification, powered by [Clerk](https://clerk.com/).
-   **Financial Dashboard**: A clear and concise home screen displaying total balance, total income, and total expenses.
-   **Transaction Management**: Users can easily create, view, and delete their financial transactions.
-   **Category-Based Tracking**: Transactions are assigned to predefined categories (e.g., Food, Shopping, Bills) for better organization.
-   **Protected Routes**: Application routes are protected, ensuring that only authenticated users can access the main app features.
-   **Intuitive UI/UX**: Built with user experience in mind, featuring clean cards, intuitive navigation, and helpful empty/loading states.
-   **Themed Interface**: A theming system is in place (`constants/colors.js`), allowing for easy visual customization across the app.
-   **Expo Router**: Utilizes Expo's file-based routing for a clean and scalable navigation structure.

## Technologies Used

-   **Framework**: [React Native](https://reactnative.dev/) with [Expo](https://expo.dev/)
-   **Authentication**: [Clerk](https://clerk.com/)
-   **Navigation**: [Expo Router](https://docs.expo.dev/router/introduction/)
-   **UI Components**: Custom components built with standard React Native APIs.
-   **Styling**: `StyleSheet` with a theming system.
-   **Icons**: [@expo/vector-icons](https://docs.expo.dev/guides/icons/) (Ionicons)

---

## Getting Started

Follow these instructions to set up and run the frontend application on your local machine.

### Prerequisites

-   [Node.js](https://nodejs.org/) (LTS version recommended)
-   [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
-   [Expo Go](https://expo.dev/go) app on your iOS or Android device for testing.
-   A [Clerk](https://clerk.com/) account to get your publishable key.
-   The [FinTrek-api](https://github.com/Aranav8/FinTrek-api) backend server must be running.

### Installation

1.  **Clone the frontend repository:**
    ```sh
    git clone https://github.com/Aranav8/FinTrek-App.git
    cd FinTrek-App
    ```

2.  **Install the required dependencies:**
    ```sh
    npm install
    ```

### Environment Variables

Before running the application, you need to set up your environment variables.

1.  Create a file named `.env` in the root of the project.
2.  Copy the contents of the example below into your new `.env` file and add your credentials.

    ```env
    # Your Clerk Publishable Key (required)
    # The 'EXPO_PUBLIC_' prefix is required by Expo to expose this variable to the client-side app.
    EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY="pk_test_YOUR_CLERK_KEY"

    # The URL of your backend API (optional, defaults to the production URL)
    # Uncomment and use this for local development if your backend is running on a different port.
    # EXPO_PUBLIC_API_URL="http://localhost:5001/api"
    ```

3.  Make sure your code uses this new API URL variable. In `constants/api.js`, you can update it to:
    ```javascript
    const API_URL = process.env.EXPO_PUBLIC_API_URL || "https://fintrek-api.onrender.com/api";
    ```

### Running the Application

1.  **Start the Expo development server:**
    ```sh
    npm start
    ```

2.  This will open the Expo Dev Tools in your browser. You can then:
    -   Scan the QR code with the Expo Go app on your phone to run the app on a physical device.
    -   Press `i` to run on an iOS simulator or `a` to run on an Android emulator (if configured).

## Available Scripts

In the project directory, you can run:

-   `npm start`: Runs the app in development mode using Expo.
-   `npm run android`: Opens the app on a connected Android device or emulator.
-   `npm run ios`: Opens the app on the iOS simulator.
-   `npm run web`: Runs the app in a web browser.
-   `npm run lint`: Lints the project files using ESLint.

## Project Structure

The project uses Expo's file-based router, which simplifies navigation and layout management.

-   **`app/`**: This is the root directory for all routes.
    -   **`(auth)/`**: A route group for authentication screens (`sign-in`, `sign-up`). Its layout `_layout.js` handles redirecting authenticated users away from these pages.
    -   **`_layout.js`**: The root layout of the application. It wraps the entire app in necessary providers like `ClerkProvider` and `SafeScreen`.
    -   **`create.js`**: The dedicated screen for creating a new transaction.
-   **`assets/`**: Contains static assets like images, fonts, and stylesheets.
    -   `styles/`: Contains stylesheets organized by screen or component.
-   **`components/`**: Shared, reusable UI components used across multiple screens (e.g., `BalanceCard`, `TransactionItem`, `PageLoader`).
-   **`constants/`**: Global application constants.
    -   `api.js`: Defines the backend API URL.
    -   `colors.js`: Defines the color palette and theming system for the app.
-   **`hooks/`**: Custom React hooks for managing state and logic, like `useTransactions` for fetching and managing transaction data.
-   **`lib/`**: General utility functions that can be used anywhere, such as `formatDate`.

## Contributing

Contributions are welcome! If you have suggestions for improvement or want to fix a bug, please feel free to:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.
