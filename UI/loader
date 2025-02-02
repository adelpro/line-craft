# Loader

## Code

```tsx
// components/Loader.tsx
import Image from 'next/image';
import React from 'react';

import spinnerSVG from '@/svgs/spinner.svg';
import { cn } from '@/utils';

interface LoaderProps {
  message?: string;
  size?: number;
  className?: string;
  textClassName?: string;
}

const Loader: React.FC<LoaderProps> = ({
  message = '',
  size = 24,
  className = '',
  textClassName = '',
}) => {
  return (
    <div
      className={cn(
        'm-5 flex flex-row items-center justify-center gap-2',
        className
      )}
    >
      <Image
        src={spinnerSVG}
        alt="Loading spinner"
        width={size}
        height={size}
      />
      <p className={textClassName}>{message}</p>
    </div>
  );
};

export default Loader;

```
