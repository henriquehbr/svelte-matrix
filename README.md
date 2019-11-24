# svelte-matrix
> Rebuild the Matrix on your Svelte applications with this amazing effect

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

## Installation

```bash
# yarn
yarn add -D svelte-matrix

# npm
npm i -D svelte-matrix
```

## Usage

```svelte
<script>
	import Matrix from 'svelte-matrix'
</script>

<Matrix />
```

## Options

You can control the behavior of the matrix effect by passing specific props to the `<Matrix />` component

### `width`

The width of the Matrix canvas

default: `window.innerWidth`

#### Example:

```svelte
<Matrix width={300} />
```

### `height`

The height of the Matrix canvas

default: `window.innerHeight`

#### Example:

```svelte
<Matrix height={150} />
```

### `noInitialDrop`

Disables the initial column drop animation

default: `false`

#### Example:

```svelte
<Matrix noInitialDrop />
```

### `fontSize`

Sets the font size of the Matrix characters

default: `16`

#### Example:

```svelte
<Matrix fontSize={24} />
```

### `color`

Sets the font color of the Matrix characters

default: `'#0f0'`

#### Example:

```svelte
<Matrix color='#fff' />
```

### `interval`

Sets the time interval of the fall speed of the characters

default: `33`

#### Example:

```svelte
<Matrix interval={33} />
```
