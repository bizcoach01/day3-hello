# Personal Portfolio Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a warm-toned, responsive single-page scrolling portfolio website in a single `index.html` file.

**Architecture:** Single `index.html` with Tailwind CSS via CDN. All sections (nav, hero, career, contact, footer) in one file. No build tools. Formspree for contact form submission.

**Tech Stack:** HTML5, Tailwind CSS (CDN), vanilla JavaScript (mobile menu toggle)

---

### Task 1: HTML Skeleton + Tailwind Setup

**Files:**
- Rewrite: `index.html`

- [ ] **Step 1: Write the HTML skeleton with Tailwind CDN and custom colors**

Replace the contents of `index.html` with:

```html
<!DOCTYPE html>
<html lang="ko" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>홍길동 - 포트폴리오</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            warm: {
              50: '#FFF8F0',
              100: '#FFFAF5',
              200: '#FDEBD0',
              300: '#F5CBA7',
              400: '#F5E6D3',
              500: '#D4845A',
              600: '#8B7355',
              700: '#6B4226',
            }
          }
        }
      }
    }
  </script>
</head>
<body class="bg-warm-50 text-warm-600">
  <!-- Navigation -->
  <nav id="navbar" class="fixed top-0 left-0 right-0 z-50 bg-warm-50/95 backdrop-blur border-b-2 border-warm-400">
    <div class="max-w-4xl mx-auto px-6 py-4 flex justify-between items-center">
      <a href="#" class="text-xl font-bold text-warm-500">홍길동</a>
      <div class="hidden md:flex gap-6">
        <a href="#intro" class="hover:text-warm-500 transition">소개</a>
        <a href="#career" class="hover:text-warm-500 transition">경력</a>
        <a href="#contact" class="hover:text-warm-500 transition">연락처</a>
      </div>
      <button id="menu-btn" class="md:hidden text-warm-700" aria-label="메뉴">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
      </button>
    </div>
    <div id="mobile-menu" class="hidden md:hidden px-6 pb-4">
      <a href="#intro" class="block py-2 hover:text-warm-500 transition">소개</a>
      <a href="#career" class="block py-2 hover:text-warm-500 transition">경력</a>
      <a href="#contact" class="block py-2 hover:text-warm-500 transition">연락처</a>
    </div>
  </nav>

  <!-- Sections will be added here -->
  <main class="pt-16">
  </main>
</body>
</html>
```

- [ ] **Step 2: Open in browser and verify**

Open `index.html` in a browser. Expected: fixed nav bar with "홍길동" on left, three links on right (desktop), hamburger on mobile-sized viewport.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add HTML skeleton with Tailwind CDN and navigation"
```

---

### Task 2: Mobile Menu JavaScript

**Files:**
- Modify: `index.html` (add script before `</body>`)

- [ ] **Step 1: Add mobile menu toggle script**

Add the following `<script>` tag just before `</body>`:

```html
  <script>
    const menuBtn = document.getElementById('menu-btn');
    const mobileMenu = document.getElementById('mobile-menu');
    menuBtn.addEventListener('click', () => {
      mobileMenu.classList.toggle('hidden');
    });
    mobileMenu.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        mobileMenu.classList.add('hidden');
      });
    });
  </script>
```

- [ ] **Step 2: Verify in browser**

Resize browser to mobile width. Click hamburger icon. Expected: menu links appear/disappear. Clicking a link closes the menu.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add mobile hamburger menu toggle"
```

---

### Task 3: Hero / Intro Section

**Files:**
- Modify: `index.html` (add inside `<main>`)

- [ ] **Step 1: Add hero section after `<main>` opening tag**

Insert the following right after `<main class="pt-16">`:

```html
    <section id="intro" class="min-h-[70vh] flex items-center justify-center bg-gradient-to-br from-warm-50 to-warm-200 px-6">
      <div class="text-center">
        <div class="w-28 h-28 rounded-full bg-warm-300 mx-auto mb-6 flex items-center justify-center text-5xl">
          👤
        </div>
        <h1 class="text-4xl md:text-5xl font-bold text-warm-700 mb-4">안녕하세요, 홍길동입니다</h1>
        <p class="text-lg text-warm-600 max-w-lg mx-auto">웹 개발자로서 사용자 경험을 개선하는 일에 열정을 가지고 있습니다.</p>
      </div>
    </section>
```

- [ ] **Step 2: Verify in browser**

Scroll to intro section. Expected: centered profile circle, large heading, subtitle with gradient background. Click "소개" in nav — should smooth-scroll here.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add hero/intro section with profile and heading"
```

---

### Task 4: Career / Experience Section

**Files:**
- Modify: `index.html` (add inside `<main>`, after intro section)

- [ ] **Step 1: Add career section after the intro section closing `</section>`**

```html
    <section id="career" class="py-20 bg-warm-100 px-6">
      <div class="max-w-2xl mx-auto">
        <h2 class="text-3xl font-bold text-warm-700 text-center mb-12">경력</h2>
        <div class="space-y-6">
          <div class="border-l-4 border-warm-300 pl-6 py-4 bg-white rounded-r-lg shadow-sm">
            <p class="text-sm font-semibold text-warm-500">2022 - 현재</p>
            <h3 class="text-lg font-bold text-warm-700 mt-1">시니어 개발자 · ABC 회사</h3>
            <p class="text-warm-600 mt-1">프론트엔드 아키텍처 설계 및 팀 리드</p>
          </div>
          <div class="border-l-4 border-warm-300 pl-6 py-4 bg-white rounded-r-lg shadow-sm">
            <p class="text-sm font-semibold text-warm-500">2019 - 2022</p>
            <h3 class="text-lg font-bold text-warm-700 mt-1">개발자 · XYZ 회사</h3>
            <p class="text-warm-600 mt-1">React 기반 웹 애플리케이션 개발</p>
          </div>
        </div>
        <div class="mt-10 text-center">
          <h3 class="text-lg font-semibold text-warm-700 mb-4">기술 스택</h3>
          <div class="flex flex-wrap gap-3 justify-center">
            <span class="bg-warm-200 text-warm-700 px-4 py-2 rounded-full text-sm font-medium">JavaScript</span>
            <span class="bg-warm-200 text-warm-700 px-4 py-2 rounded-full text-sm font-medium">React</span>
            <span class="bg-warm-200 text-warm-700 px-4 py-2 rounded-full text-sm font-medium">Node.js</span>
            <span class="bg-warm-200 text-warm-700 px-4 py-2 rounded-full text-sm font-medium">TypeScript</span>
            <span class="bg-warm-200 text-warm-700 px-4 py-2 rounded-full text-sm font-medium">Tailwind CSS</span>
            <span class="bg-warm-200 text-warm-700 px-4 py-2 rounded-full text-sm font-medium">Git</span>
          </div>
        </div>
      </div>
    </section>
```

- [ ] **Step 2: Verify in browser**

Scroll to career section. Expected: timeline with two entries (date, title, description), skill tags below. Click "경력" in nav — should smooth-scroll here.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add career timeline and skill tags section"
```

---

### Task 5: Contact Section with Formspree

**Files:**
- Modify: `index.html` (add inside `<main>`, after career section)

- [ ] **Step 1: Add contact section after the career section closing `</section>`**

```html
    <section id="contact" class="py-20 bg-warm-50 px-6">
      <div class="max-w-md mx-auto">
        <h2 class="text-3xl font-bold text-warm-700 text-center mb-12">연락처</h2>
        <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST" class="space-y-5">
          <div>
            <label for="name" class="block text-sm text-warm-600 mb-1">이름</label>
            <input type="text" id="name" name="name" required
              class="w-full px-4 py-3 border-2 border-warm-400 rounded-lg bg-white text-warm-700 placeholder-warm-300 focus:outline-none focus:border-warm-500 transition"
              placeholder="이름을 입력하세요">
          </div>
          <div>
            <label for="email" class="block text-sm text-warm-600 mb-1">이메일</label>
            <input type="email" id="email" name="email" required
              class="w-full px-4 py-3 border-2 border-warm-400 rounded-lg bg-white text-warm-700 placeholder-warm-300 focus:outline-none focus:border-warm-500 transition"
              placeholder="이메일을 입력하세요">
          </div>
          <div>
            <label for="message" class="block text-sm text-warm-600 mb-1">메시지</label>
            <textarea id="message" name="message" rows="4" required
              class="w-full px-4 py-3 border-2 border-warm-400 rounded-lg bg-white text-warm-700 placeholder-warm-300 focus:outline-none focus:border-warm-500 transition resize-none"
              placeholder="메시지를 입력하세요"></textarea>
          </div>
          <button type="submit"
            class="w-full bg-warm-500 text-white font-semibold py-3 rounded-lg hover:bg-warm-700 transition">
            보내기
          </button>
        </form>
      </div>
    </section>
```

- [ ] **Step 2: Verify in browser**

Scroll to contact section. Expected: three-field form with labels, submit button in accent color. Try submitting empty form — HTML5 validation should block. Click "연락처" in nav — should smooth-scroll here.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add contact form with Formspree integration"
```

---

### Task 6: Footer

**Files:**
- Modify: `index.html` (add inside `<main>`, after contact section)

- [ ] **Step 1: Add footer after the contact section closing `</section>`**

```html
    <footer class="py-6 text-center text-sm text-warm-600 bg-warm-400">
      &copy; 2026 홍길동. All rights reserved.
    </footer>
```

- [ ] **Step 2: Verify in browser**

Expected: footer with copyright text on warm-400 background at bottom of page.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add footer with copyright"
```

---

### Task 7: Final Verification and Responsive Check

**Files:**
- Verify: `index.html`

- [ ] **Step 1: Full page walkthrough in browser (desktop)**

Open `index.html` at full browser width. Verify:
- Nav is fixed at top with all links visible
- Hero section centered with gradient background
- Career timeline displays properly with skill tags
- Contact form fields are styled, submit button works (validation blocks empty submit)
- Footer at bottom
- Smooth scroll works for all nav links

- [ ] **Step 2: Mobile responsive check**

Resize browser to ~375px width. Verify:
- Hamburger menu appears, nav links hidden
- Click hamburger opens mobile menu
- Clicking a mobile link closes menu and scrolls to section
- All sections stack vertically and remain readable
- Form inputs are full-width

- [ ] **Step 3: Final commit (if any fixes needed)**

If any issues found, fix and commit:

```bash
git add index.html
git commit -m "fix: responsive layout and interaction polish"
```

---

## Notes

- Replace `YOUR_FORMSPREE_ID` in the contact form action with your actual Formspree form ID after signing up at [formspree.io](https://formspree.io).
- Replace `👤` emoji and "홍길동" placeholder text with real name and profile image.
- Career entries are placeholder data — update with real experience.
