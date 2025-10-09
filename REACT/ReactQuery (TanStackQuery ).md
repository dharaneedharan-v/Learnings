
## *1. **What is React Query?***

***React Query** is a **data-fetching library** for React apps that helps you **fetch, cache, synchronize, and update server data** in your components automatically.*

*Simple line:*

> *React Query handles API calls + caching + updates so you don’t have to manually manage state for server data.*

---

## *2. **Real-World Analogy***

*Imagine **Netflix app**:*

- *You scroll movies (UI)*
- *Netflix server sends **movie data***
- *React Query = **smart librarian**:*
    - *Fetches movies from server*
    - *Remembers (caches) them*
    - *Automatically updates when new movies are released*
- *You don’t need to manually refresh the page*

## *3. **Technical Terms Breakdown***

|Term|Explanation|
|---|---|
|**Server State**|Data that lives on the server (not your local component). Example: posts, users, products.|
|**Caching**|Storing data temporarily for faster access next time. Like remembering last watched movies.|
|**Refetching**|Automatically updating data from server. Like Netflix checking for new releases.|
|**Query**|A request to fetch some server data.|
|**Mutation**|A request to create/update/delete server data.|
|**Stale Time**|How long cached data is considered “fresh”.|
|**Query Key**|Unique identifier for a piece of server data.|
|**DevTools**|Debugging tool to see queries, cache, and status.|



## *4. **What Problem Does It Solve?***

- ***Why needed:***
    - *Manual API + state + caching is messy*
    - *Handling loading, error, and refetch logic everywhere → repetitive*
- ***Without React Query:***
    - *Use `useState` + `useEffect` for every API*
    - *Manual caching / refetch*
    - *Error handling scattered*
- ***With React Query:***
    - *One place handles fetch, cache, refetch, stale data*
    - *Less boilerplate*
    - *Predictable, fast UI*



## *5. **Key Concepts***

- ***Queries** → fetch & cache server data*
- ***Mutations** → update server data (POST/PUT/DELETE)*
- ***Query Keys** → unique keys for each query*
- ***Caching** → data automatically stored & reused*
- ***Automatic Refetching** → refresh data on focus or interval*
- ***DevTools** → inspect queries & cache*

***Common mistakes:***

- *Forgetting unique query keys*
- *Mutations without invalidating cache → stale data*
- *Overusing queries for static data*



## *6. **Visual / Mental Model***

```
[React Component] --> triggers [Query] --> [React Query Client]
        |                                         |
        | <-------- cached or fresh data ---------|
        |
     UI updates automatically

```

- *Component asks React Query for data*
- *React Query checks cache → if stale, fetch from server*
- *Updates component state automatically*

***Queries = GET requests***

***Mutations = POST/PUT/DELETE requests***



## *7. **Simple Code Example***

### ***Setup***

```bash
npm install @tanstack/react-query

```

```jsx
// main.jsx
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import ReactDOM from "react-dom/client";
import App from "./App";

const queryClient = new QueryClient();

ReactDOM.createRoot(document.getElementById("root")).render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
);

```

### ***Fetching Data (Query)***

```jsx
import { useQuery } from "@tanstack/react-query";
import axios from "axios";

function Posts() {
  const { data, isLoading, error } = useQuery({
    queryKey: ["posts"], // unique key
    queryFn: () => axios.get("<https://jsonplaceholder.typicode.com/posts>").then(res => res.data)
  });

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error fetching posts</div>;

  return (
    <ul>
      {data.map(post => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  );
}

export default Posts;

```

### ***Updating Data (Mutation)***

```jsx
import { useMutation, useQueryClient } from "@tanstack/react-query";
import axios from "axios";

function AddPost() {
  const queryClient = useQueryClient();

  const mutation = useMutation({
    mutationFn: newPost => axios.post("<https://jsonplaceholder.typicode.com/posts>", newPost),
    onSuccess: () => queryClient.invalidateQueries(["posts"]) // refetch posts
  });

  const handleAdd = () => {
    mutation.mutate({ title: "New Post" });
  };

  return <button onClick={handleAdd}>Add Post</button>;
}

```



## *8. **When to Use / When NOT to Use***

***Use React Query when:***

- *App has **lots of server data***
- *You want **caching, background updates, retries***
- *Want simpler async / loading / error handling*

***Avoid React Query when:***

- *Only static local state is needed*
- *Minimal API calls, simple apps*
- *You don’t need caching or background updates*



## *9. **Quick Revision Points***

- *Queries = fetch & cache*
- *Mutations = create/update/delete*
- *Query Keys = unique identifier for cache*
- *Automatic refetch & caching*
- *DevTools = inspect queries & cache*



### *🔹 Advanced Notes*

- ***Why created:** Reduce boilerplate for fetching, caching, updating data*
- ***Internals:** Maintains cache, invalidates stale data, triggers re-renders automatically*
- ***Alternative Approaches:** Axios + useEffect + useState (manual), SWR (simpler caching)*
- ***Advanced Use Cases:** Pagination, infinite scroll, dependent queries, offline support*


	