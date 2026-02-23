# Design System - Portfolio Tech (MASTER)

Mục tiêu: Trang portfolio cá nhân cho vị trí tech (frontend / fullstack), tone màu sáng, đơn giản, hiện đại, tập trung vào đọc được thông tin, tối ưu cho tuyển dụng.

---

## 1. Tông màu (Light-first)
- Primary: #0EA5A4 (teal-500) — tươi, hiện đại
- Primary-700: #059E9D
- Accent / CTA: #2563EB (blue-600)
- Background: #FFFFFF
- Surface / Card: #F8FAFC (slate-50)
- Muted text: #475569 (slate-600)
- Body text: #0F172A (slate-900)
- Border / Divider: #E6EEF6
- Success: #16A34A, Warning: #F59E0B, Error: #EF4444

Tỉ lệ sử dụng: background 60–70%, surfaces 20–30%, accents/CTAs 5–10%.

Anti-patterns: tránh gradient quá rực, tránh tông xám nhạt cho body text.

---

## 2. Typography
- Primary font: Inter (Google) — trọng tâm readability
- Heading font (optional): Poppins Medium cho H1/H2 (nếu cần nét hiện đại hơn)
- Font sizes (base 16px):
  - H1: 40px / 3rem (xl hero)
  - H2: 28px / 1.75rem
  - H3: 20px / 1.25rem
  - Body: 16px / 1rem
  - Small/caption: 13px / 0.8125rem

Line-height: headings 1.1–1.25, body 1.5.

---

## 3. Layout & Grid
- Max-width content: max-w-6xl (≈ 1152px)
- Container padding: px-4 (mobile) -> px-8 (desktop)
- Grid for projects: responsive grid
  - mobile: grid-cols-1
  - md: grid-cols-2
  - lg: grid-cols-3

Spacing scale: 4/8/12/16/24/32 px (tailwind multiples: 1,2,3,4,6,8).

---

## 4. Components
1. Navbar (floating minimal)
   - Transparent bg on scroll, small shadow
   - Items: Home | Projects | Experience | Blog (optional) | Contact (CTA)
   - CTA style: bg-primary text-white rounded-md px-4 py-2

2. Hero
   - Left: short intro (1–2 câu), role, value prop
   - Right: portrait (round), hoặc code-ish illustration
   - Primary CTA: "Xem dự án" (scroll to projects)
   - Secondary CTA: "Tải CV" (link PDF)

3. Project Card
   - Title, short tech stack (badges), 1–2 dòng mô tả, link GitHub / Live
   - Hover: subtle translate-y and shadow; cursor-pointer

4. Experience / Timeline
   - Clean list, company, role, duration, 1–2 bullets

5. Footer
   - Links: GitHub, LinkedIn, Email
   - Small copyright

Accessibility: tất cả nút có focus-visible rõ ràng (ring-primary/2), alt text cho ảnh.

---

## 5. UX Guidelines (Ngắn)
- CTA hierarchy rõ ràng: primary màu nổi, secondary outline
- Giữ navbar nhỏ, avoid large hero CTAs che khuất nội dung
- Tối ưu performance: lazy-load images, preconnect fonts
- Keyboard accessible: tab order hợp lý, skip-to-content link
- prefers-reduced-motion respected

---

## 6. Tailwind (Stack recommendation)
- Stack mặc định: html + TailwindCSS
- Tailwind utilities gợi ý: rounded-md, shadow-sm, transition-colors duration-200, text-slate-900, bg-white, border-gray-100

Ví dụ template nhanh (sao chép vào `src/index.html`) để bắt đầu:

```html
<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Portfolio — [Tên của bạn]</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Poppins:wght@500&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body { font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; }
  </style>
</head>
<body class="bg-white text-slate-900 antialiased">
  <header class="fixed inset-x-4 top-4 z-50">
    <nav class="max-w-6xl mx-auto flex items-center justify-between bg-white/80 backdrop-blur-md rounded-lg px-4 py-2 shadow-sm">
      <a class="font-semibold">[Tên]</a>
      <div class="hidden md:flex items-center gap-4 text-sm text-slate-700">
        <a href="#projects" class="hover:text-slate-900">Projects</a>
        <a href="#experience" class="hover:text-slate-900">Experience</a>
        <a href="#contact" class="px-3 py-1 rounded-md bg-teal-500 text-white">Contact</a>
      </div>
    </nav>
  </header>

  <main class="pt-28">
    <section class="max-w-6xl mx-auto px-4 grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
      <div>
        <p class="text-teal-500 font-medium">Hi, tôi là [Tên] — Frontend Developer</p>
        <h1 class="mt-4 text-4xl font-bold leading-tight">Xây dựng giao diện nhanh, sạch và có hiệu suất</h1>
        <p class="mt-4 text-slate-600">Tôi tập trung vào React, Next.js và trải nghiệm người dùng tốt. Dưới đây là một vài dự án tiêu biểu.</p>
        <div class="mt-6 flex gap-3">
          <a href="#projects" class="px-4 py-2 rounded-md bg-teal-500 text-white shadow-sm">Xem dự án</a>
          <a href="/cv.pdf" class="px-4 py-2 rounded-md border border-gray-200 text-slate-800">Tải CV</a>
        </div>
      </div>
      <div class="flex justify-center lg:justify-end">
        <img src="/me.jpg" alt="[Tên] portrait" class="w-48 h-48 rounded-full object-cover shadow-md">
      </div>
    </section>

    <section id="projects" class="mt-16 max-w-6xl mx-auto px-4">
      <h2 class="text-2xl font-semibold">Dự án tiêu biểu</h2>
      <div class="mt-6 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- Project cards -->
      </div>
    </section>

  </main>

  <footer class="mt-20 py-8 border-t border-gray-100">
    <div class="max-w-6xl mx-auto px-4 text-sm text-slate-600 flex justify-between">
      <div>© 2026 [Tên của bạn]</div>
      <div class="flex gap-4">
        <a href="#">GitHub</a>
        <a href="#">LinkedIn</a>
      </div>
    </div>
  </footer>
</body>
</html>
```

---

## 7. Pre-delivery checklist
- [ ] Nội dung hero ngắn gọn, rõ value
- [ ] Tất cả ảnh có alt
- [ ] CV PDF sẵn link
- [ ] Focus states, keyboard test
- [ ] Responsive: 375 / 768 / 1024 / 1440

---

## Ghi chú nhanh
- File này là bản MASTER: khi triển khai page cụ thể, tạo `design-system/pages/<page>.md` để override các quy tắc.
- Đầu tư 15 phút tối ưu ảnh (avif/webp) và lazy-load.

