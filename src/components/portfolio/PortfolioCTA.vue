<template>
  <section class="pc-section" dir="rtl" ref="elRef">
    <div class="pc-bg"></div>
    <div class="pc-grid-lines"></div>
    <div class="pc-orb-l"></div>
    <div class="pc-orb-r"></div>
    <div class="pc-beam"></div>

    <div class="pc-container" :class="{ visible }">

      <div class="pc-text-col">
        <div class="pc-label">هل أعجبك ما شاهدت؟</div>
        <h2 class="pc-title">
          مشروعك القادم<br>
          <span class="pc-title-green">يبدأ من هنا</span>
        </h2>
        <p class="pc-desc">
          تواصل معنا اليوم واحصل على استشارة مجانية.
          سنناقش فكرتك ونرسم معك خارطة طريق واضحة لحضورك الرقمي.
        </p>

        <!-- Trust row -->
        <div class="pc-trust">
          <div v-for="t in trust" :key="t.text" class="pc-trust-item">
            <span class="pc-trust-icon">{{ t.icon }}</span>
            {{ t.text }}
          </div>
        </div>
      </div>

      <div class="pc-action-col">
        <!-- CTA card -->
        <div class="pc-card">
          <div class="pc-card-header">
            <div class="pc-card-title">ابدأ مشروعك</div>
            <div class="pc-card-badge">مجاني ١٠٠٪</div>
          </div>
          <p class="pc-card-desc">لا تحتاج بيانات بنكية. فقط أخبرنا عن فكرتك.</p>
          <RouterLink to="/contact" class="pc-btn-primary">
            <span class="pc-btn-fill"></span>
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.41 2 2 0 0 1 3.6 1.22h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L7.91 8.8a16 16 0 0 0 6.29 6.29l.96-.96a2 2 0 0 1 2.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92z"/>
            </svg>
            اطلب استشارة مجانية
          </RouterLink>
          <RouterLink to="/services" class="pc-btn-ghost">
            تعرف على خدماتنا أولاً
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </RouterLink>

          <!-- Divider -->
          <div class="pc-divider"><span>أو</span></div>

          <!-- Quick contact info -->
          <div class="pc-quick-contact">
            <a href="https://wa.me/962777210884" target="_blank" rel="noopener" class="pc-contact-item">
              <div class="pc-contact-icon green">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.127.558 4.122 1.533 5.855L0 24l6.335-1.521A11.945 11.945 0 0 0 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.803 9.803 0 0 1-5.034-1.388l-.36-.214-3.735.897.934-3.617-.235-.375A9.79 9.79 0 0 1 2.182 12c0-5.42 4.398-9.818 9.818-9.818 5.42 0 9.818 4.398 9.818 9.818 0 5.42-4.398 9.818-9.818 9.818z"/></svg>
              </div>
              <div class="pc-contact-text">
                <span class="pc-contact-label">واتساب</span>
                <span class="pc-contact-val">+962777210884</span>
              </div>
            </a>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { useReveal } from "@/composables/useReveal";
const { elRef, visible } = useReveal(0.12);

const trust = [
  { icon: "✅", text: "استشارة مجانية بدون التزام" },
  { icon: "⚡", text: "رد خلال 24 ساعة" },
  { icon: "🔒", text: "سرية تامة لفكرتك" },
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

.pc-section {
  font-family: 'Tajawal', sans-serif;
  position: relative;
  padding: 8rem 0 10rem;
  overflow: hidden;
  color: white;
}

.pc-bg {
  position: absolute; inset: 0;
  background: linear-gradient(150deg, #0d1b35 0%, #1A2B4C 60%, #0f2044 100%);
}
.pc-grid-lines {
  position: absolute; inset: 0;
  background-image:
    linear-gradient(rgba(0,184,148,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,184,148,0.04) 1px, transparent 1px);
  background-size: 50px 50px;
}
.pc-orb-l {
  position: absolute; width: 500px; height: 500px;
  top: -100px; left: -150px; border-radius: 50%;
  background: radial-gradient(circle, rgba(0,184,148,0.14), transparent 65%);
  filter: blur(80px); pointer-events: none;
  animation: orbFloat 12s ease-in-out infinite;
}
.pc-orb-r {
  position: absolute; width: 400px; height: 400px;
  bottom: -100px; right: -100px; border-radius: 50%;
  background: radial-gradient(circle, rgba(44,62,107,0.4), transparent 65%);
  filter: blur(80px); pointer-events: none;
  animation: orbFloat 15s ease-in-out infinite reverse;
}
@keyframes orbFloat { 0%,100%{transform:translate(0,0);} 50%{transform:translate(40px,-40px);} }

.pc-beam {
  position: absolute; top: 0; bottom: 0; width: 200px;
  background: linear-gradient(90deg, transparent, rgba(0,184,148,0.04), transparent);
  animation: beamMove 14s ease-in-out infinite;
}
@keyframes beamMove { 0%{left:-200px;} 100%{left:110%;} }

.pc-container {
  position: relative; z-index: 2;
  max-width: 1200px; margin: 0 auto; padding: 0 2rem;
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 5rem; align-items: center;
  opacity: 0; transform: translateY(28px);
  transition: opacity 0.9s cubic-bezier(0.16,1,0.3,1), transform 0.9s cubic-bezier(0.16,1,0.3,1);
}
.pc-container.visible { opacity: 1; transform: translateY(0); }
@media (max-width: 900px) { .pc-container { grid-template-columns: 1fr; gap: 3rem; } }

/* Text col */
.pc-label {
  display: inline-block; font-size: 0.75rem; font-weight: 700;
  letter-spacing: 0.15em; color: #00B894; text-transform: uppercase;
  margin-bottom: 1rem; padding-bottom: 0.5rem;
  border-bottom: 2px solid rgba(0,184,148,0.3);
}
.pc-title {
  font-size: clamp(2.2rem, 5vw, 3.5rem); font-weight: 900;
  line-height: 1.1; letter-spacing: -1.5px; margin-bottom: 1.5rem;
}
.pc-title-green {
  background: linear-gradient(135deg, #00B894, #55E6C1);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
.pc-desc {
  font-size: 1rem; color: rgba(255,255,255,0.55); line-height: 1.85; margin-bottom: 2.5rem;
}

.pc-trust { display: flex; flex-direction: column; gap: 0.75rem; }
.pc-trust-item {
  display: flex; align-items: center; gap: 0.6rem;
  font-size: 0.88rem; color: rgba(255,255,255,0.55); font-weight: 500;
}
.pc-trust-icon { font-size: 1rem; }

/* Action col: CTA card */
.pc-card {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 24px; padding: 2.5rem;
  backdrop-filter: blur(20px);
  box-shadow: 0 24px 70px rgba(0,0,0,0.35);
  position: relative; overflow: hidden;
}
.pc-card::before {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(ellipse 70% 40% at 50% 110%, rgba(0,184,148,0.09), transparent);
  pointer-events: none;
}

.pc-card-header {
  display: flex; align-items: center; justify-content: space-between;
  margin-bottom: 0.5rem;
}
.pc-card-title { font-size: 1.2rem; font-weight: 800; color: white; }
.pc-card-badge {
  font-size: 0.7rem; font-weight: 700; color: #00B894;
  background: rgba(0,184,148,0.12); border: 1px solid rgba(0,184,148,0.25);
  padding: 0.2rem 0.65rem; border-radius: 100px;
}
.pc-card-desc { font-size: 0.85rem; color: rgba(255,255,255,0.4); margin-bottom: 1.75rem; }

.pc-btn-primary {
  display: flex; align-items: center; justify-content: center; gap: 0.6rem;
  width: 100%; padding: 1rem;
  background: #00B894; color: white;
  border-radius: 14px; font-family: 'Tajawal', sans-serif;
  font-size: 1rem; font-weight: 700; text-decoration: none;
  position: relative; overflow: hidden;
  box-shadow: 0 8px 28px rgba(0,184,148,0.35);
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
  margin-bottom: 0.9rem;
}
.pc-btn-primary:hover { transform: translateY(-4px) scale(1.02); box-shadow: 0 14px 40px rgba(0,184,148,0.5); }
.pc-btn-fill {
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(255,255,255,0.15), transparent);
  transform: translateX(-100%); transition: transform 0.4s; border-radius: inherit;
}
.pc-btn-primary:hover .pc-btn-fill { transform: translateX(0); }

.pc-btn-ghost {
  display: flex; align-items: center; justify-content: center; gap: 0.5rem;
  width: 100%; padding: 0.9rem;
  background: transparent; color: rgba(255,255,255,0.6);
  border: 1.5px solid rgba(255,255,255,0.12);
  border-radius: 14px; font-family: 'Tajawal', sans-serif;
  font-size: 0.9rem; font-weight: 600; text-decoration: none;
  transition: background 0.3s, border-color 0.3s, color 0.3s, transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.pc-btn-ghost:hover {
  background: rgba(255,255,255,0.06); border-color: rgba(255,255,255,0.25);
  color: white; transform: translateY(-2px);
}

.pc-divider {
  display: flex; align-items: center; gap: 0.75rem;
  color: rgba(255,255,255,0.2); font-size: 0.78rem;
  margin: 1.5rem 0;
}
.pc-divider::before,
.pc-divider::after { content: ''; flex: 1; height: 1px; background: rgba(255,255,255,0.08); }

/* Quick contact */
.pc-quick-contact { display: flex; flex-direction: column; gap: 0.75rem; }
.pc-contact-item {
  display: flex; align-items: center; gap: 0.85rem;
  text-decoration: none;
  padding: 0.75rem; border-radius: 12px;
  border: 1px solid rgba(255,255,255,0.07);
  background: rgba(255,255,255,0.03);
  transition: background 0.3s, border-color 0.3s;
}
.pc-contact-item:hover {
  background: rgba(0,184,148,0.08); border-color: rgba(0,184,148,0.25);
}
.pc-contact-icon {
  width: 38px; height: 38px; border-radius: 10px; flex-shrink: 0;
  display: flex; align-items: center; justify-content: center;
}
.pc-contact-icon.green { background: rgba(0,184,148,0.15); color: #00B894; }
.pc-contact-label { display: block; font-size: 0.7rem; color: rgba(255,255,255,0.35); font-weight: 500; }
.pc-contact-val   { display: block; font-size: 0.9rem; color: white; font-weight: 700; margin-top: 0.1rem; }
</style>