# Spring AI - README

## Introduction to AI in Spring

Spring AI provides a simple and consistent way to integrate Large Language Models (LLMs) into Spring applications. It abstracts the complexity of dealing with AI providers and gives developers familiar Spring-style APIs.

---

## 1) ChatClient

**ChatClient** is a high-level API used to send prompts to an AI model and receive responses.

* It acts as the main interface for interacting with AI.
* Provides simple methods like `.prompt()` and `.call()`.
* Handles request formatting, model selection, and response mapping.

**Example:**

```java
ChatResponse response = chatClient.prompt("Hello").call();
System.out.println(response.getResult());
```

---

## 2) ChatModel

**ChatModel** represents the LLM (Large Language Model) being used.

* Spring AI wraps different model providers (OpenAI, Ollama, Azure OpenAI, etc.).
* ChatClient internally uses ChatModel to generate text.
* You can switch the model without changing business logic.

**Example:**

```java
@Bean
public ChatModel chatModel() {
    return new OpenAiChatModel(apiKey);
}
```

---

## 3) ChatResponse

**ChatResponse** is the structured response received from the AI.

* Contains generated text, metadata, usage tokens, etc.
* Helps developers extract final text safely.

**Example:**

```java
String output = response.getResult().getOutputText();
```

---

## AI Processing Flow (Simple Explanation)

AI models process your input through several steps:

1. **Prompt** → The user query or message is received.
2. **Tokenization** → The text is split into smaller units called *tokens* (words, subwords, characters).
3. **Embedding / Vectorization** → Each token is converted into high‑dimensional numerical vectors.

   * Words like **king** and **queen** get vectors with similar patterns because their meanings are related.
4. **Neural Network Processing** → The model applies multiple transformer layers to understand context, relationships, and meaning.
5. **Output Generation** → The model predicts the next tokens and forms the final response.
