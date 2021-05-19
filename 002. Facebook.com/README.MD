# Facebook with tailwindcss 2.1.2

Cảm ơn tác giả của bài hướng dẫn: https://www.youtube.com/watch?v=FzJkNtixGuQ

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

Thêm class cho body

```html
<body class="bg-gray-100 dark:bg-main-dark"></body>
```

## Phần 1: Navbar

![ScreenShot](1.png)
Gồm 3 phần: Trái - Giữa - Phải

### Tạo HTML

```
nav
  // Trái
  div
    a > img[src: Facebook-logo]
    a > img[src: Facebook-logo-text]

  //Giữa
  ul
    li > a > icon home (Trang chủ)
    li > a > icon movie (Watch)
    li > a > icon store (Marketplace)
    li > a > icon group (Nhóm)
    li > a > icon layout (Trò chơi)

  //Phải
  ul
    li > a
          img[src: profile image]
          span>{Tâm}
    li > div > icon plus (Tạo)
    li > div > icon messenger (Messenger)
    li > div > icon bell (Thông báo)
    li > div > icon moon (Darkmode)
```

### Thêm class cho nav

```html
<nav
  class="
  bg-white 
  h-max w-full 
  shadow 
  flex flex-col 
  items-center justify-center 
  fixed top-0 z-50 
  border-b 
  
  md:h-14
  md:flex-row 
  md:justify-between

  dark:bg-dark-second 
  dark:border-dark-third
  "
></nav>
```

### div left con của nav

1. Thêm class cho div left

- display flex
- center các item, căn giữa

```html
<div
  class="
flex 
items-center justify-between 
w-full 
px-4 py-2

md:w-max"
></div>
```

2. Thêm class cho thẻ a con của div left

```html
<a
  href="#"
  class="
mr-2 
hidden 

md:inline-block"
></a>
```

3. Thêm class cho thẻ img con của thẻ a (hiện trên màn hình lớn)

```html
<img
  src="./images/fb-logo.png"
  alt="Facebook logo"
  class="
  w-24 
  sm:w-20 
  lg:w-10"
/>
```

4. Thêm class cho thẻ a con thứ 2 của div left (hiện cho màn hình nhỏ)

```html
<a
  href="#"
  class="
inline-block 
md:hidden"
>
  <img src="./images/fb-logo-mb.png" alt="" class="w-32" />
</a>
```

### input search và mobile nav (con của div left)

```html
<div
  class="
  relative 
  bg-gray-100 
  px-2 py-2 w-10 h-10  
  rounded-full 
  flex items-center justify-center 
  cursor-pointer
  
  sm:w-11 sm:h-11 
  lg:w-10 lg:h-10 
  xl:w-max xl:pl-3 xl:pr-8

  dark:border-dark-third 
  "
>
  <i
    class="bx bx-search-alt-2 
  text-xl 
  xl:mr-2 
  dark:text-dark-txt"
  ></i>
  <input
    type="text"
    placeholder="Search Facebook"
    class="outline-none bg-transparent hidden xl:inline-block"
  />
</div>
```

### nav right (mobile)

![ScreenShot](2.png)

```html
<div
  class="
  text-2xl 
  bg-gray-200 

  grid place-items-center 
  rounded-full 
  w-10 h-10 
  cursor-pointer 

  hover:bg-gray-300 

  dark:bg-dark-third 
  dark-text-dark-txt

  md:hidden 
  "
>
  <i class="bx bxl-messenger"></i>
</div>
<div
  class="
  text-2xl 
  bg-gray-200 

  grid place-items-center 
  rounded-full 
  w-10 h-10 
  cursor-pointer 

  hover:bg-gray-300 

  dark:bg-dark-third 
  dark-text-dark-txt

  md:hidden 
  "
>
  <i class="bx bxs-moon"></i>
</div>
```

## Phần 2: Main center nav

### 1. class cho ul

```html

```

### 2. class cho 1 item trên menu

1 item chiếm 20% chiều rộng (khi md trở xuống)

1 item chiếm chiều rộng vừa đủ nội dung (khi md trở lên)

```html
<li class="w-1/5 md:w-max text-center"></li>
```

Nút active màu xanh

```html
<a
  href="#"
  class="
  inline-block 
  
  text-3xl 
  text-center 
  text-blue-500 
  
  w-full 
  py-2 px-3 
  border-b-4 border-blue-500
  
  cursor-pointer 

  xl:px-12 
  "
>
  <i class="bx bxs-home"></i>
</a>
```

Bình thường màu transparent khi hover thì nền màu xám

```html
  <a
    href="#"
    class="
    inline-block
    text-3xl
    text-center
    text-gray-600

    w-full
    py-2 px-3
    rounded
    cursor-pointer

    hover:bg-gray-100

    dark:hover:bg-dark-third
    dark:text-dark-txt relative

    xl:px-12
    "
  >
    <i class="bx bx-movie-play"></i>
  </a>
</li>
```

## Phần 3: Right nav

### Class cho ul

Màn hình md trở xuống sẽ ẩn

```html
<ul
  class="
mx-4 
items-center justify-center

hidden 
md:flex 
"
></ul>
```

### Class cho avatar

```html
<li class="h-full hidden xl:flex">
  <a
    href="#"
    class="
    inline-flex 
    items-center justify-center 
    
    p-1 
    mx-1
    rounded-full 
    
    hover:bg-gray-200 
    dark:hover:bg-dark-third 
    "
  >
    <img
      src="./images/aiony50.jpeg"
      alt="Profile picture"
      class="
      rounded-full 
      object-cover
      
      h-7 w-7 
      "
    />
    <span
      class="
    mx-2 
    font-medium 
    dark:text-dark-txt"
      >Tâm</span
    >
  </a>
</li>
```

### Class cho các item right khác (trừ thông báo và darkmode)

```html
<li>
  <div
    class="
    text-xl 
    bg-gray-200 
    
    mx-1 p-3 
    rounded-full 
    place-items-center 
    cursor-pointer 
    hidden 
    
    hover:bg-gray-300
    dark:bg-dark-third 
    dark:text-dark-txt 
    
    xl:grid 
    "
  >
    <i class="bx bxs-moon"></i>
  </div>
</li>
```

### Class cho item darkmode và thông báo

2 items này vẫn hiển thị khi màn hình nhỏ

Class cho số thông báo

```html
<li>
  <div
    class="
    relative
    text-xl 
    bg-gray-200 
    rounded-full 
    
    mx-1 p-3 
    cursor-pointer 
    
    grid 
    place-items-center 
    
    hover:bg-gray-300 
    dark:bg-dark-third 
    dark:text-dark-txt 
    "
  >
    <i class="bx bxs-bell"></i>
    <span
      class="
      absolute 
      top-0 right-0 
      px-1 
      
      text-xs 
      text-center
      text-white 
      bg-red-500 
      font-semibold 
      
      rounded-full 
      "
      >9+</span
    >
  </div>
</li>
```

### Class cho số thông báo ở item Trò chơi, và item Watch (con của main center nav)

Chỉnh vị trí right của số thông báo ở màn hình nhỏ thì right là 0; ở màn hình lớn khi mà chiều rộng của item nav lớn, thì cho right là 25%

```html
<span
  class="
  absolute 
  text-xs 
  top-0 right-1/4 
  px-1 
  
  font-semibold 
  text-white 
  bg-red-500 
  text-center 
  
  rounded-full 
  
  md:right-0
  "
  >9+</span
>
```

### Thêm icon menu khi màn hình nhỏ

Màn hình md trở lên thì ẩn icon menu, hiện icon Trò chơi

```html
<li
  class="w-1/5 md:w-max text-center 
inline-block 
md:hidden
"
>
  <a
    href="#"
    class="w-full text-3xl py-2 px-3 xl:px-12 cursor-pointer text-center inline-block rounded text-gray-600 hover:bg-gray-100 dark:hover:bg-dark-third dark:text-dark-txt relative"
  >
    <i class="bx bx-menu"></i>
  </a>
</li>
```

Màn hình md trở xuống thì hiện icon menu, ẩn icon Trò chơi

```html
<li
  class="w-1/5 md:w-max text-center 
hidden 
md:inline-block
"
></li>
```

## Phần thân

Chiếm 100% chiều cao toàn trình duyệt

Gồm 3 phần:

- Bên trái
- Giữa
- Bền phải

Bên trái:

- Mặc định ẩn, màn hình xl trở lên sẽ hiển thị
- Độ rộng: 1/5

Giữa:

- Mặc định 100% độ rộng
- Màn hình lg trở lên 2/3 độ rộng
- Màn hình xl trở lên thì 2/5 độ rộng

Phải:

- Mặc định ẩn
- Màn hình xl trở lên hiển thị
- Độ rộng: 1/5

```html
<div
  class="
flex justify-center 
h-screen
"
></div>
```

### Bên trái của phần thân

Fixed bên trái

Mặc định là ẩn, nhưng trên màn hình lớn sẽ hiển thị kiểu flex

Danh sách ul các items

```html
<div
  class="
  fixed 
  top-0 left-0 
  flex-col 
  
  w-1/5 
  h-full 
  pt-16 
  bg-blue-200
  
  hidden 
  xl:flex 
  "
></div>
```

#### li > a > img + span

Đặt class cho thẻ a:

- Hiển thị flex (để 2 item bên trong bao gồm img và span nằm ngang hàng nhau và canh giữa)
- Canh chỉnh khoảng cách
- hover đổi màu nền
- border radius
- transition
- chuẩn bị sẵn thuộc tính darkmode (đổi màu chữ và màu nền)

```html
<li>
  <a
    href="#"
    class="
    flex 
    items-center space-x-2 
    p-2 
    rounded-lg 
    transition-all 
    
    hover:bg-gray-200 
    dark:text-dark-txt 
    dark:hover:bg-dark-third
    "
  >
    <img
      src="./images/group.png"
      alt=""
      class="w-10 h-10 rounded-full object-cover"
    />
    <span class="font-semibold">Groups</span>
  </a>
</li>
```

Để hình được bo tròn, và giữ đúng tỷ lệ hình thì dùng các class:

```html
w-10 h-10 rounded-full object-cover
```

#### Class cho nút See more

Để icon chevron căn giữa có thể dùng class:

- grid
- place-items-center

```html
<span
  class="
  w-10 h-10 
  grid place-items-center 
  rounded-full 
  
  bg-gray-300 
  dark:bg-dark-second
  "
>
  <i class="bx bx-chevron-down"></i>
</span>
<span class="font-semibold">See more</span>
```

#### Css cho thanh ngang

Dùng class:

- border

```html
<div
  class="
mt-6
border-b border-gray-200 

dark:border-dark-third 
"
></div>
```

#### CSS cho phần Your Shortcuts

1. Bao gồm 2 thành phần:

- Thẻ span chữ Your shortcuts (1)
- Thẻ span chữ Edit (2)

2. Chức năng:

- Khi hover vào thẻ span (1) thì thẻ span (2) xuất hiện
- Khi hover vào thẻ span(2) thì thẻ span (2) đổi màu nền.

```html
<div
  class="
flex justify-between items-center 
px-4 h-4 
group
"
>
  <span
    class="
    font-semibold 
    text-gray-500 
    text-lg 
    
    dark:text-dark-txt 
    cursor-pointer"
    >Your shortcuts</span
  >
  <span
    class="
    p-2 
    text-blue-500 
    
    rounded-md 
    cursor-pointer 
    hidden 

    hover:bg-gray-200 
    group-hover:inline-block
    dark:hover:bg-dark-third 
    "
    >Edit</span
  >
</div>
```

#### CSS cho phần link dưới cùng của bên trái

- Dùng mt-auto để tự động đẩy phần link xuống dưới cùng của bên trái

```html
<div
  class="
mt-auto 
p-6 
text-sm 
text-gray-500 

dark:text-dark-txt 
"
>
  <a href="#">Privacy</a>
  <span>.</span>
  <a href="#">Termns</a>
  <span>.</span>
  <a href="#">Advertising</a>
  <span>.</span>
  <a href="#">Cookies</a>
  <span>.</span>
  <a href="#">Ad choices</a>
  <span>.</span>
  <a href="#">More</a>
  <span>.</span>
  <a href="#">Facebook &copy; 2021</a>
</div>
```

### Bên phải của phần thân (Friend request...)

```html
<div
  class="
  fixed 
  top-0 right-0 
  
  px-4 
  w-1/5 pt-16 
  h-full 
  bg-blue-200
  
  hidden 
  xl:block 
  "
></div>
```

#### Friend request

```
div.h-full
```

Phần 1:

2 items between 2 bên:

- Friends requests
- See All

```html
<div
  class="
flex justify-between items-center 
px-4 pt-4
"
>
  <span
    class="
  font-semibold 
  text-gray-500 
  text-lg 
  
  dark:text-dark-txt
  "
    >Friend requests</span
  >
  <span
    class="
    p-2 
    text-blue-500 
    
    rounded-md
    cursor-pointer 
    
    hover:bg-gray-200 
    dark:hover:bg-dark-third 
    "
    >See All</span
  >
</div>
```

Phần 2: Chia layout item friend request
Dùng class space-x-2 tạo khoảng cách giữa 2 nút bấm Confirm và Delete

```html
<div class="p-2">
  <a
    href="#"
    class="flex items-center space-x-4 p-2 hover:bg-gray-200 dark:hover:bg-dark-third rounded-lg transition-all"
  >
    <img
      src="./images/avt.jpg"
      alt="Friend request picture"
      class="w-16 h-16 rounded-full object-cover"
    />
    <div class="flex-1 h-full">
      <div class="dark:text-dark-txt">
        <span class="font-semibold">Phương Hằng</span>
        <span class="float-right">6d</span>
      </div>
      <div class="flex space-x-2 mt-2">
        <div
          class="w-1/2 bg-blue-500 cursor-pointer py-1 text-center font-semibold text-white rounded-lg"
        >
          Confirm
        </div>
        <div
          class="w-1/2 bg-gray-300 cursor-pointer py-1 text-center font-semibold text-black rounded-lg"
        >
          Delete
        </div>
      </div>
    </div>
  </a>
</div>
```

#### Friends (Contacts)

Thẻ div bao ngoài danh sách contacts

```html
<div
  class="flex justify-between items-center px-4 pt-4 text-gray-500 dark:text-dark-txt"
></div>
```

Tiêu đề contacts

icon search

icon ...

```html
<span class="font-semibold text-lg">Contacts</span>

<div class="flex space-x-1">
  <div
    class="w-8 h-8 grid place-items-center text-sl hover:bg-gray-200 dark:hover:bg-dark-third rounded-full cursor-pointer"
  >
    <i class="bx bx-search-alt-2"></i>
  </div>
  <div
    class="w-8 h-8 grid place-items-center text-sl hover:bg-gray-200 dark:hover:bg-dark-third rounded-full cursor-pointer"
  >
    <i class="bx bx-dots-horizontal-rounded"></i>
  </div>
</div>
```

#### Friends (Danh sách bạn bè)

1. Thẻ bao ngoài ul

```html
<ul class="p-2"></ul>
```

2. Từng item:

```
li
  div (display flex)
    div (relative)
      img (avatar)
      span (absolute: chấm xanh)
    div
      span (Vũ Hùng)
```

3. C

### PHẦN MAIN
