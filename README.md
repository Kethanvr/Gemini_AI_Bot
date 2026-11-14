# WhatsApp Gemini Bot

A Flask webhook prototype that connects incoming WhatsApp Cloud API messages to Google Gemini. The current handler processes text and attempts to handle image, audio, and PDF messages.

## Configuration

The application reads these environment variables:

- `WA_TOKEN` — WhatsApp Cloud API access token
- `GEN_API` — Google Gemini API key
- `PHONE_ID` — WhatsApp phone-number ID
- `PHONE_NUMBER` — recipient number used by the current sender function

Do not commit real credentials. The webhook verification value is currently fixed in `main.py`; replace it with a unique secret and use the same value in your Meta webhook configuration before exposing the endpoint.

## Run locally

The project uses Flask and runs on port `8000`:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python main.py
```

The current requirements file does not list `requests`, which `main.py` imports. Install it in the environment or correct the dependency file before running. A local server also needs a publicly reachable HTTPS webhook URL to receive WhatsApp callbacks.

This repository is an experimental integration. Review provider requirements, webhook validation, error handling, and data handling before deploying it.
