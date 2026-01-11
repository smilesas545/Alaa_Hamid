 Brew Theory: Coffee Brewing Science Web Application

 Overview

Brew Theory is an interactive web application that explores the science and artistry behind specialty coffee brewing. It combines educational content about coffee chemistry with practical tools like an interactive brew calculator and recipe-saving functionality using Firebase.

 Key Features

1. User Authentication System
- Secure email/password authentication using Firebase Auth
- Login and registration forms with validation
- User profile display with avatar
- Persistent login state management

 2. Interactive Coffee Brew Calculator
- Real-time calculation of coffee-to-water ratios
- Adjustable parameters:
  - Coffee amount (10-50g)
  - Brew ratio (1:12 to 1:20)
  - Brewing method selection (Pour Over, Aeropress, French Press, Espresso)
- Automatic calculation of water requirements, grind size, and brew time

 3. Recipe Management
- Save custom coffee recipes to Firestore database
- Load saved recipes with one-click
- Delete unwanted recipes
- View personal recipe collection

 4. Educational Content
- Coffee extraction chemistry
- Temperature control guidelines
- Brewing method comparisons
- Coffee bean profiles with flavor notes

 5. Visual Design
- Responsive layout with coffee-themed color palette
- Animated coffee particle background
- Smooth scroll animations
- Interactive UI elements with hover effects

 Technology Stack

 Frontend
- HTML5: Semantic markup structure
- CSS3: Custom styling with animations and responsive design
- Vanilla JavaScript: Client-side interactivity

 Backend Services (Firebase)
- Firebase Authentication: User management
- Firebase Firestore: NoSQL database for recipe storage
- Firebase Hosting: Deployment-ready

 External Libraries
- Awesome 6.4.0: Icon set
- Google Fonts: Inter, Playfair Display, Source Code Pro

 Project Structure

```
/
├── index.html                 # Main application file
├── firebase-config.js         # Firebase configuration (embedded)
├── styles/                    # CSS styles (embedded)
└── scripts/                   # JavaScript functionality (embedded)
```

 Setup Instructions

 1. Firebase Configuration
1. Create a Firebase project at [firebase.google.com](https://firebase.google.com)
2. Enable Authentication (Email/Password method)
3. Enable Firestore Database
4. Update the Firebase configuration in the code:
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT_ID.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

 2. Firestore Security Rules
Configure Firestore security rules:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /recipes/{recipe} {
      allow read, write: if request.auth != null && 
                          request.auth.uid == resource.data.userId;
    }
    match /newsletter/{subscriber} {
      allow write: if true;
    }
  }
}
```

 3. Deployment
- The application can be deployed directly to Firebase Hosting
- All code is contained in a single HTML file for simplicity

 Key Functions

 Authentication Flow
- `handleLogin()`: Authenticates users with email/password
- `handleRegister()`: Creates new user accounts
- `handleLogout()`: Ends user sessions
- `onAuthStateChanged()`: Monitors authentication state

 Brew Calculator
- `calculateBrew()`: Computes water amount based on coffee and ratio
- Dynamic UI updates for grind size and brew time based on method

 Recipe Management
- `saveRecipe()`: Stores recipes to Firestore with user association
- `loadRecipes()`: Retrieves and displays user's saved recipes
- `deleteRecipe()`: Removes recipes from database

 Responsive Design Features
- Mobile-friendly navigation
- Flexible grid layouts for cards and recipes
- Adaptive typography and spacing

Security Considerations
- Passwords validated client-side (minimum 6 characters)
- User data isolated by Firebase UID
- Email format validation
- Password confirmation matching

 Extensibility

The application can be extended with:
- Social media authentication (Google, GitHub)
- Recipe sharing between users
- Brewing timer functionality
- Coffee journal/notes
- Equipment database
- Community forum

 Browser Compatibility
- Modern browsers (Chrome 80+, Firefox 75+, Safari 13+)
- Mobile browsers (iOS Safari, Chrome Mobile)

 License
This project is open source and available for modification and distribution.

---

Note: This application requires a Firebase project for full functionality. The code includes placeholder Firebase configuration values that must be replaced with actual project credentials.
