# Facebook with tailwindcss 2.1.2

Darkmode

Lightmode

Responsive

## Setup

1. Folder

```
images
static
tailwind
```

2. Bash

```
cd taildwind
npx tailwindcss-cli@latest init
```

3. Edit file tailwind.config.js

```
tailwind/tailwind.config.js
```

4. Tạo file tailwind.custom.css
   Vị trí:

```
tailwind/tailwind.custom.css
```

Nội dung

```js
@tailwind base;
@tailwind components;
@tailwind utilities;

```

5. set NODE_ENV
   terminal

```
NODE_ENV=development
```

6. build tailwind
   terminal

```
npx tailwindcss-cli@latest build tailwind.custom.css -c tailwind.config.js -o tailwind.css
```

Kết quả:

```
tailwindcss 2.1.2

   🚀 Building: tailwind.custom.css

   ✅ Finished in 4.92 s
   📦 Size: 6.75MB
   💾 Saved to tailwind.css
```

7. tạo file index.html

- favicon fb
- thư viện boxicons
- tailwind.css

```html
<title>Facebook - Tailwindcss</title>
<link rel="shortcut icon" href="./images/fb-logo.png" type="image/png" />
<link
  href="https://unpkg.com/boxicons@2.0.7/css/boxicons.min.css"
  rel="stylesheet"
/>

<link rel="stylesheet" href="./tailwind/tailwind.css" />
```
