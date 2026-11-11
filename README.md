# My Blog
![App Preview](https://imgix.cosmicjs.com/0d599bf0-d620-11f1-be00-97e7be1d270d-autopilot-photo-1498050108023-c5249f4df085-1793556857524.jpeg?w=1200&h=630&fit=crop&auto=format,compress)

A modern, fast blog website built with Astro, powered by your existing Cosmic content model of Posts, Authors, and Categories.

## Features

- 🏠 Hero homepage with a grid of the latest posts
- 📰 Full posts listing and detail pages with rendered markdown content
- 🏷️ Category listing and detail pages
- ✍️ Author listing and detail pages with bio cards
- 📱 Fully responsive header nav and footer
- 🖼️ Imgix-optimized images throughout
- 🔍 SEO-friendly meta tags on every page
- ⚡ Statically generated with Astro for blazing-fast performance

## Clone this Project

## Clone this Project

Want to create your own version of this project with all the content and structure? Clone this Cosmic bucket and code repository to get started instantly:

[![Clone this Project](https://img.shields.io/badge/Clone%20this%20Project-29abe2?style=for-the-badge&logo=cosmic&logoColor=white)](https://app.cosmicjs.com/projects/new?clone_bucket=6ae7814f5b93710bce4e2967&clone_repository=6ae7839a5b93710bce4e2ab4)

## Prompts

This application was built using the following prompts to generate the content structure and code:

### Content Model Prompt

> Create content models for a blog with posts (including featured images, content, and tags), authors, and categories.
>
> User instructions: A blog with posts, authors, and categories

### Code Generation Prompt

> Build a Next.js application for a creative portfolio called "My Blog". The content is managed in Cosmic CMS with the following object types: authors, categories, posts. Create a beautiful, modern, responsive design with a homepage and pages for each content type.
>
> User instructions: A modern, fast blog website built with Astro, powered by the existing Cosmic content model. Use the Astro framework.
>
> Content types:
> - posts: title, featured_image (image), content (rich-text markdown), author (object -> authors), category (object -> categories), tags (multi-select: Tutorial, News, Tips, Guide, Opinion, Inspiration)
> - authors: name, bio, avatar (image)
> - categories: name, description
>
> Pages:
> - Home: hero section plus a grid of the latest posts (featured image, title, excerpt, author avatar/name, category badge, date)
> - /posts: all posts listing
> - /posts/[slug]: post detail with featured image, rendered markdown content, tags, category link, and an author bio card at the bottom
> - /categories: list of categories; /categories/[slug]: category description plus its posts
> - /authors: list of authors; /authors/[slug]: author profile (avatar, bio) plus their posts
> - Responsive header nav (Home, Posts, Categories, Authors) and footer
>
> Clean, readable typography, responsive design, good SEO meta tags, and image optimization via imgix.

The app has been tailored to work with your existing Cosmic content structure and includes all the features requested above.

## Technologies Used

- [Astro](https://astro.build/) - Modern static site framework
- [Cosmic](https://www.cosmicjs.com) - Headless CMS for content management
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework
- [TypeScript](https://www.typescriptlang.org/) - Type-safe JavaScript
- [Marked](https://marked.js.org/) - Markdown to HTML rendering

## Getting Started

### Prerequisites

- [Bun](https://bun.sh/) installed on your machine
- A Cosmic account with a bucket containing `posts`, `authors`, and `categories` object types

### Installation

1. Clone this repository
2. Install dependencies:
   ```bash
   bun install
   ```
3. Set up your environment variables (see below)
4. Run the development server:
   ```bash
   bun run dev
   ```

### Environment Variables

Create a `.env` file in the root of your project with:

```env
COSMIC_BUCKET_SLUG=your-bucket-slug
COSMIC_READ_KEY=your-read-key
COSMIC_WRITE_KEY=your-write-key
```

## Cosmic SDK Examples

```typescript
// Fetch all posts with connected author and category
const { objects: posts } = await cosmic.objects
  .find({ type: 'posts' })
  .props(['id', 'slug', 'title', 'metadata'])
  .depth(1)

// Fetch posts by category id
const { objects: posts } = await cosmic.objects
  .find({ type: 'posts', 'metadata.category': categoryId })
  .depth(1)
```

## Cosmic CMS Integration

This app reads from three Cosmic object types:

- **posts** — `featured_image`, `content` (markdown), `author` (connected to authors), `category` (connected to categories), `tags` (multi-select)
- **authors** — `name`, `bio`, `avatar`
- **categories** — `name`, `description`

Connected objects (author, category) are resolved automatically using the `depth(1)` parameter so no extra API calls are required when rendering post cards or detail pages. Learn more in the [Cosmic docs](https://www.cosmicjs.com/docs).

## Deployment Options

### Vercel

1. Push your code to GitHub
2. Import the project in [Vercel](https://vercel.com)
3. Add your environment variables in the Vercel dashboard
4. Deploy

### Netlify

1. Push your code to GitHub
2. Import the project in [Netlify](https://netlify.com)
3. Set build command to `bun run build` and publish directory to `dist`
4. Add your environment variables in the Netlify dashboard
5. Deploy

<!-- README_END -->