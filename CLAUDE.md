# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Dyad is a local, open-source AI app builder using Electron + React + TypeScript. It runs entirely on your local machine as an alternative to cloud-based AI builders.

## Essential Commands

### Development
```bash
npm start              # Start dev server
npm run dev:engine     # Start with local engine
npm run ts             # Type check all TypeScript
```

### Testing
```bash
npm test               # Run unit tests (Vitest)
npm run test:watch     # Run tests in watch mode
npm run e2e            # Run Playwright E2E tests
npm run pre:e2e        # Build app for E2E testing
```

### Code Quality
```bash
npm run lint           # Run oxlint linter
npm run prettier       # Format code
npm run presubmit      # Run all pre-submit checks
```

### Database
```bash
npm run db:generate    # Generate Drizzle migrations
npm run db:push        # Apply migrations
npm run db:studio      # Open Drizzle Studio
```

### Build & Package
```bash
npm run package        # Package for current platform
npm run make           # Create distributable
```

## Architecture

### Electron IPC Pattern (CRITICAL)

This project uses a specific IPC + React Query pattern. When implementing features:

1. **React Hook** (renderer process):
   ```typescript
   // src/hooks/useFeature.ts
   export function useFeature() {
     return useQuery({
       queryKey: ['feature'],
       queryFn: () => IpcClient.instance.getFeature()
     })
   }
   ```

2. **IPC Client** (renderer process):
   ```typescript
   // src/ipc/ipc_client.ts
   async getFeature() {
     return await ipcRenderer.invoke('get-feature')
   }
   ```

3. **IPC Handler** (main process):
   ```typescript
   // src/ipc/handlers/feature.ts
   ipcMain.handle('get-feature', async () => {
     // CRITICAL: Must throw Error for failures, not return error
     if (error) throw new Error('Failed to get feature')
     return data
   })
   ```

**IMPORTANT**: Handlers must `throw new Error()` for failures, never return error objects.

### State Management
- **Global State**: Jotai atoms (`src/atoms/`)
- **Server State**: TanStack Query for async operations
- **Routing**: TanStack Router (NOT React Router or Next.js)

### Database
- SQLite with Drizzle ORM
- Schema in `src/db/schema.ts`
- Migrations in `drizzle/` directory

### UI Components
- Tailwind CSS v4 + shadcn/ui (New York style)
- Components in `src/components/ui/`
- Custom components in `src/components/`

## Key Directories

```
src/
├── ipc/handlers/      # Main process IPC handlers (40+ files)
├── hooks/             # React hooks with TanStack Query (41+ files)
├── atoms/             # Jotai state atoms
├── components/        # React components (64+ files)
├── routes/            # TanStack Router route components
└── db/                # Database schema and utilities
```

## Testing Approach

- **Unit Tests**: Use Vitest with React Testing Library
- **E2E Tests**: Comprehensive Playwright tests in `e2e-tests/`
- **Test files**: Place in `src/__tests__/` or `e2e-tests/`
- Run `npm test` before committing changes

## AI Integration

The project supports multiple AI providers (OpenAI, Anthropic, Google, etc.) and uses custom XML-like tags for AI tool calling:
- `<dyad-write>`, `<dyad-read>`, `<dyad-run>` for file operations
- MCP (Model Context Protocol) support for extended capabilities

## Development Tips

1. Always check existing patterns in similar files before implementing new features
2. Use the IPC pattern consistently - never access Node.js APIs directly from renderer
3. Handle errors by throwing in IPC handlers, not returning error objects
4. Use TanStack Query for all async data fetching in React components
5. Follow the existing file naming conventions (kebab-case for files, PascalCase for components)
6. When modifying database schema, generate migrations with `npm run db:generate`