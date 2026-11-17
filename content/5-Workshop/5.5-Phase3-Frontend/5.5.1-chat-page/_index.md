---
title : "Build the chat page"
date : 2026-01-01 
weight : 1
chapter : false
pre : " <b> 5.5.1 </b> "
---

#### Goal
Create a single static page that talks to the backend with `fetch`.

#### Steps
1. Build the chat layout: title, status badge, welcome message, message list, input box, and send button.
2. On send, call `fetch` with an HTTP POST to the API URL and show a loading state.
3. Show a clear message for errors (`400`, `429`, `502/504`).
4. **Recommended:** Add a visible disclaimer that answers are preliminary and not legal advice.

![The chat page of the live site](/images/5-Workshop/5.5-Frontend/frontend-ui.png)

#### Verify
Opening `index.html` locally shows the chat page and the welcome message.