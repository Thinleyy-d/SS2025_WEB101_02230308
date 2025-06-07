# Practical 6: State Management ( Todo List Application with Zustand ) 

A minimal yet powerful Todo List app built with **React**, powered by **Zustand** for simple and efficient state management.


## Features

- Add, toggle, and delete todos
- Clear all completed tasks
- Auto-saves using localStorage
- Responsive and clean UI

## Tech Stack

- **React** + **Vite**
- **Zustand** (state management)
- **CSS** (styling)

## Getting Started

1. **Create project & install deps**
   ```bash
   npx create-vite@latest todo-zustand
   cd todo-zustand
   npm install
   npm install zustand

2. **Start dev server**
- npm run dev
- Visit http://localhost:5173

## File Structure
```
src/
├── components/
│   ├── TodoInput.jsx
│   ├── TodoItem.jsx
│   └── TodoList.jsx
├── store/todoStore.js
├── App.js
└── App.css
```
## Zustand in a Nutshell
- Define store using create()

- Update state with simple set() calls

- Auto-persist using persist() middleware

## Why Zustand?
- Minimal boilerplate

- Easy to use and debug

- React-friendly with auto re-renders

- Supports persistence out of the box

## How to Use
- Type a task and click Add

- Mark as done with checkbox

- Delete a task

- Clear all completed with one click