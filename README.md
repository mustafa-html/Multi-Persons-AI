# 
# The Council – Multi-Persona AI Advisor

What if you could ask the same question to four completely different personalities and see what each of them thinks?

That's the idea behind **The Council**.

The Council is an AI-powered web app where you can assemble a group of four virtual advisors, ask them a question, and get four different perspectives. Whether you're making a decision, looking for advice, or just curious about how different personalities would respond, the goal is to make interacting with AI a little more interesting.

Instead of relying on one AI response, you get an entire council of opinions.

## How It Works

The app lets you choose four advisors from a collection of **10 unique personalities**. Each advisor has their own way of approaching a question.

Some are logical and straightforward, while others are empathetic, optimistic, skeptical, or chaotic.

Here's how it works:

1. Choose four advisors to form your council.
2. Ask a question or describe a situation.
3. All four advisors receive your question simultaneously.
4. Each advisor responds according to their personality and conversation history.
5. Compare their perspectives and decide which advice works best for you.

Each advisor is represented by a 3D animal character, making the experience feel more like an actual council than a traditional chatbot.

## Tech Stack

| Technology | Purpose |
|------------|---------|
| React | Frontend application |
| JavaScript | Application logic |
| OpenAI API | AI-generated advisor responses |
| Three.js | 3D rendering |
| React Three Fiber | Integrating 3D scenes with React |
| React Three Drei | 3D scene utilities |
| Chakra UI | UI components and styling |
| Framer Motion | Interface animations |

## Technical Features

### 1. Multi-Persona AI System

Each advisor has a dedicated system prompt that defines their personality, behaviour, and approach to answering questions.

Rather than generating four identical answers, the application provides different instructions to the same underlying AI model.

Each advisor also maintains a separate conversation history, helping preserve context throughout the discussion.

### 2. Concurrent API Requests

One challenge was figuring out how to generate four AI responses without making users wait for each request individually.

I used JavaScript's `Promise.all()` to execute the four OpenAI API requests concurrently.

```javascript
const responses = await Promise.all(
  selectedAdvisors.map((advisor) =>
    getAdvisorResponse(advisor, userMessage)
  )
);
```

*This snippet illustrates the concurrency approach used in the project.*

Instead of waiting for four sequential requests, the application waits approximately as long as the slowest individual response.

This makes the experience much more responsive.

### 3. Interactive 3D Interface

I wanted the app to feel different from a normal chatbot.

Using Three.js and React Three Fiber, I integrated animated 3D animal characters representing the different council members.

Each character has its own personality, giving users a more visual and interactive way to engage with the AI advisors.

### 4. Independent Conversation Context

Every advisor maintains its own conversation history.

This allows different advisors to develop their responses based on their previous interactions rather than sharing one combined conversation.

## Getting Started

### Prerequisites

Before running the project, make sure you have:

- Node.js
- npm
- An OpenAI API key

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/YOUR_USERNAME/thecouncil.git
cd thecouncil
```

**2. Install dependencies**

```bash
npm install
```

**3. Configure your environment variables**

Create a `.env` file in the project root:

```env
REACT_APP_API_KEY=your_openai_api_key
```

**4. Start the application**

```bash
npm start
```

The application should be available at:

```text
http://localhost:3000
```

> **Security note:** The current implementation makes OpenAI API requests directly from the browser. React environment variables are exposed in client-side builds. For production use, API requests should be moved to a backend that securely stores the API key. Do not deploy a publicly accessible version with a private API key embedded in the frontend.

## What I Learned

This project started as an experiment with a simple question: what would happen if multiple AI personalities answered the same question?

Building it gave me experience with:

- Integrating the OpenAI API into a React application
- Designing different AI behaviours through prompt engineering
- Managing multiple independent conversation histories
- Running asynchronous API requests concurrently
- Working with 3D models and animations in a web application
- Combining AI functionality with an interactive frontend

One of the biggest things I learned was how much the instructions and context given to an AI model can influence its responses, even when every advisor uses the same model.

## Future Improvements

Some features I'd like to add:

- [ ] Move OpenAI requests to a secure backend
- [ ] Allow users to create custom advisor personalities
- [ ] Save and revisit previous conversations
- [ ] Add support for newer OpenAI models
- [ ] Improve error handling for individual advisor responses
- [ ] Add more interactive 3D characters

## Built With

React • JavaScript • OpenAI API • Three.js • React Three Fiber • Chakra UI • Framer Motion

---

*Sometimes one opinion isn't enough.*
