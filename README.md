# GHG-GoHighLevel-Playground
GoHighLevel (GHL) is a CRM platform that offers APIs to interact with various features like leads, workflows, pipelines, and more. To use the GoHighLevel API in Python, you will need to send HTTP requests (such as GET, POST, PUT) to their endpoints, typically using a library like requests.
Steps to Access GoHighLevel API

    Obtain API Key: You will need your GoHighLevel API key, which can be found in the GoHighLevel dashboard under Settings > API.

    API Documentation: Familiarize yourself with the official GoHighLevel API documentation. The base URL typically is https://api.gohighlevel.com/v1/.

    Install Required Libraries: Use the requests library in Python to interact with the GoHighLevel API.

    pip install requests

    Make API Requests: Use Python to interact with the GoHighLevel API. Below are a few basic examples.

Example 1: Authenticating and Sending Requests to GoHighLevel API
Python Code to Create a Lead in GoHighLevel

In this example, we will send a POST request to create a new lead.

import requests
import json

# Replace with your actual API Key
API_KEY = 'your_api_key_here'

# Define the API endpoint
url = "https://api.gohighlevel.com/v1/contacts"

# Define the headers with your API Key
headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

# Example lead data to send to the API
data = {
    "firstName": "John",
    "lastName": "Doe",
    "email": "johndoe@example.com",
    "phone": "+1234567890",
    "address": "1234 Elm Street",
    "city": "Sample City",
    "state": "SC",
    "zip": "12345",
}

# Send the POST request to create a new lead
response = requests.post(url, headers=headers, data=json.dumps(data))

# Check if the request was successful
if response.status_code == 201:
    print(f"Lead created successfully: {response.json()}")
else:
    print(f"Error: {response.status_code}, {response.text}")

Explanation of the Code:

    API Key: You need to replace 'your_api_key_here' with your GoHighLevel API key.
    Endpoint: The endpoint for creating a contact (lead) in GoHighLevel is /contacts.
    Headers: The Authorization header contains your API key, and Content-Type is set to application/json because we are sending JSON data.
    Data: The contact data (first name, last name, email, phone, etc.) is passed as a JSON object.
    Response: If the response status is 201, the lead is created successfully. Otherwise, the error message is printed.

Example 2: Retrieving a Contact from GoHighLevel

To get information about a contact, you would make a GET request with the contact ID.

import requests

# Replace with your actual API Key and the contact ID you want to retrieve
API_KEY = 'your_api_key_here'
CONTACT_ID = 'contact_id_here'

# Define the API endpoint
url = f"https://api.gohighlevel.com/v1/contacts/{CONTACT_ID}"

# Define the headers with your API Key
headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

# Send the GET request to retrieve contact details
response = requests.get(url, headers=headers)

# Check if the request was successful
if response.status_code == 200:
    print(f"Contact details: {response.json()}")
else:
    print(f"Error: {response.status_code}, {response.text}")

Explanation:

    The CONTACT_ID is a unique identifier for a contact in GoHighLevel.
    The API request fetches contact details using the endpoint contacts/{contact_id}.

Example 3: Listing All Contacts in GoHighLevel

To retrieve a list of all contacts:

import requests

# Replace with your actual API Key
API_KEY = 'your_api_key_here'

# Define the API endpoint for listing all contacts
url = "https://api.gohighlevel.com/v1/contacts"

# Define the headers with your API Key
headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

# Send the GET request to fetch all contacts
response = requests.get(url, headers=headers)

# Check if the request was successful
if response.status_code == 200:
    contacts = response.json()
    print(f"Contacts: {contacts}")
else:
    print(f"Error: {response.status_code}, {response.text}")

Example 4: Updating a Contact in GoHighLevel

To update a contact’s information:

import requests
import json

# Replace with your actual API Key and Contact ID
API_KEY = 'your_api_key_here'
CONTACT_ID = 'contact_id_here'

# Define the API endpoint to update the contact
url = f"https://api.gohighlevel.com/v1/contacts/{CONTACT_ID}"

# Define the headers with your API Key
headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

# Example data to update
data = {
    "firstName": "UpdatedName",
    "lastName": "UpdatedLastName",
    "email": "updatedemail@example.com",
}

# Send the PUT request to update the contact
response = requests.put(url, headers=headers, data=json.dumps(data))

# Check if the request was successful
if response.status_code == 200:
    print(f"Contact updated successfully: {response.json()}")
else:
    print(f"Error: {response.status_code}, {response.text}")

Example 5: Deleting a Contact in GoHighLevel

To delete a contact from GoHighLevel:

import requests

# Replace with your actual API Key and Contact ID
API_KEY = 'your_api_key_here'
CONTACT_ID = 'contact_id_here'

# Define the API endpoint to delete the contact
url = f"https://api.gohighlevel.com/v1/contacts/{CONTACT_ID}"

# Define the headers with your API Key
headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Content-Type": "application/json"
}

# Send the DELETE request to remove the contact
response = requests.delete(url, headers=headers)

# Check if the request was successful
if response.status_code == 204:
    print("Contact deleted successfully.")
else:
    print(f"Error: {response.status_code}, {response.text}")

Conclusion

These examples demonstrate how you can use the GoHighLevel API to perform basic operations like creating, retrieving, updating, and deleting contacts. By integrating GoHighLevel API into your Python code, you can build powerful automation systems for managing leads, tracking conversations, and improving your customer relationship management in the real estate sector.

Remember to:

    Replace the placeholder API key with your actual key.
    Ensure your GoHighLevel account has access to the necessary endpoints (API access may depend on your subscription plan).
    Handle exceptions and API rate limits for robust production code.
