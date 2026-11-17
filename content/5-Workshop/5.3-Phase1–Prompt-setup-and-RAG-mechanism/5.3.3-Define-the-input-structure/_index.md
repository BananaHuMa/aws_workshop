---
title : "Define the input structure"
date : 2026-01-01 
weight : 3
chapter : false
pre : " <b> 5.3.3 </b> "
---

#### Goal
Decide how Lambda injects DynamoDB data into the prompt sent to the model.

#### Steps
1. Format each retrieved article as a labelled block (article number + content).
2. Place the legal context before the user's question in the message.
3. Limit the number and length of articles to stay within the model's rate and token limits.
4. Record the final template in `docs/`.

![Prompt assembly: system prompt + legal context + question → Groq](/images/5-Workshop/5.3-Prompt/prompt-assembly.png)

#### Verify
A printed prompt shows the three parts in the intended order.