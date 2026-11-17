---
title : "Set the context constraint"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "
---

#### Goal
Force the model to answer only from the legal text retrieved from the database.

#### Steps
1. Add the strict rule: answer only from the provided legal text; never invent or extrapolate.
2. Add a fallback: if the provided text is not enough, say that there is not enough basis.
3. Test with an out-of-scope question (for example, a tax question).

![Out-of-scope question handled correctly](/images/5-Workshop/5.3-Prompt/context-constraint-test.png)

#### Verify
An out-of-scope question gets a 'not enough basis' answer instead of an invented one.