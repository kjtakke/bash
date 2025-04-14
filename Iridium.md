**Bash**
```bash
#!/bin/bash

payload='{
        "userReferenceID": 99,
        "options": 0,
        "imei": "300534062621380",
        "payload": "48656c6c6f21205468697320697320612074657374206d6573736167652066726f6d20526f636b424c4f434b21"
}'

# Send message
curl -i \
    -H "Accept: application/json" \
    -H "Content-Type:application/json" \
    -X POST --data "${payload}" "https://xlink.readyfleet.com.au/sendMaxwayMessage"
```

**Python** 
```python
import requests
import json


def send_maxway_message(user_reference_id, options, imei, payload,
                        url="https://xlink.readyfleet.com.au/sendMaxwayMessage"):
    """
    Sends a POST request to the given URL with the specified parameters.

    Args:
        user_reference_id (int): The user reference ID.
        options (int): Options flag to determine behavior (default 0).
        imei (str): The IMEI number to send.
        payload (str): The payload in hex format.
        url (str): The URL to send the request to (default is ReadyFleet URL).

    Returns:
        response (object): Response object from the POST request.
    """

    # Define the request payload
    data = {
        "userReferenceID": user_reference_id,
        "options": options,
        "imei": imei,
        "payload": payload
    }

    try:
        # Send the POST request
        response = requests.post(
            url,
            headers={"Accept": "application/json", "Content-Type": "application/json"},
            data=json.dumps(data)
        )
        # Return the response
        return response

    except requests.RequestException as e:
        print(f"Error during the request: {e}")
        return None


# Example usage (replace the data with yours):
if __name__ == "__main__":
    user_reference_id = 99
    options = 0
    imei = "300534062621380"
    payload = "48656c6c6f21205468697320697320612074657374206d6573736167652066726f6d20526f636b424c4f434b21"

    response = send_maxway_message(user_reference_id, options, imei, payload)

    if response:
        print(f"Status Code: {response.status_code}")
        print(f"Response Body: {response.text}")

```