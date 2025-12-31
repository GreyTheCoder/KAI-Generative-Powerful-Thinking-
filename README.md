A personal project that connects a MERN stack app to the OpenAI API — built to learn how to stream AI responses, render Markdown/code nicely, and keep conversations around between refreshes. I built this to understand the plumbing behind chat UIs and to practice making something that feels smooth and natural.

## What it does
- Chat with OpenAI models from a custom UI
- Streams responses so the assistant appears to “type” in real time
- Renders Markdown and syntax-highlighted code blocks (rehype-highlight + react-markdown)
- Persists conversations in MongoDB and keeps sessions separate using UUIDs

## Why I built it
I wanted a hands-on way to learn streaming responses, manage conversational state, and handle code blocks correctly in the browser. It’s small but packed with practical patterns I keep reaching for in production apps.

## Tech
- Frontend: React 19 + Vite, react-markdown, rehype-highlight, react-spinners
- Backend: Node, Express, Mongoose (MongoDB), OpenAI SDK, dotenv
- Utilities: uuid for session IDs

## Quick start
1. Clone
   git clone https://github.com/GreyTheCoder/KAI-Generative-Powerful-Thinking-.git

2. Backend
   cd backend
   npm install

https://github.com/user-attachments/assets/f8041eb7-3c92-49a2-928e-2ce0ec70ecd1


   create a `.env`:
   ```
   PORT=5000
   MONGO_URI=your_mongo_uri
   OPENAI_API_KEY=your_openai_key
   ```
   npm start

3. Frontend
   cd frontend
   npm install
   npm run dev
   Open the Vite URL (usually http://localhost:5173)

## Notes on implementation
- Streaming: backend proxies OpenAI streaming responses to the frontend so the UI can update incrementally.
- Markdown & code: react-markdown + rehype-highlight for safe, readable output.
- Persistence: messages saved with Mongoose (author, text, timestamp, sessionId) so you can resume conversations later.

## Challenges I ran into
- Making streaming feel smooth without re-render thrash — solved with small buffering and throttled UI updates.
- Handling token limits — solved by pruning or summarizing older context before sending.
- Keeping the OpenAI key secure — always call the API from the backend, never expose keys to the client.

## What I learned
Streaming changes how you design the UI: incremental rendering and careful state updates matter. Small UX details (loading indicators, message pacing) make the chat feel alive. Also got better at balancing model costs vs. user context.


