# Whatsappcommerce Bot

This folder/repository contains the code to a Whatsapp & Ecommerce tutorial <br/>

<br/><br/>

````markdown
# WhatsApp E-Commerce Chatbot with Node.js

![WhatsApp Chatbot Demo](https://img.shields.io/badge/Demo-YouTube_Link-red)
[![Blog Post](https://img.shields.io/badge/Blog_Post-Dev.to-blue)](https://dev.to/logrocket/build-an-automated-ecommerce-app-with-whatsapp-cloud-api-and-nodejs-5g3a)

A fully automated WhatsApp chatbot for e-commerce stores, built with Node.js and Meta's WhatsApp Cloud API. Customers can browse products, manage carts, and receive invoices via WhatsApp.

---

## 📖 Overview

This repository implements a WhatsApp Business solution that enables:

-   Product catalog browsing
-   Cart management
-   PDF invoice generation
-   Location-based order pickup
-   Read receipts and conversation flows

**Key Features**:

-   Integration with FakeStoreAPI for product data
-   Session-based shopping carts
-   Automated document/location sharing
-   Meta Webhooks for real-time messaging

---

## 🙏 Acknowledgements

**Original Tutorial Author**:  
Daggie Douglas Mwangi  
[View Original Blog Post](https://dev.to/logrocket/build-an-automated-ecommerce-app-with-whatsapp-cloud-api-and-nodejs-5g3a) | [PDF Copy Included](./Tutorial%20by%20Daggie%20Douglas%20Mwangi.pdf)

**Credit Notice**:  
This implementation is based entirely on Daggie Douglas Mwangi's tutorial. All core logic and architectural decisions follow the patterns outlined in the original blog post.

---

## 🛠 Installation

### Prerequisites

1. [Meta Developer Account](https://developers.facebook.com/)
2. [Node.js](https://nodejs.org/) (v16+ recommended)
3. [ngrok Account](https://ngrok.com/)
4. WhatsApp-enabled phone number

### Setup Steps

1. **Clone Repository**
    ```bash
    git clone https://github.com/yourusername/whatsapp-ecommerce-bot.git
    cd whatsapp-ecommerce-bot
    ```
````

2. **Install Dependencies**

    ```bash
    npm install
    ```

3. **Configure Environment**  
   Rename `sample.env.js` to `.env.js` and update:
    ```javascript
    const development = {
        ...process.env,
        NODE_ENV: 'development',
        PORT: '9000',
        Meta_WA_accessToken: 'YOUR_TEMP_ACCESS_TOKEN', // From Meta Dashboard
        Meta_WA_SenderPhoneNumberId: 'YOUR_PHONE_NUMBER_ID',
        Meta_WA_wabaId: 'YOUR_WABA_ID',
        Meta_WA_VerifyToken: 'YOUR_SECURE_TOKEN', // Custom verify token
    };
    ```

---

## 🚀 Running the App

1. **Start Server**

    ```bash
    nodemon app.js
    ```

    or you can run

    ```bash
    nvm use 14.17.5 && npm run dev
    ```

2. **Expose via ngrok** (new terminal)

    ```bash
    ngrok http 9000
    ```

    Copy the HTTPS Forwarding URL (e.g., `https://abc123.ngrok.io`)

3. **Configure Webhooks**  
   In [Meta Developer Dashboard](https://developers.facebook.com/):

    - Set Callback URL: `https://abc123.ngrok.io/meta_wa_callbackurl`
    - Verify Token: Match your `.env.js` `Meta_WA_VerifyToken`
    - Subscribe to "messages" event

4. **Test Flow**  
   Send "Hello" to your WhatsApp Business number to start interaction.

---

## 🔍 Troubleshooting

**Common Issues**:

-   `401 Unauthorized`: Verify access token validity (expires every 24h in dev mode)
-   `404 Template Errors`: Ensure WhatsApp message templates are approved
-   `Ngrok Disconnects`: Keep ngrok terminal active during testing
-   `Session Persistence`: Cart data resets on server restart (uses in-memory Map)

**Debugging Tips**:

```bash
# Check environment variables
console.log(process.env)

# Monitor webhook pings
tail -f ngrok.log
```

---

## 📜 License

MIT License - See [LICENSE](LICENSE).  
**Disclaimer**: Not affiliated with Meta/Facebook. Use WhatsApp API in compliance with [Meta's Policies](https://developers.facebook.com/docs/whatsapp/policy-overview).
