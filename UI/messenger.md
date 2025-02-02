# messenger

```tsx
"use client";
import Script from "next/script";
import React, { useEffect } from "react";

declare global {
  interface Window {
    fbAsyncInit: () => void;
    FB?: any;
  }
}

type Props = {
  pageId: string;
  themeColor?: string;
};
export default function Messenger({ pageId, themeColor = "#0084FF" }: Props) {
  useEffect(() => {
    // Check if the Facebook SDK is already initialized
    if (window.FB) {
      return;
    }

    // Initialize the Facebook SDK
    window.fbAsyncInit = function () {
      window.FB.init({
        xfbml: true,
        version: "v18.0",
      });
    };

    // Load the Facebook SDK script
    (function (d, s, id) {
      const fjs = d.getElementsByTagName(s)[0];
      if (!fjs) return;
      if (d.getElementById(id)) return;
      let js = d.createElement(s) as HTMLScriptElement;
      if (!js) return;
      js.id = id;
      js.src = "https://connect.facebook.net/en_US/sdk/xfbml.customerchat.js";
      js.crossOrigin = "anonymous";
      fjs.parentNode?.insertBefore(js, fjs);
    })(document, "script", "facebook-jssdk");
  }, []); // Run this effect only once on mount

  return (
    <div>
      <div id="fb-root"></div>
      <div id="fb-customer-chat" className="fb-customerchat" />

      <Script strategy="afterInteractive">
        {`
      var chatbox = document.getElementById('fb-customer-chat');
      chatbox.setAttribute("page_id", "${pageId}");
      chatbox.setAttribute("attribution", "biz_inbox");      
      `}
      </Script>
      <style jsx>{`
        .fb-customerchat {
          --theme-color: ${themeColor};
        }
      `}</style>
    </div>
  );
}
```
