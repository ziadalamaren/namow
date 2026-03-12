<template>
  <section class="cta-strip" ref="elRef">
    <div class="cta-bg"></div>
    <div class="cta-beam"></div>

    <div class="cta-container" :class="{ visible }">
      <div class="cta-text-side">
        <h2 class="cta-title">جاهز تبدأ<br>معنا؟</h2>
        <p class="cta-desc">احجز استشارة مجانية وسنساعدك على رسم خارطة طريق حضورك الرقمي.</p>
      </div>
      <div class="cta-action-side">
        <a href="/contact" class="cta-btn-primary">
          <span class="cta-btn-fill"></span>
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24"
            fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.41 2 2 0 0 1 3.6 1.22h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L7.91 8.8a16 16 0 0 0 6.29 6.29l.96-.96a2 2 0 0 1 2.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92z"/>
          </svg>
          اطلب استشارة مجانية
        </a>
        <a href="/" class="cta-btn-ghost">العودة للرئيسية</a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useReveal } from "@/composables/useReveal";
const { elRef, visible } = useReveal(0.12);
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

.cta-strip {
  font-family: 'Tajawal', sans-serif;
  position: relative; padding: 6rem 0;
  overflow: hidden; background: #F5F6FA;
  color: #1A2B4C;
}
.cta-bg {
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,184,148,0.06), rgba(85,230,193,0.03));
  border-top: 1px solid rgba(0,184,148,0.1);
  border-bottom: 1px solid rgba(0,184,148,0.1);
}
.cta-beam {
  position: absolute; top: 0; bottom: 0; width: 160px;
  background: linear-gradient(90deg, transparent, rgba(0,184,148,0.06), transparent);
  animation: beamMove 10s ease-in-out infinite;
}
@keyframes beamMove { 0%{left:-200px;} 100%{left:110%;} }

.cta-container {
  position: relative; z-index: 1;
  max-width: 1100px; margin: 0 auto; padding: 0 2rem;
  display: flex; align-items: center;
  justify-content: space-between;
  gap: 3rem; flex-wrap: wrap;
  opacity: 0; transform: translateY(24px);
  transition: opacity 0.8s cubic-bezier(0.16,1,0.3,1), transform 0.8s cubic-bezier(0.16,1,0.3,1);
}
.cta-container.visible { opacity: 1; transform: translateY(0); }

.cta-title {
  font-size: clamp(2rem, 4vw, 2.8rem); font-weight: 900;
  color: #1A2B4C; letter-spacing: -1px; line-height: 1.15; margin-bottom: 0.75rem;
}
.cta-desc { font-size: 1rem; color: #5a6a85; max-width: 420px; line-height: 1.75; }

.cta-action-side {
  display: flex; gap: 0.9rem; flex-wrap: wrap; align-items: center;
}

.cta-btn-primary {
  position: relative;
  display: inline-flex; align-items: center; gap: 0.55rem;
  background: #00B894; color: white;
  padding: 0.9rem 1.8rem; border-radius: 14px;
  font-family: 'Tajawal', sans-serif; font-size: 0.98rem; font-weight: 700;
  text-decoration: none; overflow: hidden;
  box-shadow: 0 8px 28px rgba(0,184,148,0.3);
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
}
.cta-btn-primary:hover {
  transform: translateY(-4px) scale(1.03);
  box-shadow: 0 14px 40px rgba(0,184,148,0.45);
}
.cta-btn-fill {
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(255,255,255,0.15), transparent);
  transform: translateX(-100%); transition: transform 0.4s; border-radius: inherit;
}
.cta-btn-primary:hover .cta-btn-fill { transform: translateX(0); }

.cta-btn-ghost {
  display: inline-flex; align-items: center; gap: 0.5rem;
  background: transparent; color: #1A2B4C;
  padding: 0.9rem 1.6rem; border-radius: 14px;
  border: 1.5px solid rgba(26,43,76,0.15);
  font-family: 'Tajawal', sans-serif; font-size: 0.95rem; font-weight: 600;
  text-decoration: none;
  transition: background 0.3s, border-color 0.3s, transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.cta-btn-ghost:hover {
  background: rgba(26,43,76,0.05); border-color: rgba(26,43,76,0.3);
  transform: translateY(-3px);
}
</style>