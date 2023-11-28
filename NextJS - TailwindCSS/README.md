# NEXTJS & TailwindCSS

## NEXTJS
React framework for Web - that support for a faster web
### App vs Page Router
App Router
- Directory: ./app dir
- New May 2023
- Recommended for new apps
- More features: React Components, Nested layout, etc
- Redering in server side only
  - How can we run the client functionality ? - We can use `'use client'` tag in top of file, that will say we need the rendering from client to support for especially client functionality as `window.alert('This is alert')` => have explicit in code

Pages Router
- Directory: ./pages dir
- Old
- Maintain mode
- Rendering html from both server and in browser - why : because they would like to run something that must render in broswer as `alert('This is alert')`
  - Step1 pre-render the HTML from server side then send the same component as script bundle so that can run the functioonality

#### App Router
#### 1. [app] Routing and Layouts
1.1 Create a nextjs project
`npx create-next-app@latest`

In the case you would like to use `typescript` - just add the `typescript` lib and write your `*.tsx` file

1.2 App routes
app
 /page.tsx
 /about/page.tsx
 /reviews/page.tsx
 /review/1/page.tsx

 nextjs will auto render the navigation page


 - All nextjs render on server side then send the html/text to browser that called pre-rendering.
 - React Single Page is rendered in browser

Why pre-rendering (https://react.dev/blog/2020/12/21/data-fetching-with-react-server-components)
- Faster Page load (Html just display HTML)
- Search Engine Friendly (SEO - that work better to understand our HTML only)
- Support non-JS clients

#### 2 React Server component
That can't use the React Hook or event handle

We have 2 differnt parts:
Server Components
   - Default
   - Rendered only on server -> No JS sent to the browser

Client Components
   - 'use client' directive
   - Rendered on server + client

#### 3. Style with TailwindCSS
3.1 Installation
`npm install --save-dev tailwindcss postcss autoprefixer`'
`npx tailwindcss init --postcss`

3.2 tsconfig.json or jsconfig.json for import alias
```json
  "complilerOptions": {
    "paths": {
      "@/*":["./*"]
    }
  }
```
For import we sat `@` is root so we have never use the `../../` anymore