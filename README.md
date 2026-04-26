# 🚀 Docker Golden Rules Cheat Sheet

<p align="center">
  <img src="https://media.giphy.com/media/kH1DBkPNyZPOk0BxrM/giphy.gif" width="300"/>
</p>

<p align="center">
  <b>Master Dockerfile writing like a pro 🔥</b><br>
  <i>Simple rules to identify, build & run any project</i>
</p>

---

## 🧠 1. Identify Your Project First

| 🔍 Files You See             | 📦 Project Type | ⚡ What To Do      |
| ---------------------------- | --------------- | ----------------- |
| `index.html`, `assets/`      | Static Website  | Serve using Nginx |
| `package.json`, `src/`       | React / Angular | Build + Serve     |
| `app.py`, `requirements.txt` | Python Backend  | Run with Python   |
| `server.js`                  | Node Backend    | Run with Node     |
| `pom.xml`, `build.gradle`    | Java App        | Run with Java     |

---

## ⚙️ 2. Docker Strategy

| 🧩 Case      | 🚀 Strategy                    |
| ------------ | ------------------------------ |
| Static Site  | Nginx only                     |
| Frontend App | Multi-stage (Node + Nginx)     |
| Backend      | Runtime (Node / Python / Java) |

---

## 🔧 3. Dockerfile Pattern (Always Follow)

```dockerfile
FROM        # Base image
WORKDIR     # Set working directory
COPY        # Copy code
RUN         # Install / Build
CMD         # Run app
```

---

## ⚡ 4. 2-Second Decision Rule

| 👀 If You See          | ✅ Action    |
| ---------------------- | ----------- |
| `index.html` ready     | Use Nginx   |
| `package.json`         | Build first |
| `app.py` / `server.js` | Run app     |

---

## 🧪 5. Examples

### 🟢 Static Website

```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
```

---

### 🟡 React App (Multi-stage)

```dockerfile
FROM node:16 AS builder
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
```

---

### 🔵 Node Backend

```dockerfile
FROM node:16
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]
```

---

### 🟣 Python Backend

```dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

---

## ⚠️ 6. Common Mistakes

❌ Running `npm install` in static project
❌ Using Nginx for backend apps
❌ Forgetting to copy build folder
❌ Not using multi-stage for frontend

---

## 🔄 7. Thinking Flow

```text
Code → Build → Output → Serve
```

---

## 🎯 8. Final Decision Table

| Situation           | Decision      |
| ------------------- | ------------- |
| Already built files | Serve (Nginx) |
| Source code         | Build         |
| Backend code        | Run           |

---

## 💡 Ultimate Memory Trick

👉 HTML → Serve
👉 package.json → Build
👉 App file → Run

---

<p align="center">
  <img src="https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif" width="250"/>
</p>

---

## 🏁 Final Note

> 💬 Dockerfile doesn't decide the strategy —
> 🔥 **Project type decides everything**

---

## ⭐ If this helped you

Give this repo a ⭐ and keep learning DevOps 🚀
