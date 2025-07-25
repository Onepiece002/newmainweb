# Portfolio Website and Blog - Static Version

## Overview

This is a modern, responsive portfolio website and blog built with React, TypeScript, and Tailwind CSS. The application has been converted to a static site for Netlify deployment, featuring a Peter McKinnon-inspired dark theme with smooth parallax animations, 10 sample blog posts, and a comprehensive portfolio gallery with 15 categorized images.

## Recent Changes (January 23, 2025)

✓ **Static Site Conversion**: Removed database and authentication dependencies
✓ **Content Population**: Added 10 detailed blog posts about photography
✓ **Portfolio Gallery**: Added 15 portfolio images across 8 categories  
✓ **Footer Component**: Created comprehensive footer with social links
✓ **Netlify Configuration**: Added netlify.toml for deployment
✓ **Static Contact Form**: Converted to mailto-based contact form
✓ **Build Optimization**: Optimized for static deployment
✓ **Dark/Light Theme Toggle**: Added theme switcher with CSS variable support
✓ **Blog Card Aspect Ratio**: Updated to 1:1.5 ratio as requested
✓ **Parallax Sections**: Removed "Nature's Canvas", repositioned "Beyond Boundaries"
✓ **Fully Static**: Eliminated all API calls, database queries, and authentication

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **State Management**: TanStack Query for server state management
- **UI Framework**: Shadcn/ui components with Radix UI primitives
- **Styling**: Tailwind CSS with custom dark theme variables
- **Animation**: Framer Motion for smooth parallax and page transitions
- **Build Tool**: Vite with hot module replacement

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **API Design**: RESTful endpoints with proper HTTP status codes
- **Database**: PostgreSQL with Drizzle ORM for type-safe queries
- **Database Provider**: Neon serverless PostgreSQL

### Data Flow
1. Client makes requests to Express API endpoints
2. Express middleware handles authentication and request validation
3. Drizzle ORM translates queries to PostgreSQL
4. Responses flow back through Express to React frontend
5. TanStack Query caches and manages client-side state

## Key Components

### Authentication System
- **Current Implementation**: Replit Auth with OpenID Connect
- **Session Management**: PostgreSQL-backed sessions with connect-pg-simple
- **Authorization**: Role-based access control (admin/user roles)
- **Migration Ready**: Abstracted auth service layer for future Firebase integration

### Database Schema
- **Users**: Stores user profiles with admin flags
- **Blog Posts**: Full blog functionality with slug-based routing, drafts, and publishing
- **Portfolio Images**: Categorized image gallery with admin management
- **Contact Messages**: Contact form submissions with read/unread status
- **Sessions**: Secure session storage for authentication

### Content Management
- **Blog System**: Full CRUD operations, draft/publish workflow, featured images
- **Portfolio Management**: Image upload, categorization, and organization
- **Contact System**: Form handling with admin notification system
- **Admin Dashboard**: Comprehensive content management interface

### UI/UX Features
- **Dark Theme**: Peter McKinnon-inspired design with CSS custom properties
- **Responsive Design**: Mobile-first approach with Tailwind breakpoints
- **Animations**: Parallax scrolling, fade-in effects, and smooth transitions
- **Component Library**: Consistent design system with Shadcn/ui components

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL connection
- **drizzle-orm**: Type-safe database ORM with PostgreSQL dialect
- **@tanstack/react-query**: Server state management and caching
- **framer-motion**: Animation library for smooth transitions
- **wouter**: Lightweight client-side routing

### Authentication
- **openid-client**: OpenID Connect client for Replit Auth
- **passport**: Authentication middleware framework
- **express-session**: Session management with PostgreSQL storage

### UI Components
- **@radix-ui/***: Accessible UI component primitives
- **tailwindcss**: Utility-first CSS framework
- **lucide-react**: Icon library with consistent design

## Deployment Strategy

### Development Environment
- **Replit Integration**: Native Replit development with hot reload
- **Vite Dev Server**: Fast development builds with HMR
- **Database**: Automatic Neon PostgreSQL provisioning
- **Environment Variables**: Secure secret management via Replit

### Production Build
- **Frontend**: Vite builds optimized React bundle to `dist/public`
- **Backend**: ESBuild compiles TypeScript server to `dist/index.js`
- **Static Assets**: Served via Express static middleware
- **Database Migrations**: Drizzle Kit handles schema changes

### Architecture Decisions

#### Database Choice
- **Problem**: Need reliable, scalable PostgreSQL for production workloads
- **Solution**: Neon serverless PostgreSQL with connection pooling
- **Rationale**: Automatic scaling, built-in connection pooling, and seamless Replit integration
- **Alternatives**: Traditional PostgreSQL instances require more DevOps overhead

#### Authentication Strategy
- **Problem**: Secure user authentication with minimal setup complexity
- **Solution**: Replit Auth with abstracted service layer
- **Rationale**: Zero-config authentication for Replit deployment with clean migration path
- **Migration Path**: Service abstraction allows easy Firebase Auth integration later

#### State Management
- **Problem**: Complex server state synchronization and caching
- **Solution**: TanStack Query with RESTful API design
- **Rationale**: Automatic caching, background updates, and optimistic UI updates
- **Alternatives**: Context/Redux would require manual cache management

#### UI Framework
- **Problem**: Need consistent, accessible component library with dark theme support
- **Solution**: Shadcn/ui with Radix primitives and Tailwind CSS
- **Rationale**: Type-safe components, built-in accessibility, and easy theming
- **Customization**: CSS custom properties enable easy theme switching

#### Database ORM
- **Problem**: Type safety and developer experience for database operations
- **Solution**: Drizzle ORM with TypeScript schema definitions
- **Rationale**: Full type safety, excellent DX, and lightweight runtime
- **Benefits**: Prevents SQL injection, catches schema mismatches at compile time