# Neo-Brutalism UI Skill

A custom skill for generative AI coding assistants to build bold, raw, and high-contrast **Neo-Brutalism UI** components.

This skill acts as a comprehensive set of design guidelines, material recipes, and interaction rules that direct the AI to build websites characterized by hard offset shadows, thick black borders, flat vivid colors, and snappy press interactions.

## What is Neo-Brutalism in Web Design?

Neo-Brutalism (or Neobrutalism) is a modern web design trend that marries raw, unpolished, brutalist HTML structures with vibrant color schemes and high-contrast geometry.

Key characteristics:
- **Hard Offset Shadows**: Shadows with zero blur and solid black colors (`+x, +y` offset).
- **Thick Borders**: Container and interactive objects feature bold `2px` black borders.
- **Flat Surfaces**: Solid vivid backgrounds with no gradients.
- **Micro-Interactions**: Snappy translate-on-press patterns where elements physically collapse onto their shadows.
- **Warm Neutral Backgrounds**: High-contrast contrasts anchored by warm canvas backgrounds (e.g., `#e3dfd7` to `#f5f1eb`).

## Installation

To use this skill with your AI assistant (e.g., Gemini / Antigravity), copy the `brutalism.md` file into your local config directory:

```bash
cp brutalism.md ~/.gemini/config/skills/neo-brutalism-ui/SKILL.md
```

*(Make sure the target directory exists before running the command)*

## How to Trigger

Once installed, simply prompt your AI with:

> *"Build a brutalist landing page..."*  
> *"Create a card component with a neo-brutal design..."*  
> *"Use a chunky UI style with hard shadows for this form..."*

The AI will automatically parse the guidelines in `brutalism.md` to design containers, inputs, buttons, and badges that match the neo-brutal aesthetic.

## Core Features

- **Standardized Shadow Offsets**: Exact instructions for styling cards (`shadow-[4px_4px_0px_0px_#000000]`) and matching their hover states.
- **Tactile Recessed Surfaces**: Guidelines for nesting secondary surfaces (like input fields) flush within parent cards without adding redundant shadows.
- **Snappy Press-Flat Interaction**: A signature mechanical transition rule where buttons shift `+4px, +4px` on hover/active states to collapse the shadow completely.
- **High Contrast Focus**: Bold focus outlines for accessibility that align with the high-contrast aesthetic.

## License

MIT License. Feel free to copy, modify, and build your own UI design skills!
