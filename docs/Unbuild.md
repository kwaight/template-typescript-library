# Unbuild

Unbuild is a zero-config bundler for TypeScript libraries. It simplifies the build process by automatically generating the necessary files and configurations.
It is designed to work seamlessly with TypeScript, allowing you to focus on writing code without worrying about the underlying build setup.

## Installation

To install Unbuild, you can use npm or yarn. Here’s how to do it:

```bash
npm install unbuild --save-dev
```

or

```bash
yarn add unbuild --dev
```

## Usage

Unbuild is typically used in the package.json scripts section. Here’s an example of how to set it up:

```json
{
 "scripts": {
  "build": "unbuild",
  "dev": "unbuild --stub"
 }
}
```

### Explanation of the Scripts

Here’s a breakdown of the two selected package.json scripts:

"build": "unbuild",
"dev": "unbuild --stub",

🔨 build: "unbuild"

This runs the unbuild CLI tool, which is a zero-config bundler designed for TypeScript libraries.
• It compiles your TypeScript source code into distributable JavaScript files.
• By default, it generates dist/ with:
• ESM: .mjs
• CJS: .cjs
• Type definitions: .d.ts / .d.mts

This is your production-ready build step.

⸻

🧪 dev: "unbuild --stub"

This runs unbuild in stub mode.
• --stub generates placeholder files in dist/ that re-export directly from src/.
• Useful for faster local development because it avoids full compilation.
• Works well with tools like vitest, tsx, and editors that resolve modules via exports.

Example:

// dist/index.mjs (stub output)
export \* from '../src/index.ts'

This lets you test your exports and structure without bundling.

⸻

Summary

Script Purpose Behavior
build Production build Full compile with unbuild
dev Development mode Fast “stub” build that links to source
