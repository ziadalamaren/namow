<template>
  <section id="contact" class="contact-section" dir="rtl" ref="sectionRef">

    <!-- Animated mesh background -->
    <div class="mesh"></div>

    <!-- Floating rings -->
    <div class="ring ring-1"></div>
    <div class="ring ring-2"></div>
    <div class="ring ring-3"></div>

    <!-- Floating particles -->
    <div class="particles">
      <span v-for="n in 12" :key="n" class="particle" :style="particleStyle(n)"></span>
    </div>

    <!-- Traveling beam -->
    <div class="beam beam-1"></div>
    <div class="beam beam-2"></div>

    <div class="container">

      <!-- Badge -->
      <div class="badge" :class="{ visible: visible }">
        <span class="badge-dot"></span>
        نبدأ معك الآن
      </div>

      <!-- Headline -->
      <h2 class="headline" :class="{ visible: visible }">
        <span class="line-1">جاهز لتطوير</span>
        <span class="line-2">موقعك؟ <em>ابدأ الآن</em></span>
      </h2>

      <!-- Subtext -->
      <p class="subtext" :class="{ visible: visible }">
        تواصل معنا اليوم واحصل على استشارة مجانية لمعرفة كيف يمكننا تطوير حضورك الرقمي.
      </p>

      <!-- CTA buttons -->
      <div class="cta-group" :class="{ visible: visible }">
        <button class="btn-primary" @mouseenter="btnHover = true" @mouseleave="btnHover = false" @click="goToContact"> 
          <span class="btn-fill"></span>
          <span class="btn-content">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.41 2 2 0 0 1 3.6 1.22h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 8.8a16 16 0 0 0 6.29 6.29l.96-.96a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/>
            </svg>
            احجز استشارة مجانية
          </span>
          <span class="btn-arrow">←</span>
        </button>

        <button class="btn-ghost" @click="goToContact">
          <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>
          </svg>
          تحدث مع فريقنا
        </button>
      </div>

      <!-- Trust signals -->
      <div class="trust-row" :class="{ visible: visible }">
        <div v-for="(t, i) in trust" :key="i" class="trust-item" :style="{ transitionDelay: `${i * 100 + 700}ms` }">
          <span class="trust-icon" v-html="t.icon"></span>
          <span>{{ t.text }}</span>
        </div>
      </div>

    </div>

    <!-- Bottom wave -->
    <div class="bottom-wave">
      <svg viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
        <path d="M0,40 C240,80 480,0 720,40 C960,80 1200,0 1440,40 L1440,80 L0,80 Z" fill="rgba(255,255,255,0.06)"/>
      </svg>
    </div>

  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { useRouter } from "vue-router";

const sectionRef = ref(null);
const visible = ref(false);
const btnHover = ref(false);
const router = useRouter();

function goToContact() {
  router.push("/contact");
}
function particleStyle(n) {
  const size = Math.random() * 6 + 3;
  const left = (n / 12) * 100;
  const duration = 4 + (n % 4) * 2;
  const delay = (n % 6) * 0.8;
  return {
    width: `${size}px`,
    height: `${size}px`,
    left: `${left}%`,
    animationDuration: `${duration}s`,
    animationDelay: `${delay}s`,
    opacity: 0.15 + (n % 4) * 0.1
  };
}

let observer;
onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) visible.value = true; },
    { threshold: 0.2 }
  );
  if (sectionRef.value) observer.observe(sectionRef.value);
});
onUnmounted(() => observer?.disconnect());

const trust = [
  {
    text: "استشارة مجانية 100%",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/></svg>`
  },
  {
    text: "رد خلال 24 ساعة",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>`
  },
  {
    text: "+120 مشروع ناجح",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`
  }
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

.contact-section {
  font-family: 'Tajawal', sans-serif;
  position: relative;
  padding: 9rem 0 8rem;
  background: linear-gradient(135deg, #00B894 0%, #00a381 40%, #2C3E6B 100%);
  overflow: hidden;
  color: white;
  text-align: center;
}

/* ── Mesh background ── */
.mesh {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255,255,255,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.04) 1px, transparent 1px);
  background-size: 44px 44px;
  animation: meshDrift 25s linear infinite;
}
@keyframes meshDrift {
  from { background-position: 0 0; }
  to   { background-position: 44px 44px; }
}

/* ── Rings ── */
.ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid rgba(255,255,255,0.12);
  pointer-events: none;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) scale(0);
  animation: ringExpand 6s ease-out infinite;
}
.ring-1 { width: 400px; height: 400px; animation-delay: 0s; }
.ring-2 { width: 650px; height: 650px; animation-delay: 2s; }
.ring-3 { width: 900px; height: 900px; animation-delay: 4s; }

@keyframes ringExpand {
  0%   { transform: translate(-50%, -50%) scale(0.3); opacity: 0.6; }
  100% { transform: translate(-50%, -50%) scale(1);   opacity: 0; }
}

/* ── Particles ── */
.particles {
  position: absolute;
  inset: 0;
  pointer-events: none;
}
.particle {
  position: absolute;
  bottom: -10px;
  border-radius: 50%;
  background: white;
  animation: particleRise linear infinite;
}
@keyframes particleRise {
  0%   { transform: translateY(0) scale(1); opacity: 0.2; }
  50%  { opacity: 0.6; }
  100% { transform: translateY(-100vh) scale(0.3); opacity: 0; }
}

/* ── Beams ── */
.beam {
  position: absolute;
  top: 0; bottom: 0;
  width: 150px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.06), transparent);
  pointer-events: none;
}
.beam-1 { animation: beamMove 10s ease-in-out infinite; }
.beam-2 { animation: beamMove 10s ease-in-out infinite 5s; }
@keyframes beamMove {
  0%   { left: -200px; }
  100% { left: 110%; }
}

/* ── Container ── */
.container {
  position: relative;
  z-index: 2;
  max-width: 780px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* ── Badge ── */
.badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(255,255,255,0.15);
  border: 1px solid rgba(255,255,255,0.25);
  backdrop-filter: blur(8px);
  color: white;
  font-size: 0.82rem;
  font-weight: 600;
  padding: 0.35rem 1rem;
  border-radius: 100px;
  margin-bottom: 2rem;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.7s cubic-bezier(0.16,1,0.3,1), transform 0.7s cubic-bezier(0.16,1,0.3,1);
}
.badge.visible { opacity: 1; transform: translateY(0); }

.badge-dot {
  width: 7px; height: 7px;
  border-radius: 50%;
  background: white;
  animation: dotPulse 2s ease-in-out infinite;
}
@keyframes dotPulse {
  0%,100% { transform: scale(1); opacity: 1; }
  50%      { transform: scale(1.5); opacity: 0.5; }
}

/* ── Headline ── */
.headline {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: clamp(2.8rem, 7vw, 5rem);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -2px;
  margin-bottom: 1.5rem;
  opacity: 0;
  transform: translateY(32px);
  transition: opacity 0.8s 0.1s cubic-bezier(0.16,1,0.3,1), transform 0.8s 0.1s cubic-bezier(0.16,1,0.3,1);
}
.headline.visible { opacity: 1; transform: translateY(0); }

.line-1 { color: rgba(255,255,255,0.75); }
.line-2 { color: white; }

.headline em {
  font-style: normal;
  position: relative;
  display: inline-block;
}
.headline em::after {
  content: '';
  position: absolute;
  bottom: 4px;
  left: 0; right: 0;
  height: 4px;
  border-radius: 4px;
  background: rgba(255,255,255,0.4);
  animation: underlineGrow 1.2s 1s cubic-bezier(0.16,1,0.3,1) both;
  transform-origin: right;
}
@keyframes underlineGrow {
  from { transform: scaleX(0); }
  to   { transform: scaleX(1); }
}

/* ── Subtext ── */
.subtext {
  font-size: 1.1rem;
  color: rgba(255,255,255,0.75);
  line-height: 1.75;
  max-width: 480px;
  margin: 0 auto 2.5rem;
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s 0.25s cubic-bezier(0.16,1,0.3,1), transform 0.7s 0.25s cubic-bezier(0.16,1,0.3,1);
}
.subtext.visible { opacity: 1; transform: translateY(0); }

/* ── CTA group ── */
.cta-group {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 2.5rem;
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s 0.4s cubic-bezier(0.16,1,0.3,1), transform 0.7s 0.4s cubic-bezier(0.16,1,0.3,1);
}
.cta-group.visible { opacity: 1; transform: translateY(0); }

/* Primary button */
.btn-primary {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  background: white;
  color: #00B894;
  border: none;
  padding: 0.9rem 2rem;
  border-radius: 14px;
  font-family: 'Tajawal', sans-serif;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  overflow: hidden;
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
  box-shadow: 0 8px 30px rgba(0,0,0,0.2);
}
.btn-primary:hover {
  transform: translateY(-4px) scale(1.03);
  box-shadow: 0 16px 40px rgba(0,0,0,0.25);
}
.btn-fill {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, #f0fdf8, #dcfdf2);
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
  border-radius: inherit;
}
.btn-primary:hover .btn-fill { transform: scaleX(1); }
.btn-content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.btn-arrow {
  position: relative;
  z-index: 1;
  font-size: 1rem;
  transition: transform 0.3s;
}
.btn-primary:hover .btn-arrow { transform: translateX(-4px); }

/* Ghost button */
.btn-ghost {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(255,255,255,0.12);
  border: 1.5px solid rgba(255,255,255,0.3);
  color: white;
  padding: 0.9rem 1.75rem;
  border-radius: 14px;
  font-family: 'Tajawal', sans-serif;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  backdrop-filter: blur(8px);
  transition: background 0.3s, border-color 0.3s, transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.btn-ghost:hover {
  background: rgba(255,255,255,0.2);
  border-color: rgba(255,255,255,0.5);
  transform: translateY(-4px);
}

/* ── Trust row ── */
.trust-row {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  flex-wrap: wrap;
  opacity: 0;
  transform: translateY(16px);
  transition: opacity 0.7s 0.55s cubic-bezier(0.16,1,0.3,1), transform 0.7s 0.55s cubic-bezier(0.16,1,0.3,1);
}
.trust-row.visible { opacity: 1; transform: translateY(0); }

.trust-item {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.82rem;
  color: rgba(255,255,255,0.8);
  font-weight: 500;
  opacity: 0;
  transform: translateY(8px);
  transition: opacity 0.5s, transform 0.5s cubic-bezier(0.16,1,0.3,1);
}
.trust-row.visible .trust-item {
  opacity: 1;
  transform: translateY(0);
}
.trust-icon {
  display: flex;
  align-items: center;
  color: rgba(255,255,255,0.9);
}

/* Dividers between trust items */
.trust-item:not(:last-child)::after {
  content: '·';
  margin-right: -1.3rem;
  opacity: 0.4;
  margin-left: 0.7rem;
}

/* ── Bottom wave ── */
.bottom-wave {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  height: 80px;
  pointer-events: none;
}
.bottom-wave svg {
  width: 100%; height: 100%;
}
</style>