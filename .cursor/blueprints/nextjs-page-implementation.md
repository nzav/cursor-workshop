# NextJS Page Implementation Blueprint

## Overview

This document provides a step-by-step guide for implementing a new page in our NextJS application using the established project patterns.

## Project Structure

- `src/app`: Contains pages and app-specific components
- `src/components`: Global reusable components (shadcn/ui)
- `src/lib`: Utilities and helpers
- `src/hooks`: Custom React hooks

## Steps to Create a New Page

### 1. Create the Page File

- Create a new directory in `src/app` for your route (e.g., `src/app/your-route`)
- Add a `page.tsx` file in that directory:

```tsx
import YourPageComponent from "@/app/components/YourPageComponent";

/**
 * Main page component for the your-route path.
 *
 * @returns {JSX.Element} The rendered page component
 */
const Page = () => {
  return <YourPageComponent />;
};

export default Page;
```

### 2. Create Page-Specific Components

- Create your page component in `src/app/components`:

```tsx
const YourPageComponent: React.FC = () => {
  return (
    <main className="mx-auto mt-6 flex max-w-7xl flex-col justify-center gap-6 px-3">
      {/* Your page content goes here */}
    </main>
  );
};

export default YourPageComponent;
```

### 3. Add Required Data Fetching (if needed)

- For server components, add data fetching in the page file:

```tsx
// For server components
export async function getData() {
  // Fetch your data
  return { ... };
}

// In Page component
const Page = async () => {
  const data = await getData();
  return <YourPageComponent data={data} />;
};
```

### 4. Add Navigation Links (if needed)

- Update the navigation links in `src/app/components/NavigationLinks.tsx`

### 5. Testing

- Run the app with `npm run dev`
- Verify your page is accessible at the expected route

## Best Practices

- Follow existing code style and patterns
- Use shadcn/ui components for consistent UI
- Keep components modular and reusable
- Leverage the app router correctly
- Use TypeScript for type safety

## Tech Stack Reference

- NextJS 15.x (App Router)
- React 19.x
- TypeScript
- shadcn/ui components
- Tailwind CSS for styling
