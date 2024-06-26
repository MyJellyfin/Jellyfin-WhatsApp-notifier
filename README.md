# Jellyfin WhatsApp Notifier

This application serves as a bridge between Jellyfin Media Server and WhatsApp, sending notifications about Jellyfin events to a specified WhatsApp group.

## Features

- Receives webhook notifications from Jellyfin
- Processes various Jellyfin event types:
  - Item Added
  - Playback Start
  - Playback Stop
  - Authentication Success
  - Authentication Failure
- Sends formatted notifications to a WhatsApp group
- Automatically reconnects to WhatsApp if disconnected

## Prerequisites

- Node.js (v14 or later recommended)
- npm (Node Package Manager)
- A Jellyfin server with webhook capabilities
- A WhatsApp account for the bot

## Installation

1. Clone this repository:
```cmd
git clone https://github.com/Myjellyfin/Jellyfin-WhatsApp-notifier.git
cd Jellyfin-Whatsapp-notifier
```
2. Install dependencies:
```cmd
npm install
```
3. Create a `.env` file in the root directory with the following content:
PORT=3000
WHATSAPP_GROUP_ID=your_whatsapp_group_id
Replace `your_whatsapp_group_id` with the actual ID of your WhatsApp group.

## Usage

1. Start the server:
```cmd
npm run start
```
2. The first time you run the app, you'll need to scan a QR code to authenticate the WhatsApp session.

3. Configure your Jellyfin server to send webhook notifications to `http://your-server-ip:3000/webhook`

## API Endpoints

- `POST /webhook`: Receives notifications from Jellyfin
- `GET /groups`: Lists available WhatsApp groups (useful for finding group IDs)

## Notification Formats

- **Item Added**: `New {ItemType} Added\nName: {Name}\nRuntime: {RunTime}\nPremiere Date: {PremiereDate}`
- **Playback Start**: `{NotificationUsername} started watching\n{Name}`
- **Playback Stop**: `{NotificationUsername} stopped watching\n{Name}`
- **Authentication Success**: `Successful Login\n{NotificationUsername} Logged in`
- **Authentication Failure**: `Failed Login Attempt\n{Username} login attempt failed`


## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.
