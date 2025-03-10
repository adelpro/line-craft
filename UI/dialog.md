# Dialog

A modal dialog component that interrupts user workflow to demand attention. Built with HTML `<dialog>` element for better accessibility and browser support.

## Code

  ```tsx
import { cn } from "@/utils";
import React, { ReactNode, useLayoutEffect } from "react";

type DialogProps = {
  ref: React.RefObject<HTMLDialogElement | null>;
  children: ReactNode;
  hideCloseButton?: boolean;
  className?: string;
  closeButtonLeft?: boolean;
};

export default function Dialog({
  ref: dialogRef,
  hideCloseButton = false,
  closeButtonLeft = false,
  className,
  children,
}: DialogProps) {
  const closeDialog = () => {
    dialogRef.current?.close();
  };
  useLayoutEffect(() => {
    if (dialogRef.current?.open) {
      dialogRef.current?.showModal();
      return;
    }
    dialogRef.current?.close();
  }, [dialogRef]);

  return (
    <dialog
      ref={dialogRef}
      onClick={(event) => {
        if (event.target === dialogRef.current) {
          dialogRef.current?.close();
        }
      }}
      onKeyDown={(event) => {
        if (event.key === "Escape") {
          dialogRef.current?.close();
        }
      }}
      className="rounded-xl backdrop:bg-zinc-800/50 dark:backdrop:bg-zinc-200/50"
    >
      <main className="fixed top-1/2 left-1/2 -translate-y-1/2 -translate-x-1/2 w-full max-w-xl rounded-xl bg-background p-2 text-foreground">
        {!hideCloseButton && (
          <div
            className={cn(
              "flex justify-end items-center p-2",
              closeButtonLeft && "justify-start"
            )}
          >
            <button
              type="button"
              onClick={closeDialog}
              aria-label="Close"
              className=" cursor-pointer transition-transform duration-200 hover:scale-110"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="#6B7280"
                aria-hidden="true"
                focusable="false"
                width="32"
                height="32"
                viewBox="0 0 32 32"
              >
                <path
                  fill="#6B7280"
                  d="M16 2C8.2 2 2 8.2 2 16s6.2 14 14 14s14-6.2 14-14S23.8 2 16 2m0 26C9.4 28 4 22.6 4 16S9.4 4 16 4s12 5.4 12 12s-5.4 12-12 12"
                />
                <path
                  fill="#6B7280"
                  d="M21.4 23L16 17.6L10.6 23L9 21.4l5.4-5.4L9 10.6L10.6 9l5.4 5.4L21.4 9l1.6 1.6l-5.4 5.4l5.4 5.4z"
                />
              </svg>
            </button>
          </div>
        )}
        <div className={className}>{children}</div>
      </main>
    </dialog>
  );
}
  ```

## Props

| Prop                | Type                                  | Default     | Description                              |
|---------------------|---------------------------------------|-------------|------------------------------------------|
| **ref**             | `React.RefObject<HTMLDialogElement \| null>` | -           | Dialog element reference                 |
| **children**        | `ReactNode`                           | -           | Dialog content                           |
| **hideCloseButton** | `boolean`                             | `false`     | Hide the close button                    |
| **className**       | `string`                              | -           | Custom CSS classes for content container |
| **closeButtonLeft** | `boolean`                             | `false`     | Position close button on left side       |

## Utilities

 - [cn() Helper](https://github.com/adelpro/line-craft/blob/main/utils/cn.md)

 - useLayoutEffect Hook (from React): The component uses useLayoutEffect for immediate DOM measurements when opening/closing. This ensures proper positioning before paint.

 - TailwindCSS: for styling

## How to Use

To use the Dialog component, follow the example below:

```tsx
import React, { useRef } from 'react';
import Dialog from './path/to/Dialog';

function App() {
  const dialogRef = useRef<HTMLDialogElement | null>(null);

  const openDialog = () => {
    dialogRef.current?.showModal();
  };

  return (
    <div>
      <button onClick={openDialog}>Open Dialog</button>
      <Dialog ref={dialogRef} className="custom-class">
        <p>This is a sample dialog content.</p>
      </Dialog>
    </div>
  );
}

export default App;
```

In this example:

    The Dialog component is imported and rendered.
    A useRef hook is used to create a reference for the dialog.
    A button is provided to open the dialog by calling the showModal method on the dialog reference.
    The dialog contains sample content and can be styled with custom classes using the className prop.
