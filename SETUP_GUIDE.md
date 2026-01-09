# 🚀 COMPLETE SETUP GUIDE FOR VERCEL WORKFLOW EXAMPLES

## Welcome to Your Forked Repository!

This repository has been forked and is ready for you to clone and run locally. Follow this comprehensive guide to get started with Vercel Workflows with zero errors.

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed on your machine:

- **Node.js** (v18 or later) - [Download here](https://nodejs.org/)
- **pnpm** (recommended) or npm - Install pnpm: `npm install -g pnpm`
- **Git** - [Download here](https://git-scm.com/)
- A code editor (VS Code recommended)

---

## 🔧 Step 1: Clone Your Fork

Open your terminal and run:

```bash
git clone https://github.com/mrwebwork/workflow-examples.git
cd workflow-examples
```

---

## 📚 Available Examples

This repository contains multiple workflow examples. Here's what's available:

### Framework Examples
- **Next.js** - Full-stack React framework with workflows
- **Astro** - Modern static site builder
- **Hono** - Lightweight web framework
- **Nitro** - Universal web server
- **Nuxt** - Vue.js framework
- **SvelteKit** - Svelte application framework
- **Vite** - Frontend build tool

### Feature Examples
- **AI SDK Workflow Patterns** - Common AI workflow patterns
- **Birthday Card Generator** - Creative workflow example
- **Custom Adapter** - Build workflows for any runtime
- **Flight Booking App** - Complex multi-step workflow
- **FFmpeg Processing** - Media processing workflows
- **Kitchen Sink** - Comprehensive reference with all patterns
- **RAG Agent** - AI agent with retrieval augmented generation

---

## 🎯 Quick Start: Next.js Example

The Next.js example is the most comprehensive. Let's set it up:

### Step 1: Navigate to Next.js Directory
```bash
cd nextjs
```

### Step 2: Install Dependencies
```bash
pnpm install
```
*Or if using npm:*
```bash
npm install
```

### Step 3: Start Development Server
```bash
pnpm dev
```
*Or:*
```bash
npm run dev
```

Your dev server will start at **http://localhost:3000**

### Step 4: Test the Workflow

Open a new terminal window and run:

```bash
curl -X POST --json '{"email":"hello@example.com"}' http://localhost:3000/api/signup
```

You should see:
```json
{"message":"User signup workflow started"}
```

### Step 5: View Workflow Execution

Check your development server logs to see the workflow executing!

You can also use the **Workflow DevKit Web UI**:

```bash
npx workflow web
```

Or use the CLI:
```bash
npx workflow inspect runs
```

---

## 📖 Understanding the Code Structure

### Next.js Project Structure
```
nextjs/
├── app/
│   ├── api/
│   │   └── signup/
│   │       └── route.ts       # API endpoint that triggers workflow
│   ├── layout.tsx
│   └── page.tsx
├── workflows/
│   └── user-signup.ts         # Main workflow logic with steps
├── next.config.ts             # Next.js config with Workflow
├── package.json
└── README.md
```

### Key Files

**`next.config.ts`** - Workflow integration:
```typescript
import { withWorkflow } from "workflow/next";
export default withWorkflow(nextConfig);
```

**`workflows/user-signup.ts`** - The workflow:
- Uses `"use workflow"` directive
- Defines steps with `"use step"` directive
- Handles errors and retries
- Uses `sleep()` for delays

**`app/api/signup/route.ts`** - API trigger:
- Imports the workflow function
- Uses `start()` to begin workflow execution
- Returns immediately without blocking

---

## 🎨 Try Other Examples

Each example folder has its own README with specific instructions:

### RAG Agent Example
```bash
cd ../rag-agent
pnpm install
pnpm dev
```

### Flight Booking App
```bash
cd ../flight-booking-app
pnpm install
pnpm dev
```

### Kitchen Sink (All Patterns)
```bash
cd ../kitchen-sink
pnpm install
pnpm dev
```

---

## 🌩️ Deploy to Production

### Deploy to Vercel (Recommended)

1. Push your fork to GitHub (already done!)

2. Go to [Vercel Dashboard](https://vercel.com/new)

3. Import your repository: `mrwebwork/workflow-examples`

4. Select the framework directory (e.g., `nextjs`)

5. Click Deploy

**That's it!** Vercel automatically:
- Configures Workflow storage
- Sets up queuing infrastructure
- Handles authentication
- Provides observability dashboard

---

## 🔍 Observability & Debugging

### Local Development

**Web UI (Recommended):**
```bash
npx workflow web
```
Opens a browser interface to:
- View all workflow runs
- Inspect step execution
- See inputs/outputs
- Track errors and retries

**CLI:**
```bash
# List all runs
npx workflow inspect runs

# Inspect specific run
npx workflow inspect run <run-id>

# View steps
npx workflow inspect steps
```

### Production (Vercel Dashboard)

1. Go to your project in Vercel Dashboard
2. Navigate to **AI > Workflows**
3. See real-time workflow execution
4. Trace failures and analyze performance

---

## 🛠️ Common Issues & Solutions

### Issue: "Cannot find module 'workflow'"
**Solution:** Make sure you're in the correct example directory and ran `pnpm install`

### Issue: Port 3000 already in use
**Solution:** 
```bash
# Kill the process
lsof -ti:3000 | xargs kill -9

# Or use a different port
PORT=3001 pnpm dev
```

### Issue: Workflow not executing
**Solution:** Check the console for errors. Make sure you're calling the correct API endpoint.

### Issue: TypeScript errors
**Solution:** 
```bash
# Clear cache and reinstall
rm -rf node_modules pnpm-lock.yaml
pnpm install
```

---

## 📚 Learning Resources

### Documentation
- [Workflow DevKit Docs](https://useworkflow.dev/docs)
- [Next.js Getting Started](https://useworkflow.dev/docs/getting-started/next)
- [Foundations](https://useworkflow.dev/docs/foundations)
- [Deploying](https://useworkflow.dev/docs/deploying)
- [API Reference](https://useworkflow.dev/docs/api-reference)

### Key Concepts

**Workflows** - Orchestrator functions that coordinate steps
- Use `"use workflow"` directive
- Can pause with `sleep()`
- Survive crashes and deployments

**Steps** - Individual units of work
- Use `"use step"` directive
- Automatically retry on failure
- Run in isolation

**Error Handling:**
- Regular errors → automatic retry
- `FatalError` → no retry (for validation failures)

**Control Flow:**
- Use standard JavaScript: loops, conditionals, try/catch
- `sleep()` for delays without resource consumption
- Hooks & webhooks for external events

---

## 🤝 Contributing

Want to contribute? 

1. Make changes in your fork
2. Test locally
3. Create a pull request to the original repo: [vercel/workflow-examples](https://github.com/vercel/workflow-examples)

---

## 🎯 Next Steps

1. ✅ Clone the repository
2. ✅ Run the Next.js example
3. ✅ Test with curl command
4. ✅ Explore the Workflow Web UI
5. 📝 Read the workflow code in `workflows/user-signup.ts`
6. 🔧 Modify the workflow to add your own steps
7. 🚀 Deploy to Vercel
8. 🎨 Try other examples (RAG Agent, Flight Booking, etc.)
9. 📖 Read the [Foundations](https://useworkflow.dev/docs/foundations) documentation
10. 🏗️ Build your own workflow application!

---

## 💡 Pro Tips

- Use `npx workflow web` frequently during development
- Check the `.workflow-data/` directory to see persisted workflow state
- Each example is standalone - you can delete others if focusing on one
- The `kitchen-sink` example shows ALL workflow patterns in one place
- Read the source code - it's well-commented and educational

---

## 🆘 Need Help?

- **Documentation:** [useworkflow.dev](https://useworkflow.dev)
- **GitHub Issues:** [vercel/workflow](https://github.com/vercel/workflow/issues)
- **Examples Issues:** [vercel/workflow-examples/issues](https://github.com/vercel/workflow-examples/issues)
- **Discussions:** [vercel/workflow/discussions](https://github.com/vercel/workflow/discussions)

---

## 📜 License

MIT License - See [LICENSE](LICENSE) file

---

**Happy Building! 🎉**

You now have everything you need to build durable, reliable workflows with Vercel. Start with the Next.js example and explore from there!
