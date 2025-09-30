# Helix

**Helix** is Halo's VCaaS (Vibe Coding as a Service) platform - a customized fork of [Dyad](https://github.com/dyad-sh/dyad), the local, open-source AI app builder.

## About This Fork

This is a specialized fork of Dyad maintained by [Halo](https://halo.nyc), an NYC-based software development agency. We use Helix to deliver immersive, real-time "vibe coding" sessions for client demonstrations and discovery meetings.

### Why Fork Dyad?

Dyad is an excellent open-source AI app builder, but our use case at Halo requires significant customization:

- **Pre-configured setups**: We prepare custom system prompts and baseline prototypes for each client
- **Connected endpoints**: Pre-integrated with client-specific APIs and data sources
- **Demo-ready environments**: Thoroughly tested and rehearsed for live presentations
- **Branded experience**: Customized to represent Halo's internal tooling ecosystem

By maintaining this as a separate fork branded as "Helix", we:
1. Avoid confusion - clients understand they're getting a curated, production-ready service, not just the open-source tool
2. Protect attribution - we maintain full credit to the original Dyad creators
3. Enable customization - we can tailor the experience for VCaaS without affecting the upstream project

## Original Dyad Project

Dyad is created and maintained by the team at [dyad.sh](https://dyad.sh). It's a local, open-source AI app builder that's fast, private, and fully under your control — like Lovable, v0, or Bolt, but running right on your machine.

**Original Dyad Features:**
- ⚡️ **Local**: Fast, private and no lock-in
- 🛠 **Bring your own keys**: Use your own AI API keys — no vendor lock-in
- 🖥️ **Cross-platform**: Easy to run on Mac or Windows

Learn more about Dyad:
- Website: [dyad.sh](https://dyad.sh)
- Repository: [github.com/dyad-sh/dyad](https://github.com/dyad-sh/dyad)
- Community: [r/dyadbuilders](https://www.reddit.com/r/dyadbuilders/)

## Development

This fork follows the same development workflow as upstream Dyad.

### Essential Commands

```bash
npm install            # Install dependencies
npm start              # Start dev server
npm run dev:engine     # Start with local engine
npm test               # Run tests
npm run lint           # Lint code
npm run package        # Package for current platform
```

### Requirements

- Node.js >= 20
- npm

For detailed development instructions, see [CLAUDE.md](./CLAUDE.md).

## License

This fork maintains the same Apache 2.0 license as the original Dyad project.

## Attribution

Helix is built on top of [Dyad](https://github.com/dyad-sh/dyad), created by the team at dyad.sh. We're grateful for their work on this excellent open-source foundation.

All modifications in this fork are © 2025 Halo and are also released under Apache 2.0.

---

**For Halo team members**: See internal documentation for VCaaS session preparation workflows and client demo guidelines.