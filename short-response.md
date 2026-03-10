# Short Response Questions

Answer each question below in your own words. Aim for 3–5 sentences per answer. Be specific — use the exact terms and concepts from the lesson.

Your responses will each be evaluated out of 6 points. You can earn 3 points for writing quality and 3 points for the accuracy and precision of the technical content per question.

---

## Question 1: Express vs `node:http`

Express is described as a framework that "wraps" `node:http`. What does that mean? Compare how you would handle a `GET /api/users` request in `node:http` versus in Express. What does Express do for you automatically that you had to write manually with `node:http`?

**Your answer here**:

**"Wrapping"** `node:http` means **Express** is built on it, making it so we dont have to work with **HTTP** directly. With `node:http`, handling `GET /api/users` requires checking `req.method` and `req.url`, then parsing the **URL** and writing the correct headers before sending responses. **Express** would handle all of that with `app.get('api/users', controller)`, routes by method and path, parses query strings into `req.query`, and lets you call `res.json()`.

---

## Question 2: Endpoints, Controllers, and Middleware

What are **controllers** and **middleware** in Express? What are each responsible for and how do they work together to handle incoming requests?

**Your answer here**:

**Controllers** are functions that handle a specific route and sends a response. **Middleware** are functions that run before the **controller**, processing the request and then passing it along by calling `next()`. Together, when a request comes in, **Express** runs each registered **middleware** in order, and if none of them send a response first, the request reaches the matching **controller** which sends the final response.

---

## Question 3: Query Strings and Route Parameters

How are **query strings** and **route parameters** similar? How are they different? In your answer, provide an example of when you would use each.

**Your answer here**:

Both **query strings** and **route parameters** let clients pass data to the server as part of a **URL**, and both are accessible in **Express** via the `req` object. The difference is in how and when you use them, **route parameters** are part of the **URL** path itself and are used to identify a specific resource, while **query strings** are appended after a `?` and are used to filter, sort, or modify a broader collection. You'd use a **route parameter** to fetch one specific quote by its ID, and a **query string** to request only quotes that belong to a particular topic.

---

## Question 4: Same-Origin Requests

For API fetch calls from a client-side application, explain the difference between fetching from endpoints with relative paths like `/api/quotes` and fetching from endpoints with a full URL like `https://dog.ceo/api/breeds/image/random`. Why do we not send a fetch using a url like `http://localhost:8080/api/quotes`?

**Your answer here**:

When a **frontend** and its **API** are served from the same **host** and **port**, **fetch calls** can use relative paths like `/api/quotes`, the browser resolves them against the current **origin**. **Fetching** from an external **API** like `https://dog.ceo/api/breeds/image/random` requires a full **URL** because it lives on a completely different **origin**. We avoid hardcoding `http://localhost:8080/api/quotes` in frontend code because `localhost:8080` only exists on our development machine, once the app is deployed, that address won't work correctly for any real user.
