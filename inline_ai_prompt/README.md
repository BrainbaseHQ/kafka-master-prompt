# Inline AI Prompts

This folder contains system prompts for the inline AI assistant used in the text editor.

## Files

### Generation Prompts (for content creation)

- **generation_prompt.md** - Base prompt for all content generation tasks
- **blocknote_additions.md** - Additional instructions specific to BlockNote editor

### Edit Prompts (for text editing)

- **edit_prompt.md** - Base prompt for all text editing tasks
- **edit_blocknote_additions.md** - Additional instructions for editing in BlockNote editor

## How It Works

The `inline_ai.py` module in kafka-master-server fetches these prompts from GitHub on every request.

- **Fetch URL**: `https://raw.githubusercontent.com/BrainbaseHQ/kafka-master-prompt/main/inline_ai_prompt/`
- **Timeout**: 1 second (fast fetch for quick iteration)
- **Fallback**: If GitHub fetch fails, uses hardcoded fallback prompts

## Testing Changes

Since prompts are fetched on every request:

1. Edit any `.md` file in this folder
2. Commit and push to GitHub
3. Changes are live immediately (no server restart needed)

## Future Improvements

- Add caching with TTL to reduce GitHub API calls
- Add support for markdown, textarea, and default editor types
- Version prompts for A/B testing
