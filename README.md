# ECO WARM · Халаалтын тооцоолуур

ECO WARM тоосгон халаагуурын загвар, үнэ болон сарын цахилгааны зардлыг тооцоолох нэг хуудас вэб.

- Цэвэр HTML + CSS + JavaScript (framework, build алхам байхгүй)
- `index.html` — хуудас, компонентын CSS, JS
- `tokens.css` — design system (өнгө, фонт, зай, радиус, сүүдэр); тайлбар нь [DESIGN.md](DESIGN.md)
- `img/` — бүтээгдэхүүний зургууд

## Агуулга засах

- **Хэрэглэгчийн сэтгэгдэл (Facebook reel) нэмэх:** `index.html` доторх `REVIEWS` жагсаалтад нэг мөр нэмнэ:
  ```js
  { url: 'https://www.facebook.com/reel/…', title: 'Богино гарчиг', meta: 'Хуудасны нэр · Facebook' },
  ```
  Гүйдэг жагсаалт, сум товч, анимаци өөрөө тохирно. Бичлэг олон нийтэд нээлттэй (Public) байх ёстой.
- **Гэрчилгээ:** PDF файлууд `docs/`, жижиг зургууд `img/cert-*.webp`, жагсаалт нь `CERTS`.

## Локал дээр ажиллуулах

```bash
python -m http.server 5180
```

Дараа нь http://localhost:5180 нээнэ.

## Deploy

Static сайт тул Vercel, Netlify, GitHub Pages дээр шууд байршина. Environment variable шаардлагагүй.
