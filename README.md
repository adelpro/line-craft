# lineCraft

lineCraft is a curated, hand-made collection of React UI components, custom hooks, and utilities all built with TypeScript. Designed for performance and ease-of-use, lineCraft follows SOLID principles and modern best practices to empower developers with ready-to-use, lightweight building blocks for your web applications. No installation required, simply copy & paste the code into your project.

## Features

- **Modular Components**: Reusable, customizable React components.
- **Custom Hooks**: Enhance your workflow with utility hooks.
- **TypeScript Support**: Strongly typed for reliability and clarity.
- **SOLID Principles**: Built to be scalable, maintainable, and testable.
- **Zero Dependencies**: No external libraries required.
- **Responsive Design**: Optimized for all screen sizes.
- **Accessible**: Components follow ARIA and accessibility best practices.
- **Lightweight**: Minimal footprint to keep your project fast.

## Installation

No installation required! Simply copy and paste the components, hooks, or utilities directly into your project.

## Getting Started

1. Browse the collection of components and hooks.
2. Copy the code snippet you need.
3. Paste it into your React project.
4. Customize and use as required.

## Usage Examples

### Button Component

```tsx
import React from 'react';

interface ButtonProps {
  label: string;
  onClick: () => void;
}

export const Button: React.FC<ButtonProps> = ({ label, onClick }) => (
  <button onClick={onClick} className="px-4 py-2 bg-blue-500 text-white rounded">
    {label}
  </button>
);
```

### Custom Hook: useToggle

```tsx
import { useState } from 'react';

export const useToggle = (initialState: boolean = false): [boolean, () => void] => {
  const [state, setState] = useState(initialState);
  const toggle = () => setState(prev => !prev);
  return [state, toggle];
};
```

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## License

This project is licensed under the MIT License.

## Contact

For any inquiries, reach out via [contact@adelpro.us.kg](mailto:contact@adelpro.us.kg).

## Acknowledgements

Special thanks to the open-source community for inspiration and resources.

