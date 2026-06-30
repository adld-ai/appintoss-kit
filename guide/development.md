# Development

## Scaffold

```bash
npx create-ait-app <appName> --inline --pm npm --template react-ts --tds --skills --ai claude
```

- `appName` must be lowercase, hyphen-separated, for example `pill-timer`.
- The scaffold creates a React + TypeScript + Vite project with TDS and AI
  skill docs.
- `granite.config.ts` holds the app identity: `appName`, `displayName`,
  `primaryColor`, and `icon`.

## Commands

```bash
npm run dev      # granite dev - starts Vite dev server on localhost:5173
npm run build    # ait build - produces <appName>.ait bundle
npm run lint     # eslint
npm run format   # prettier
```

## Key SDK APIs

- **Storage**: `import { Storage } from "@apps-in-toss/web-framework"` -
  native key-value store. Use this, not AsyncStorage. In browser dev mode, fall
  back to `localStorage` because the native bridge is unavailable.
- **TDS components**:
  `import { Top, Button, BottomSheet, TextField, Switch, Badge, ... } from "@toss/tds-mobile"`.
  These require the Toss native bridge and will hang in a regular browser. For
  browser-testable UI, use plain HTML/CSS equivalents.
- **TDSMobileAITProvider**: wraps the app in `src/main.tsx` for TDS theming.
  Remove it if not using TDS components, or it will hang outside Toss.

## Browser Testing

TDS components and the Storage SDK require the Toss app's native bridge. To test
in a regular browser:

1. Add a `localStorage` fallback in storage helpers by detecting
   `__AIT_INTERNAL__` in `window`.
2. Replace TDS components with plain HTML/CSS, or guard them behind environment
   checks.
3. Run `npm run dev` and open `http://localhost:5173`.
4. Follow the loop in
   [`development-verification-loop.md`](development-verification-loop.md).

## Build and Deploy

```bash
npm run build
```

The build outputs `<appName>.ait` in the project root. Upload the `.ait` file in
the Apps in Toss console under 앱 출시. The bundle works for both WebView and
React Native runtimes.
