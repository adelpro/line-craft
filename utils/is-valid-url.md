# is-valid-url

```ts
import { formatURL } from './format-url';

export function isValidURL(url: string | undefined): boolean {
  if (!url) return false;

  try {
    // Add "https://" if not present
    const formattedURL = formatURL(url);
    if (!formattedURL) {
      return false;
    }

    new URL(formattedURL);
    return true;
  } catch {
    return false;
  }
}
```