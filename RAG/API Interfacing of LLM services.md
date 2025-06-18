
LLM services that are hosted online of a Cloud or even on localhost can be easily accessed in a optimized and quick way using **Query Router** Service which enables api gateway based communication between client and the service.

![[ac1d5ef8-6685-4576-bb28-677f9a8d77a8.png]]
Well a query router is a efficient method to make query requests to the remote llm hosted services/apps on cloud in form of formats e.g. json query.
The left side of the image depicts an example of a JSON payload sent to a large language model (LLM) API, such as Open AI's or a similar instruction-based model. Here's a breakdown of the attributes shown:

### JSON Payload Attributes (Left Side):

```json
{
  "messages": [
    {
      "content": "...",
      "role": "system"
    },
    {
      "content": "...",
      "role": "user"
    }
  ],
  "temperature": 0.2,
  "top_p": 0.7,
  "max_tokens": 1024,
  "stream": true
}
```

### Explanation:

1. **`messages`**:
    
    - A list of message objects that simulate a conversation between roles.
        
    - **`role`**: Specifies who is speaking. Common values:
        
        - `"system"`: Instructions or behavior settings for the assistant.
            
        - `"user"`: The user’s query or prompt.
            
        - `"assistant"` (not shown here): Previous model responses, if context/history is needed.
            
    - **`content`**: The actual text/message for each role.
        
2. **`temperature`**:
    
    - Controls randomness in output.
        
    - Lower values like `0.2` make the output more focused and deterministic.
        
    - Higher values increase creativity.
        
3. **`top_p`**:
    
    - Nucleus sampling parameter.
        
    - The model considers the smallest set of tokens whose cumulative probability is ≥ `top_p`.
        
    - Combines with `temperature` to control randomness.
        
4. **`max_tokens`**:
    
    - Limits the maximum number of tokens (words/pieces) in the generated response.
        
    - Here it's set to `1024`.
        
5. **`stream`**:
    
    - If `true`, the response is returned as a stream of tokens (useful for live typing or partial outputs).
        

This configuration is typically used in chat-based interfaces to control how the LLM responds to input.

### Sending API requests to NGC models

![[Pasted image 20250613180433.png]]

### 🔍 **Breakdown of the `curl` command**

```bash
curl --request POST \
--url https://api.nvcf.nvidia.com/v2/nvcf/pexec/functions/8f4118ba-60a8-4e6b-8574-e38a4067a4a3 \
--header 'Authorization: Bearer $API_KEY' \
--header 'Accept: text/event-stream' \
--header 'Content-Type: application/json' \
--data '{
  "messages": [
    {
      "content": "I am going to Paris, what should I see?",
      "role": "user"
    }
  ],
  "temperature": 0.2,
  "top_p": 0.7,
  "max_tokens": 1024,
  "seed": 42,
  "stream": true
}'
```

---

###  **Headers**

- **`Authorization: Bearer $API_KEY`**
    
    - This header passes the **API key** to authenticate your request.
        
    - `$API_KEY` is a placeholder; you must replace it with your actual NVIDIA API key.
        
- **`Accept: text/event-stream`**
    
    - Indicates the client expects the response in **streaming mode**.
        
    - Commonly used for live token-by-token output (like typing effect).
        
- **`Content-Type: application/json`**
    
    - Specifies that the request body is formatted in JSON.
        

---

### 📦 **Payload (`--data`) Fields**

This block matches what was in your previous image:

```json
{
  "messages": [
    {
      "content": "I am going to Paris, what should I see?",
      "role": "user"
    }
  ],
  "temperature": 0.2,
  "top_p": 0.7,
  "max_tokens": 1024,
  "seed": 42,
  "stream": true
}
```

- **`messages`**: List of chat messages (mimicking a chat interface).
    
- **`temperature`**: Controls randomness — `0.2` is more deterministic.
    
- **`top_p`**: Nucleus sampling parameter (limits sampling to top tokens).
    
- **`max_tokens`**: Max number of tokens in the model’s reply.
    
- **`seed`**: Fixes randomness for reproducibility.
    
- **`stream`**: Enables token streaming (live output instead of waiting for the full answer).
    

---

### 📌 API Endpoint

```
https://api.nvcf.nvidia.com/v2/nvcf/pexec/functions/<function-id>
```

- This calls a specific deployed **function (LLM)** in NVIDIA's **NIM (NVIDIA Inference Microservices)**.
    
- The UUID at the end (`8f4118ba...`) identifies the deployed model instance.
    

## Python code for the same

```python
import requests
import json

# Replace with your actual API key and model function URL
API_KEY = "your_api_key_here"
ENDPOINT_URL = "https://api.nvcf.nvidia.com/v2/nvcf/pexec/functions/8f4118ba-60a8-4e6b-8574-e38a4067a4a3"

headers = {
    "Authorization": f"Bearer {API_KEY}",
    "Accept": "text/event-stream",  # For streaming responses
    "Content-Type": "application/json"
}

payload = {
    "messages": [
        {
            "content": "I am going to Paris, what should I see?",
            "role": "user"
        }
    ],
    "temperature": 0.2,
    "top_p": 0.7,
    "max_tokens": 1024,
    "seed": 42,
    "stream": True
}

# Make the POST request
response = requests.post(ENDPOINT_URL, headers=headers, json=payload, stream=True)

# Handle streaming output
if response.status_code == 200:
    print("Response (streamed):")
    for line in response.iter_lines():
        if line:
            print(line.decode("utf-8"))
else:
    print(f"Request failed with status {response.status_code}: {response.text}")

```
![[download.png]]