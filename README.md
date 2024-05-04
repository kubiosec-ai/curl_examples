# curl_examples
```
YOUR_API_KEY=xxxxxx
```
## Embedding
```
curl https://api.openai.com/v1/embeddings \
  -X POST \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"input": "The food was delicious and the waiter...",
       "model": "text-embedding-ada-002"}'
```
## Completion
```
curl https://api.openai.com/v1/completions \
-H "Content-Type: application/json" \
-H "Authorization: Bearer $YOUR_API_KEY" \
-d '{"model": "davinci-002", "prompt": "what is devops?",  "max_tokens": 300}' | jq -r '.choices[0].text'
```
```
curl https://api.openai.com/v1/completions \
-H "Content-Type: application/json" \
-H "Authorization: Bearer $YOUR_API_KEY" \
-d '{"model": "davinci-002", "prompt": "what is devops?",  "max_tokens": 300}' >test.json
```
```
curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -d '{
  "model": "gpt-3.5-turbo",
  "messages": [
    {
      "role": "system",
      "content": "what is devops\n"
    },
    {
      "role": "user",
      "content": ""
    },
    {
      "role": "assistant",
      "content": "DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) in order to improve collaboration and communication between teams. It aims to automate and streamline processes, reduce deployment time, and increase the overall efficiency and quality of software development and delivery. DevOps also emphasizes the importance of continuous integration, continuous delivery, and monitoring in order to quickly detect and address issues in software development lifecycle."
    }
  ],
  "temperature": 1,
  "max_tokens": 256,
  "top_p": 1,
  "frequency_penalty": 0,
  "presence_penalty": 0
}'
```
```
curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -d '{
  "model": "gpt-4-turbo",
  "messages": [
    {
      "role": "system",
      "content": "what is devops\n"
    },
    {
      "role": "user",
      "content": ""
    },
    {
      "role": "assistant",
      "content": "DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) in order to improve collaboration and communication between teams. It aims to automate and streamline processes, reduce deployment time, and increase the overall efficiency and quality of software development and delivery. DevOps also emphasizes the importance of continuous integration, continuous delivery, and monitoring in order to quickly detect and address issues in software development lifecycle."
    }
  ],
  "temperature": 1,
  "max_tokens": 256,
  "top_p": 1,
  "frequency_penalty": 0,
  "presence_penalty": 0
}'
```
## Image generation
```
curl https://api.openai.com/v1/images/generations \
  -H 'Content-Type: application/json' \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -d '{
  "prompt": "riding a horse in the sea artistic image",
  "n": 2,
  "size": "1024x1024"
}'
```
```
curl https://api.openai.com/v1/images/generations \
  -H 'Content-Type: application/json' \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -d '{
  "prompt": "devops in artistic surrealism style with English wording",
  "n": 2,
  "size": "1024x1024"
}'
```
```
curl https://api.openai.com/v1/images/generations \
  -H 'Content-Type: application/json' \
  -H "Authorization: Bearer $YOUR_API_KEY" \
  -d '{
  "prompt": "artistic logo for a flowershop run by cats",
  "n": 2,
  "size": "1024x1024"
}'
```
