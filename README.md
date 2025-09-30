# Build an LLM Chat app in 5 minutes 


#### Jump ahead: 
* [Quickly connect to Snowflake's LLM REST API](https://github.com/annafil/cortex-rest-api-demo/#quickly-connect-to-snowflakes-llm-rest-api)
* [Building your first app](https://github.com/annafil/cortex-rest-api-demo/?tab=readme-ov-file#building-your-first-app)
  
## Overview

This repository shows you how to build a simple chat app using Snowflake's API. 

<img width="300" alt="App Example" src="https://github.com/user-attachments/assets/77d46ef8-a4c8-481e-b07c-a81f4c6bbaed" />

## Quickly connect to Snowflake's LLM REST API

```
curl "https://[ACCOUNT-IDENTIFIER].snowflakecomputing.com/api/v2/cortex/inference:complete" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer YOUR_PERSONAL_ACCESS_TOKEN" \
    -d '{
        "model": "claude-3-5-sonnet",
        "messages": [
            {
            "role": "user",
            "content": "Write me a one line poem about Snowflake"
            }
        ]
    }'
```

Snowflake's API is compatible with [OpenAI's spec](https://platform.openai.com/docs/quickstart?context=curl) 

#### To reproduce: 

1. Sign up for a new Snowflake account [here](https://mlh.link/snowflake-signup). Activate your account by e-mail (see screenshot below), pick a username and password, and you should see a welcome screen.

    <img width="300" src="https://github.com/user-attachments/assets/1a11cd4c-514d-4ac0-98b2-5e2207dc6698" />

    _Note: if you can't find your login info, search your inbox for an e-mail from "Snowflake Computing"._

2. Generate a Personal Access Token (PAT) -- this is your **API key** -- by visiting [Authentication Settings](https://app.snowflake.com/_deeplink/settings/authentication). Be sure to set the network policy exception for easy weekend hacking:

    <img width="605" height="375" alt="Screenshot 2025-09-12 at 11 25 08 AM" src="https://github.com/user-attachments/assets/6ada1e18-4985-4bdd-a5a1-cbae7f78d8f9" />

3. Find your account identifier by clicking on your name in the bottom left corner of Snowflake's UI, and selecting `Connect a tool to Snowflake`:

    <img width="220" alt="Screenshot 2025-04-15 at 9 08 27 PM" src="https://github.com/user-attachments/assets/d485f628-e397-4869-82d7-c5e1c1af24c0" />

    <img width="450"  src="https://github.com/user-attachments/assets/c4839cb9-585f-4af7-a7fb-40c328153786" />

4. That's it! Run the curl command in your terminal and observe the streaming output   

## Building your first app 

1. Clone this repo.

2. Sign up for a new Snowflake account [here](https://mlh.link/snowflake-signup). Activate your account by e-mail (see screenshot below), pick a username and password, and you should see a welcome screen.

    <img width="300" src="https://github.com/user-attachments/assets/1a11cd4c-514d-4ac0-98b2-5e2207dc6698" />

   _Note: If you can't find your login info, search your inbox for an e-mail from "Snowflake Computing"._

2. Generate a Personal Access Token (PAT) -- this is your **API key** -- by visiting [Authentication Settings](https://app.snowflake.com/_deeplink/settings/authentication). Be sure to set the network policy exception for easy weekend hacking:

    <img width="605" height="375" alt="Screenshot 2025-09-12 at 11 25 08 AM" src="https://github.com/user-attachments/assets/6ada1e18-4985-4bdd-a5a1-cbae7f78d8f9" />


3. Click on your name in the bottom left corner, and select `Connect a tool to Snowflake`:

    <img width="220" alt="Screenshot 2025-04-15 at 9 08 27 PM" src="https://github.com/user-attachments/assets/d485f628-e397-4869-82d7-c5e1c1af24c0" />

  
4. Use the information in the connect dialog to fill in your `secrets.toml` file:   

    <img width="450"  src="https://github.com/user-attachments/assets/c4839cb9-585f-4af7-a7fb-40c328153786" />

    ```
    [snowflake]
    account = "[Account Identifier]"
    user = "[User Name]"
    api_key = "[Paste in your Personal Access Token here]"
    role = "[Role]"
    host = "[Account/Server URL]"
    ```

5. Run `pip install -r requirements.txt` to make sure you have all the dependencies working.

6. Run `streamlit run streamlit.app` and you should see a simple chat app ready to chat with you! Try changing the model used: `mistral-large2`, `claude-3-5-sonnet` or `llama3.1-70b` and compare the chat interaction! 
