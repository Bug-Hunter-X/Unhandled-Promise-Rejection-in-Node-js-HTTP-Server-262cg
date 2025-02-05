# Unhandled Promise Rejection in Node.js HTTP Server

This repository demonstrates a common error in Node.js where errors thrown within asynchronous operations inside HTTP request handlers are not properly caught, potentially leading to silent failures or incomplete responses.  The `bug.js` file contains the erroneous code, while `bugSolution.js` provides the corrected implementation.

## Problem

The `bug.js` example uses promises to simulate an asynchronous operation that might throw an error. The error handling is within the promise's `catch` block.  However, this is insufficient to handle errors gracefully from the server's perspective. If an error is thrown inside `doSomethingAsync`, the server might not respond correctly, and the error might go unnoticed.

## Solution

The `bugSolution.js` file demonstrates the correct approach. The solution utilizes a `try...catch` block around the asynchronous operation to capture any errors that occur during request processing and sends a proper error response to the client. This ensures that errors are handled properly and prevents unexpected behavior.