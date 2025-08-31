# AI Architecture Prompts - From Eskil Steenberg's "Architecting LARGE Software Projects"

Transform any codebase into modular, replaceable "black boxes" using AI-powered architecture principles derived from Eskil Steenberg's legendary systems programming lecture.

## 🎯 What This Is

Three specialized AI prompts that teach Claude, ChatGPT, and Cursor to think in terms of:

- **Black box interfaces** - Clean APIs between modules
- **Replaceable components** - If you can't understand it, rewrite it
- **Constant velocity** - Write 5 lines today vs. edit 1 line later
- **Single responsibility** - One module, one person

## 🔥 Real Results

Used these prompts to completely refactor [Mentis](https://github.com/Alexanderdunlop/mentis) - my React mention component that was plagued with DOM manipulation bugs. The AI suggested a black box DOM interface that now supports multiple frameworks with zero overhead.

**Before**: Tangled DOM manipulation breaking on every React update  
**After**: Clean interface supporting React, Vue, Svelte, vanilla JS

## 📁 What's Included

- **`claude-code-prompt.md`** - For hands-on development and refactoring
- **`claude-prompt.md`** - For architectural planning and system design
- **`cursor-prompt.md`** - For debugging and testing strategies
- **`eskil-transcript.txt`** - Complete lecture transcript (1 hour of pure gold)
- **`examples/`** - Real refactoring examples from Mentis
- **`usage-guide.md`** - How to combine with AI context tools

## 🚀 Quick Start

1. **Clone this repo**

```bash
git clone git@github.com:Alexanderdunlop/ai-architecture-prompts.git
```

2. **Choose your AI tool and prompt**

- Claude Code → Use `claude-code-prompt.md`
- Claude → Use `claude-prompt.md`
- Cursor → Use `cursor-prompt.md`

3. **Extract your code context** (recommended)

```bash
# For JavaScript/TypeScript
npx repomix --include "src/**" --output context.xml

# For Python
python onefilellm.py ./src/ --output context.xml
```

4. **Apply the prompt**

- Paste the prompt into your AI tool
- Include your code context
- Ask for architectural analysis

## 💡 Best Practices

### For New Projects

Use the planning prompt first to establish your black box architecture, then implement with the development prompts.

### For Refactoring Existing Code

1. Focus on single folders/modules at a time
2. Use context extraction tools for precise control
3. Let AI identify black box opportunities
4. Implement incrementally

### The Magic Combination

These prompts work best with AI context tools:

- [repomix](https://github.com/yamadashy/repomix) (JS/TS)
- [onefilellm](https://github.com/jimmc414/onefilellm) (Python)

## 📖 Core Principles (From Eskil)

> "It's faster to write five lines of code today than to write one line today and then have to edit it in the future."

- **Constant developer velocity** regardless of project size
- **One module, one person** - complete ownership and understanding
- **Everything replaceable** - modular components you can rewrite
- **Black box interfaces** - clean APIs hide implementation details
- **Reusable modules** - components that work across projects

## 🎬 Original Source

Watch Eskil Steenberg's complete lecture: [Architecting LARGE Software Projects](https://www.youtube.com/watch?v=sSpULGNHyoI)

This legend has built 3D engines, networked games, and complex systems all in C using these exact principles.

## 🛠️ Examples

### Before (Tangled)

```javascript
// DOM manipulation scattered throughout React components
const MentionInput = () => {
  const handleClick = (e) => {
    // Direct DOM manipulation
    const selection = window.getSelection();
    const range = selection.getRangeAt(0);
    // 50+ lines of cursor positioning logic...
  };
};
```

### After (Black Box Interface)

```javascript
// Clean interface - implementation details hidden
interface DOMAdapter {
  insertMention(mention: Mention, position: number): void;
  getCursorPosition(): number;
  updateContent(content: string): void;
}

// Now supports React, Vue, Svelte, vanilla JS
const MentionInput = ({ adapter }: { adapter: DOMAdapter }) => {
  const handleClick = () => adapter.insertMention(mention, position);
};
```

## 🔗 Related Resources

- [Eskil's Video Architecting LARGE Software Projects](https://www.youtube.com/watch?v=sSpULGNHyoI)
- [Original Blog Post](medium-link)
- [Mentis](https://github.com/Alexanderdunlop/mentis)
- [How I Turn Any GitHub Repo Into Perfect AI Context](https://medium.com/vibe-coding/how-i-turn-any-github-repo-into-perfect-ai-context-game-changer-71919d497531)

## 🤝 Contributing

Found improvements to the prompts? Tried them on interesting projects? PRs welcome!

---

_Not affiliated with Anthropic, Eskil Steenberg, or any tools mentioned. These are battle-tested prompts from real development work._