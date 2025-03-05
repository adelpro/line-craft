# cn

The `cn` utility function is used to merge Tailwind CSS class names conditionally. It combines `clsx` and `twMerge` to handle class names efficiently.

## Code

```ts
import clsx, { ClassValue } from 'clsx';
import { twMerge } from 'tailwind-merge';

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(...inputs));
}
```
## Packages to Install

To use the cn utility function, you need to install the following packages:

```sh
npm install clsx tailwind-merge
```

## How to Use

```ts
import clsx, { ClassValue } from 'clsx';
import { twMerge } from 'tailwind-merge';

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(...inputs));
}

// Example usage:
const className = cn('bg-red-500', isActive && 'text-white', 'hover:bg-red-700');
