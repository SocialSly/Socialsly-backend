# Social Sly AI: Disposable Communication App Documentation

## Overview

**Social Sly AI** is an AI-powered disposable communication app that allows users to efficiently manage temporary SMS numbers and email addresses. By leveraging GPT-3.5 for natural language understanding, the app ensures seamless interaction for requesting temporary numbers, generating email addresses, managing communication assets, and retrieving messages in real time.

With **Social Sly AI**, users can interact naturally with the chatbot assistant to generate temporary numbers for services like Discord or WhatsApp, create email addresses, list their generated assets, and fetch messages—all while maintaining their privacy.

---

## Features

### 1. Temporary SMS Number Generation
- Generate temporary SMS numbers for various services (e.g., Discord, WhatsApp) and countries.
- The assistant intelligently matches requested services and countries or defaults to predefined values (e.g., **India** and **Discord**).

### 2. Temporary Email Address Generation
- Instantly generate disposable email addresses without additional input.

### 3. List Generated Numbers and Emails
- View all previously generated SMS numbers and email addresses at any time.

### 4. Fetch Messages
- Retrieve messages received on any of your generated phone numbers or email addresses.

### 5. Natural Language Understanding
- The app uses GPT-3.5 to process queries, enabling users to interact with the assistant naturally, as though chatting with a person.

---

## How It Works

The **Social Sly AI** chatbot assistant processes user requests based on specific intents and rules. Below is an overview of its logic and workflows.

### 1. **General Queries**
For simple inquiries (e.g., "Tell me a joke"), the assistant responds with plain-text messages without requiring JSON output.

### 2. **Email Address Generation**
When a user requests an email address, the assistant responds with a JSON object indicating an email request:
```json
{
  "type": "email_request"
}
```

### 3. **SMS Number Generation**
Users can request SMS numbers by specifying a service and country. If no country or service is provided, the system defaults to **India** and **Discord**:
```json
{
  "type": "sms_request",
  "content": {
    "country": "USA",
    "service": "WhatsApp"
  }
}
```

The assistant matches user input against a predefined list of **countries** and **services** (see below for full lists).

### 4. **Listing Numbers and Emails**
Users can request a list of all their generated SMS numbers or email addresses:
- **List SMS Numbers:**
  ```json
  {
    "type": "list_numbers"
  }
  ```
- **List Email Addresses:**
  ```json
  {
    "type": "list_emails"
  }
  ```

### 5. **View Messages**
To fetch messages, users can specify a phone number/email or an index (e.g., "1"):
- **View Messages for an SMS Number:**
  ```json
  {
    "type": "view_messages_intent",
    "index_or_number": "1"
  }
  ```
- **View Messages for an Email Address:**
  ```json
  {
    "type": "view_email_intent",
    "index_or_email": "1"
  }
  ```

---

## Default Behavior

- **Country Default**: If not specified, the default country is **India**.
- **Service Default**: If not specified, the default service is **Discord**.

---

## Supported Countries and Services

### Countries
The app supports a wide range of countries, including but not limited to:
- Afghanistan, Albania, Algeria, Argentina, Australia, Bangladesh, Canada, France, Germany, India, United Kingdom, USA, and many more.

### Services
The app supports a variety of services, including:
- Discord, WhatsApp, Facebook, Instagram, Telegram, Airbnb, PayPal, Netflix, Twitter, Uber, and more.

---

## Workflow Example

### Step 1: Request an SMS Number
**User Input:**  
*"Can I get an SMS number for WhatsApp in the USA?"*  

**Response:**  
```json
{
  "type": "sms_request",
  "content": {
    "country": "USA",
    "service": "WhatsApp"
  }
}
```

---

### Step 2: Fetch Messages
**User Input:**  
*"Show me messages for my WhatsApp number."*  

**Response:**  
```json
{
  "type": "view_messages_intent",
  "index_or_number": "1"
}
```

---

### Step 3: Request an Email Address
**User Input:**  
*"Create an email address for me."*  

**Response:**  
```json
{
  "type": "email_request"
}
```

---

### Step 4: List Emails
**User Input:**  
*"Can you show me all my emails?"*  

**Response:**  
```json
{
  "type": "list_emails"
}
```

---

## API Integration

The app interacts with various APIs to manage communication assets:

1. **SMS Number Generation**  
   The app sends requests to generate temporary SMS numbers based on the specified service and country.

2. **Email Address Generation**  
   The app creates disposable email addresses via a dedicated API.

3. **Message Retrieval**  
   The app retrieves messages from the respective service provider for a specific phone number or email address.

---

## Conclusion

**Social Sly AI** offers a secure and efficient way to manage temporary communication assets, such as disposable phone numbers and email addresses. With its GPT-3.5-powered natural language understanding, the app simplifies user interaction while ensuring privacy and security.

Whether you need an SMS number for service verification, a temporary email for online activities, or a way to view messages, **Social Sly AI** provides a comprehensive solution for disposable communication.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## Contributing

We welcome contributions to improve **Social Sly AI**. If you'd like to contribute:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m 'Add a new feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Submit a pull request.

---

## Contact

For support or inquiries, feel free to reach out at **support@socialsly.ai**.
