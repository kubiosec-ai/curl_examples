### Step 1: Create an Assistant
```
curl "https://api.openai.com/v1/assistants" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "OpenAI-Beta: assistants=v2" \
  -d '{
    "instructions": "You are a personal math tutor. Write and run code to answer math questions.",
    "name": "Math Tutor",
    "tools": [{"type": "code_interpreter"}],
    "model": "gpt-4"
  }'
```
```
{
  "id": "asst_yIoFBvGm8p67BHxTWcYQjVEk",
  "object": "assistant",
  "created_at": 1714820633,
  "name": "Math Tutor",
  "description": null,
  "model": "gpt-4",
  "instructions": "You are a personal math tutor. Write and run code to answer math questions.",
  "tools": [
    {
      "type": "code_interpreter"
    }
  ],
  "top_p": 1.0,
  "temperature": 1.0,
  "tool_resources": {
    "code_interpreter": {
      "file_ids": []
    }
  },
  "metadata": {},
  "response_format": "auto"
}
```

### Step 2: Create a Thread
```
curl https://api.openai.com/v1/threads \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "OpenAI-Beta: assistants=v2" \
  -d ''
```
```
{
  "id": "thread_IepEBcsZ8xDOagph4Y3BBgC9",
  "object": "thread",
  "created_at": 1714820717,
  "metadata": {},
  "tool_resources": {}
}
```
### Step 3: Add a Message to the Thread
```
curl https://api.openai.com/v1/threads/thread_IepEBcsZ8xDOagph4Y3BBgC9/messages \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "OpenAI-Beta: assistants=v2" \
  -d '{
      "role": "user",
      "content": "I need to solve the equation `3x + 11 = 14`. Can you help me?"
    }'
```
```
{
  "id": "msg_0cK0r1FOTLs3yKYDv6XLvwS1",
  "object": "thread.message",
  "created_at": 1714820996,
  "assistant_id": null,
  "thread_id": "thread_IepEBcsZ8xDOagph4Y3BBgC9",
  "run_id": null,
  "role": "user",
  "content": [
    {
      "type": "text",
      "text": {
        "value": "I need to solve the equation `3x + 11 = 14`. Can you help me?",
        "annotations": []
      }
    }
  ],
  "attachments": [],
  "metadata": {}
}
```
### Step 4: Create a Run
```
curl https://api.openai.com/v1/threads/thread_IepEBcsZ8xDOagph4Y3BBgC9/runs \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -H "OpenAI-Beta: assistants=v2" \
  -d '{
    "assistant_id": "asst_yIoFBvGm8p67BHxTWcYQjVEk",
    "instructions": "Please address the user as Jane Doe. The user has a premium account."
  }'
```
```
{
  "id": "run_3YC6bWXpe58F8QMLc5m3binG",
  "object": "thread.run",
  "created_at": 1714821176,
  "assistant_id": "asst_yIoFBvGm8p67BHxTWcYQjVEk",
  "thread_id": "thread_IepEBcsZ8xDOagph4Y3BBgC9",
  "status": "queued",
  "started_at": null,
  "expires_at": 1714821776,
  "cancelled_at": null,
  "failed_at": null,
  "completed_at": null,
  "required_action": null,
  "last_error": null,
  "model": "gpt-4",
  "instructions": "Please address the user as Jane Doe. The user has a premium account.",
  "tools": [
    {
      "type": "code_interpreter"
    }
  ],
  "tool_resources": {},
  "metadata": {},
  "temperature": 1.0,
  "top_p": 1.0,
  "max_completion_tokens": null,
  "max_prompt_tokens": null,
  "truncation_strategy": {
    "type": "auto",
    "last_messages": null
  },
  "incomplete_details": null,
  "usage": null,
  "response_format": "auto",
  "tool_choice": "auto"
}
```
### Step 5: List the messages
```
curl https://api.openai.com/v1/threads/thread_IepEBcsZ8xDOagph4Y3BBgC9/messages \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "OpenAI-Beta: assistants=v2"
```
```
{
  "object": "list",
  "data": [
    {
      "id": "msg_fp0hGG1crpUawGxClbxd7pDq",
      "object": "thread.message",
      "created_at": 1714821183,
      "assistant_id": "asst_yIoFBvGm8p67BHxTWcYQjVEk",
      "thread_id": "thread_IepEBcsZ8xDOagph4Y3BBgC9",
      "run_id": "run_3YC6bWXpe58F8QMLc5m3binG",
      "role": "assistant",
      "content": [
        {
          "type": "text",
          "text": {
            "value": "The solution to the equation `3x + 11 = 14` is `x = 1.0`, Jane Doe.",
            "annotations": []
          }
        }
      ],
      "attachments": [],
      "metadata": {}
    },
    {
      "id": "msg_LvCfDuIOvMgzsvxLyulEp4le",
      "object": "thread.message",
      "created_at": 1714821177,
      "assistant_id": "asst_yIoFBvGm8p67BHxTWcYQjVEk",
      "thread_id": "thread_IepEBcsZ8xDOagph4Y3BBgC9",
      "run_id": "run_3YC6bWXpe58F8QMLc5m3binG",
      "role": "assistant",
      "content": [
        {
          "type": "text",
          "text": {
            "value": "Sure, Jane Doe. \n\nTo solve the equation `3x + 11 = 14`, you need to isolate the variable `x`. Here are the steps:\n\n1. Subtract 11 from both sides of the equation, so it becomes `3x = 14 - 11`.\n2. Divide both sides of the equation by 3 to solve for `x`.\n\nLet's calculate it.",
            "annotations": []
          }
        }
      ],
      "attachments": [],
      "metadata": {}
    },
    {
      "id": "msg_0cK0r1FOTLs3yKYDv6XLvwS1",
      "object": "thread.message",
      "created_at": 1714820996,
      "assistant_id": null,
      "thread_id": "thread_IepEBcsZ8xDOagph4Y3BBgC9",
      "run_id": null,
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": {
            "value": "I need to solve the equation `3x + 11 = 14`. Can you help me?",
            "annotations": []
          }
        }
      ],
      "attachments": [],
      "metadata": {}
    }
  ],
  "first_id": "msg_fp0hGG1crpUawGxClbxd7pDq",
  "last_id": "msg_0cK0r1FOTLs3yKYDv6XLvwS1",
  "has_more": false
}
```
