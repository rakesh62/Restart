# Restart App

A beautiful and interactive SwiftUI application designed to inspire users with motivational content and smooth animations. This project demonstrates modern iOS development practices using SwiftUI with interactive gestures, state management, and engaging visual design.

## 📱 Overview

The **Restart App** is a SwiftUI-based iOS application that features an onboarding flow with interactive elements and a home screen with motivational content. The app uses smooth animations, gesture recognition, and haptic feedback to create an engaging user experience.

## 🎯 Key Features

- **Interactive Onboarding Screen**: Draggable character with smooth animations and visual feedback
- **Home Screen**: Animated character with inspirational quotes
- **Gesture Recognition**: Drag gestures for interactive character movement
- **Haptic Feedback**: Tactile feedback on user interactions
- **Audio Player**: Sound effects integration (success.m4a, chimeup.mp3)
- **Responsive Design**: Supports all iOS devices (iPhone SE to iPad)
- **State Management**: Uses @AppStorage for persistent app state
- **Dynamic Animations**: Easing animations and view transitions

## 📁 Project Structure

```
Restart/
├── RestartApp.swift              # App entry point
├── Screens/
│   ├── ContentView.swift         # Root view with navigation logic
│   ├── OnboardingView.swift      # Interactive onboarding flow
│   └── HomeView.swift            # Main home screen with animations
├── Views/
│   └── CircleGroupView.swift     # Reusable animated circle component
├── Sounds/
│   ├── AudioPlayer.swift         # Audio playback utility
│   ├── chimeup.mp3               # Chime sound effect
│   └── success.m4a               # Success sound effect
├── Assets.xcassets/
│   ├── Characters/               # Character images
│   │   ├── character-1.imageset  # Onboarding character
│   │   └── character-2.imageset  # Home screen character
│   ├── Colors/                   # Color set assets
│   │   ├── ColorBlue.colorset    # Primary blue color
│   │   └── ColorRed.colorset     # Secondary red color
│   ├── AppIcon.appiconset        # App icons for various devices
│   └── AccentColor.colorset      # Accent color
└── Info.plist                     # App configuration
```

## 📋 File Descriptions

### **RestartApp.swift**
- Entry point of the application
- Defines the main App structure
- Sets up the initial ContentView in a WindowGroup

### **Screens/**

#### **ContentView.swift**
- Root view that controls navigation between screens
- Uses @AppStorage to persist onboarding state
- Conditionally displays OnboardingView or HomeView based on user progress

#### **OnboardingView.swift**
- Interactive onboarding experience
- Features:
  - Animated header text that transitions between "Share." and "Give."
  - Draggable character image with rotation effect based on drag distance
  - Animated circle group background
  - Drag gesture handling with haptic feedback
  - Skip button and drag-to-confirm slider button
  - Smooth opacity and offset animations
  - All animations use easeOut timing with 1-second duration

#### **HomeView.swift**
- Main screen displayed after onboarding
- Features:
  - Animated character that bounces up and down
  - Motivational quote display
  - Circle group background with subtle animation
  - Restart button to return to onboarding
  - Uses infinite animation loop for character movement

### **Views/**

#### **CircleGroupView.swift**
- Reusable component displaying animated concentric circles
- Customizable shape color and opacity
- Animates on appearance with blur, opacity, and scale effects
- Used in both OnboardingView and HomeView with different styling

### **Sounds/**

#### **AudioPlayer.swift**
- Utility function for playing sound effects
- Uses AVAudioPlayer for audio playback
- Function signature: `playSound(sound: String, type: String)`
- Includes error handling for missing audio files

**Audio Files:**
- `chimeup.mp3`: Brief chime sound effect
- `success.m4a`: Success notification sound

### **Assets/**

- **Characters**: Character images for visual content
  - character-1: Onboarding screen character
  - character-2: Home screen character
- **Colors**: Custom color sets for consistent theming
  - ColorBlue: Primary theme color
  - ColorRed: Secondary accent color
- **AppIcon**: Icons for all required iOS device sizes and scales

## 🎨 Design Features

### Color Scheme
- **Primary**: Blue (#ColorBlue) - Used in onboarding screen background
- **Secondary**: Red (#ColorRed) - Accent color for buttons and highlights
- **Text**: White text on blue background for high contrast

### Animations
- **Easing**: EaseOut timing for smooth, natural animations
- **Duration**: 1 second for most view animations, 0.25 seconds for quick transitions
- **Effects**: Opacity changes, offset movements, scale effects, and rotation
- **Gesture-based**: Interactive animations respond to user drag gestures

### Responsive Layout
- **Device Support**: All iOS devices from iPhone SE to iPad
- **GeometryReader**: Used for responsive width calculations
- **Safe Area**: Properly handled with ignoresSafeArea modifiers where appropriate

## 🔄 App Flow

```
RestartApp (Entry Point)
    ↓
ContentView (Navigation Root)
    ├─ If isOnboardingViewActive = true
    │   ↓
    │  OnboardingView
    │   └─ User interacts and completes onboarding
    │       └─ Sets isOnboardingViewActive = false
    │
    └─ If isOnboardingViewActive = false
        ↓
       HomeView
        └─ User can tap "Restart" button
            └─ Sets isOnboardingViewActive = true
```

## 🛠️ Technologies Used

- **SwiftUI**: Modern declarative UI framework
- **AVFoundation**: Audio playback
- **AppStorage**: Persistent user preferences
- **UINotificationFeedbackGenerator**: Haptic feedback
- **Gesture Recognition**: DragGesture for interactive elements

## 📱 iOS Requirements

- **Minimum iOS Version**: iOS 15+
- **Supported Devices**: iPhone, iPad
- **Orientations**: Portrait (primary support)

## 💾 State Management

The app uses @AppStorage for persisting the onboarding state:
```swift
@AppStorage("onboarding") var isOnboardingViewActive: Bool = true
```

This ensures that once a user completes the onboarding, they won't see it again unless they explicitly restart.

## 🎬 Animation Details

### OnboardingView Animations
- **Header**: Opacity and vertical offset animation (1s easeOut)
- **Character**: Opacity animation, drag-based translation and rotation
- **Circle Background**: Blur effect synchronized with character drag
- **Button Width**: Animated from 0 to full width on completion

### HomeView Animations
- **Character**: Vertical bounce animation (4s infinite easeInOut)
- **Circle Background**: Fade in and scale animation on appearance

## 🔊 Sound Integration

The app can play sound effects using the AudioPlayer utility:
```swift
playSound(sound: "success", type: "m4a")
playSound(sound: "chimeup", type: "mp3")
```

## 📝 Notes

- All animations are optimized for performance with proper use of withAnimation blocks
- The app follows SwiftUI best practices with proper state management
- Color assets are centralized for consistent theming across the app
- The codebase demonstrates effective use of view composition and reusable components

## 🚀 Future Enhancement Ideas

- Add more onboarding screens
- Implement user preferences/settings screen
- Add more sound effects and music options
- Include share functionality with social media integration
- Add progress tracking and achievement system
- Implement dark mode support
- Add localization for multiple languages

## 👨‍💻 Developer

Created by Rakesh Jadhav

