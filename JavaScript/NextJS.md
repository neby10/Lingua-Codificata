# Next.js

## What is Next.js?

Next.js is a React framework that provides building blocks for fast web applications. [Cheatsheet](https://blog.wrappixel.com/nextjs-cheat-sheet/)

Some of the key features of NextJS include: [Source](https://www.xenonstack.com/blog/next.js-features)
- Page-based routing system: Do not have to write router code. Create a page in a special folder and NextJS provides routing.
- Pre-rendering: both static generation (SSG) and server-side rendering (SSR) are supported. Server-side rendering (SSR) prepares the content of a page on a server, while a one-page React application uses client-side rendering (CSR). The problem with CSR is that it's not SEO-friendly because search engines will not see the page's actual content. Using SSR in NextJS can avoid such issues as a flickering page while data fetching, and our website content will be SEO friendly.
- Built-in CSS and Sass support: and support for any CSS-in-JS library
- Full-stack capabilities: NextJS makes it easier for React developers to add backend code to the project. It is very easy to add our code for storing data, getting data, authentication, etc.
- Static Exports: Using the next export command, Next.js allows you to export a fully static site from your app.
- Dynamic components: We can also import javascript modules and React components dynamically.
- Prefetching: The Link component, used to link different pages, supports a prefetch prop that automatically prefetches page resources (including code missing due to code splitting) in the background.