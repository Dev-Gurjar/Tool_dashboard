HOMESPICE DECOR

━━━━━━━━━━━━━━━━━━━━━━━━━━━━

COMMAND CENTER

Complete System Architecture & Build Specification

The Definitive Blueprint for AI-Powered Marketing Infrastructure

Version 2.0 | Expanded Build Specification

Brand: Homespice Decor — Family-owned braided rug manufacturer since 1980

Products: Jute, Cotton, and Ultra Durable polypropylene braided rugs

Channels: Amazon & Shopify

TABLE OF CONTENTS

Section 1 System Overview & Purpose

Section 2 Architecture & How It All Fits Together

Section 3 Technology Stack — Complete Reference

Section 4 The Hub (Home Screen) — Design & Behavior

Section 5 Knowledge Base — Architecture & Content Map

Section 6 Users, Roles & Access Control

Section 7 Authentication & Security

Section 8 Prompt Enhancement System

Section 9 Product Accuracy Rules Engine

Section 10 Generation Feedback Loop

Section 11 Cost Tracking & Budget Controls

Section 12 Tool Specifications — Rug Image Generator

Section 13 Tool Specifications — Static Ads Builder

Section 14 Tool Specifications — UGC Builder

Section 15 Tool Specifications — CMO Dashboard

Section 16 Tool Specifications — Copy & Script Generator

Section 17 Tool Specifications — Social Media Pack

Section 18 Tool Specifications — Homespice Bot

Section 19 External Service Integrations

Section 20 Database Schema & Data Models

Section 21 API Routes & Endpoint Reference

Section 22 Frontend Component Architecture

Section 23 Settings Page — Complete Specification

Section 24 Error Handling, Logging & Monitoring

Section 25 Deployment, Environment & DevOps

Section 26 File & Folder Structure

Section 27 Build Priority & Phased Rollout Plan

Section 28 Testing Strategy

Section 29 Performance & Scalability

Section 30 Appendices — Design Tokens, Wireframes, Data Dictionaries

# SECTION 1: SYSTEM OVERVIEW & PURPOSE

## 1.1 What This Is

The Homespice Command Center is a single internal web application where the Homespice Decor team logs in and accesses all their AI-powered marketing tools from one unified interface. Think of it as a home screen with tool cards — click a card, launch that tool. It is the central nervous system for all creative and marketing operations at Homespice Decor.

The command center itself is not a tool. It is the shell that holds tools. It provides the infrastructure, authentication, shared services, and navigation that every individual tool plugs into. Tools are built separately and added one at a time. When a tool is not yet built, it simply does not appear on the Hub — there are no 'coming soon' placeholders.

## 1.2 What The Command Center Provides

- A login page — only team members with accounts created by an Admin can access the system

- A home screen (the Hub) showing all available tools as visual cards with icons, descriptions, and category tags

- A shared knowledge base that feeds brand context into every tool — ensuring every AI generation sounds like Homespice, follows the brand rules, and references real product details

- A shared prompt enhancement system that transforms rough, casual user input into detailed, brand-aware AI prompts before generation

- A Settings page for managing users, API connections, the knowledge base, and system configuration

- A generation feedback system so the team can flag bad AI outputs with structured issue categories, enabling continuous improvement

- A cost counter showing real-time and cumulative spending on AI generation across all tools

- A collapsible sidebar for quick navigation between tools without returning to the Hub

- A notification system for completed generations, flagged issues, and system alerts

## 1.3 The Brand — Homespice Decor

Homespice Decor is a family-owned braided rug manufacturer operating since 1980. They are vertically integrated — they control the entire process from raw fiber to finished rug. Their product lines span three material categories: natural jute braided rugs, cotton blend braided rugs, and Ultra Durable solution-dyed polypropylene braided rugs (including the premium Luxuria sub-line). Rugs are sold primarily through Amazon and Shopify, with the company targeting both direct-to-consumer and wholesale channels.

The brand identity is warm, natural, authentic, and family-oriented. It is not luxury, not tech-forward, not minimalist. Think 'well-organized workshop' — clean, professional, approachable. The visual identity draws from earth tones, warm neutrals, sage greens, and rustic browns.

## 1.4 Why This Exists

Without the Command Center, the Homespice marketing team faces fragmented workflows: separate tools for image generation, separate tools for ad copy, no centralized brand context, no way to track AI spending, and no structured feedback loop to improve generation quality over time. Every AI tool produces generic, off-brand output because it has no context about what Homespice is, what their rugs look like, or how the brand communicates.

The Command Center solves this by providing a single entry point with shared brand intelligence that makes every tool smarter, a unified cost tracking system, and a feedback loop that improves output quality over time.

## 1.5 Tools — Complete List & Build Priority

Each tool is built as a separate task with its own detailed specification. The build priority order reflects business impact and dependency chains:

| Priority | Tool Name | Category | What It Does | Primary AI Service |
| --- | --- | --- | --- | --- |
| 1 | Rug Image Generator | Image Generation | Generate product images across sizes, shapes, and room settings for Amazon/Shopify product listings. Supports all 3 material lines, all shapes, all colorways. | FAL AI (Flux, SDXL) |
| 2 | Static Ads Builder | Ad Creative | Build ad concepts and generate production-ready static images for Meta ads. Includes headline/body copy overlay, CTA placement, brand badge. | FAL AI + Claude |
| 3 | UGC Builder | Video Production | Generate AI video content — quick hooks (5-15s), extended reviews (30-60s), and atmospheric B-roll clips. Includes AI voice-over and actor selection. | FAL AI (video) + Claude |
| 4 | CMO Dashboard | Analytics | Automated marketing reporting with AI weekly summaries, performance tracking across Shopify, Amazon, Meta, Google Ads. Manual data entry + API pulls. | Claude (summaries) |
| 5 | Copy & Script Generator | Copywriting | Build a strategic brief, then generate ad copy across formats: headlines, body copy, email sequences, product descriptions, social captions. | Claude |
| 6 | Social Media Pack | Social Media | Generate platform-native content packages for Instagram, TikTok, Pinterest, and Facebook with correct dimensions, hashtags, and posting schedules. | Claude + FAL AI |
| 7 | Homespice Bot | Knowledge Chat | Chat with an AI that knows everything about the Homespice brand — products, positioning, history, voice, competitors. Internal Q&A for the team. | Claude |

| CRITICAL BUILD RULE<br>Each tool has its own detailed specification submitted as a separate task document. This architecture document defines the shell, shared services, and integration points. It does NOT contain the full internal logic of each tool — only enough context for an AI to understand how each tool connects to the Command Center. |
| --- |

# SECTION 2: ARCHITECTURE & HOW IT ALL FITS TOGETHER

## 2.1 The Two-App Architecture

The system runs two applications within the same Replit project, each on its own port:

### Main App (Port 3000)

The command center itself. This is a React frontend with an Express/Node.js backend. It contains the Hub, login page, Settings, knowledge base management, the prompt enhancement service, cost tracking, feedback system, and every tool EXCEPT the Static Ads Builder. All new tools are built directly inside this app as new routes and React pages.

### Static Ads Builder (Port 3001)

A standalone application that runs on a separate port. It has its own complete frontend and backend — over 15,000 lines of tested, working code. Rather than rewriting this into the main app (which would be risky and time-consuming), it runs alongside the main app and is embedded via an iframe when the user clicks 'Static Ads Builder' on the Hub.

When a user navigates to the Static Ads Builder from the Hub, it loads inside the main app's layout — the user does not know or care that it is technically a separate app. The iframe fills the content area, and the main app's sidebar and header remain visible.

## 2.2 System Connection Diagram

Here is how every component connects:

| User opens browser → Login Page → Hub (Home Screen)<br>│<br>├── [Rug Image Generator] ── built inside Main App<br>├── [UGC Builder] ── built inside Main App<br>├── [Copy & Script Generator] ── built inside Main App<br>├── [Social Media Pack] ── built inside Main App<br>├── [Homespice Bot] ── built inside Main App<br>├── [CMO Dashboard] ── built inside Main App<br>│<br>└── [Static Ads Builder] ── separate app, port 3001, embedded via iframe<br>│<br>└── Has its own product-specs.js (kept in sync manually with KB)<br>All tools above connect to SHARED SERVICES:<br>├── Knowledge Base (tag-filtered context per tool)<br>├── Prompt Enhancement Engine (Claude-powered)<br>├── FAL AI Client (image & video generation)<br>├── Cost Tracking Service<br>├── Feedback System<br>└── Authentication Middleware<br>EXTERNAL SERVICES:<br>├── FAL AI → images (Flux, SDXL), video, voice cloning<br>├── Claude API → prompt enhancement, chat, copy generation, AI summaries<br>├── Google Gemini → planning, validation, alternative generation<br>├── Airtable → UGC actor/scene data management<br>├── Shopify API → revenue, orders, product data (dashboard)<br>├── Amazon SP-API → sales, advertising metrics (dashboard)<br>├── Meta Ads API → campaign performance, ad spend (dashboard)<br>└── Google Ads API → search/display campaign data (dashboard) |
| --- |

## 2.3 Data Flow — How a Generation Request Works

This is the complete data flow for any generation request (image, video, or text) from user input to final output:

- User Input: Team member types a rough description in a tool (e.g., 'Kilimanjaro rug in a farmhouse kitchen with a dog')

- KB Context Load: Backend loads knowledge base documents tagged for this specific tool (e.g., Rug Image Generator loads: all, products, rug-accuracy)

- Prompt Enhancement: The rough input + KB context are sent to Claude API. Claude returns a detailed, brand-aware prompt with material textures, color depth rules, room proportions, camera angles, and accuracy constraints.

- User Review: Enhanced prompt appears in an editable text box. User can approve, edit, or re-enhance.

- Generation: Approved prompt is sent to the generation service (FAL AI for images/video, Claude for text). Request is logged with timestamp, user, tool, prompt, and cost.

- Cost Recording: API cost is calculated and added to the running total. Per-user, per-tool, and per-day breakdowns are updated.

- Output Display: Generated result is displayed to the user with a thumbs-down feedback button.

- Feedback (if needed): User clicks thumbs-down, selects issue category from dropdown, optionally adds notes. Feedback is stored and visible in Settings for the developer to analyze.

## 2.4 Adding a New Tool — The Plugin Pattern

The Command Center is designed so that adding a new tool requires exactly three steps:

- Add the tool's page: Create a new React page component in the frontend and its corresponding backend route file.

- Add a card entry to the Hub config: One object in the tools array: { name, icon, description, categoryTag, categoryColor, route, kbTags }.

- Register the backend routes: Import and mount the tool's Express router in the main server file.

That is it. The command center does not need to be rewritten or restructured for each new tool. The Hub automatically renders cards for all registered tools. The knowledge base tag system automatically provides the right context. The prompt enhancer automatically uses the tool's configured KB tags.

# SECTION 3: TECHNOLOGY STACK — COMPLETE REFERENCE

## 3.1 Frontend Stack

| Technology | Version | Purpose | Notes |
| --- | --- | --- | --- |
| React | 18.x | UI framework | Functional components + hooks only. No class components. |
| React Router | 6.x | Client-side routing | Nested routes for tool pages. Protected routes for auth. |
| Tailwind CSS | 3.x | Styling | Utility-first CSS. Custom brand color palette in tailwind.config.js. |
| Axios | 1.x | HTTP client | All API calls. Interceptors for auth token injection and error handling. |
| React Hook Form | 7.x | Form management | Used in Settings, KB editor, feedback forms. |
| Zustand | 4.x | State management | Lightweight global state for auth, active tool, cost counter. |
| Lucide React | Latest | Icons | Clean, consistent icon set throughout the UI. |
| React Toastify | Latest | Notifications | Toast notifications for generation complete, errors, feedback sent. |
| React Markdown | Latest | Markdown rendering | Used in Homespice Bot and KB document viewer. |

## 3.2 Backend Stack

| Technology | Version | Purpose | Notes |
| --- | --- | --- | --- |
| Node.js | 20.x LTS | Runtime | LTS version for stability. Runs both Main App and Static Ads Builder. |
| Express | 4.x | HTTP framework | RESTful API. Middleware chain for auth, rate limiting, error handling. |
| SQLite | Better-sqlite3 | Database | File-based DB. No external DB server needed. Single file: data.db. |
| bcrypt | 5.x | Password hashing | Salt rounds: 12. Used for user password storage. |
| jsonwebtoken | 9.x | JWT auth | Access tokens (15min) + refresh tokens (7 days). |
| multer | 1.x | File uploads | Handles image uploads for KB docs, edited images, profile photos. |
| node-cron | 3.x | Scheduled tasks | Daily cost rollup, weekly dashboard summary generation. |
| winston | 3.x | Logging | Structured JSON logs. Separate files for errors, access, generation. |
| helmet | 7.x | Security headers | HSTS, XSS protection, content security policy. |
| cors | 2.x | CORS | Configured to allow iframe communication with Static Ads Builder. |
| compression | 1.x | Gzip | Response compression for all API responses. |

## 3.3 External APIs & Services

| Service | API Type | Used By | Purpose | Auth Method |
| --- | --- | --- | --- | --- |
| FAL AI | REST | Rug Generator, Static Ads, UGC Builder, Social Pack | Image generation (Flux Pro, SDXL), video generation, voice cloning | API key in header |
| Anthropic Claude | REST | Prompt Enhancer, Copy Generator, Bot, Dashboard summaries | Text generation, prompt enhancement, chat, copy writing, AI summaries | API key in header |
| Google Gemini | REST | Copy Generator, UGC Builder | Planning, validation, strategic brief generation, alternative approaches | API key in header |
| Airtable | REST | UGC Builder | Actor database, scene templates, shoot schedules, asset management | Bearer token |
| Shopify Admin API | GraphQL | CMO Dashboard | Revenue, orders, products, customer data, inventory | Access token |
| Amazon SP-API | REST | CMO Dashboard | Sales data, advertising metrics, product performance | OAuth 2.0 + STS |
| Meta Marketing API | REST | CMO Dashboard, Static Ads Builder | Ad campaign performance, spend, ROAS, audience insights | Access token |
| Google Ads API | REST | CMO Dashboard | Search/display campaign data, keyword performance | OAuth 2.0 |

## 3.4 Development & Deployment

| Aspect | Choice | Details |
| --- | --- | --- |
| Hosting | Replit | Both apps run in the same Replit project. Main App on port 3000, Static Ads Builder on port 3001. |
| Version Control | Git (Replit integrated) | Commit after every feature. Branches for major features. |
| Environment Variables | .env file | All API keys, JWT secrets, database paths stored in .env. Never committed to repo. |
| Build Process | Vite | React frontend built with Vite for fast dev server and optimized production builds. |
| Package Manager | npm | Lock file committed. No yarn or pnpm. |
| Process Management | Replit + concurrently | Both apps started via concurrently in package.json start script. |

# SECTION 4: THE HUB (HOME SCREEN) — DESIGN & BEHAVIOR

## 4.1 Layout Specification

After login, the user sees the Hub. This is the command center's home screen. The layout consists of a top header bar, a collapsible left sidebar, and a main content area with tool cards.

### Header Bar

- Left: hamburger menu icon (toggles sidebar) + 'Homespice Command Center' title text

- Right: cost counter badge (shows today's AI spend), notification bell, user avatar + name, Settings gear icon

- Fixed position — stays visible when scrolling the Hub content

### Sidebar (Collapsible)

- Shows icons + names of all available tools for quick navigation without returning to Hub

- Collapsed state: icons only (60px wide). Expanded state: icons + labels (240px wide)

- Persists user's collapse preference in localStorage

- On mobile: slides in as an overlay, closes on navigation or outside tap

### Main Content Area

- Hero section: 'Homespice Command Center' heading + 'Your AI-powered marketing studio.' subheading

- Tool card grid: 2 columns on desktop (min-width: 768px), 1 column on mobile

- Cards appear only for tools that are built and registered. No 'coming soon' cards ever.

## 4.2 Tool Card Specification

Each tool card displays the following elements:

| Element | Position | Details |
| --- | --- | --- |
| Category Tag Badge | Top-right corner | Colored pill badge — e.g., 'Image Generation' (sage green), 'Video' (rust), 'Analytics' (navy), 'Copywriting' (warm brown), 'Chat' (accent) |
| Icon | Top-left | Lucide icon matching the tool's function. 24x24px. Same color as category tag. |
| Tool Name | Below icon | Bold, 16px, dark brown (#4A3728). The tool's display name. |
| Description | Below name | Regular, 14px, medium gray. 1-2 sentences max. What the tool does. |
| Launch Link | Bottom-right | 'Launch →' link text. Navigates to tool page on click. |
| Card Container | Full card | Rounded corners (8px), subtle shadow, white background, hover: slight lift + shadow increase, border: 1px solid #E8E4DE |

## 4.3 Tool Card Configuration

Each tool card is defined by a single config object. When a new tool is ready, add one entry to this array:

| // /src/config/tools.js<br>export const tools = [<br>{<br>id: "rug-generator",<br>name: "Rug Image Generator",<br>description: "Generate product images across sizes, shapes, and room settings for Amazon/Shopify listings.",<br>icon: "Image", // Lucide icon name<br>category: "Image Generation",<br>categoryColor: "#7A8B6F", // sage green<br>route: "/tools/rug-generator",<br>kbTags: ["all", "products", "rug-accuracy"],<br>roles: ["admin", "manager", "creator"], // who can see this card<br>enabled: true,<br>},<br>// ... more tools<br>]; |
| --- |

## 4.4 Visual Design System

### Brand Color Palette

| Token Name | Hex Value | Usage |
| --- | --- | --- |
| --color-dark-brown | #4A3728 | Primary headings, card titles, sidebar active state |
| --color-warm-brown | #6B4F3A | Secondary headings, hover states, accents |
| --color-sage | #7A8B6F | Success states, image generation category, nature feel |
| --color-cream | #F5F0E8 | Page background, card hover background |
| --color-rust | #B85C3A | Warnings, video category, callout borders, error states |
| --color-navy | #2C3E50 | Analytics category, dashboard elements, data visualizations |
| --color-light-gray | #E8E4DE | Card borders, dividers, disabled states |
| --color-accent | #D4A574 | CTAs, links, active tab indicators, cost counter |
| --color-white | #FFFFFF | Card backgrounds, input fields, content areas |
| --color-black | #1A1A1A | Body text, form labels |

### Typography

- Primary font: Inter (fallback: system-ui, sans-serif)

- Heading 1: 24px, bold, dark brown

- Heading 2: 20px, semibold, warm brown

- Heading 3: 16px, semibold, sage

- Body: 14px, regular, black (#1A1A1A)

- Small/caption: 12px, regular, medium gray (#999999)

- Code/monospace: JetBrains Mono or Fira Code, 13px

### Spacing & Layout

- Base unit: 4px. All spacing is multiples of 4px.

- Card padding: 24px

- Card gap: 24px (grid gap)

- Page margin: 32px on desktop, 16px on mobile

- Section spacing: 48px between major sections

- Border radius: 8px for cards, 6px for buttons, 4px for inputs

### Design Philosophy

Light mode with warm, natural colors matching Homespice's brand identity. The visual feel is 'well-organized workshop' — clean, professional, approachable. NOT luxury boutique. NOT tech startup. Think warm wood tones, natural textures, craft sensibility. Desktop is the primary use case, but everything should stack cleanly on mobile.

# SECTION 5: KNOWLEDGE BASE — ARCHITECTURE & CONTENT MAP

## 5.1 What It Is & Why It Matters

The knowledge base is a collection of structured documents about the Homespice brand that AI tools use as context when generating any output. When the Rug Image Generator creates a prompt for FAL AI, or the Copy Generator writes ad copy, or the Homespice Bot answers a question — they all pull from this knowledge base to stay on-brand and accurate.

Without the knowledge base, every tool produces generic output. With it, outputs sound like Homespice, follow the brand's rules, reference real product details, use the correct terminology, and avoid common mistakes. The knowledge base is the single source of truth that makes every tool intelligent about the brand.

## 5.2 Storage Architecture

Documents are stored in a SQLite database with the following schema:

| CREATE TABLE kb_documents (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>name TEXT NOT NULL, -- Human-readable document name<br>slug TEXT NOT NULL UNIQUE, -- URL-safe identifier<br>content TEXT NOT NULL, -- The actual document content (markdown)<br>tags TEXT NOT NULL, -- JSON array of tag strings<br>size_limit INTEGER DEFAULT 100000, -- Max characters for this doc<br>created_at TEXT NOT NULL,<br>updated_at TEXT NOT NULL,<br>created_by INTEGER REFERENCES users(id),<br>updated_by INTEGER REFERENCES users(id)<br>);<br>CREATE TABLE kb_versions (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>document_id INTEGER REFERENCES kb_documents(id),<br>content TEXT NOT NULL, -- Snapshot of content at this version<br>tags TEXT NOT NULL, -- Snapshot of tags at this version<br>saved_at TEXT NOT NULL,<br>saved_by INTEGER REFERENCES users(id),<br>version_num INTEGER NOT NULL -- Sequential version number<br>); |
| --- |

## 5.3 Tag System — Complete Reference

Each document is tagged with one or more tags. Tags control which tools receive which documents as context. When a tool needs KB context, it loads ONLY the documents tagged for that tool. This keeps AI prompts focused and relevant instead of dumping everything into every API call.

| Tag | What Goes Here | Documents |
| --- | --- | --- |
| all | Core brand info that every tool needs — company story, key differentiators, mission statement, what Homespice is and is NOT | Homespice — Who We Are |
| brand | Brand guidelines, visual identity, photography direction, logo usage, social media visual identity, photography standards | Visual Direction & Brand Guidelines; Photography Standards |
| products | Product catalog — materials, construction, sizing chart, colorway names and visual descriptions, availability matrix, care instructions | Complete Product Catalog; Material Deep Dive |
| rug-accuracy | AI generation rules — braided texture definition, color depth rules (14-21 shades), edge behavior, proportion tables, common AI mistakes and corrections | How to Generate Accurate Rug Images; Room Scene Reference Guide |
| voice | Brand voice guide — tone, word choices, phrases to use and avoid, reading level, sentence structure, how to talk about price and competitors | How Homespice Talks |
| copy-angles | Proven messaging frameworks — persona-angle matrix, proof points, objection handling, winning hooks, hook library | Proven Angles & Messaging Framework; Hook Library |
| personas | Customer persona profiles — P1 through P4 with demographics, pain points, visual direction, buying triggers, objections | The Homespice Personas |
| competitive | Competitor analysis — how Homespice compares to Amazon commodity rugs, Wayfair, Pottery Barn, West Elm, Target | Competitive Intelligence docs (TBD) |
| performance | What has worked in past campaigns — winning angles, best formats, top hooks, seasonal patterns, creative fatigue observations | Campaign Performance Log (starts empty, grows over time) |

## 5.4 Tool-to-Tag Mapping

This mapping is critical — it defines exactly what context each tool receives. The mapping is stored as a constant in the backend and displayed in the Settings UI as a reference:

| Tool | Tags Loaded |
| --- | --- |
| Rug Image Generator | all, products, rug-accuracy |
| Static Ads Builder | all, brand, products, rug-accuracy, personas, performance |
| UGC Builder | all, brand, products, personas |
| Copy & Script Generator | all, brand, voice, copy-angles, personas, competitive, performance |
| Social Media Pack | all, brand, voice, personas |
| Homespice Bot | all, brand, products, voice, copy-angles, competitive, personas |
| CMO Dashboard (AI summaries only) | all, brand |

## 5.5 Knowledge Base Content Structure — Document Map

This is the complete skeleton of what needs to exist in the knowledge base. Content is built as a separate project — this defines the structure only.

### A. Brand Foundation (tag: all)

"Homespice — Who We Are"

- Company origin story — founded in 1980, family-owned, the founder's vision

- Vertically integrated manufacturing — what this means specifically (control from raw fiber to finished rug, quality at every step)

- Three product lines overview: jute (natural, handcrafted), cotton blend (soft, colorful), Ultra Durable (solution-dyed polypropylene, indoor/outdoor)

- Five key differentiators vs. commodity rugs on Amazon/Wayfair

- Price positioning and justification — why Homespice rugs cost what they cost and why they're worth it

- Repeat buyer data — loyalty metrics, customer lifetime value signals

- What Homespice is NOT — not mass-produced, not cheap, not synthetic-feeling, not trend-chasing

### B. Brand Identity (tag: brand)

"Visual Direction & Brand Guidelines"

- Brand colors with hex values — primary, secondary, accent, neutrals

- Typography — primary and secondary fonts, sizes, weights, hierarchy

- Logo usage — placement rules, minimum sizes, clear space, what not to do

- Photography direction — the overall visual feel, what to shoot, what to avoid

- Visual feel definition (one sentence that captures the brand's visual identity)

- Social media visual identity — how the brand appears on Instagram, Pinterest, Facebook, TikTok

"Photography Standards"

- Product photo requirements — angles to shoot, what to show (texture, braid pattern, color depth)

- Room setting guidelines — which rooms, which interior styles, furniture types

- Lighting rules — natural light preferred, warm tone, no harsh studio lighting

- People and pet inclusion rules — when to include, how to style, diversity guidelines

### C. Product Catalog (tag: products)

"Complete Product Catalog"

- All active colorways — name plus a detailed visual description for each (what colors are in the braid, the dominant tone, the mood)

- Size chart with exact dimensions for each shape

- Available shapes: oval, round, rectangle, runner, heart, special shapes

- Price ranges by size and material line

- Colorway × shape × size availability matrix — not every colorway comes in every size and shape

- Care instructions per material line

- Custom rug capability and lead times

"Material Deep Dive"

- Jute: fiber source, dye process, braiding technique, finish, pile height, how it differs from sisal and seagrass

- Cotton blend: fiber composition, visual and tactile differences from jute, color vibrancy

- Ultra Durable: solution-dyed polypropylene, what makes it indoor/outdoor, how it looks different from natural fibers

- Luxuria: what makes it premium within the Ultra Durable line, tactile feel, visual characteristics

### D. AI Generation Rules (tag: rug-accuracy)

"How to Generate Accurate Rug Images"

- Braided texture definition — what braided construction looks like vs. flat-weave, tufted, knotted, woven

- Color depth rule: every rug must show 14-21 distinct shades within its colorway, not flat uniform color

- Edge behavior rules — clean folded edges, no fringe, no unraveling, no visible seams (unless the rug actually has them)

- Shape-specific construction details — how round rugs spiral, how rectangles have straight-line braids, how runners maintain consistency

- Size-to-room proportion guidance per size — a 2x3 looks one way in a kitchen, a 8x10 looks different under a dining table

- Floor contact rules — the rug must lay flat on the floor, no floating, no curling, no hovering above the surface

- Common AI mistakes and their corrections — with visual examples of what goes wrong and how to fix the prompt

- Material-specific appearance differences — jute looks rough and natural, cotton looks soft and bright, Ultra Durable looks clean and uniform

"Room Scene Reference Guide"

- Per room type: typical furniture, rug sizes used, lighting style, interior design feel, camera angles

- Rooms covered: living room, kitchen, entryway/foyer, bedroom, bathroom, hallway/runner, dining room, outdoor patio

### E. Brand Voice (tag: voice)

"How Homespice Talks"

- Reading level target — what grade level the copy should hit

- Tone definition — warm, approachable, knowledgeable, craft-proud, never condescending or salesy

- Brand voice character description — if the brand were a person, who would they be

- Words and phrases TO USE — approved vocabulary list

- Words and phrases to AVOID — banned vocabulary list with reasons

- Sentence structure rules — short sentences, active voice, concrete details over abstractions

- How to talk about price — value framing, not discount framing

- How to talk about competitors — without naming them, positioning on quality and craft

- Good copy vs. bad copy examples — side-by-side comparisons

### F. Customer Personas (tag: personas)

"The Homespice Personas" — P1 through P4

Structure and content to be defined by Viktor and team. Each persona should include: demographic profile, psychographic profile, pain points, buying triggers, objections, preferred channels, visual direction for targeting this persona, and messaging angles that resonate.

### G. Copy & Messaging (tag: copy-angles)

"Proven Angles & Messaging Framework"

Structure to be defined by Viktor. Should include: persona-angle matrix (which angles work for which personas), proof points per angle, objection handling scripts, winning hooks organized by angle.

"Hook Library"

A growing collection of hooks that have been tested and performed well. Organized by format (headline, opening line, question hook, story hook) and by persona target.

### H. Competitive Intelligence (tag: competitive)

Will have a more elaborate architecture than a single document. Multiple documents covering: Amazon commodity rug comparison, Wayfair comparison, Pottery Barn / West Elm comparison, Target / big box comparison. Each includes: price comparison, quality differences, customer review analysis, positioning opportunities.

### I. Performance Learnings (tag: performance)

"Campaign Performance Log" — starts empty, grows over time

- Best and worst ad formats by actual performance data

- Angle × audience resonance — which messages resonate with which personas

- Top-performing colorways in ads

- Best room settings for lifestyle images

- Seasonal patterns — what works in spring vs. fall, holiday season insights

- Creative fatigue observations — when ads start losing performance

- Platform-specific learnings — what works on Meta vs. Amazon vs. Google

## 5.6 Knowledge Base Size Limits

Per-file size limit: 100,000 characters by default. This can be adjusted per document via the size_limit field in the database. Some files (like a comprehensive product catalog with all colorways) may need a higher limit (200,000+), while short docs like the voice guide will stay well under 50,000.

## 5.7 Access Control

- Admin and Manager: Full CRUD access — can add, edit, delete, and restore knowledge base documents

- Creator: Read-only access — can view documents to understand brand context but cannot modify them

- Editor and Viewer: No KB access (Editors work on image editing queue; Viewers only see generation history)

## 5.8 Version History

Every time a document is saved, the previous version is automatically preserved in the kb_versions table. Each version records: the full content snapshot, tags at that point in time, timestamp, and the user who made the change. If someone edits the brand guidelines and the next batch of generated images looks wrong, the team can see exactly what changed and restore the previous version with one click.

## 5.9 Sync Note — Static Ads Builder

| SYNC WARNING<br>The Static Ads Builder has its own product-specs.js file containing rug accuracy rules in a code format optimized for image generation. The knowledge base also has rug accuracy documents in prose format. These contain overlapping information in different formats. There is NO automatic sync between them. When accuracy rules change (based on generation feedback), the developer must update BOTH the KB document AND the product-specs.js file. The Settings UI should include a visible reminder about this. |
| --- |

# SECTION 6: USERS, ROLES & ACCESS CONTROL

## 6.1 Role Definitions

| Role | Tools Access | Knowledge Base | Dashboard | User Mgmt | Settings |
| --- | --- | --- | --- | --- | --- |
| Admin | All tools — full generation + review + approve | Full CRUD — add, edit, delete, restore | Full access — all 10 screens, drill-downs, manual entry, export | Yes — create invite links, assign roles, deactivate users | Full — API keys, system config, cost limits |
| Manager | All tools — full generation + review + approve | Full CRUD — add, edit, delete, restore | Full access — all 10 screens, drill-downs, manual entry, export | No | KB management only |
| Creator | All creation tools — images, video, copy, social | Read-only — can view but not edit documents | Executive Summary only | No | No |
| Editor | Editing queue only — flagged images for manual touch-up. Can upload edited versions. Cannot generate new content. | No access | Executive Summary only | No | No |
| Viewer | View generation history only — no generation capability | No access | Executive Summary only | No | No |

## 6.2 Dashboard Access Tiers

The CMO Dashboard has two distinct access levels:

- Full Access: All 10 dashboard screens, drill-downs, manual data entry, settings, CSV/PDF export. Granted to Admin, Manager, and specifically designated team members.

- Executive Summary Only: The top-level overview screen showing revenue, transactions, CVR, ROAS, and channel performance. Granted to all authenticated users (Creator, Editor, Viewer). This gives the whole team visibility into how the business is doing without exposing detailed campaign data or financial inputs.

## 6.3 User Onboarding Flow

- Admin creates an invite link: Selects a role for the new user. The link is valid for 72 hours and single-use.

- New user opens the link: Sees a registration form — enters their display name and creates a password. Email is optional (used for notifications only, not for login).

- Account is created: The user can now log in and see tools appropriate to their role. They land on the Hub.

## 6.4 Initial Team Roster

| Person | Title/Role | System Role | Access Level |
| --- | --- | --- | --- |
| Viktor | Developer / System Admin | Admin | Everything — full system control |
| Junior (CEO) | CEO | Admin | All tools + full dashboard |
| Josue | Team Member | Manager | Full dashboard access, all creation tools, KB management |
| Usama | Amazon CMO | Manager | Full dashboard access, all creation tools, KB management |
| Sumit | Team Member | Manager | Full dashboard access, all creation tools, KB management |
| Aashiq | Team Member | Creator | All creation tools |
| Sonu | Team Member | Creator | All creation tools |
| Ravi | Team Member | Creator | All creation tools |
| Shalini | Team Member | Editor | Rug Generator editing queue, all creation tools |
| Ipek | Creative Strategist | Creator | All creation tools, view-only KB access |
| Malva | Creative Editor/Manager | Manager | All creation tools, full KB access, review/approve |

# SECTION 7: AUTHENTICATION & SECURITY

## 7.1 Authentication Flow

The system uses JWT (JSON Web Token) based authentication with access and refresh tokens.

### Login Flow

- User navigates to /login — sees username and password fields

- User enters credentials and submits the form

- Backend validates credentials against bcrypt-hashed password in SQLite

- On success: backend returns an access token (15-minute expiry) and a refresh token (7-day expiry, stored as httpOnly cookie)

- Frontend stores the access token in memory (Zustand store) — NOT in localStorage

- All subsequent API requests include the access token in the Authorization header

- When the access token expires, the frontend silently calls /api/auth/refresh using the httpOnly refresh cookie

- If the refresh token is also expired, the user is redirected to /login

## 7.2 Database Schema — Users

| CREATE TABLE users (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>username TEXT NOT NULL UNIQUE,<br>display_name TEXT NOT NULL,<br>password_hash TEXT NOT NULL, -- bcrypt, 12 salt rounds<br>email TEXT, -- optional, for notifications<br>role TEXT NOT NULL, -- 'admin', 'manager', 'creator', 'editor', 'viewer'<br>is_active BOOLEAN DEFAULT 1, -- soft delete / deactivation<br>created_at TEXT NOT NULL,<br>last_login TEXT<br>);<br>CREATE TABLE invite_links (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>token TEXT NOT NULL UNIQUE, -- crypto.randomBytes(32).toString('hex')<br>role TEXT NOT NULL,<br>created_by INTEGER REFERENCES users(id),<br>created_at TEXT NOT NULL,<br>expires_at TEXT NOT NULL, -- 72 hours from creation<br>used BOOLEAN DEFAULT 0<br>);<br>CREATE TABLE refresh_tokens (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>user_id INTEGER REFERENCES users(id),<br>token_hash TEXT NOT NULL, -- bcrypt hash of the actual token<br>expires_at TEXT NOT NULL,<br>created_at TEXT NOT NULL<br>); |
| --- |

## 7.3 Route Protection

Every API route (except /api/auth/login, /api/auth/register, and /api/auth/refresh) goes through authentication middleware. The middleware verifies the JWT access token, extracts the user's ID and role, and attaches them to the request object. Routes that require specific roles use a second middleware layer:

| // Middleware chain example:<br>router.post('/api/kb/documents', authenticate, requireRole(['admin', 'manager']), createDocument);<br>router.get('/api/kb/documents', authenticate, getDocuments); // any authenticated user<br>router.delete('/api/users/:id', authenticate, requireRole(['admin']), deactivateUser); |
| --- |

## 7.4 Security Measures

- All passwords hashed with bcrypt (12 salt rounds) — never stored in plaintext

- Access tokens are short-lived (15 minutes) and stored only in memory — not localStorage

- Refresh tokens are stored as httpOnly, secure, sameSite=strict cookies — inaccessible to JavaScript

- Helmet middleware sets security headers: HSTS, X-Content-Type-Options, X-Frame-Options (SAMEORIGIN for iframe support)

- Rate limiting on login endpoint: 5 attempts per IP per 15 minutes

- All API keys stored in .env file — never committed to version control

- CORS configured to allow only the main app domain and the Static Ads Builder port

- Input sanitization on all user-facing endpoints to prevent XSS and SQL injection

# SECTION 8: PROMPT ENHANCEMENT SYSTEM

## 8.1 The Problem

When a team member types 'rug in living room' into an AI image generator, the output is generic garbage. AI models need highly specific, detailed descriptions to produce good results — what material, what texture, what colors, what room style, what furniture, what lighting, what camera angle, how big the rug is relative to the furniture, what the edges look like, how the light hits the braid pattern.

Nobody on the Homespice team should have to write prompts like that. The prompt enhancer does it for them.

## 8.2 Two-Step Generation Flow

Every tool that generates images or video follows this same two-step flow:

### Step 1: Describe What You Want

The user types a rough, casual description. Examples: 'Kilimanjaro rug in a cozy farmhouse kitchen, maybe with a dog.' or 'Ultra Durable rug on a patio, modern house, summer vibes.' That is all they need to write.

### Step 2: Review the Enhanced Prompt

The system takes the rough input, loads the relevant knowledge base documents (based on the tool's tag configuration), and sends both to Claude API. Claude returns a detailed, polished prompt that includes all the specifics the AI image model needs — material textures, color depth, room proportions, camera angles, lighting direction, edge behavior, furniture placement, and more.

This enhanced prompt appears in an editable text box. The user can: read it and click 'Generate' if it looks good; edit parts of it (change 'kitchen' to 'entryway', remove the dog); completely rewrite it if they want; or click 'Enhance' again with a different rough description.

## 8.3 Why the Editable Step Matters

- The user sees exactly what the AI will be asked to create — full transparency

- Bad prompts get caught before money is spent on generation — cost savings

- Users learn over time what prompt language produces good results — team skill building

- Quick edits are faster than re-enhancing — productivity boost

## 8.4 Technical Implementation

| // POST /api/enhance<br>// Request body: { toolId, roughPrompt, selectedOptions }<br>// Response: { enhancedPrompt, tokensUsed, cost }<br>async function enhancePrompt(toolId, roughPrompt, selectedOptions) {<br>// 1. Look up the tool's KB tag configuration<br>const tool = getToolConfig(toolId);<br>const kbTags = tool.kbTags; // e.g., ['all', 'products', 'rug-accuracy']<br>// 2. Load all KB documents matching these tags<br>const kbDocs = await loadKBDocuments(kbTags);<br>const kbContext = kbDocs.map(d => `## ${d.name}\n${d.content}`).join('\n\n');<br>// 3. Build the Claude system prompt<br>const systemPrompt = buildEnhancerSystemPrompt(toolId, kbContext);<br>// 4. Call Claude API<br>const response = await claude.messages.create({<br>model: 'claude-sonnet-4-20250514',<br>max_tokens: 2000,<br>system: systemPrompt,<br>messages: [{ role: 'user', content: roughPrompt }]<br>});<br>// 5. Extract the enhanced prompt and log the cost<br>const enhancedPrompt = response.content[0].text;<br>await logCost('enhancement', toolId, response.usage);<br>return { enhancedPrompt, tokensUsed: response.usage, cost: calculateCost(response.usage) };<br>} |
| --- |

## 8.5 Enhancement by Tool — What Gets Added

| Tool | What the Enhancer Adds to the Rough Prompt |
| --- | --- |
| Rug Image Generator | Material texture description, color depth rules (14-21 shades), size-to-room proportions, edge behavior (clean folded, no fringe), floor contact (flat, no hovering), shape construction details (spiral for round, linear for rectangle), room scene direction, camera angle, lighting quality |
| Static Ads Builder | Brand visual style, persona targeting direction, ad format structure (headline zone, product zone, CTA zone), product accuracy rules, color palette adherence, text overlay space reservation |
| UGC Builder (B-roll) | Camera movement direction (slow pan, dolly, static), scene composition, atmospheric details (warm light, morning feel), product placement rules (rug is on the floor, not held, not flying), transition suggestions |
| UGC Builder (Dialogue) | Script polish, natural conversational tone, brand-appropriate language, product reference accuracy, pacing notes, emotional beats, call-to-action integration |
| Copy & Script Generator | Persona targeting, angle selection, proof points, objection preemption, platform-specific format constraints, brand voice adherence, reading level compliance |
| Social Media Pack | Platform-specific format (Instagram carousel vs. TikTok caption vs. Pinterest description), hashtag strategy, posting time suggestions, visual direction for accompanying images |

## 8.6 Loading States

Enhancement typically takes 2-5 seconds. During this time: the Enhance button shows a spinner animation, the input field is disabled (grayed out), a subtle progress indicator appears below the input, and the user cannot submit a generation request until enhancement completes or they switch to manual mode.

# SECTION 9: PRODUCT ACCURACY RULES ENGINE

## 9.1 Why Accuracy Rules Exist

AI image models have never seen a Homespice braided rug. Without explicit rules, they will generate flat-weave textures, add fringe to edges, use uniform single colors instead of the 14-21 shade braid pattern, float the rug above the floor, render the wrong proportions, or confuse braided construction with knotted or tufted construction. Every one of these mistakes has happened repeatedly in testing.

The accuracy rules are a codified set of constraints that get injected into every image generation prompt to prevent these specific mistakes. They are stored in the knowledge base under the rug-accuracy tag and loaded by the prompt enhancer for any tool that generates rug imagery.

## 9.2 Core Accuracy Rules

### Braided Texture

- Rugs MUST show braided construction: interlocking rows of braided fiber visible as a pattern

- NOT flat-weave (flat, no texture), NOT tufted (cut pile), NOT knotted (Persian/Oriental style), NOT woven (visible warp/weft)

- The braid pattern should be visible at medium zoom but blend into a unified texture at room-scale views

### Color Depth

- Every rug must display 14-21 distinct shades within its colorway — this is non-negotiable

- NOT flat, uniform, single-color surfaces

- The shades come from different colored fibers braided together, creating natural variation and depth

- Even 'solid' colorways have tonal variation from the braiding process

### Edge Behavior

- Clean, folded edges — the braid is tucked and sewn at the border

- NO fringe (this is the #1 most common AI mistake)

- NO unraveling or loose fibers at edges

- NO visible seams or stitching unless the specific product has them

- Oval and round rugs: the edge follows a smooth curve, maintaining braid density

### Shape Construction

- Round rugs: spiral braid pattern radiating from center

- Oval rugs: similar spiral with elongated center section

- Rectangle rugs: straight-line braids running lengthwise, turned at corners

- Runners: consistent parallel braids along the long axis

- Heart shapes: the braid follows the heart contour, maintaining consistent density

### Size-to-Room Proportions

Each rug size has specific room placement rules:

| Size | Typical Room | Proportion Guidance |
| --- | --- | --- |
| 2' x 3' | Kitchen, bathroom, doorway | Small accent — fits in front of a sink, beside a bed, or inside a doorway. Should not dominate the space. |
| 3' x 5' | Entryway, kitchen, small office | Medium accent — anchors a small seating area or defines an entryway. Furniture legs may be on or off. |
| 4' x 6' | Living room accent, dining nook | Visible focal point — front legs of a sofa might rest on it. Should feel intentional, not lost. |
| 5' x 8' | Living room, bedroom | Room anchor — front legs of all seating should be on the rug. Defines the conversation area. |
| 6' x 9' | Living room, dining room | Full coverage — all primary furniture sits on or mostly on the rug. |
| 8' x 10' | Large living room, dining room | Full room anchor — extends well beyond the furniture group. 18-24 inches of rug visible beyond furniture. |
| Runners | Hallway, kitchen galley | Long and narrow — runs along the traffic path. Width typically 2-2.5 feet. |

### Floor Contact

- The rug must lay FLAT on the floor surface

- NO floating above the floor (common AI mistake — the rug hovers like a magic carpet)

- NO curling edges (unless deliberately showing a natural settled look)

- Shadows should appear under/around the rug, consistent with room lighting

- The rug should show subtle deformation where heavy furniture legs press into it

### Material-Specific Appearance

| Material | Visual Characteristics |
| --- | --- |
| Jute | Rough, natural fiber texture. Visible individual fibers in the braid. Matte finish. Earth tones — browns, tans, greens, rusts. Slightly irregular surface that catches light unevenly. Organic feel. |
| Cotton Blend | Softer, smoother braid surface. Brighter, more saturated colors possible. Slight sheen. Tighter braid construction. More uniform surface than jute. Comfortable, inviting feel. |
| Ultra Durable (Polypropylene) | Clean, consistent surface. Solution-dyed means colors are uniform and fade-resistant. Slightly smoother than natural fibers. Indoor/outdoor appropriate — no degradation in wet scenes. More 'manufactured' precision than natural fibers. |
| Luxuria (Premium Ultra Durable) | Softer hand-feel suggested by slightly more texture variation. Premium appearance — colors are richer, braid pattern is more refined. Sits between the precision of Ultra Durable and the warmth of natural fibers. |

## 9.3 Static Ads Builder Sync

The Static Ads Builder has its own product-specs.js file containing these same rules in a JavaScript code format optimized for programmatic use during image generation. The knowledge base has the rules in prose format for prompt enhancement. These are two representations of the same information. There is no automatic sync — the developer must update both when rules change.

# SECTION 10: GENERATION FEEDBACK LOOP

## 10.1 The Problem

AI generation is imperfect. Some images will have flat colors instead of the 14-21 shade depth. Some will render flat-weave texture instead of braided. Some will add fringe to edges that should be clean. Some will float the rug above the floor. These bad generations cost money and waste time. Without structured feedback, the developer has no way to know WHAT went wrong or HOW OFTEN each issue occurs.

## 10.2 How It Works

- Every generated image or video has a small thumbs-down icon next to it

- Clicking the icon opens a dropdown with common issue categories (see below)

- User selects one or more issue categories and optionally types a freeform note

- Feedback is stored with: the generation ID, the prompt used, the issue categories, the note, the user who flagged it, and the timestamp

- Flagged generations appear in the Feedback Log in Settings (Admin and Manager only)

- The developer reviews the log weekly to identify patterns and update accuracy rules accordingly

## 10.3 Issue Categories

| Category | Description | Example |
| --- | --- | --- |
| Wrong Texture | Rug shows flat-weave, tufted, knotted, or woven texture instead of braided | Rug looks like a Persian carpet instead of a braided rug |
| Flat Color | Rug appears as a single uniform color instead of showing 14-21 shade depth | Kilimanjaro rug looks solid brown instead of multi-tonal |
| Fringe/Edge Error | Rug has fringe, unraveling edges, or incorrect edge treatment | Visible tassels at the edge of an oval rug |
| Wrong Shape | Rug is the wrong shape or the shape is distorted | Requested round but generated oval |
| Wrong Proportions | Rug is too big or too small relative to the room/furniture | 5x8 rug looks like a doormat under a sofa |
| Floating Rug | Rug is hovering above the floor surface | Visible gap between rug and floor, no shadow contact |
| Wrong Material Look | The rug looks like the wrong material (e.g., jute looks like polypropylene) | Ultra Durable rug looks rough and natural like jute |
| Bad Room Scene | Room setting is wrong — wrong style, wrong lighting, wrong furniture | Farmhouse rug in a ultra-modern minimalist space |
| Brand Mismatch | Output doesn't feel like Homespice — wrong tone, wrong aesthetic | Copy sounds like a luxury brand instead of warm/approachable |
| Other | Any issue not covered above — requires freeform note | User describes the specific problem |

## 10.4 Feedback Database Schema

| CREATE TABLE generation_feedback (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>generation_id INTEGER REFERENCES generations(id),<br>user_id INTEGER REFERENCES users(id),<br>categories TEXT NOT NULL, -- JSON array of category slugs<br>note TEXT, -- optional freeform note<br>created_at TEXT NOT NULL,<br>resolved BOOLEAN DEFAULT 0, -- has the dev addressed this?<br>resolution_note TEXT -- what was done to fix it<br>); |
| --- |

# SECTION 11: COST TRACKING & BUDGET CONTROLS

## 11.1 Why Cost Tracking Matters

AI generation costs real money. Every image generated through FAL AI, every prompt enhanced through Claude, every video rendered — each has a cost. Without tracking, spending can spiral without anyone noticing until the monthly API bill arrives. The cost tracking system provides real-time visibility into AI spending across all tools.

## 11.2 What Gets Tracked

| Action | Service | Approximate Cost | Where It Shows |
| --- | --- | --- | --- |
| Prompt Enhancement | Claude API | $0.003 - $0.01 per enhancement | Per-generation cost breakdown |
| Image Generation (Flux) | FAL AI | $0.03 - $0.08 per image | Per-generation cost breakdown |
| Image Generation (SDXL) | FAL AI | $0.01 - $0.03 per image | Per-generation cost breakdown |
| Video Generation | FAL AI | $0.10 - $0.50 per clip | Per-generation cost breakdown |
| Voice Cloning | FAL AI | $0.02 - $0.05 per clip | Per-generation cost breakdown |
| Copy Generation | Claude API | $0.005 - $0.02 per generation | Per-generation cost breakdown |
| Bot Chat Message | Claude API | $0.002 - $0.01 per message | Per-message cost |
| Dashboard AI Summary | Claude API | $0.01 - $0.03 per summary | Weekly summary cost |

## 11.3 Cost Display

- Header Badge: Shows today's total AI spend in the top header bar. Updates in real-time after each generation. Green if under daily budget, yellow if approaching limit, red if over.

- Settings → Cost Dashboard: Detailed breakdown by day, week, month. Filterable by tool, by user, by generation type. Shows trend charts.

- Per-Generation: Each generated item shows its individual cost — enhancement cost + generation cost.

## 11.4 Budget Controls

- Daily spending limit (configurable by Admin) — when reached, generation is paused and Admin is notified

- Monthly spending limit — same behavior, monthly scope

- Per-tool spending limits — optional, allows throttling expensive tools independently

- Override: Admin can temporarily lift a limit for a specific tool or user

## 11.5 Database Schema

| CREATE TABLE cost_log (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>generation_id INTEGER REFERENCES generations(id),<br>user_id INTEGER REFERENCES users(id),<br>tool_id TEXT NOT NULL, -- 'rug-generator', 'static-ads', etc.<br>action_type TEXT NOT NULL, -- 'enhancement', 'image-gen', 'video-gen', etc.<br>service TEXT NOT NULL, -- 'claude', 'fal', 'gemini'<br>tokens_input INTEGER, -- for text APIs<br>tokens_output INTEGER, -- for text APIs<br>cost_usd REAL NOT NULL, -- actual cost in USD<br>created_at TEXT NOT NULL<br>);<br>CREATE TABLE cost_budgets (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>scope TEXT NOT NULL, -- 'daily', 'monthly', 'tool'<br>scope_key TEXT, -- tool_id if scope='tool', null otherwise<br>limit_usd REAL NOT NULL,<br>updated_by INTEGER REFERENCES users(id),<br>updated_at TEXT NOT NULL<br>); |
| --- |

# SECTIONS 12-18: TOOL SPECIFICATIONS — OVERVIEWS

Each tool has its own detailed specification submitted as a separate task document. This section provides the integration overview for each tool — how it connects to the Command Center's shared services.

## 12. Rug Image Generator

### Purpose

Generate product images of Homespice braided rugs across all sizes, shapes, colorways, and room settings. Output used for Amazon and Shopify product listings, social media, and marketing materials.

### Integration Points

- KB Tags: all, products, rug-accuracy

- AI Services: FAL AI (Flux Pro for high-quality, SDXL for variations), Claude (prompt enhancement)

- Shared Services Used: Prompt Enhancer, Cost Tracker, Feedback System, Knowledge Base

### User Flow

- Select material line (jute / cotton / ultra durable / luxuria)

- Select colorway from filtered dropdown

- Select shape and size

- Select or describe room setting (or choose 'product only' for white background)

- Write rough description (optional — system can auto-generate from selections)

- Review enhanced prompt → Edit if needed → Generate

- View results → Download, flag with feedback, or regenerate

### Output Formats

- 1024x1024, 1024x1536, 1536x1024 (standard generation sizes)

- Upscaling to 2048+ available as post-processing step

- PNG format for product listings, JPEG for social media

### Special Features

- Batch generation — generate multiple colorways in the same room scene

- Reference image upload — 'generate something like this but with a different rug'

- Editing queue — flagged images route to Editors for manual Photoshop touch-up

- Generation history — browse and re-download all past generations

## 13. Static Ads Builder

### Purpose

Build ad concepts and generate production-ready static images for Meta (Facebook/Instagram) ads. Combines AI-generated rug images with text overlays, brand badges, and CTA elements.

### Architecture Note

| SEPARATE APP<br>The Static Ads Builder is a standalone application running on port 3001 with its own frontend and backend (15,000+ lines of code). It is embedded in the Command Center via an iframe. It has its own product-specs.js file that must be kept in sync with the KB's rug-accuracy documents manually. |
| --- |

### Integration Points

- KB Tags: all, brand, products, rug-accuracy, personas, performance

- AI Services: FAL AI (image generation), Claude (ad concept planning, headline generation)

- Communication: postMessage API for iframe ↔ parent communication (auth token passing, navigation events)

## 14. UGC Builder

### Purpose

Generate AI video content for social media and ads. Three content types: quick hooks (5-15 seconds, attention-grabbing openers), extended reviews (30-60 seconds, product deep-dives), and atmospheric B-roll clips (ambient, mood-setting footage of rugs in beautiful settings).

### Integration Points

- KB Tags: all, brand, products, personas

- AI Services: FAL AI (video generation, voice cloning), Claude (script writing, prompt enhancement), Gemini (scene planning)

- External Data: Airtable (actor database, scene templates, shoot schedules)

## 15. CMO Dashboard

### Purpose

Automated marketing reporting with AI-powered weekly summaries. Pulls data from Shopify, Amazon, Meta Ads, and Google Ads to provide a unified view of business performance. Includes manual data entry for metrics not available via API.

### Integration Points

- KB Tags: all, brand (for AI summary context)

- AI Services: Claude (weekly AI summary generation, trend analysis, anomaly detection)

- Data Sources: Shopify Admin API (GraphQL), Amazon SP-API, Meta Marketing API, Google Ads API

### Dashboard Screens (10 total)

- Executive Summary — revenue, transactions, CVR, ROAS, channel overview (available to ALL roles)

- Revenue Deep Dive — daily/weekly/monthly revenue by channel, product, and geography

- Amazon Performance — sales, advertising, organic vs. paid, keyword rankings

- Shopify Performance — traffic, conversion, AOV, product performance, customer cohorts

- Meta Ads — campaign performance, ad set analysis, creative performance, audience insights

- Google Ads — search/display/shopping campaigns, keyword performance, quality scores

- Creative Performance — which images, videos, and copy are performing best across channels

- AI Weekly Summary — Claude-generated narrative summary of the week's performance with insights

- Manual Data Entry — input metrics not available via API (e.g., wholesale orders, returns, custom rug revenue)

- Settings — API connections, data refresh schedules, report recipients, export configuration

## 16. Copy & Script Generator

### Purpose

Build a strategic brief for a campaign or product, then generate ad copy across multiple formats: headlines, body copy, email sequences, product descriptions, social captions, and video scripts. All copy is informed by the knowledge base's brand voice, proven angles, and persona targeting.

### Integration Points

- KB Tags: all, brand, voice, copy-angles, personas, competitive, performance

- AI Services: Claude (primary copy generation), Gemini (strategic brief planning, alternative angles)

## 17. Social Media Pack

### Purpose

Generate complete, platform-native content packages for Instagram, TikTok, Pinterest, and Facebook. Each pack includes correctly sized images, platform-appropriate captions, hashtags, and posting schedule suggestions.

### Integration Points

- KB Tags: all, brand, voice, personas

- AI Services: Claude (captions, hashtags, scheduling), FAL AI (image generation/adaptation)

### Platform Specifications

| Platform | Image Sizes | Content Types |
| --- | --- | --- |
| Instagram | 1080x1080 (feed), 1080x1350 (portrait), 1080x1920 (stories/reels) | Single image, carousel (up to 10), stories, reels cover |
| TikTok | 1080x1920 (vertical) | Video thumbnail, caption overlay text |
| Pinterest | 1000x1500 (standard pin), 1000x2100 (long pin) | Standard pin, idea pin, product pin |
| Facebook | 1200x628 (link), 1080x1080 (post), 1080x1920 (stories) | Single image, carousel, stories, cover photo |

## 18. Homespice Bot

### Purpose

An internal AI chat assistant that knows everything about the Homespice brand. Team members can ask questions about products, brand guidelines, competitive positioning, campaign history, or anything else in the knowledge base. Think of it as an always-available brand expert.

### Integration Points

- KB Tags: all, brand, products, voice, copy-angles, competitive, personas — the bot loads the most comprehensive context of any tool

- AI Service: Claude (conversational AI with full KB context in system prompt)

### Features

- Conversational chat interface with message history

- Source citations — bot indicates which KB document it's drawing from

- Follow-up questions — maintains conversation context within a session

- Suggested questions — 'Try asking about...' prompts for new users

- Export — copy a bot answer to clipboard for use in other contexts

# SECTION 19: EXTERNAL SERVICE INTEGRATIONS

## 19.1 FAL AI Integration

### Purpose

FAL AI is the primary image and video generation service. It provides access to multiple AI models including Flux Pro (high-quality image generation), SDXL (fast variations), video generation models, and voice cloning.

### Implementation

| // /src/services/fal.js<br>const fal = require('@fal-ai/serverless-client');<br>fal.config({ credentials: process.env.FAL_API_KEY });<br>async function generateImage(prompt, model = 'fal-ai/flux-pro', options = {}) {<br>const result = await fal.subscribe(model, {<br>input: {<br>prompt,<br>image_size: options.size \|\| 'landscape_16_9',<br>num_inference_steps: options.steps \|\| 28,<br>guidance_scale: options.guidance \|\| 3.5,<br>num_images: options.count \|\| 1,<br>enable_safety_checker: true,<br>...(options.seed && { seed: options.seed }),<br>},<br>logs: true,<br>onQueueUpdate: (update) => {<br>// Emit progress to frontend via WebSocket<br>},<br>});<br>return result;<br>} |
| --- |

### Models Used

| Model | Use Case | Quality | Speed | Cost |
| --- | --- | --- | --- | --- |
| fal-ai/flux-pro | Primary rug image generation | Highest | 15-30 seconds | ~$0.05/image |
| fal-ai/flux/dev | Draft variations, testing | High | 8-15 seconds | ~$0.03/image |
| fal-ai/fast-sdxl | Quick previews, batch thumbnails | Good | 3-8 seconds | ~$0.01/image |
| fal-ai/minimax-video | UGC video generation | High | 60-120 seconds | ~$0.30/clip |

## 19.2 Claude API Integration

### Purpose

Claude is used for prompt enhancement, copy generation, chatbot functionality, dashboard AI summaries, and any task requiring text understanding or generation.

| // /src/services/claude.js<br>const Anthropic = require('@anthropic-ai/sdk');<br>const client = new Anthropic({ apiKey: process.env.ANTHROPIC_API_KEY });<br>async function generate(systemPrompt, userMessage, options = {}) {<br>const response = await client.messages.create({<br>model: options.model \|\| 'claude-sonnet-4-20250514',<br>max_tokens: options.maxTokens \|\| 2000,<br>system: systemPrompt,<br>messages: [{ role: 'user', content: userMessage }],<br>});<br>return {<br>text: response.content[0].text,<br>usage: response.usage,<br>cost: calculateClaudeCost(response.usage),<br>};<br>} |
| --- |

## 19.3 Google Gemini Integration

Used for planning, validation, and alternative generation in tools like the Copy Generator and UGC Builder. Provides a second AI perspective for strategic brief generation and content planning.

## 19.4 Airtable Integration

Used exclusively by the UGC Builder for managing the actor database, scene templates, and shoot schedules. Airtable serves as a structured data source that the team can manage without developer involvement.

## 19.5 Dashboard Data Sources

The CMO Dashboard pulls data from four external sources, each with its own authentication and rate limiting:

| Source | API Type | Data Pulled | Refresh Frequency | Auth |
| --- | --- | --- | --- | --- |
| Shopify | GraphQL Admin API | Revenue, orders, products, customers, inventory | Every 6 hours | Access token |
| Amazon | SP-API + Advertising API | Sales, organic + paid performance, keyword data | Every 12 hours | OAuth 2.0 + STS |
| Meta Ads | Marketing API v19 | Campaign performance, ad creative performance, audience data | Every 6 hours | Access token |
| Google Ads | Ads API v16 | Search, display, shopping campaigns, keywords | Every 12 hours | OAuth 2.0 |

# SECTION 20: DATABASE SCHEMA & DATA MODELS

## 20.1 Database Technology

SQLite via better-sqlite3 for Node.js. File-based database stored as data.db in the project root. No external database server required. This keeps the deployment simple for Replit and provides sufficient performance for the team size (10-15 concurrent users).

## 20.2 Complete Schema

| -- ═══ USERS & AUTH ═══<br>CREATE TABLE users (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>username TEXT NOT NULL UNIQUE,<br>display_name TEXT NOT NULL,<br>password_hash TEXT NOT NULL,<br>email TEXT,<br>role TEXT NOT NULL CHECK(role IN ('admin','manager','creator','editor','viewer')),<br>is_active BOOLEAN DEFAULT 1,<br>created_at TEXT NOT NULL DEFAULT (datetime('now')),<br>last_login TEXT<br>);<br>CREATE TABLE invite_links (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>token TEXT NOT NULL UNIQUE,<br>role TEXT NOT NULL,<br>created_by INTEGER REFERENCES users(id),<br>created_at TEXT NOT NULL DEFAULT (datetime('now')),<br>expires_at TEXT NOT NULL,<br>used BOOLEAN DEFAULT 0<br>);<br>CREATE TABLE refresh_tokens (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>user_id INTEGER REFERENCES users(id),<br>token_hash TEXT NOT NULL,<br>expires_at TEXT NOT NULL,<br>created_at TEXT NOT NULL DEFAULT (datetime('now'))<br>);<br>-- ═══ KNOWLEDGE BASE ═══<br>CREATE TABLE kb_documents (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>name TEXT NOT NULL,<br>slug TEXT NOT NULL UNIQUE,<br>content TEXT NOT NULL,<br>tags TEXT NOT NULL DEFAULT '[]',<br>size_limit INTEGER DEFAULT 100000,<br>created_at TEXT NOT NULL DEFAULT (datetime('now')),<br>updated_at TEXT NOT NULL DEFAULT (datetime('now')),<br>created_by INTEGER REFERENCES users(id),<br>updated_by INTEGER REFERENCES users(id)<br>);<br>CREATE TABLE kb_versions (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>document_id INTEGER REFERENCES kb_documents(id),<br>content TEXT NOT NULL,<br>tags TEXT NOT NULL,<br>saved_at TEXT NOT NULL DEFAULT (datetime('now')),<br>saved_by INTEGER REFERENCES users(id),<br>version_num INTEGER NOT NULL<br>);<br>-- ═══ GENERATIONS ═══<br>CREATE TABLE generations (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>user_id INTEGER REFERENCES users(id),<br>tool_id TEXT NOT NULL,<br>rough_prompt TEXT,<br>enhanced_prompt TEXT,<br>final_prompt TEXT NOT NULL,<br>model_used TEXT NOT NULL,<br>output_url TEXT,<br>output_type TEXT NOT NULL CHECK(output_type IN ('image','video','text','audio')),<br>metadata TEXT DEFAULT '{}',<br>total_cost_usd REAL DEFAULT 0,<br>status TEXT DEFAULT 'completed',<br>created_at TEXT NOT NULL DEFAULT (datetime('now'))<br>);<br>-- ═══ COST TRACKING ═══<br>CREATE TABLE cost_log (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>generation_id INTEGER REFERENCES generations(id),<br>user_id INTEGER REFERENCES users(id),<br>tool_id TEXT NOT NULL,<br>action_type TEXT NOT NULL,<br>service TEXT NOT NULL,<br>tokens_input INTEGER,<br>tokens_output INTEGER,<br>cost_usd REAL NOT NULL,<br>created_at TEXT NOT NULL DEFAULT (datetime('now'))<br>);<br>CREATE TABLE cost_budgets (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>scope TEXT NOT NULL,<br>scope_key TEXT,<br>limit_usd REAL NOT NULL,<br>updated_by INTEGER REFERENCES users(id),<br>updated_at TEXT NOT NULL DEFAULT (datetime('now'))<br>);<br>-- ═══ FEEDBACK ═══<br>CREATE TABLE generation_feedback (<br>id INTEGER PRIMARY KEY AUTOINCREMENT,<br>generation_id INTEGER REFERENCES generations(id),<br>user_id INTEGER REFERENCES users(id),<br>categories TEXT NOT NULL DEFAULT '[]',<br>note TEXT,<br>created_at TEXT NOT NULL DEFAULT (datetime('now')),<br>resolved BOOLEAN DEFAULT 0,<br>resolution_note TEXT<br>);<br>-- ═══ INDEXES ═══<br>CREATE INDEX idx_generations_user ON generations(user_id);<br>CREATE INDEX idx_generations_tool ON generations(tool_id);<br>CREATE INDEX idx_generations_date ON generations(created_at);<br>CREATE INDEX idx_cost_log_date ON cost_log(created_at);<br>CREATE INDEX idx_cost_log_tool ON cost_log(tool_id);<br>CREATE INDEX idx_kb_docs_tags ON kb_documents(tags);<br>CREATE INDEX idx_feedback_gen ON generation_feedback(generation_id); |
| --- |

# SECTION 21: API ROUTES & ENDPOINT REFERENCE

## 21.1 Authentication Routes

| Method | Endpoint | Auth Required | Roles | Description |
| --- | --- | --- | --- | --- |
| POST | /api/auth/login | No | Any | Login with username + password. Returns access token + sets refresh cookie. |
| POST | /api/auth/register | No (invite token) | Any | Register via invite link. Creates account with pre-assigned role. |
| POST | /api/auth/refresh | Refresh cookie | Any | Refresh expired access token using httpOnly refresh cookie. |
| POST | /api/auth/logout | Yes | Any | Invalidate refresh token and clear cookie. |
| GET | /api/auth/me | Yes | Any | Get current user profile and role. |

## 21.2 Knowledge Base Routes

| Method | Endpoint | Roles | Description |
| --- | --- | --- | --- |
| GET | /api/kb/documents | Any authenticated | List all KB documents (name, tags, size, last updated). Content excluded for list view. |
| GET | /api/kb/documents/:id | Any authenticated | Get full document including content. |
| POST | /api/kb/documents | Admin, Manager | Create new document. Body: { name, content, tags }. |
| PUT | /api/kb/documents/:id | Admin, Manager | Update document. Auto-creates version snapshot of previous content. |
| DELETE | /api/kb/documents/:id | Admin, Manager | Delete document (soft delete — marks inactive). |
| GET | /api/kb/documents/:id/versions | Admin, Manager | List all versions of a document. |
| POST | /api/kb/documents/:id/restore/:versionId | Admin, Manager | Restore a previous version of a document. |
| GET | /api/kb/by-tags?tags=all,products | Internal (tools) | Load documents matching any of the specified tags. Used by tools internally. |

## 21.3 Generation & Enhancement Routes

| Method | Endpoint | Roles | Description |
| --- | --- | --- | --- |
| POST | /api/enhance | Creator+ | Enhance a rough prompt. Body: { toolId, roughPrompt, options }. |
| POST | /api/generate/image | Creator+ | Generate an image. Body: { toolId, prompt, model, options }. |
| POST | /api/generate/video | Creator+ | Generate a video. Body: { toolId, prompt, model, options }. |
| POST | /api/generate/text | Creator+ | Generate text/copy. Body: { toolId, prompt, format, options }. |
| GET | /api/generations | Any authenticated | List generation history. Filterable by tool, user, date, status. |
| GET | /api/generations/:id | Any authenticated | Get generation details including prompt, output, cost, feedback. |
| POST | /api/generations/:id/feedback | Creator+ | Submit feedback on a generation. Body: { categories, note }. |

## 21.4 User Management Routes

| Method | Endpoint | Roles | Description |
| --- | --- | --- | --- |
| GET | /api/users | Admin | List all users with roles and status. |
| POST | /api/users/invite | Admin | Create an invite link. Body: { role, expiresInHours }. |
| PUT | /api/users/:id/role | Admin | Change a user's role. |
| PUT | /api/users/:id/deactivate | Admin | Deactivate a user account (soft delete). |
| PUT | /api/users/:id/reactivate | Admin | Reactivate a previously deactivated user. |

## 21.5 Cost & Settings Routes

| Method | Endpoint | Roles | Description |
| --- | --- | --- | --- |
| GET | /api/costs/today | Any authenticated | Get today's total spend (for header badge). |
| GET | /api/costs/summary | Admin, Manager | Get cost breakdown by day/week/month, tool, user. |
| GET | /api/costs/budgets | Admin | Get current budget limits. |
| PUT | /api/costs/budgets | Admin | Update budget limits. Body: { scope, scopeKey, limitUsd }. |
| GET | /api/settings | Admin | Get system settings (API connection status, feature flags). |
| PUT | /api/settings | Admin | Update system settings. |
| GET | /api/feedback | Admin, Manager | List all feedback entries. Filterable. |
| PUT | /api/feedback/:id/resolve | Admin, Manager | Mark feedback as resolved with resolution note. |

# SECTION 22: FRONTEND COMPONENT ARCHITECTURE

## 22.1 Page Components (Routes)

| src/<br>├── pages/<br>│ ├── LoginPage.jsx -- /login<br>│ ├── RegisterPage.jsx -- /register/:token<br>│ ├── HubPage.jsx -- / (home screen with tool cards)<br>│ ├── SettingsPage.jsx -- /settings<br>│ ├── tools/<br>│ │ ├── RugGeneratorPage.jsx -- /tools/rug-generator<br>│ │ ├── StaticAdsPage.jsx -- /tools/static-ads (iframe wrapper)<br>│ │ ├── UGCBuilderPage.jsx -- /tools/ugc-builder<br>│ │ ├── DashboardPage.jsx -- /tools/dashboard<br>│ │ ├── CopyGeneratorPage.jsx -- /tools/copy-generator<br>│ │ ├── SocialPackPage.jsx -- /tools/social-pack<br>│ │ └── BotPage.jsx -- /tools/bot |
| --- |

## 22.2 Shared Components

| │ ├── components/<br>│ │ ├── layout/<br>│ │ │ ├── AppLayout.jsx -- Main layout: header + sidebar + content area<br>│ │ │ ├── Header.jsx -- Top bar: menu, title, cost badge, user avatar<br>│ │ │ ├── Sidebar.jsx -- Collapsible tool navigation<br>│ │ │ └── ProtectedRoute.jsx -- Route wrapper for auth + role checks<br>│ │ ├── hub/<br>│ │ │ ├── ToolCard.jsx -- Individual tool card component<br>│ │ │ └── ToolGrid.jsx -- Grid layout for tool cards<br>│ │ ├── generation/<br>│ │ │ ├── PromptInput.jsx -- Rough prompt input with Enhance button<br>│ │ │ ├── EnhancedPromptEditor.jsx -- Editable enhanced prompt display<br>│ │ │ ├── GenerationResult.jsx -- Display generated image/video/text<br>│ │ │ ├── FeedbackButton.jsx -- Thumbs-down + issue category dropdown<br>│ │ │ ├── CostBadge.jsx -- Per-generation cost display<br>│ │ │ └── GenerationHistory.jsx -- Paginated history of past generations<br>│ │ ├── kb/<br>│ │ │ ├── DocumentList.jsx -- KB document list with tag badges<br>│ │ │ ├── DocumentEditor.jsx -- Rich text editor for KB content<br>│ │ │ ├── VersionHistory.jsx -- Version timeline with restore capability<br>│ │ │ └── TagManager.jsx -- Tag assignment interface<br>│ │ └── settings/<br>│ │ ├── UserManagement.jsx -- User list, invite link generation, role changes<br>│ │ ├── APIConnections.jsx -- API key status, connection health<br>│ │ ├── CostDashboard.jsx -- Cost breakdown charts and budget controls<br>│ │ └── FeedbackLog.jsx -- Filterable feedback entries with resolution |
| --- |

## 22.3 State Management (Zustand)

| │ ├── stores/<br>│ │ ├── authStore.js -- user, token, login/logout, role checks<br>│ │ ├── toolStore.js -- active tool, sidebar state, tool configs<br>│ │ ├── costStore.js -- today's total, budget status, real-time updates<br>│ │ └── notificationStore.js -- toast queue, unread count |
| --- |

# SECTION 23: SETTINGS PAGE — COMPLETE SPECIFICATION

## 23.1 Settings Tabs

The Settings page uses a tabbed interface. Each tab is accessible only to roles with the appropriate permissions:

| Tab | Visible To | Contains |
| --- | --- | --- |
| Knowledge Base | Admin, Manager | Document list, add/edit/delete, version history, tag reference, sync reminder |
| Users | Admin only | User list, invite link generation, role changes, deactivation |
| API Connections | Admin only | API key status for each service, connection health checks, key rotation |
| Cost & Budget | Admin, Manager (view), Admin (edit) | Cost breakdown, budget limits, trend charts, per-tool and per-user spend |
| Feedback Log | Admin, Manager | All flagged generations, filterable by tool/category/date, resolution tracking |
| System | Admin only | Feature flags, maintenance mode, data export, Static Ads Builder sync reminder |

## 23.2 Knowledge Base Management UI

- Document list view: name, tags (colored badges), content size, last updated timestamp, version count, last editor name

- Add document: modal with name field, tag selector (multi-select checkboxes), and content editor (markdown-capable textarea with preview)

- Edit document: same modal, pre-populated. Save creates a new version automatically.

- Delete document: confirmation dialog with document name displayed

- Version history: expandable timeline per document showing versions with timestamp, editor name, and 'Restore' button

- Tag reference: static display showing the tool-to-tag mapping table (which tags feed which tools)

| SYNC REMINDER<br>A persistent yellow banner at the top of the KB tab: 'Reminder: When rug accuracy rules change, update both the KB document AND the Static Ads Builder product-specs.js file.' This ensures the developer never forgets the manual sync requirement. |
| --- |

# SECTION 24: ERROR HANDLING, LOGGING & MONITORING

## 24.1 Error Categories

| Category | Example | User-Facing Response | Backend Action |
| --- | --- | --- | --- |
| Auth Error | Expired token, invalid credentials | Redirect to login or show 'Session expired' toast | Log attempt, increment rate limiter |
| Validation Error | Missing required field, invalid input | Inline field error messages | Return 400 with field-specific errors |
| API Rate Limit | FAL AI or Claude rate limited | 'Generation service is busy. Please try again in 30 seconds.' | Log, implement exponential backoff retry |
| API Failure | FAL AI returns 500, network timeout | 'Generation failed. Your prompt has been saved — try again.' | Log full error, alert Admin via notification |
| Budget Exceeded | Daily or monthly limit reached | 'Daily AI budget reached. Contact an Admin to continue.' | Block generation, notify Admin |
| KB Error | Document too large, invalid tags | Inline error on save form | Return 400 with specific message |
| Permission Error | Creator tries to edit KB | 'You don\'t have permission for this action.' | Return 403, log attempt |

## 24.2 Logging

- Access Log: Every API request — method, path, user, response time, status code. File: logs/access.log

- Error Log: All errors with full stack traces, request context, user context. File: logs/error.log

- Generation Log: Every generation request — prompt, model, output URL, cost, duration. File: logs/generation.log

- Auth Log: Login attempts (success and failure), token refreshes, password changes. File: logs/auth.log

# SECTION 25: DEPLOYMENT, ENVIRONMENT & DEVOPS

## 25.1 Environment Variables

| # ═══ Authentication ═══<br>JWT_SECRET=<random-64-char-string><br>JWT_REFRESH_SECRET=<different-random-64-char-string><br># ═══ AI Services ═══<br>FAL_API_KEY=<fal-api-key><br>ANTHROPIC_API_KEY=<claude-api-key><br>GEMINI_API_KEY=<gemini-api-key><br># ═══ Data Sources (Dashboard) ═══<br>SHOPIFY_SHOP_URL=<shop>.myshopify.com<br>SHOPIFY_ACCESS_TOKEN=<token><br>AMAZON_CLIENT_ID=<id><br>AMAZON_CLIENT_SECRET=<secret><br>AMAZON_REFRESH_TOKEN=<token><br>META_ACCESS_TOKEN=<token><br>META_AD_ACCOUNT_ID=<id><br>GOOGLE_ADS_DEVELOPER_TOKEN=<token><br>GOOGLE_ADS_CLIENT_ID=<id><br>GOOGLE_ADS_CLIENT_SECRET=<secret><br>GOOGLE_ADS_REFRESH_TOKEN=<token><br># ═══ External Data ═══<br>AIRTABLE_API_KEY=<key><br>AIRTABLE_BASE_ID=<id><br># ═══ App Config ═══<br>MAIN_APP_PORT=3000<br>STATIC_ADS_PORT=3001<br>NODE_ENV=production<br>DATABASE_PATH=./data.db |
| --- |

## 25.2 Start Scripts

| // package.json<br>"scripts": {<br>"dev": "concurrently \"npm run dev:main\" \"npm run dev:ads\"",<br>"dev:main": "vite & node server/index.js",<br>"dev:ads": "cd static-ads-builder && node server.js",<br>"build": "vite build",<br>"start": "concurrently \"node server/index.js\" \"cd static-ads-builder && node server.js\"",<br>"db:migrate": "node server/db/migrate.js",<br>"db:seed": "node server/db/seed.js"<br>} |
| --- |

## 25.3 Database Initialization

On first run, the migration script creates all tables. The seed script creates the initial Admin user (Viktor) and populates the tool configuration. No manual database setup is required — SQLite creates the data.db file automatically.

# SECTION 26: FILE & FOLDER STRUCTURE

| homespice-command-center/<br>├── .env # Environment variables (never committed)<br>├── .gitignore<br>├── package.json<br>├── vite.config.js<br>├── tailwind.config.js # Custom brand color palette<br>├── data.db # SQLite database (auto-created)<br>│<br>├── server/ # Express backend<br>│ ├── index.js # Main server entry point<br>│ ├── db/<br>│ │ ├── connection.js # better-sqlite3 connection<br>│ │ ├── migrate.js # Schema creation<br>│ │ └── seed.js # Initial data (admin user, tool configs)<br>│ ├── middleware/<br>│ │ ├── authenticate.js # JWT verification<br>│ │ ├── requireRole.js # Role-based access control<br>│ │ ├── rateLimiter.js # Rate limiting<br>│ │ └── errorHandler.js # Global error handler<br>│ ├── routes/<br>│ │ ├── auth.js # Login, register, refresh, logout<br>│ │ ├── kb.js # Knowledge base CRUD + versions<br>│ │ ├── enhance.js # Prompt enhancement<br>│ │ ├── generate.js # Image, video, text generation<br>│ │ ├── users.js # User management<br>│ │ ├── costs.js # Cost tracking + budgets<br>│ │ ├── feedback.js # Generation feedback<br>│ │ ├── settings.js # System settings<br>│ │ └── tools/ # Tool-specific routes<br>│ │ ├── rug-generator.js<br>│ │ ├── ugc-builder.js<br>│ │ ├── dashboard.js<br>│ │ ├── copy-generator.js<br>│ │ ├── social-pack.js<br>│ │ └── bot.js<br>│ ├── services/<br>│ │ ├── fal.js # FAL AI client<br>│ │ ├── claude.js # Anthropic Claude client<br>│ │ ├── gemini.js # Google Gemini client<br>│ │ ├── airtable.js # Airtable client<br>│ │ ├── enhancer.js # Prompt enhancement logic<br>│ │ ├── costTracker.js # Cost calculation + logging<br>│ │ └── kbLoader.js # Load KB docs by tags<br>│ └── config/<br>│ ├── tools.js # Tool definitions + KB tag mappings<br>│ └── constants.js # App-wide constants<br>│<br>├── src/ # React frontend<br>│ ├── App.jsx # Root component + router<br>│ ├── index.jsx # Entry point<br>│ ├── pages/ # (see Section 22)<br>│ ├── components/ # (see Section 22)<br>│ ├── stores/ # Zustand stores<br>│ ├── hooks/ # Custom React hooks<br>│ ├── utils/ # Utility functions<br>│ └── config/<br>│ └── tools.js # Frontend tool card configs<br>│<br>├── static-ads-builder/ # Standalone Static Ads Builder app<br>│ ├── server.js # Express server (port 3001)<br>│ ├── product-specs.js # Rug accuracy rules (sync with KB)<br>│ ├── src/ # Its own React frontend<br>│ └── ... # 15,000+ lines of existing code<br>│<br>├── logs/ # Log files<br>│ ├── access.log<br>│ ├── error.log<br>│ ├── generation.log<br>│ └── auth.log<br>│<br>└── public/ # Static assets<br>├── favicon.ico<br>└── images/<br>└── homespice-logo.png |
| --- |

# SECTION 27: BUILD PRIORITY & PHASED ROLLOUT PLAN

## Phase 0: Foundation (Build First)

The Command Center shell must be built before any tool. This includes:

- Authentication system (login, register, JWT, roles)

- Database schema and migrations

- Hub page with tool card grid (empty initially)

- Sidebar navigation

- Settings page shell (tabs, but content filled as features are built)

- Knowledge base CRUD + version history

- Prompt enhancement service (generic, tool-agnostic)

- Cost tracking service

- Feedback system

- Error handling and logging

## Phase 1: Rug Image Generator

The first tool. Highest immediate value — the team needs product images for Amazon and Shopify listings daily. Exercises the full generation pipeline: KB context loading → prompt enhancement → FAL AI generation → cost tracking → feedback.

## Phase 2: Static Ads Builder

Already built as a standalone app. Integration work: iframe embedding, auth token passing via postMessage, Hub card registration. Minimal new code needed.

## Phase 3: UGC Builder

Video generation is the next highest-value capability. Requires Airtable integration for actor/scene data. More complex generation pipeline (video + voice + script).

## Phase 4: CMO Dashboard

Requires API integrations with Shopify, Amazon, Meta, and Google Ads. Complex data aggregation. Manual data entry forms. AI weekly summary generation.

## Phase 5: Copy & Script Generator

Text-only generation — simpler pipeline. Strategic brief builder + multi-format output. Leverages the heaviest KB context (voice, angles, personas, competitive).

## Phase 6: Social Media Pack

Combines image generation with platform-specific text generation. Requires understanding of each platform's format requirements.

## Phase 7: Homespice Bot

Chat interface with full KB context. Simplest tool technically — conversational AI with document retrieval. High value for team onboarding and quick answers.

# SECTION 28: TESTING STRATEGY

## 28.1 Testing Layers

| Layer | What's Tested | Tools |
| --- | --- | --- |
| Unit Tests | Individual functions — cost calculation, tag filtering, role checks, prompt building | Jest |
| API Tests | Each endpoint — correct responses, error handling, auth enforcement, role restrictions | Supertest + Jest |
| Integration Tests | Full flows — login → enhance → generate → feedback | Jest + test database |
| Manual Testing | Visual quality of generations, UI/UX flows, cross-browser compatibility | Human review checklist |
| Accuracy Testing | Generated rug images against accuracy rules — braided texture, color depth, edges | Human review with scoring rubric |

## 28.2 Key Test Scenarios

- Auth: Login with valid/invalid credentials, token refresh, expired tokens, role-based access denial

- KB: Create document, edit with version created, delete, restore version, tag filtering returns correct docs

- Enhancement: Rough prompt → enhanced prompt includes brand-specific details, different tools get different context

- Generation: Image generation returns valid output, cost is logged, generation appears in history

- Feedback: Thumbs-down → category selection → stored in DB → visible in feedback log

- Cost: Daily total calculation, budget limit enforcement, per-tool breakdown accuracy

# SECTION 29: PERFORMANCE & SCALABILITY

## 29.1 Performance Targets

| Action | Target Response Time | Notes |
| --- | --- | --- |
| Page load (Hub) | < 1 second | Static content, cached tool configs |
| Login | < 500ms | bcrypt verification is CPU-bound; acceptable for auth |
| KB document load | < 200ms | SQLite query, indexed by tags |
| Prompt enhancement | 2-5 seconds | Claude API latency — show loading spinner |
| Image generation | 10-30 seconds | FAL AI latency — show progress indicator |
| Video generation | 60-120 seconds | FAL AI latency — show progress bar with status updates |
| Cost badge update | < 100ms | In-memory aggregation from cost_log |

## 29.2 Scalability Notes

The current architecture is designed for a team of 10-15 concurrent users. SQLite handles this comfortably. If the team grows beyond 50 users or generation volume exceeds 1,000 per day, consider: migrating from SQLite to PostgreSQL, adding Redis for session/cache management, implementing a job queue (Bull/BullMQ) for generation requests, and moving to a dedicated hosting provider instead of Replit.

# SECTION 30: APPENDICES

## Appendix A: Tailwind Config — Brand Colors

| // tailwind.config.js<br>module.exports = {<br>theme: {<br>extend: {<br>colors: {<br>brand: {<br>'dark-brown': '#4A3728',<br>'warm-brown': '#6B4F3A',<br>'sage': '#7A8B6F',<br>'cream': '#F5F0E8',<br>'rust': '#B85C3A',<br>'navy': '#2C3E50',<br>'light-gray': '#E8E4DE',<br>'accent': '#D4A574',<br>}<br>},<br>fontFamily: {<br>sans: ['Inter', 'system-ui', 'sans-serif'],<br>mono: ['JetBrains Mono', 'Fira Code', 'monospace'],<br>}<br>}<br>}<br>} |
| --- |

## Appendix B: Tool Category Tags & Colors

| Category | Color | Hex | Tools |
| --- | --- | --- | --- |
| Image Generation | Sage Green | #7A8B6F | Rug Image Generator |
| Ad Creative | Warm Brown | #6B4F3A | Static Ads Builder |
| Video Production | Rust | #B85C3A | UGC Builder |
| Analytics | Navy | #2C3E50 | CMO Dashboard |
| Copywriting | Dark Brown | #4A3728 | Copy & Script Generator |
| Social Media | Accent Gold | #D4A574 | Social Media Pack |
| Knowledge Chat | Sage Green | #7A8B6F | Homespice Bot |

## Appendix C: Generation Status Codes

| Status | Meaning | User-Facing Display |
| --- | --- | --- |
| queued | Request submitted, waiting in queue | Spinner + 'Queued...' |
| processing | AI model is generating | Progress bar + 'Generating...' |
| completed | Generation successful | Output displayed with download + feedback buttons |
| failed | Generation error | Error message + 'Try Again' button + prompt preserved |
| cancelled | User cancelled during generation | 'Cancelled' label, no cost charged |

## Appendix D: Quick Reference — Who Can Do What

| Action | Admin | Manager | Creator | Editor | Viewer |
| --- | --- | --- | --- | --- | --- |
| Use generation tools | Yes | Yes | Yes | No | No |
| Edit images (editing queue) | Yes | Yes | No | Yes | No |
| View generation history | Yes | Yes | Yes | Yes | Yes |
| Submit generation feedback | Yes | Yes | Yes | Yes | No |
| View KB documents | Yes | Yes | Yes (read-only) | No | No |
| Edit KB documents | Yes | Yes | No | No | No |
| View full dashboard | Yes | Yes | No | No | No |
| View executive summary | Yes | Yes | Yes | Yes | Yes |
| Manage users | Yes | No | No | No | No |
| Set budgets | Yes | No | No | No | No |
| View cost data | Yes | Yes | No | No | No |
| Review feedback log | Yes | Yes | No | No | No |
| Manage API connections | Yes | No | No | No | No |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━

END OF DOCUMENT

Homespice Command Center — Complete System Architecture v2.0