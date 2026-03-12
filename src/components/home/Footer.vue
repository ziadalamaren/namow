<template>
  <footer class="site-footer" dir="rtl" ref="footerRef">

    <!-- Background -->
    <div class="footer-bg"></div>
    <div class="footer-mesh"></div>
    <div class="footer-orb"></div>

    <!-- Top wave -->
    <div class="top-wave">
      <svg viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
        <path d="M0,40 C360,80 720,0 1080,40 C1260,60 1380,30 1440,20 L1440,0 L0,0 Z" fill="#F5F6FA"/>
      </svg>
    </div>
    <!-- dark mode wave -->
    <div class="top-wave top-wave-dark">
      <svg viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
        <path d="M0,40 C360,80 720,0 1080,40 C1260,60 1380,30 1440,20 L1440,0 L0,0 Z" fill="#0d1526"/>
      </svg>
    </div>

    <div class="container">

      <!-- Main footer grid -->
      <div class="footer-grid" :class="{ visible: visible }">

        <!-- Brand column -->
        <div class="brand-col">
          <div class="brand-logo">
            <span class="logo-mark">N</span>
            <span class="logo-name">نمو</span>
            <span class="logo-dot"></span>
          </div>
          <p class="brand-tagline">
            نصمم مواقع إلكترونية احترافية وندير محتواها، لتوفر وقتك وتركز على نجاح مشروعك.
          </p>
          <!-- Social links -->
          <div class="socials">
            <a v-for="s in socials" :key="s.name" :href="s.href" class="social-btn" :title="s.name">
              <span v-html="s.icon"></span>
            </a>
          </div>
        </div>

        <!-- Links columns -->
        <div class="links-col">
          <h5 class="col-title">الخدمات</h5>
          <ul>
            <li v-for="l in serviceLinks" :key="l"><a :href="l.href" class="footer-link">{{ l.label }}</a></li>
          </ul>
        </div>

        <div class="links-col">
          <h5 class="col-title">الشركة</h5>
          <ul>
            <li v-for="l in companyLinks" :key="l"><a :href="l.href" class="footer-link">{{ l.label }}</a></li>
          </ul>
        </div>

        <!-- Contact column -->
        <div class="contact-col">
          <h5 class="col-title">تواصل معنا</h5>
          <a href="mailto:zeadamaren24@gmail.com" class="contact-item">
            <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/>
            </svg>
            zeadamaren24@gmail.com
          </a>
          <a href="tel:+962777210884" class="contact-item">
            <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.41 2 2 0 0 1 3.6 1.22h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L7.91 8.8a16 16 0 0 0 6.29 6.29l.96-.96a2 2 0 0 1 2.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92z"/>
            </svg>
            +962777210884
          </a>
        </div>

      </div>

      <!-- Divider -->
      <div class="divider" :class="{ visible: visible }">
        <span class="divider-glow"></span>
      </div>

      <!-- Bottom bar -->
      <div class="bottom-bar" :class="{ visible: visible }">
        <p class="copyright">© 2026 نمو - جميع الحقوق محفوظة.</p>
        <div class="legal-links">
          <a href="#" class="legal-link">سياسة الخصوصية</a>
          <span class="sep">·</span>
          <a href="#" class="legal-link">الشروط والأحكام</a>
        </div>
        <div class="made-with">
          صُنع بـ
          <svg xmlns="http://www.w3.org/2000/svg" width="13" height="13" viewBox="0 0 24 24" fill="#00B894" stroke="none">
            <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
          </svg>
          في المملكة العربية السعودية
        </div>
      </div>

    </div>

  </footer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const footerRef = ref(null);
const visible = ref(false);

let observer;
onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) visible.value = true; },
    { threshold: 0.1 }
  );
  if (footerRef.value) observer.observe(footerRef.value);
});
onUnmounted(() => observer?.disconnect());

const socials = [
  {
    name: "X",
    href: "#",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.73-8.835L2.18 2.25h6.963l4.259 5.631zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>`
  },
  {
    name: "Instagram",
    href: "#",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/></svg>`
  },
  {
    name: "LinkedIn",
    href: "#",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg>`
  }
];

const serviceLinks = [
  { label: "مواقع تعريفية", href: "#services" },
  { label: "متاجر إلكترونية", href: "#services" },
  { label: "هوية بصرية", href: "#services" },
  { label: "تطبيقات الجوال", href: "#services" }
];

const companyLinks = [
  { label: "من نحن", href: "#why" },
  { label: "أعمالنا", href: "#features" },
  { label: "المدونة", href: "#" },
  { label: "تواصل معنا", href: "#contact" }
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

.site-footer {
  font-family: 'Tajawal', sans-serif;
  position: relative;
  padding: 5rem 0 3rem;
  overflow: hidden;
  color: rgba(255,255,255,0.75);
}

/* ── Background ── */
.footer-bg {
  position: absolute;
  inset: 0;
  background: linear-gradient(160deg, #1A2B4C 0%, #0d1728 60%, #1a2440 100%);
}
.footer-mesh {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(0,184,148,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,184,148,0.04) 1px, transparent 1px);
  background-size: 44px 44px;
}
.footer-orb {
  position: absolute;
  width: 600px; height: 400px;
  bottom: -200px; right: -100px;
  border-radius: 50%;
  background: radial-gradient(ellipse, rgba(0,184,148,0.1), transparent 65%);
  filter: blur(60px);
  pointer-events: none;
  animation: orbPulse 8s ease-in-out infinite;
}
@keyframes orbPulse {
  0%,100% { transform: scale(1); opacity: 0.7; }
  50%      { transform: scale(1.15); opacity: 1; }
}

/* Wave */
.top-wave {
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 80px;
  pointer-events: none;
}
.top-wave svg { width: 100%; height: 100%; }
.top-wave-dark { display: none; }
.dark .top-wave:not(.top-wave-dark) { display: none; }
.dark .top-wave-dark { display: block; }

/* ── Container ── */
.container {
  position: relative;
  z-index: 2;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* ── Footer grid ── */
.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1.5fr;
  gap: 3rem;
  padding-top: 2rem;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.9s cubic-bezier(0.16,1,0.3,1), transform 0.9s cubic-bezier(0.16,1,0.3,1);
}
.footer-grid.visible { opacity: 1; transform: translateY(0); }
@media (max-width: 900px) {
  .footer-grid { grid-template-columns: 1fr 1fr; gap: 2rem; }
}
@media (max-width: 560px) {
  .footer-grid { grid-template-columns: 1fr; }
}

/* ── Brand col ── */
.brand-logo {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  margin-bottom: 1.1rem;
}
.logo-mark {
  width: 36px; height: 36px;
  background: linear-gradient(135deg, #00B894, #55E6C1);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: 900;
  font-size: 1.1rem;
  box-shadow: 0 4px 14px rgba(0,184,148,0.35);
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.brand-logo:hover .logo-mark { transform: rotate(-8deg) scale(1.1); }
.logo-name {
  font-size: 1.4rem;
  font-weight: 900;
  color: white;
  letter-spacing: -0.5px;
}
.logo-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: #00B894;
  margin-bottom: 14px;
  animation: dotPulse 2.5s ease-in-out infinite;
}
@keyframes dotPulse {
  0%,100% { transform: scale(1); opacity: 1; }
  50%      { transform: scale(1.6); opacity: 0.5; }
}

.brand-tagline {
  font-size: 0.88rem;
  color: rgba(255,255,255,0.45);
  line-height: 1.75;
  max-width: 260px;
  margin-bottom: 1.5rem;
}

.socials {
  display: flex;
  gap: 0.6rem;
}
.social-btn {
  width: 36px; height: 36px;
  border-radius: 9px;
  border: 1px solid rgba(255,255,255,0.1);
  background: rgba(255,255,255,0.05);
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgba(255,255,255,0.55);
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.social-btn:hover {
  background: rgba(0,184,148,0.15);
  border-color: rgba(0,184,148,0.4);
  color: #00B894;
  transform: translateY(-3px) scale(1.08);
}

/* ── Links cols ── */
.col-title {
  font-size: 0.82rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  color: rgba(255,255,255,0.4);
  text-transform: uppercase;
  margin-bottom: 1.25rem;
}
ul { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.6rem; }

.footer-link {
  font-size: 0.9rem;
  color: rgba(255,255,255,0.55);
  text-decoration: none;
  transition: color 0.25s, transform 0.25s;
  display: inline-block;
  position: relative;
}
.footer-link::after {
  content: '';
  position: absolute;
  bottom: -1px;
  right: 0; left: 0;
  height: 1px;
  background: #00B894;
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.3s cubic-bezier(0.16,1,0.3,1);
}
.footer-link:hover { color: white; transform: translateX(-4px); }
.footer-link:hover::after { transform: scaleX(1); }

/* ── Contact col ── */
.contact-item {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.88rem;
  color: rgba(255,255,255,0.55);
  text-decoration: none;
  margin-bottom: 0.85rem;
  transition: color 0.25s, transform 0.25s;
}
.contact-item:hover { color: #55E6C1; transform: translateX(-4px); }
.contact-item svg { color: #00B894; flex-shrink: 0; }

/* ── Divider ── */
.divider {
  position: relative;
  height: 1px;
  background: rgba(255,255,255,0.07);
  margin: 3rem 0 1.75rem;
  opacity: 0;
  transition: opacity 1s 0.4s;
}
.divider.visible { opacity: 1; }
.divider-glow {
  position: absolute;
  top: 0; left: 20%; right: 20%;
  height: 1px;
  background: linear-gradient(90deg, transparent, #00B894, transparent);
  animation: glowSlide 4s ease-in-out infinite;
}
@keyframes glowSlide {
  0%   { left: 0%; right: 80%; opacity: 0; }
  20%  { opacity: 1; }
  80%  { opacity: 1; }
  100% { left: 80%; right: 0%; opacity: 0; }
}

/* ── Bottom bar ── */
.bottom-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
  opacity: 0;
  transform: translateY(12px);
  transition: opacity 0.7s 0.6s cubic-bezier(0.16,1,0.3,1), transform 0.7s 0.6s cubic-bezier(0.16,1,0.3,1);
}
.bottom-bar.visible { opacity: 1; transform: translateY(0); }

.copyright {
  font-size: 0.82rem;
  color: rgba(255,255,255,0.35);
}

.legal-links {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}
.legal-link {
  font-size: 0.82rem;
  color: rgba(255,255,255,0.4);
  text-decoration: none;
  transition: color 0.25s;
}
.legal-link:hover { color: #00B894; }
.sep { color: rgba(255,255,255,0.2); }

.made-with {
  display: flex;
  align-items: center;
  gap: 0.35rem;
  font-size: 0.8rem;
  color: rgba(255,255,255,0.3);
}
.made-with svg { animation: heartBeat 2s ease-in-out infinite; }
@keyframes heartBeat {
  0%,100% { transform: scale(1); }
  14%      { transform: scale(1.3); }
  28%      { transform: scale(1); }
  42%      { transform: scale(1.2); }
  70%      { transform: scale(1); }
}
</style>