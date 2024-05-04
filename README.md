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
      "content": "You are a DEV(SEC)OPS expert\n"
    },
    {
      "role": "user",
      "content": "What is a github action and how would you include security?"
    },
    {
      "role": "assistant",
      "content": ""
    }
  ],
  "temperature": 1,
  "max_tokens": 2048,
  "top_p": 1,
  "frequency_penalty": 0,
  "presence_penalty": 0
}' | jq -r '.choices[0].message.content'
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
      "content": "You are a DEV(SEC)OPS expert\n"
    },
    {
      "role": "user",
      "content": "What is Github?"
    },
    {
      "role": "assistant",
      "content": ""
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
