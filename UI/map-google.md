# map-google

```tsx
import React from "react";
type Props = {
  lat: number;
  lng: number;
};
export default function MapGoogle({ lat, lng }: Props) {
  return (
    <iframe
      className="shadow-md mx-auto border-0 sm:w-full md:max-w-[600px] h-[60vh] sm:h-[85vh] rounded-md transition-all duration-300 ease-in-out transform hover:scale-y-[101%] hover:scale-x-[105%]"
      style={{ border: 0 }}
      title="MD Pumps Location"
      loading="lazy"
      src={`https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d26015.792334872556!2d${lng}!3d${lat}!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x12f4c17c256aafd1%3A0xd4db0b732948869a!2zTUQg2YTYqNmK2Lkg2KzZhdmK2Lkg2KPZhtmI2KfYuSDZhdi22K7Yp9iqINin2YTZhdmK2KfZhyDZiNmC2LfYuSDYutmK2KfYsdmH2Kc!5e0!3m2!1sen!2sdz!4v1685039653389!5m2!1sen!2sdz`}
      allowFullScreen
    ></iframe>
  );
}
```
