# Next.js 15 Server Component Layout Dynamic Import Crash

This repository demonstrates an uncommon bug in Next.js 15 related to dynamic imports within server components used as layouts.  If a dynamic import in the layout fails, the entire application can crash, producing cryptic 500 errors.

## Bug Description

When a dynamic import within a server component layout fails (e.g., due to a network error or incorrect import path), Next.js's error handling doesn't gracefully degrade. Instead, the entire application crashes, masking the true source of the problem.

## Reproduction Steps

1. Clone this repository.
2. Install dependencies: `npm install`
3. Run the development server: `npm run dev`
4. Observe that the application renders correctly initially.
5. Simulate a failure by modifying the path in `bug.js` to an incorrect path or remove the network resource. 
6. The application will crash with a 500 Internal Server Error or an equivalent error, making the issue hard to trace back to the failing dynamic import within the layout.

## Solution

The solution involves robust error handling in the server component layout, ensuring that any errors during dynamic import are caught and handled gracefully.  This prevents the entire application from crashing.  See `bugSolution.js` for the corrected code.
