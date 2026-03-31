# humanizer-karu-custom

A **self-improving** AI writing humanizer skill for [KiloCode CLI](https://kilo.ai/) (compatible with Claude Code and other Agent Skills-compatible agents).

Remove AI-generated writing patterns from any text and continuously improve through a self-correction feedback loop. Based on Wikipedia's comprehensive "Signs of AI writing" guide.

## Features

- **24 AI Pattern Categories**: Detects inflated symbolism, promotional language, em dash overuse, rule of three, vague attributions, and more
- **Self-Improving**: Logs corrections and learns from user feedback across sessions
- **Soul Injection**: Doesn't just remove AI patterns - adds personality and voice
- **Cross-Platform**: Works with KiloCode CLI, Claude Code, and any Agent Skills-compatible agent

## Installation

### For KiloCode CLI

```bash
# Clone the repo
git clone https://github.com/karu-custom/humanizer-karu-custom.git

# Copy to your skills directory
cp -r humanizer-karu-custom ~/.agents/skills/

# Or link it
ln -s $(pwd)/humanizer-karu-custom ~/.agents/skills/
```

### For Claude Code

```bash
git clone https://github.com/karu-custom/humanizer-karu-custom.git
cp -r humanizer-karu-custom ~/.claude/skills/
```

### For Other Agents

Copy `humanizer-karu-custom/` to your agent's skills directory.

## Usage

### Explicit Invocation (Recommended)

```
Use the humanizer-karu-custom skill to fix this text
```

### Automatic Trigger

The skill may automatically activate when you ask the agent to:
- "Humanize this text"
- "Make this sound more natural"
- "Remove AI patterns from this"
- "Fix my LinkedIn post"

## Self-Improvement System

The skill includes a self-improvement protocol that learns from corrections:

### How It Works

1. **Humanize text** - Agent processes using 24 pattern categories
2. **Review changes** - After output, agent checks for:
   - Novel patterns not in the 24 categories
   - Context-specific fixes
   - False positives
3. **Log corrections** - If worthy, appends to `.learnings/` files:
   - `CORRECTIONS.md` - Individual corrections with context
   - `PATTERNS.md` - Emerging patterns across sessions
   - `LEARNINGS.md` - Validated, promoted patterns
4. **Periodic review** - Patterns with 3+ occurrences get promoted

### Manual Review

```bash
# Check logged corrections
cat ~/.agents/skills/humanizer-karu-custom/.learnings/CORRECTIONS.md

# Review emerging patterns
cat ~/.agents/skills/humanizer-karu-custom/.learnings/PATTERNS.md

# Check promoted learnings
cat ~/.agents/skills/humanizer-karu-custom/.learnings/LEARNINGS.md
```

## Pattern Categories

### Content Patterns
1. Undue Emphasis on Significance/Legacy
2. Undue Emphasis on Notability/Media Coverage
3. Superficial -ing Analyses
4. Promotional/Advertisement-like Language
5. Vague Attributions/Weasel Words
6. Outline-like "Challenges and Future Prospects" Sections

### Language & Grammar
7. Overused "AI Vocabulary" Words
8. Copula Avoidance (is/are → serves as/stands as)
9. Negative Parallelisms
10. Rule of Three Overuse
11. Elegant Variation (Synonym Cycling)
12. False Ranges

### Style
13. Em Dash Overuse
14. Overuse of Boldface
15. Inline-Header Vertical Lists
16. Title Case in Headings
17. Emojis
18. Curly Quotation Marks

### Communication
19. Collaborative Communication Artifacts
20. Knowledge-Cutoff Disclaimers
21. Sycophantic/Servile Tone

### Filler & Hedging
22. Filler Phrases
23. Excessive Hedging
24. Generic Positive Conclusions

## Examples

### Before (AI-sounding)

```
The new software update serves as a testament to the company's commitment to innovation. Moreover, it provides a seamless, intuitive, and powerful user experience—ensuring that users can accomplish their goals efficiently. It's not just an update, it's a revolution in how we think about productivity.
```

### After (Humanized)

```
The software update adds batch processing, keyboard shortcuts, and offline mode. Early feedback from beta testers has been positive, with most reporting faster task completion.
```

## Development

### Testing

Test files are in `/tmp/humanizer-eval/` (not included in repo).

### Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test with real-world text
5. Submit a pull request

## Credits

- Original skill concept: [@blader](https://github.com/blader/humanizer)
- Pattern guide: [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Signs_of_AI_writing)
- Self-improvement protocol inspired by: [OpenClaw self-improving-agent](https://github.com/openclaw/skills)

## License

MIT License