# ArchSpace Design - Developer Quick Reference

## 🎯 QUICK NAVIGATION

### **Key Sections to Know**

```html
<!-- NAVIGATION BAR (Line ~690) -->
<nav class="navbar navbar-expand-lg">

<!-- HERO SECTION (Line ~705) -->
<section class="hero">

<!-- ABOUT SECTION (Line ~735) -->
<section id="about" class="section-padding">

<!-- SERVICES SECTION (Line ~775) -->
<section id="services" class="section-padding">

<!-- PROJECTS SECTION (Line ~870) -->
<section id="projects" class="section-padding">

<!-- CTA SECTION (Line ~925) -->
<section id="cta" class="section-padding">

<!-- CONTACT SECTION (Line ~945) -->
<section id="contact" class="section-padding">

<!-- FOOTER (Line ~985) -->
<footer>

<!-- JAVASCRIPT (Line ~1010+) -->
<script>
```

---

## 🎨 CSS VARIABLES TO CUSTOMIZE

```css
:root {
  --dark-navy: #0f172a;         /* Main background */
  --dark-charcoal: #1a202c;     /* Dark accent */
  --steel-blue: #38bdf8;        /* Primary color */
  --cyan-accent: #06b6d4;       /* Secondary color */
  --white: #ffffff;             /* Text/surfaces */
  --light-gray: #f1f5f9;        /* Light background */
  --medium-gray: #94a3b8;       /* Secondary text */
  --border-light: #e2e8f0;      /* Borders */
  --text-dark: #1e293b;         /* Text color */
  
  /* Shadows */
  --shadow-soft: 0 10px 40px rgba(15, 23, 42, 0.15);
  --shadow-medium: 0 20px 60px rgba(15, 23, 42, 0.25);
  --shadow-deep: 0 30px 80px rgba(15, 23, 42, 0.35);
  
  /* Transitions */
  --transition-smooth: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --transition-bounce: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

---

## 🎬 ANIMATION TIMING REFERENCE

### **Hero Section** (Lines ~200-235)
```css
.hero h1 {
  animation: fade-up-hero 1s ease-out 0.2s forwards;
}

.hero-subtitle {
  animation: fade-up-hero 1s ease-out 0.4s forwards;
}

.hero-cta {
  animation: fade-up-hero 1s ease-out 0.6s forwards;
}

@keyframes fade-up-hero {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
```

### **Service Cards** (Lines ~420-430)
```css
.service-card:nth-child(1) { animation-delay: 0.1s; }
.service-card:nth-child(2) { animation-delay: 0.3s; }
.service-card:nth-child(3) { animation-delay: 0.5s; }
.service-card:nth-child(4) { animation-delay: 0.7s; }
.service-card:nth-child(5) { animation-delay: 0.9s; }
.service-card:nth-child(6) { animation-delay: 1.1s; }
```

### **3D Hover Effects** (Lines ~440-460)
```css
.service-card:hover {
  transform: translateY(-15px) rotateX(5deg) rotateY(-2deg);
  box-shadow: var(--shadow-deep);
  border-color: var(--steel-blue);
}
```

---

## 📱 RESPONSIVE BREAKPOINTS

```css
/* Large Desktop - No changes needed */
/* Default styling applies */

/* Tablet - max-width: 768px */
@media (max-width: 768px) {
  .hero { margin-top: 60px; }
  .about-image { height: 300px; }
  .contact-form { padding: 2rem; }
  .projects-grid { grid-template-columns: 1fr; }
}

/* Mobile - max-width: 576px */
@media (max-width: 576px) {
  .hero h1 { font-size: 2rem; }
  h2 { font-size: 1.5rem; }
  .service-card { padding: 1.5rem 1rem; }
}
```

---

## 🔧 JAVASCRIPT FUNCTIONS REFERENCE

### **1. Navbar Scroll Effect**
```javascript
const navbar = document.querySelector('.navbar');
window.addEventListener('scroll', () => {
  if (window.scrollY > 100) {
    navbar.classList.add('scrolled');
  } else {
    navbar.classList.remove('scrolled');
  }
});
// Trigger at 100px scroll, adds 'scrolled' class
```

### **2. 3D Mouse Tilt (About Image)**
```javascript
const aboutImage = document.querySelector('.about-image');
aboutImage.addEventListener('mousemove', (e) => {
  const rect = aboutImage.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  const centerX = rect.width / 2;
  const centerY = rect.height / 2;
  const rotateX = (y - centerY) / 10;
  const rotateY = (centerX - x) / 10;
  aboutImage.style.transform = 
    `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.02)`;
});
```

### **3. Intersection Observer**
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -100px 0px' });
```

### **4. Form Validation**
```javascript
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
if (!emailRegex.test(email)) {
  alert('Please enter a valid email address.');
  return;
}
```

### **5. Parallax Scrolling**
```javascript
window.addEventListener('scroll', () => {
  const scrollPosition = window.scrollY;
  hero.style.backgroundPosition = `center ${scrollPosition * 0.5}px`;
});
// Background moves at 50% of scroll speed
```

---

## 🎨 COLOR USAGE GUIDE

### **Where Each Color is Used**

**Steel Blue (#38bdf8)**
- Primary buttons
- Service icons
- Nav link underlines
- Accents and highlights
- Gradient text

**Cyan Accent (#06b6d4)**
- Gradient secondary color
- Icon hover state
- CTA section accents

**Dark Navy (#0f172a)**
- Background
- Navbar default
- CTA section
- Footer
- Text on light backgrounds

**Light Gray (#f1f5f9)**
- About section background
- Form input backgrounds
- Projects section background
- Light accents

**Medium Gray (#94a3b8)**
- Secondary text
- Placeholder text
- Footer text
- Subtle elements

---

## 📏 SPACING SCALE

```
XS: 0.5rem (8px)
S:  1rem (16px)
M:  1.5rem (24px)
L:  2rem (32px)
XL: 2.5rem (40px)
2XL: 3rem (48px)

Section Padding: 100px (desktop), 60px (tablet), 50px (mobile)
Card Padding: 2.5rem
Gap (grid): 2rem
```

---

## 🎯 HOVER EFFECT TIMING

| Element | Duration | Easing | Transform |
|---------|----------|--------|-----------|
| Nav Link | 0.3s | ease | gradient underline |
| Service Card | 0.4s | smooth | lift + 3D |
| Service Icon | 0.5s | bounce | scale + rotate |
| Project Card | 0.4s | smooth | 3D tilt |
| Button | 0.6s | smooth | ripple + lift |
| Form Input | varies | smooth | scale |
| Image Tilt | instant | none | perspective |

---

## 🚀 PERFORMANCE TIPS

### **What NOT to Do**
- ❌ Add more JavaScript libraries
- ❌ Use heavy frameworks
- ❌ Add auto-playing videos
- ❌ Load unoptimized images
- ❌ Add too many animations
- ❌ Use block-rendering animations

### **What TO Do**
- ✅ Keep CSS-based animations
- ✅ Use transform and opacity
- ✅ Optimize images (compress, webp)
- ✅ Lazy load below-fold images
- ✅ Minify CSS and JS
- ✅ Use CDN for assets

---

## 🔗 IMPORTANT CLASSES & IDs

### **Navigation Elements**
- `.navbar` - Main navigation bar
- `.scrolled` - Added when scrolling
- `.nav-link` - Individual nav links
- `.navbar-brand` - Logo/branding

### **Sections**
- `.hero` - Hero section
- `#about` - About section
- `#services` - Services section
- `#projects` - Projects section
- `#cta` - Call to action
- `#contact` - Contact section

### **Cards & Elements**
- `.service-card` - Service cards
- `.project-card` - Project cards
- `.about-image` - About image with 3D effect
- `.contact-form` - Contact form
- `.form-control` - Form inputs

### **Animations**
- `.scroll-fade` - Scroll animation class
- `.visible` - Added when visible

---

## 📝 COMMON MODIFICATIONS

### **Change Button Text**
```html
<!-- Find and replace -->
Get Consultation
Start Your Project
Send Message
```

### **Add Another Service**
```html
<!-- Copy this block and change content -->
<div class="col-md-6 col-lg-4">
  <div class="service-card">
    <div class="service-card-content">
      <div class="service-icon">
        <i class="bi bi-ICON-NAME"></i>
      </div>
      <h5>Service Name</h5>
      <p>Description here</p>
    </div>
  </div>
</div>
```

### **Add Another Project**
```html
<!-- Copy this block and change content -->
<div class="project-card">
  <img src="IMAGE-URL" alt="Description" class="project-image">
  <div class="project-overlay">
    <div class="project-info">
      <h6>Project Title</h6>
      <p>Project Type</p>
    </div>
  </div>
</div>
```

### **Update Contact Info**
```html
<!-- Find and update -->
Solan, Himachal Pradesh
<!-- Add your location, phone, email as needed -->
```

---

## 🎓 LEARNING RESOURCES

### **Animation Tutorials**
- [CSS Tricks: Animations](https://css-tricks.com/almanac/properties/a/animation/)
- [MDN: Transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)
- [Easing Functions](https://easings.net/)

### **3D CSS**
- [MDN: 3D Transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms)
- [CSS Perspective](https://developer.mozilla.org/en-US/docs/Web/CSS/perspective)

### **JavaScript**
- [MDN: Event Listeners](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- [Intersection Observer](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)

### **Bootstrap**
- [Bootstrap 5 Documentation](https://getbootstrap.com/docs/5.3/)
- [Bootstrap Grid System](https://getbootstrap.com/docs/5.3/layout/grid/)

---

## ✅ CHECKLIST BEFORE DEPLOYMENT

- [ ] Update all company information
- [ ] Replace images with your own
- [ ] Update phone number and email
- [ ] Check form validation works
- [ ] Test on mobile devices
- [ ] Verify all links work
- [ ] Check console for errors
- [ ] Set up backend for form submission
- [ ] Add Google Analytics
- [ ] Set up SSL certificate (HTTPS)
- [ ] Test in multiple browsers
- [ ] Optimize images
- [ ] Set up email notifications

---

## 🐛 DEBUGGING TIPS

### **Check Browser Console**
```javascript
// Open DevTools (F12 or Ctrl+Shift+I)
// Go to Console tab
// Check for any red errors
// Use console.log() for debugging
```

### **Common Issues**
| Issue | Solution |
|-------|----------|
| Animations not working | Check browser support, enable JS |
| Images not showing | Verify URLs, check console |
| Form not submitting | Check validation, browser console |
| Mobile menu not working | Check Bootstrap JS loaded |
| 3D effects not visible | Check browser compatibility |

---

## 📞 QUICK CONTACT

For detailed information, refer to:
- **TRANSFORMATION_SUMMARY.md** - Project overview
- **FEATURES.md** - Complete feature list
- **README.md** - Getting started guide
- **This file** - Quick reference

---

**Last Updated**: January 16, 2026
**Status**: Production Ready ✅
**Version**: 1.0 Premium Edition

*Build with confidence. Deploy with pride.* 🚀
