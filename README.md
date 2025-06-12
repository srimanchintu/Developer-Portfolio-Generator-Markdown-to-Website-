# Project: Developer Portfolio Generator (Markdown to Website) 

# Objective 

Build a web app that:

Takes Markdown input (resume / portfolio).

Converts to HTML using templates/themes.

Allows live customization and preview.

Exports to static files for deployment (GitHub Pages). 

# Tech Stack 

Layer	Tools
Framework	Next.js
Styling	Tailwind CSS
Markdown Parsing	remark / react-markdown
Deployment	GitHub Pages
Optional Export	next export 

# Implementation Steps 
# Next.js Setup 
npx create-next-app portfolio-generator
cd portfolio-generator
npm install tailwindcss postcss autoprefixer
npx tailwindcss init -p 

Edit tailwind.config.js & add paths for purge.

module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: { extend: {} },
  plugins: [],
}

# Set up Tailwind in ./styles/globals.css:

@tailwind base;
@tailwind components;
@tailwind utilities;

# Install Markdown Parser 
npm install react-markdown remark-gfm

# Build Markdown Editor + Preview 

import { useState } from 'react';
import ReactMarkdown from 'react-markdown';
import remarkGfm from 'remark-gfm';

export default function Home() {
  const [markdown, setMarkdown] = useState(`# John Doe\n## About Me\nFull stack developer`);

  return (
    <div className="flex h-screen">
      <textarea 
        value={markdown} 
        onChange={(e) => setMarkdown(e.target.value)} 
        className="w-1/2 p-4 border-r border-gray-300" 
      />
      <div className="w-1/2 p-4 bg-gray-50 overflow-y-scroll">
        <ReactMarkdown children={markdown} remarkPlugins={[remarkGfm]} />
      </div>
    </div>
  );
}

This creates basic live editing + preview.

# Add Themes
Create multiple Tailwind themes using classNames or CSS variables.

Allow switching themes using state. 

const themes = {
  light: 'bg-white text-black',
  dark: 'bg-gray-900 text-white',
  solarized: 'bg-yellow-50 text-gray-800'
};
const [theme, setTheme] = useState('light');

<div className={`w-1/2 p-4 overflow-y-scroll ${themes[theme]}`}> 
  
# Deployment to GitHub Pages
Add next.config.js: 

# Export static site: 
next build && next export

# Deploy to GitHub Pages via:

Manual: Upload /out folder to gh-pages branch.

Automated: Use GitHub Actions or gh-pages npm package. 

# Optional Bonus): Deploy-to-GitHub Feature
Use GitHub OAuth API to connect user repo.

Push generated static site files directly to user’s repo.

Libraries: octokit for GitHub API. 

# Optional Bonus): Section Customization
Parse Markdown frontmatter (use gray-matter package).

Build components that allow toggling sections like skills, projects, etc.

npm install gray-matter

import matter from 'gray-matter';
const { data, content } = matter(markdown);

# Final Architecture Flow

 User writes Markdown --> Markdown Parser --> Theme Template --> Live Preview
                                |
                             Export
                                |
                          Deploy to GitHub Pages 
                          
# Deliverable Outcome
 Fully functional Markdown editor

 Live preview

 Multiple themes
 
 Static export

 Deployable via GitHub Pages  
 

 # OUTPUT 
 
 # App Layout:
Markdown Editor	Live Preview
Left side of screen	Right side of screen

Split-screen layout (flex h-screen).

Fully responsive on desktop.

Plain but functional UI.  


# Functional Features:

 Markdown Input
User sees a large text area on the left.

Can type or paste Markdown like:

# John Doe

## About Me
Full stack developer with 5 years of experience.

## Skills
- JavaScript
- React
- Node.js

## Projects
- **Project A**: A web app that does amazing things.

# Live Preview
As user types, the right side updates instantly.

Supports:

Headings

Lists

Bold text

Tables (if added)

Links, images, etc.

Markdown is parsed using react-markdown and remark-gfm (so GFM extensions like tables, checkboxes work).

# Theme Switcher 

Below the editor, there are two buttons:
 Light Theme
 Dark Theme

When user clicks:

The entire page background + text color switches.

Instant visual change for the preview.

# Deployment Ready 

The project can be exported as a static site with next export.

You can host this on:

GitHub Pages

Netlify

Vercel

Any static hosting platform 

# Visual Mockup
Here’s a text-based mockup of the page:
sql 

+---------------------------------------------------------------+
| Markdown Editor           | Live Preview                     |
|                            |                                   |
| # John Doe                 | John Doe                          |
| ## About Me                | About Me                          |
| Full stack developer ...   | Full stack developer ...          |
| - JavaScript               | • JavaScript                      |
| - React                    | • React                           |
| - Node.js                  | • Node.js                         |
|                            |                                   |
+----------------------------+-----------------------------------+
| Theme: [Light] [Dark]                                         |
+---------------------------------------------------------------+

# OUTCOME IMAGE


Tools: Next.js, Tailwind CSS, Markdown parser, GitHub Pages
![image](https://github.com/user-attachments/assets/f46cc865-8ddc-47f1-a9c3-2c785f7bfd7e)


# For this project i have used some tools 
Next.js, Tailwind CSS, Markdown parser, etc.  




