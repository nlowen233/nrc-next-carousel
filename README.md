# NRC Next.js/Tailwind Carousel (Beta v0.9.0)

(NRC stands for my LLC; [Nicholas Russell Consulting](https://www.nicholasrussellconsulting.com/))

This is a swipeable, infinite scrolling, user-friendly Next.js Carousel built **only for** Next.js/Tailwind users. If you're project uses both of these technologies, this package will make your life a whole lot easier. This package was built with marketing/ecomm in mind.

## Features

- Infinite scrolling
- Swipe to slide
- Automatic blur image loading
- Render anything in the Carousel w/ access to controls
- Autoplay capabilities
- Support for responsive design based on your custom Tailwind breakpoints
- Performance first 
- Accessibility handled
  
## Installation

`npm i nrc-next-carousel`

In your tailwind.config.ts, add 
`"./node_modules/nrc-next-carousel/dist/**/*.{js,ts,jsx,tsx}"`

like...

```ts
import type { Config } from "tailwindcss";

export default {
  content: [
    "./src/pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./src/components/**/*.{js,ts,jsx,tsx,mdx}",
    "./src/app/**/*.{js,ts,jsx,tsx,mdx}",
    "./node_modules/nrc-next-carousel/dist/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    screens: {
      sm: "28rem",
    },
    extend: {
      colors: {
        background: "var(--background)",
        foreground: "var(--foreground)",
      },
    },
  },
  plugins: [],
} satisfies Config;
```

## Usage

```tsx
import { Carousel } from  "nrc-next-carousel";
export  default  function  Home() {
    return (
        <>
            <Carousel frames={[...]}/>;
        </>
    );
}
```

## Documentation (Beta)
I plan to have more documentation in the future, and this will eventually be updated with that link. Everything should work exactly how you think it works, so my hope is that this documentation is not needed. This package is **mobile-first opinionated** meaning "mobile" is treated as default. If you are not taking advantage of the breakpoint system, you will be using the props called "mobile".

### Carousel Props
The Carousel is made up of Frames which can be images, React components, or both (more on that later). The size of these frames is controlled by the aspect ratio of the image of your first Frame (alternatively you can use the `heights` prop to control the sizes of the frames). 

The `loadingComponent` is what will appear before the blurUrl is loaded. This defaults to a pulsating gray colored div.

You can adjust the `slideDuration` to change the auto-play speed. And turn off auto-play with `noAutoPlay`.

### Frames
They `key` prop is only needed if you are not using images (or your images have the same src for some reason). 

You will see there is responsive architecture here, and you can use both `mobile` & `desktop` inside each Frame. If you are only using one, use `mobile`.

### NRC Image
I strongly recommend you provide your own `alt`, especially if you are building a marketing/ecom site.

You can adjust the quality of the initial blur image by using the `blurQuality` prop (use a number between 1-100). The larger the number, the better looking the image, but the worse the load time.

You can turn off the default blur with `noBlur`. `imageFocalPoint` should be self-explanatory if you're familiar with the concept.

### NRC Frame Component
This will be either a React component, or a function that returns a React component. If it's a function, it will receive the `setCarouselIndex` prop if you need it.

The component will be inside an absolute positioned container with full width and height of the Frame.


## License

This project is licensed under the **ISC License**.

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.

