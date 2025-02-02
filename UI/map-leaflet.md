# map-leaflet

```tsx
"use client";
import { MapContainer, TileLayer, Marker, Popup } from "react-leaflet";
import "leaflet/dist/leaflet.css";
import L from "leaflet";
type Props = {
  lat: number;
  lng: number;
};
export default function MapLeaflet({ lat, lng }: Props) {
  const svgIcon = new L.Icon({
    iconUrl:
      "data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0IiBhcmlhLWhpZGRlbj0idHJ1ZSIgZm9jdXNhYmxlPSJmYWxzZSIgZmlsbD0gIiNGRjAwMDAiPjxwYXRoIGQ9Ik0xMiAyQzguMTMgMiA1IDUuMTMgNSA5YzAgNS4yNSA3IDEzIDcgMTNzNy03Ljc1IDctMTNjMC0zLjg3LTMuMTMtNy03LTd6bTAgOS41Yy0xLjM4IDAtMi41LTEuMTItMi41LTIuNXMxLjEyLTIuNSAyLjUtMi41IDIuNSAxLjEyIDIuNSAyLjUtMS4xMiAyLjUtMi41IDIuNXoiLz48L3N2Zz4gIAo=",
    iconSize: [32, 32],
    iconAnchor: [16, 32],
    popupAnchor: [0, -32],
  });
  return (
    <MapContainer
      center={[lat, lng]}
      zoom={14}
      className="shadow-md mx-auto border-0 sm:w-full md:max-w-[600px] h-[60vh] sm:h-[85vh] rounded-md transition-all duration-300 ease-in-out transform hover:scale-y-[101%] hover:scale-x-[105%]"
    >
      <TileLayer
        attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
      />

      <Marker position={[lat, lng]} icon={svgIcon}>
        <Popup>
          <span className="font-bold text-gray-800">MD-Pompe.</span>
          <br />
          <span>You are welcome.</span>
        </Popup>
      </Marker>
    </MapContainer>
  );
}
```
