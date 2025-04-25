# Next.js + Sanity Starter Template

A modern, ready-to-use template combining Next.js 15+ with Sanity CMS for building content-driven websites and applications.

## Features

- **Next.js 15+**: Latest Next.js framework with App Router support
- **Sanity CMS**: Fully integrated headless CMS
- **TypeScript**: End-to-end type safety
- **Tailwind CSS v4**: Utility-first CSS framework
- **Shadcn UI**: High-quality UI components based on Radix UI
- **Responsive Design**: Mobile-first approach
- **SEO Optimized**: Built-in metadata handling
- **Modern Fonts**: Google Fonts integration (Geist Sans and Geist Mono)

## Getting Started

### Prerequisites

- Node.js 18.17 or later
- pnpm package manager (recommended)

### Setup Instructions

1. Clone this template:

```bash
# with git
git clone https://github.com/sorryshady/next_sanity_starter.git my-project
cd my-project
```

2. Install dependencies:

```bash
pnpm install
```

3. Set up your environment variables:

```bash
# Copy the example env file
cp .env.example .env.local

# Then edit .env.local with your Sanity project details
```

4. Configure your Sanity project:

- Update the `nextsanity/sanity.config.ts` file with your project details
- Create schema types in the `nextsanity/schemaTypes` directory

5. Start the development server:

```bash
# Start Next.js development server
pnpm dev

# In a separate terminal, start Sanity Studio
cd nextsanity
pnpm dev
```

6. Open [http://localhost:3000](http://localhost:3000) to view your Next.js application
7. Open [http://localhost:3333](http://localhost:3333) to access Sanity Studio

## Environment Variables

For security and flexibility, this template uses environment variables. There are two approaches to handling them:

1. **Development (.env.local)**:

   - Create a `.env.local` file (not committed to Git)
   - Contains sensitive values for local development

2. **Production (deployment platforms)**:
   - Set environment variables in your deployment platform (Vercel, Netlify, etc.)

Required environment variables:

```
NEXT_PUBLIC_SANITY_PROJECTID=your_project_id
NEXT_PUBLIC_SANITY_DATASET=production
```

## Project Structure

```
├── app/                  # Next.js app directory
│   ├── globals.css       # Global styles
│   ├── layout.tsx        # Root layout component
│   └── page.tsx          # Home page
├── lib/                  # Utility functions and shared code
│   └── sanity_client.ts  # Sanity client configuration
├── nextsanity/           # Sanity Studio configuration
│   ├── schemaTypes/      # Content schemas
│   └── sanity.config.ts  # Sanity configuration
├── public/               # Static assets
├── .env.example          # Example environment variables
└── package.json          # Project dependencies
```

## Adding Content Models

1. Create new schema files in `nextsanity/schemaTypes/`
2. Export and add them to the `schemaTypes` array in `nextsanity/schemaTypes/index.ts`
3. Access your content via the Sanity client in your Next.js components

Example schema file (`nextsanity/schemaTypes/post.ts`):

```typescript
export default {
  name: "post",
  title: "Post",
  type: "document",
  fields: [
    {
      name: "title",
      title: "Title",
      type: "string",
    },
    {
      name: "content",
      title: "Content",
      type: "array",
      of: [{ type: "block" }],
    },
  ],
};
```

## Deployment

### Next.js Application

Deploy your Next.js application on platforms like Vercel, Netlify, or any hosting service that supports Next.js:

```bash
# Build for production
pnpm build
```

### Sanity Studio

Deploy Sanity Studio to make it accessible online:

```bash
cd nextsanity
pnpm deploy
```

## Customization

- **UI Components**: Add or customize components in the `components/` directory
- **Styling**: Modify the global styles in `app/globals.css`
- **Content Types**: Define your content models in `nextsanity/schemaTypes/`
- **Layout**: Update the app layout in `app/layout.tsx`

## License

[MIT License](LICENSE)
