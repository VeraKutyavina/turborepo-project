# Turborepo Testing

This is an app for testing Turborepo packages and configuration.


## What's inside?

### Apps and Packages

- `docs`: a [Next.js](https://nextjs.org/) app
- `site`: another [Next.js](https://nextjs.org/) app
- `@repo/ui`: a stub React component library shared by both `site` and `docs` applications
- `@repo/math`: a custom package shared by both `site` and `docs` applications
- `@repo/eslint-config`: `eslint` configurations
- `@repo/typescript-config`: `tsconfig.json`s used throughout the monorepo
- `@repo/tailwind-config`: `tailwind` configurations


### Build

To build all apps and packages, run the following command:

```
"build": {
    // A package's build script depends on that package's
    // dependencies' and devDependencies'
    // build tasks  being completed first
    // (the ^ symbol signifies upstream).
    "dependsOn": ["^build"],
    // note: output globs are relative to each package's package.json
    // (and not the monorepo root)
    "outputs": [".next/"]
},
```

```
npm run build
```

### Develop

To develop all apps and packages, run the following command:

```
npm run dev
```

### Test

```
"test": {
    // A package's test script depends on that package's
    // own build script being completed first.
    "dependsOn": ["build"],
    "outputs": [],
    // A package's test script should only be rerun when
    // either a .tsx or .ts file has changed in src or test folders.
    "inputs": ["src//*.tsx", "src//*.ts", "test//*.ts", "test/**/*.tsx"]
},
```

```
npm run test
```

## Useful Links

Learn more about the power of Turborepo:

- [Tasks](https://turbo.build/repo/docs/core-concepts/monorepos/running-tasks)
- [Caching](https://turbo.build/repo/docs/core-concepts/caching)
- [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching)
- [Filtering](https://turbo.build/repo/docs/core-concepts/monorepos/filtering)
- [Configuration Options](https://turbo.build/repo/docs/reference/configuration)
- [CLI Usage](https://turbo.build/repo/docs/reference/command-line-reference)
