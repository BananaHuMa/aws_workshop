---
title : "Build the knowledge base on DynamoDB"
date : 2026-01-01 
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

#### Goal
Store legal articles in a table that Lambda can query.

#### Steps
1. Create the DynamoDB table `LegalArticles`.
2. Design the item structure (for example: article number, title, content, keywords).
3. Load the articles extracted from Decree 13/2023/ND-CP, including provisions on using ID card data, personal data, and violation handling.
4. Check the item count against the source document.

*Limitation: Lookup is keyword-based, so a question using different wording may miss the right article.*

![DynamoDB table LegalArticles](/images/5-Workshop/5.4-Backend/dynamodb-table.png)

![Sample items in the table](/images/5-Workshop/5.4-Backend/dynamodb-items.png)

#### Verify
The table returns the expected articles when scanned in the console.