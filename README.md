# Next.js 15 App Dir: Server Component Data Fetching Issue

This repository demonstrates a subtle bug in Next.js 15's `app` directory when server components attempt to fetch data relying on client-side information during concurrent rendering.  The issue leads to silent failures, resulting in inconsistent data or unexpected UI behavior.  The solution involves restructuring the data fetching to either avoid client-side dependencies or leverage client components for client-specific data.

## Bug Description

Server components in Next.js 15's `app` directory are rendered on the server.  If they depend on data only available on the client (e.g., cookies, browser settings, user preferences), the server-side rendering will fail without explicit error messages, causing inconsistencies after client hydration.

## Solution

The solution depends on the specific requirement and the nature of the client-side dependency.

* **Avoid Client-Side Dependencies:** If possible, redesign the server component to avoid relying on client-side information.
* **Client Components:**  Use client components to fetch data that requires client-side context.  These components will execute after hydration, allowing access to the necessary information.
* **Conditional Rendering:** Implement conditional rendering to handle situations where the data might be unavailable on the server.