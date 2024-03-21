# air-quality
from twilio.rest import Client

# Twilio Account SID and Auth Token (replace with your actual credentials)
account_sid = 'ACf78ef9e5d5568358c941bab618f19e14'
auth_token = '8cb9f37294cd97975cd1d4ce5f80f3a1'

# Initialize Twilio client
client = Client(account_sid, auth_token)
def send_sms_alert(recipient_number, message):
    try:
        # Send SMS message using Twilio API
        client.messages.create(
            to=recipient_number,
            from_='+14242772380',  # Twilio phone number (replace with your Twilio number)
            body=message
        )
        print(f"SMS alert sent successfully to {recipient_number}")
    except Exception as e:
        print(f"Error sending SMS alert: {str(e)}")
        # Example usage: Trigger SMS alert for high pollution level
recipient_number = '+14242772380'  # Replace with recipient's phone number
pollution_level = 150  # Example pollution level (replace with actual value)

if pollution_level > 100:
    message = f"Alert: High pollution level detected ({pollution_level} AQI). Take necessary precautions."
    send_sms_alert(recipient_number, message)
