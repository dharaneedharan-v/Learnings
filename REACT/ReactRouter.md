### React Router - Quick Revision Notes 🚀

## Topics Covered

1. What is React Router?
2. BrowserRouter
3. Route
4. Switch
5. NavLink
6. Nested Routing
7. Redirect
8. Prompt

---

## 1. What is React Router?

**Simple Explanation:** React Router helps you navigate between different pages/components in your React app without refreshing the page (SPA - Single Page Application).

**Installation:**

bash

```bash
npm install react-router-dom
```

**Think of it as:** A GPS system for your React app - it knows which component to show based on the URL.

---

## 2. BrowserRouter (Router) (BrowserNavigations->Like Forward , Backward Navigations)

**What it does:** The parent wrapper that enables routing in your app. Wraps your entire application.

**Key Point:** Everything that needs routing must be inside `<Router>`.

**Simple analogy:** Like the main door of a house - everything routing-related happens inside it.

---

## 3. Route

**What it does:** Defines a path and which component should render at that path.

**Key Props:**

- `path` - URL path (e.g., "/home", "/about")
- `component` - Which component to show
- `exact` - Match path exactly (prevents partial matches)
- `strict` - No trailing slashes allowed

**Remember:**

- Without `exact`, path="/" will match ALL routes starting with "/"
- Use `exact` to avoid this problem

---

## 4. Switch

**What it does:** Renders ONLY the first matching Route, then stops checking.

**Why use it:**

- Prevents multiple components from rendering at once
- More efficient
- Better for "Not Found" pages

**Simple analogy:** Like a light switch - only ONE can be on at a time.

---

## 5. NavLink

**What it does:** Creates navigation links (like `<a>` tag but better for React).

**Key Props:**

- `to` - Where to navigate (required)
- Automatically adds "active" class to current link
- No page refresh when clicked

**Remember:** Use NavLink instead of regular `<a>` tags for internal navigation.

---

## 6. Nested Routing

**What it does:** Routes inside routes - like having pages within pages.

**Use case:**

- Product categories → Individual products
- Dashboard → Different dashboard sections
- Challenges list → Individual challenge details

**Key Point:** Child routes inherit parent route paths.

---

## 7. Redirect

**What it does:** Automatically sends users from one route to another.

**Common Uses:**

- Login protection (not logged in → redirect to login page)
- Logged in users trying to access login page → redirect to dashboard
- Old URLs → new URLs

**Simple analogy:** Like a "Closed for Renovation" sign that points you to a new location.

---

## 8. Prompt

**What it does:** Shows a warning message before user leaves a page.

**Props:**

- `message` - What to show (string or function)
- `when` - Condition to show prompt (true/false)

**Use cases:**

- Unsaved form data
- Logout confirmation
- Incomplete tasks

**Remember:** Can be annoying if overused - use only when necessary!



## 9. Dynamic Routes / Route Parameters

**What it does:**

Dynamic routes allow you to create URLs with variables, so you can show different content for different parameters without creating separate routes manually.

**Example:**

```jsx
<Route path="/user/:id" component={User} />

```

- `:id` → dynamic segment (parameter)
- Matches URLs like:
    - `/user/1`
    - `/user/42`
    - `/user/john`

**Accessing the parameter inside the component:**

```jsx
import { useParams } from "react-router-dom";

function User() {
  const { id } = useParams();
  return <h2>User ID: {id}</h2>;
}

```

**Use Cases:**

- User profiles → `/user/:id`
- Product pages → `/product/:productId`
- Blog posts → `/post/:slug`

**Key Point:**

- Dynamic route parameters are **read via `useParams()`**
- You can use them to fetch data specific to that parameter

**Simple Analogy:**

Like a **variable slot in your GPS**: the route is fixed (`/user/:id`) but the ID changes depending on which user you want to visit.

> “React Router is the core library, and `react-router-dom` is the npm package that provides React Router features for web browsers.”


