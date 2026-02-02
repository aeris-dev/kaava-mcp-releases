# Kaava Alpha Onboarding

Welcome to the Kaava alpha program. This guide will help you get set up with both the MCP server (for Claude Desktop) and the Storyboard web app.

## What You're Getting

Kaava is a specification intelligence system that helps you think through software design conversationally with Claude, then share living specifications with stakeholders for review before implementation.

**Two Components:**
1. **Kaava MCP Server** — Runs locally, gives Claude 90+ tools for managing specifications
2. **Kaava Storyboard** — Web app at kaava.studio for sharing specs with stakeholders

## Step 1: Get Your Invitation

As an alpha user, you'll receive:
- A project invitation email with a magic link to access Storyboard
- This tarball file: `kaava-mcp-1.29.0.tgz`

If you haven't received these, contact Aaron.

## Step 2: Install the MCP Server

The MCP server lets Claude help you create and manage specifications.

### Prerequisites
- Node.js 20 or later
- Claude Desktop app installed

### Installation

```bash
# Create a directory for Kaava
mkdir -p ~/.kaava

# Install from the tarball (replace path with actual location)
npm install -g /path/to/kaava-mcp-1.29.0.tgz
```

### Configure Claude Desktop

Add Kaava to your Claude Desktop configuration:

**macOS:** Edit `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** Edit `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "kaava": {
      "command": "kaava-mcp",
      "args": [],
      "env": {
        "KAAVA_PROJECT_ROOT": "/path/to/your/projects"
      }
    }
  }
}
```

Set `KAAVA_PROJECT_ROOT` to a directory containing your project repositories.

### Restart Claude Desktop

After saving the config, restart Claude Desktop. You should see Kaava tools available when you start a new conversation.

### Verify Installation

Ask Claude:
> "List my Kaava projects"

Claude should respond using the `kaava_query` tool.

## Step 3: Create Your First Project

In Claude Desktop, say:
> "Initialize a new Kaava project called my-app in /path/to/my-app"

Claude will use `kaava_init` to set up the project structure.

## Step 4: Connect to Storyboard

Storyboard is the web interface where stakeholders can browse and comment on your specifications.

### Sign In

1. Go to [kaava.studio](https://www.kaava.studio)
2. Click "Sign in with GitHub"
3. Authorize the Kaava app

**Note:** During alpha, new signups require an invitation. If you see "invite required", make sure you've clicked the magic link in your invitation email first.

### Connect Your Repository

After signing in:
1. Click "Connect Repository"
2. Enter your repository's GitHub URL (e.g., `https://github.com/you/my-app`)
3. Storyboard will sync your Kaava specifications

### Invite Stakeholders

To share specs with reviewers who don't need the full MCP setup:
1. Go to Project Settings
2. Click "Invite Team Member"
3. Enter their email and select access level
4. They'll receive a magic link to view your specs

## The Workflow

Here's how everything fits together:

1. **Define** — Work with Claude in Claude Desktop using MCP tools
   - Add capabilities, entities, state machines
   - Log architectural decisions
   - Structure accumulates as you think out loud

2. **Push** — Commit changes to your repository
   - Claude can help: "Commit my spec changes"

3. **Review** — Stakeholders browse in Storyboard
   - They see capabilities, entities, lifecycles
   - They leave comments on specific items
   - No setup required for them—just a magic link

4. **Iterate** — Address feedback, refine specs
   - Claude helps incorporate feedback
   - Push updates, stakeholders see changes

## Common Commands

Ask Claude these things to get started:

| What to Say | What Happens |
|-------------|--------------|
| "What capabilities do we have?" | Lists all capabilities |
| "Add a capability for user authentication" | Creates a new capability |
| "What entities exist?" | Lists data entities |
| "Show me the lifecycle for Order" | Displays state machine |
| "Log a decision about API versioning" | Records architectural decision |
| "Generate implementation docs for CAP-001" | Creates detailed implementation guide |

## Troubleshooting

### "Not in a Kaava project"
Make sure `KAAVA_PROJECT_ROOT` points to a directory containing your project, and the project has been initialized with `kaava_init`.

### "invite_required" error on Storyboard
You need an invitation to sign up during alpha. Check your email for the magic link or contact Aaron.

### Claude doesn't see Kaava tools
1. Check your claude_desktop_config.json syntax (valid JSON?)
2. Make sure kaava-mcp is installed globally: `which kaava-mcp`
3. Restart Claude Desktop completely

### Specifications not appearing in Storyboard
1. Make sure you've committed and pushed your changes
2. Check that your repository URL is correct in Project Settings
3. Pull latest changes in Storyboard

## Getting Help

- **Questions?** Message Aaron directly
- **Bugs?** File an issue (Aaron will share the repo link)
- **Feedback?** We want to hear everything—what's working, what's confusing, what's missing

Welcome to the alpha. Let's build something great together.
