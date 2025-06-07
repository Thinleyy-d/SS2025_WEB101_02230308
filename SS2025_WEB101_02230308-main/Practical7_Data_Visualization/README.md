# 📊 Practical 7: Data Visualization

A clean, interactive React dashboard showcasing different chart types for data analytics.

## Overview

This project demonstrates how to build a modern analytics dashboard using React and popular charting libraries. Perfect for displaying business metrics, user analytics, and performance data.

## Features

- **Line Chart** - Monthly sales trends and targets
- **Pie Chart** - Product category distribution  
- **Bar Chart** - Customer acquisition metrics
- **Area Chart** - Weekly visitor patterns
- Fully responsive design
- Interactive tooltips and hover effects

## Tech Stack

- React 18
- Recharts (charting library)
- Tailwind CSS (styling)
- TypeScript (optional)

## Quick Start

1. **Install dependencies**
   ```bash
   npm install recharts
   ```

2. **Run the project**
   ```bash
   npm run dev
   ```

3. **View dashboard**
   Open `http://localhost:3000`

## Project Structure

```
src/
├── components/
│   ├── LineChart.jsx
│   ├── PieChart.jsx
│   ├── BarChart.jsx
│   └── AreaChart.jsx
└── App.jsx
```

## Chart Examples

Each chart uses sample data and can be easily customized:

```javascript
// Sample data structure
const salesData = [
  { month: 'Jan', sales: 4000, target: 3800 },
  { month: 'Feb', sales: 3000, target: 3200 }
]
```

## Customization

- **Colors**: Update color values in each chart component
- **Data**: Replace mock data with your API data
- **Styling**: Modify Tailwind classes for different themes

## Key Benefits

- **Responsive**: Works on all device sizes
- **Interactive**: Hover effects and tooltips
- **Performant**: Optimized for smooth rendering
- **Accessible**: Screen reader friendly

## Common Issues

- Ensure Recharts is installed: `npm install recharts`
- Check data format matches chart requirements
- Verify ResponsiveContainer wraps all charts



