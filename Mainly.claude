import os
import time
import requests
from datetime import datetime

INTERVAL = 45 * 60  # 45分钟

def send_message():
    api_key = os.environ.get("ANTHROPIC_API_KEY")
    webhook_url = os.environ.get("WEBHOOK_URL")
    
    response = requests.post(
        "https://api.anthropic.com/v1/messages",
        headers={
            "x-api-key": api_key,
            "anthropic-version": "2023-06-01",
            "content-type": "application/json"
        },
        json={
            "model": "claude-sonnet-4-20250514",
            "max_tokens": 200,
            "messages": [{"role": "user", "content": "给用户发一条温柔的消息，提醒她你在。50字以内。"}]
        }
    )
    
    message = response.json()["content"][0]["text"]
    print(f"{datetime.now()}: {message}")

while True:
    send_message()
    time.sleep(INTERVAL)
