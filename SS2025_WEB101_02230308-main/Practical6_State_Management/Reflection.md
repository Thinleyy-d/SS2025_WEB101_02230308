# Practical 6: State Management ( Todo List Application with Zustand ) Reflection 

## What I Learned

### 1. Zustand Makes State Management Simple
- No need for Context Providers or Redux boilerplate.
- Easy to create a store using `create`, and access state/actions with custom hooks.

### 2. Selective Subscriptions Improve Performance
- Learned to subscribe only to the parts of state needed:
  ```js
  const todos = useTodoStore(state => state.todos)
- This avoids unnecessary re-renders.

### 3. Persistence is Effortless
- Zustand’s persist middleware saved todos to localStorage with minimal setup.

- The state reloads automatically on refresh—no manual syncing needed.

### 4. State Updates Must Be Immutable
- Mistakes like mutating arrays directly led to bugs.

- Switching to immutable patterns ([...state.todos, newTodo]) solved the issue.

### 5. Clean Component Architecture Helps
1. Components had clear roles:

- TodoInput → adds todos

- TodoItem → toggles/removes todos

- TodoList → displays and clears todos

## Key Insights
- Zustand is ideal for small to medium projects that need global state.

- Mixing local (useState) and global (Zustand) state gives flexibility.

- Using selectors keeps components efficient and fast.

- Zustand’s small API = less to learn, more to build.

## Challenges & Solutions
### Challenge	
1. Too many re-renders	

2. localStorage config confusion	

3. Accidentally mutated state	

4. Unsure when to use props vs global	

### Solution
1. Used selective subscriptions (state => state.todos)

2. Wrapped store with persist(..., { name: 'todo-storage' })

3. Switched to immutable updates using spread operator

4. Passed data as props, used actions from store

## Future Ideas

- Add filtering (all, active, completed)

- Use TypeScript for better safety

- Add animations (e.g., for completed items)

- Integrate with backend for multi-device sync