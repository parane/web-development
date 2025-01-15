# Optimize fonts and image

## Why optimise fonts and images?

Optimising fonts and images is important for improving the performance of your website. By reducing the size of these assets, you can decrease the time it takes for your website to load, which can lead to a better user experience and improved SEO.

## Optimising fonts
Next.js automatically optimizes fonts in the application when you use the next/font module. It downloads font files at build time and hosts them with your other static assets. This means when a user visits your application, there are no additional network requests for fonts which would impact performance.


## Optimising images

Using the next/image Component:

Next.js provides an optimized image component that automatically resizes and serves images in the best format. This component is built on top of the popular image optimization library, sharp, and provides several benefits:

```tsx
import Image from 'next/image';

const ResponsiveImages = () => {
  return (
    <>
      <Image
        src="/hero-desktop.png"
        width={1000}
        height={760}
        className="hidden md:block"
        alt="Screenshots of the dashboard project showing desktop version"
      />
      <Image
        src="/hero-mobile.png"
        width={560}
        height={620}
        className="block md:hidden"
        alt="Screenshot of the dashboard project showing mobile version"
      />
    </>
  );
};

export default ResponsiveImages;
```


Desktop Image:  

src="/hero-desktop.png": Specifies the source of the desktop image.
width={1000} and height={760}: Sets the dimensions of the image.
className="hidden md:block": Uses Tailwind CSS classes to hide the image on small screens (hidden) and display it on medium and larger screens (md:block).
alt="Screenshots of the dashboard project showing desktop version": Provides an alternative text for accessibility.

Mobile Image:

src="/hero-mobile.png": Specifies the source of the mobile image.
width={560} and height={620}: Sets the dimensions of the image.
className="block md:hidden": Uses Tailwind CSS classes to display the image on small screens (block) and hide it on medium and larger screens (md:hidden).
alt="Screenshot of the dashboard project showing mobile version": Provides an alternative text for accessibility.
