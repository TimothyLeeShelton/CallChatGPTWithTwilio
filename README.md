# AI-Powered Twilio Voice Assistant

This project is a Flask-based AI-powered voice assistant that integrates with Twilio to facilitate phone conversations using OpenAI's GPT-3.5-turbo. The assistant engages users in natural conversations, responds to their speech inputs, and dynamically generates AI-driven replies in real-time.

## Features
- **Twilio Voice Integration**: Initiates and handles voice calls via Twilio API.
- **OpenAI GPT-3.5**: Generates intelligent responses in a conversational manner.
- **Flask Web Server**: Manages API endpoints for handling calls and user inputs.
- **Ngrok Tunneling**: Creates a public webhook URL for Twilio integration.
- **Real-Time Speech Processing**: Uses Twilio's speech recognition to process user inputs dynamically.
- **Pre-Warmed OpenAI Connection**: Ensures faster response times by maintaining an active connection to OpenAI.

## Installation

### Prerequisites
- Python 3.7+
- Twilio account with API credentials
- OpenAI API key
- Ngrok account with authentication token

### Setup
1. **Clone the repository**:
   ```sh
   git clone https://github.com/your-username/ai-twilio-voice-assistant.git
   cd ai-twilio-voice-assistant
   ```

2. **Create a virtual environment and install dependencies**:
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   pip install -r requirements.txt
   ```

3. **Set up environment variables**:
   Create a `.env` file and add the following:
   ```ini
   TWILIO_ACCOUNT_SID=your_twilio_account_sid
   TWILIO_AUTH_TOKEN=your_twilio_auth_token
   TWILIO_PHONE_NUMBER=your_twilio_phone_number
   OPENAI_API_KEY=your_openai_api_key
   NGROK_AUTH_TOKEN=your_ngrok_auth_token
   ```

4. **Start the Flask server**:
   ```sh
   python app.py
   ```
   The server will run on `http://127.0.0.1:5000`.

5. **Run Ngrok to expose the local server**:
   ```sh
   ngrok http 5000
   ```
   Copy the public `https://` URL and use it as the Twilio webhook.

## Usage

### Initiating a Call
Send a POST request to the `/initiate-call` endpoint with a JSON payload:
```json
{
  "phone_number": "+1234567890",
  "theme": "Casual conversation about technology"
}
```

### Handling User Input
Twilio will forward the speech input to `/handle-user-input`, and the AI will generate a response.

## Deployment
For production, consider deploying with:
- **Gunicorn** for running the Flask app
- **A reverse proxy** like Nginx
- **Cloud services** such as AWS, Heroku, or Google Cloud

## License
This project is licensed under the MIT License.
