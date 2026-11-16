# ECO WARM · Халаалтын тооцоолуур

ECO WARM тоосгон халаагуурын загвар, үнэ болон сарын цахилгааны зардлыг тооцоолох нэг хуудас вэб.

- Цэвэр HTML + CSS + JavaScript (framework, build алхам байхгүй)
- `index.html` — хуудас, компонентын CSS, JS
- `tokens.css` — design system (өнгө, фонт, зай, радиус, сүүдэр); тайлбар нь [DESIGN.md](DESIGN.md)
- `img/` — бүтээгдэхүүний зургууд

## Локал дээр ажиллуулах

```bash
python -m http.server 5180
```

Дараа нь http://localhost:5180 нээнэ.

## Deploy

Static сайт тул Vercel, Netlify, GitHub Pages дээр шууд байршина. Environment variable шаардлагагүй.
