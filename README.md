# ChatSphere — Real-Time Messaging Platform

A full-stack real-time messaging application built with **Next.js, TypeScript, and Supabase**. ChatSphere is designed to support private conversations, group chats, online presence, message history, and secure file sharing.

> **Project status:** In development 🚧

## Overview

ChatSphere aims to deliver a modern messaging experience with real-time communication and secure, persistent message storage. The project focuses on production-oriented application architecture, database design, access control, and real-time data synchronization.

The application uses Next.js for the frontend and server-side application logic, while Supabase provides PostgreSQL, authentication, file storage, and real-time capabilities.

## Features

### Authentication and Profiles
- User registration and login
- Email verification and password reset
- Secure session management
- User profiles and avatars
- Searchable user directory

### Real-Time Messaging
- One-to-one conversations
- Group conversations
- Real-time message delivery
- Paginated message history
- Typing indicators
- Online and offline presence
- Unread message counts and read receipts

### Conversation Management
- Create and manage group conversations
- Add and remove group members
- Assign group administrator roles
- Edit and delete messages
- Reply to messages and add emoji reactions
- Search messages and conversations

### File Sharing
- Share images and documents
- Validate file types and sizes
- Secure file storage
- Authorized access to private attachments

### Security and Reliability
- PostgreSQL Row-Level Security (RLS)
- Conversation membership-based authorization
- Server-side input validation
- Protected application routes
- Real-time channel access control
- Automated tests for critical messaging and authorization workflows

*Features will be marked complete as they are implemented and tested.*

## Tech Stack

| Technology | Purpose |
|---|---|
| Next.js App Router | Frontend and server-side application logic |
| React | User interface |
| TypeScript | Type safety |
| Tailwind CSS | Styling and responsive layouts |
| shadcn/ui | Reusable interface components |
| Supabase Auth | Authentication and sessions |
| PostgreSQL | Relational database |
| Supabase Realtime | Live messaging and presence |
| Supabase Storage | File and image attachments |
| Zod | Input validation |
| React Hook Form | Form management |
| Vitest | Unit and component testing |
| Playwright | End-to-end testing |
| Vercel | Application deployment |

## Architecture

```text
User
 |
 v
Next.js Application
 |
 +-- Authentication and session handling
 |
 +-- Server Actions / Route Handlers
 |       |
 |       +-- Input validation
 |       +-- Authorization
 |       +-- Business logic
 |
 +-- Supabase
         |
         +-- Auth
         +-- PostgreSQL
         +-- Row-Level Security
         +-- Realtime
         +-- Storage
```

PostgreSQL is the source of truth for persisted messages. Supabase Realtime delivers updates to connected clients, while clients retrieve message history from the database when loading or reconnecting.

## Database Design

The planned database schema includes the following tables:

| Table | Description |
|---|---|
| `profiles` | User profile information |
| `conversations` | Direct and group conversation metadata |
| `conversation_members` | Conversation membership and roles |
| `messages` | Persisted messages and message status metadata |
| `message_attachments` | References to uploaded files |
| `message_reads` | Per-message read receipts, if enabled |
| `message_reactions` | Emoji reactions associated with messages |

The schema will use foreign keys, uniqueness constraints, and indexes to preserve data integrity and support efficient queries.

## Security

Security is a core design requirement.

- Enable RLS on tables exposed through Supabase APIs.
- Restrict conversation and message access to authorized participants.
- Validate membership before allowing message creation or group management.
- Protect private file uploads and downloads using Storage policies.
- Keep secret and service-role keys on the server only.
- Validate user input and file uploads.
- Test access restrictions using multiple user accounts.

Client-side checks improve the user experience but do not replace database policies and server-side authorization.

## Getting Started

### Prerequisites

- Node.js LTS
- npm
- A Supabase account
- Git

### 1. Clone the repository

```bash
git clone https://github.com/mujeebrahmanik/chatsphere.git
cd chatsphere
```


### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env.local` file in the project root:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
```

Replace the placeholders with the values from your Supabase project settings.

Never commit `.env.local` or expose a Supabase secret/service-role key in client-side code.

### 4. Configure Supabase

Create a Supabase project and configure:

1. Authentication providers and email verification.
2. Database migrations and required tables.
3. Row-Level Security policies.
4. Realtime subscriptions and authorization.
5. Storage buckets and access policies when file sharing is implemented.

Apply the project's database migrations before using features that depend on the schema.

### 5. Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### 6. Build for production

```bash
npm run build
npm run start
```

## Development Roadmap

- [ ] Initialize Next.js and Supabase
- [ ] Configure Supabase SSR clients
- [ ] Implement authentication and protected routes
- [ ] Design the PostgreSQL schema and RLS policies
- [ ] Implement direct conversations
- [ ] Implement persistent message sending and history pagination
- [ ] Add real-time message delivery
- [ ] Implement group conversations and membership management
- [ ] Add online presence and typing indicators
- [ ] Implement unread counts and read receipts
- [ ] Add secure file attachments
- [ ] Add message editing, deletion, replies, and reactions
- [ ] Implement automated tests
- [ ] Deploy the application
- [ ] Document architecture and production limitations

## Testing

Automated tests will cover:

- Authentication and protected routes
- Conversation membership and access control
- Message creation and retrieval
- Pagination and ordering
- Group membership changes
- Storage access restrictions
- Real-time messaging workflows

Run the configured test scripts after they are added to the project:

```bash
npm run lint
npm run build
```

Unit, integration, and end-to-end test commands will be documented here once configured.

## Deployment

The planned deployment uses:

- **Frontend:** Vercel
- **Database and authentication:** Supabase
- **File storage:** Supabase Storage

Configure production environment variables, authentication redirect URLs, database migrations, RLS policies, and storage permissions before deploying.

## Learning Objectives

This project explores:

- Full-stack development with Next.js and Supabase
- Relational database design and PostgreSQL indexing
- Authentication and authorization
- Multi-user real-time communication
- Pagination and efficient data fetching
- Secure file storage
- Automated testing and deployment

## License

This project is intended as a portfolio and learning project. Add a license file if you intend to distribute or reuse the source code publicly.

---

**ChatSphere** — Building a secure, real-time messaging experience with Next.js and Supabase.
