# STT Interface - Machine Vision Application

A React Native Expo application that provides a speech-to-text interface for communicating with industrial machines through a natural language processing server.

## 🚀 Core Features

### Real-time Audio Recording and Transcription

- Record audio using device microphone
- Stream audio data to server for real-time transcription
- Display transcribed text and analysis results

### Machine Management

- View list of available industrial machines
- Connect/disconnect to machines via WebSocket
- Monitor machine states (Connect, Disconnect, Offline, Busy)

### Secure Connection Management

- Connect to NLP server using URL and API key
- Store multiple credential sets securely
- Automatic reconnection and authentication

### Message Analysis

- Send text messages for NLP analysis
- Receive processed commands and responses
- Real-time communication with machines

## 📱 Application Routes

### Authentication & Settings

- **`/settings/connect`** - Initial connection screen where users enter server URL and API key
- **`/settings/storedCredentials`** - Manage saved credential sets

### Main Application

- **`/(tabs)/record`** - Primary recording interface with audio controls and message input
- **`/(tabs)/machines`** - Machine management dashboard showing available machines and connection status

## 🔗 Communication Architecture

The application communicates with the Machine Vision NLP Server via WebSocket:

### Connection Process

1. User enters server URL and API key on connect screen
2. WebSocket connection established with authentication
3. Upon successful auth, redirected to main recording interface

### Message Types

- **Authentication**: `auth_response` - Confirms connection validity
- **Transcription**: `transcribe_response` - Returns transcribed audio text
- **Machine Updates**: `update_machines` - Lists available machines and states
- **Machine Control**: `machine_connection_status` - Connection/disconnection results
- **Analysis**: Send text messages for NLP processing

### Audio Streaming

- Audio captured using `expo-av` and `react-native-live-audio-stream`
- Streamed in chunks via WebSocket for real-time processing
- Supports continuous recording with live transcription feedback

## ⚙️ Environment Variables

This application does not require environment variables. All configuration is handled through the user interface:

- **Server URL**: Entered manually in the connection screen
- **API Key**: Provided by user for authentication
- **Credentials**: Stored securely using `expo-secure-store`

## 🛠️ Installation and Setup

### Prerequisites

- Node.js (LTS version)
- npm or yarn
- Expo CLI

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd MachineVisionApplication

# Install dependencies
npm install
```

### Running the Application

```bash
# Start Expo development server
npx expo start

# Run on specific platform
npx expo run:ios      # iOS simulator
npx expo run:android  # Android emulator
```

## 📋 Dependencies

### Core Dependencies

- **React Native & Expo**: Framework and development platform
- **expo-av**: Audio recording and playback
- **react-native-live-audio-stream**: Real-time audio streaming
- **@react-native-async-storage/async-storage**: Local data storage
- **expo-secure-store**: Secure credential storage
- **expo-router**: File-based routing

### UI & Navigation

- **@expo/vector-icons**: Icon library
- **react-native-safe-area-context**: Safe area handling
- **react-native-screens**: Screen management

## 🔧 Development

### Project Structure

```
MachineVisionApplication/
├── app/                    # Main application screens (file-based routing)
│   ├── (tabs)/            # Tab navigation screens
│   │   ├── machines.tsx   # Machine management
│   │   └── record.tsx     # Recording interface
│   ├── settings/          # Settings screens
│   │   ├── connect.tsx    # Connection setup
│   │   └── storedCredentials.tsx
│   └── index.tsx          # Root redirect
├── components/            # Reusable UI components
├── contexts/              # React contexts for state management
│   ├── ConnectivityContext.tsx  # WebSocket & connection logic
│   ├── CredentialsContext.tsx   # Credential management
│   └── AudioContext.tsx         # Audio state
├── constants/             # Styling constants
└── hooks/                 # Custom React hooks
```

### Key Contexts

- **ConnectivityContext**: Manages WebSocket connection, message sending/receiving, machine state
- **CredentialsContext**: Handles secure storage and retrieval of server credentials
- **AudioContext**: Audio recording state and controls

## 🚀 Getting Started

1. **Setup Server**: Ensure the Machine Vision NLP Server is running and accessible
2. **Launch App**: Run `npx expo start` and open in Expo Go or simulator
3. **Connect**: Enter server URL and API key in the connection screen
4. **Record**: Use the recording interface to capture audio and send messages
5. **Manage Machines**: Switch to machines tab to connect/disconnect from available machines

## 📚 Related Projects

- **Machine Vision NLP Server**: Django-based WebSocket server handling NLP and machine communication
- **Machine Vision Application**: This Expo/React Native client application

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.
