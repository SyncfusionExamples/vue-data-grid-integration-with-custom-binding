# Bind EJ2 Vue DataGrid to Custom Data Binding

## Repository Description
A practical demonstration of implementing the Syncfusion EJ2 Vue DataGrid component with custom data binding, supporting filtering, searching, grouping, editing, and paging operations.

## Overview
This repository provides a comprehensive example of using the EJ2 Vue DataGrid component with custom binding in Vue 3 applications. The application demonstrates how to integrate the Syncfusion Grid control with a custom backend service, enabling essential data operations while maintaining full control over data fetching and manipulation.

## Features
- **Grid Component**: Integrated Syncfusion EJ2 Vue Grid component with custom binding
- **Data Binding**: Custom data binding with remote server communication
- **Filtering**: Advanced column filtering with multiple filter operators
- **Searching**: Grid-wide search functionality via toolbar
- **Grouping**: Lazy load grouping with on-demand data loading for grouped columns
- **Editing**: Full CRUD operations (Add, Edit, Delete) with new row positioning
- **Paging**: Server-side paging for efficient data loading
- **Sorting**: Multi-column sorting support

## Project Prerequisites
Before starting, ensure you have the following installed:

- **Node.js**: Latest stable version
- **Visual Studio Code**: Latest version recommended
- **npm**: Node Package Manager (included with Node.js)
- Basic knowledge of Vue.js and JavaScript

## Installation

Clone and set up the project:

```
git clone https://github.com/SyncfusionExamples/vue-data-grid-integration-with-custom-binding
cd vue-data-grid-integration-with-custom-binding
npm install
```

## Configuring the Application

Before running the application, update the port number in two files:

1. Open `server.js` and replace `xxxx` with your desired port number:
```javascript
const port = xxxx; // Replace xxxx with your port
```

2. Open `src/orderService.ts` and update the baseUrl:
```typescript
const baseUrl = "http://localhost:xxxx/orders"; // Replace xxxx with the same port
```

## Running the Application

Start the development server:

```
npm run start
```

The command starts both the backend server and the Vue development client concurrently. The application will open in your browser at `http://localhost:5173` (default Vite port).

## Examples

Explore Syncfusion EJ2 Vue DataGrid examples:
- Local data binding: https://ej2.syncfusion.com/vue/demos/#/material3/grid/localdata
- Remote data binding: https://ej2.syncfusion.com/vue/demos/#/material3/grid/remote-data
- Custom binding: https://ej2.syncfusion.com/vue/demos/#/material3/grid/custom-binding
- Lazy load grouping: https://ej2.syncfusion.com/vue/demos/#/material3/grid/lazyload-grouping

## Documentation

For detailed information and configuration options:

https://ej2.syncfusion.com/vue/documentation/grid/data-binding/remote-data#custom-binding
