---
title : "Build a role-defining system prompt"
date : 2026-01-01 
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "
---

#### Goal
Make the model act as a legal consultant specialized in Vietnamese regulations such as Decree 13/2023/ND-CP.

#### Steps
1. Write the role statement (expert in Vietnamese personal-data law).
2. Require answers in Vietnamese and cite the article used.
3. Add the disclaimer: preliminary answer, not official legal advice.
4. Test the draft in the Groq playground.

#### Reference sample
Replace with the team's real prompt:
> You are a legal consultant specialized in Vietnamese personal-data law.
> Answer in Vietnamese and name the article you rely on.
> This is a preliminary answer, not official legal advice.

![System prompt in the Groq playground](/images/5-Workshop/5.3-Prompt/system-prompt.png)

#### Verify
The model answers in the intended role and tone.