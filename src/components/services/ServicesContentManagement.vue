<template>
  <section class="svc-section" dir="rtl" ref="sectionRef">
    <div class="container">

      <!-- Section label -->
      <div class="svc-label" :class="{ visible: visible }">
        <span class="label-num">02</span>
        <span class="label-line"></span>
        <span class="label-text">الخدمة الثانية</span>
      </div>

      <!-- ══ Layout: cards left, text right ══ -->
      <div class="svc-layout" :class="{ visible: visible }">

        <!-- ══ LEFT: full detail cards ══ -->
        <div class="svc-left">

          <div class="pkg-stack">
            <div
              v-for="(pkg, i) in packages"
              :key="i"
              class="pkg-card"
              :class="{
                'pkg-card--featured': pkg.featured,
                'pkg-card--premium': pkg.premium,
              }"
              :style="{ transitionDelay: `${i * 120 + 200}ms` }"
            >
              <!-- Top accent line -->
              <div class="card-top-line" :class="pkg.premium ? 'card-top-line--premium' : ''"></div>

              <!-- Featured glow + ribbon -->
              <div v-if="pkg.featured" class="featured-glow"></div>
              <div v-if="pkg.featured" class="featured-ribbon">الأشهر</div>

              <div class="card-inner">

                <!-- Head -->
                <div class="pkg-head">
                  <div class="pkg-icon-wrap" :class="`pkg-icon-wrap--${pkg.variant}`" v-html="pkg.icon"></div>
                  <div class="pkg-head-info">
                    <div class="pkg-badge" :class="`pkg-badge--${pkg.variant}`">{{ pkg.label }}</div>
                    <h3 class="pkg-name" :class="(pkg.featured || pkg.premium) ? 'pkg-name--light' : ''">{{ pkg.name }}</h3>
                    <p class="pkg-tagline" :class="pkg.featured ? 'pkg-tagline--featured' : pkg.premium ? 'pkg-tagline--premium' : ''">{{ pkg.tagline }}</p>
                  </div>
                </div>

                <!-- Price -->
                <div class="pkg-price-block">
                  <span class="pkg-price" :class="[`pkg-price--${pkg.variant}`, pkg.premium ? 'pkg-price--text' : '']">{{ pkg.price }}</span>
                  <div class="pkg-price-meta" v-if="pkg.period">
                    <span class="pkg-currency" :class="(pkg.featured || pkg.premium) ? 'pkg-currency--light' : ''">د.أ</span>
                    <span class="pkg-period"   :class="(pkg.featured || pkg.premium) ? 'pkg-period--light' : ''">{{ pkg.period }}</span>
                  </div>
                </div>

                <!-- Divider -->
                <div class="pkg-divider"
                  :class="pkg.featured ? 'pkg-divider--featured' : pkg.premium ? 'pkg-divider--premium' : ''">
                </div>

                <!-- Spec rows -->
                <div class="pkg-rows">
                  <div v-for="row in pkg.rows" :key="row.label" class="pkg-row">
                    <span class="row-label" :class="pkg.featured ? 'row-label--featured' : pkg.premium ? 'row-label--premium' : ''">{{ row.label }}</span>
                    <span class="row-val"   :class="pkg.featured ? 'row-val--featured'   : pkg.premium ? 'row-val--premium'   : ''">{{ row.val }}</span>
                  </div>
                </div>

                <!-- Divider 2 -->
                <div class="pkg-divider"
                  :class="pkg.featured ? 'pkg-divider--featured' : pkg.premium ? 'pkg-divider--premium' : ''">
                </div>

                <!-- Features list -->
                <ul class="pkg-features">
                  <li v-for="f in pkg.features" :key="f"
                    :class="pkg.featured ? 'feat-li--featured' : pkg.premium ? 'feat-li--premium' : ''">
                    <span class="feat-icon" :class="`feat-icon--${pkg.variant}`">
                      <svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 24 24"
                        fill="none" stroke="currentColor" stroke-width="3.5"
                        stroke-linecap="round" stroke-linejoin="round">
                        <polyline points="20 6 9 17 4 12"/>
                      </svg>
                    </span>
                    {{ f }}
                  </li>
                </ul>

                <!-- CTA button -->
                <a href="https://wa.me/962777210884?text=I%20need%20a%20service" class="pkg-btn" :class="`pkg-btn--${pkg.variant}`">
                  <span class="pkg-btn-bg"    v-if="!pkg.featured"></span>
                  <span class="pkg-btn-shine" v-if="pkg.featured"></span>
                  <span class="pkg-btn-content">اطلب الخدمة الآن</span>
                  <span class="pkg-btn-arrow">←</span>
                </a>

              </div>
            </div>
          </div>
        </div>

        <!-- ══ RIGHT: big title block ══ -->
        <div class="svc-right">
          <div class="icon-wrap">
            <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24"
              fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
              <polyline points="14 2 14 8 20 8"/>
              <line x1="16" y1="13" x2="8" y2="13"/>
              <line x1="16" y1="17" x2="8" y2="17"/>
            </svg>
            <div class="icon-glow"></div>
          </div>

          <h2 class="svc-title">إدارة<br/>المحتوى</h2>

          <p class="svc-desc">
            حافظ على موقعك نشيطاً ومتجدداً دون عناء — نكتب، ننشر، ونحلل لك كل شيء.
          </p>

          <div class="big-stat">
            <span class="bs-num">97%</span>
            <div class="bs-meta">
              <span class="bs-label">رضا</span>
              <span class="bs-sub">عملاؤنا يجددون</span>
            </div>
          </div>

          <div class="prog-row">
            <span class="prog-label">معدل التجديد الشهري</span>
            <span class="prog-val">97%</span>
          </div>
          <div class="prog-track">
            <div class="prog-fill" :style="{ width: visible ? '97%' : '0%' }"></div>
          </div>

          <div class="cta-row">
            <a href="/contact" class="btn-main">
              <span class="btn-bg"></span>
              <span class="btn-text">
                <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24"
                  fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>
                </svg>
              استفسر عن التفاصيل
              </span>
              <span class="btn-arr">←</span>
            </a>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const sectionRef = ref(null);
const visible    = ref(false);
let observer;
onMounted(() => {
  observer = new IntersectionObserver(
    ([e]) => { if (e.isIntersecting) visible.value = true; },
    { threshold: 0.1 }
  );
  if (sectionRef.value) observer.observe(sectionRef.value);
});
onUnmounted(() => observer?.disconnect());

const packages = [
  {
    name: "باقة المحتوى الأساسية",
    label: "Basic",
    tagline: "للمشاريع الصغيرة والمدونات",
    price: "60",
    period: "شهرياً",
    featured: false,
    premium: false,
    variant: "basic",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/></svg>`,
    rows: [
      { label: "المقالات الشهرية",  val: "4 مقالات" },
      { label: "تحديث الموقع",      val: "مرة شهرياً" },
      { label: "تقرير الأداء",      val: "مبسط" },
    ],
    features: [
      "4 مقالات متوافقة مع SEO",
      "تحديث الصور والعروض شهرياً",
      "تقرير أداء مبسط",
    ],
  },
  {
    name: "باقة المحتوى المتقدمة",
    label: "Advanced",
    tagline: "للشركات التي تريد نمواً مستمراً",
    price: "100",
    period: "شهرياً",
    featured: true,
    premium: false,
    variant: "featured",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`,
    rows: [
      { label: "المقالات الشهرية",  val: "8 مقالات احترافية" },
      { label: "تحديث العروض",      val: "أسبوعياً" },
      { label: "تقرير الأداء",      val: "مفصّل" },
    ],
    features: [
      "8 مقالات شهرية احترافية",
      "تحديث أسبوعي للعروض والأخبار",
      "تصميم صور مصاحبة للمقالات",
      "تقرير أداء مفصّل",
    ],
  },
  {
    name: "باقة المحتوى الشاملة",
    label: "Premium",
    tagline: "للمتاجر والشركات الكبرى",
    price: "تواصل معنا",
    period: "",
    featured: false,
    premium: true,
    variant: "premium",
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>`,
    rows: [
      { label: "المقالات",           val: "غير محدودة" },
      { label: "تحديث الموقع",      val: "يومي عند الحاجة" },
      { label: "سوشيال ميديا",      val: "منشورين أسبوعياً" },
    ],
    features: [
      "مقالات غير محدودة",
      "تحديث يومي عند الحاجة",
      "إدارة وسائل التواصل الاجتماعي",
      "تحسين محركات بحث متقدم",
      "تقارير أداء أسبوعية",
    ],
  },
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

/* ════════════ BASE */
.svc-section {
  font-family: 'Tajawal', sans-serif;
  background: #F5F6FA;
  padding: 6rem 0 8rem;
  position: relative;
}
.dark .svc-section { background: #0d1526; }
.container { max-width: 1200px; margin: 0 auto; padding: 0 2.5rem; }

/* ════════════ LABEL */
.svc-label {
  display: flex; align-items: center; gap: 1rem; margin-bottom: 3.5rem;
  opacity: 0; transform: translateX(20px);
  transition: opacity 0.6s cubic-bezier(0.16,1,0.3,1), transform 0.6s cubic-bezier(0.16,1,0.3,1);
}
.svc-label.visible { opacity: 1; transform: translateX(0); }
.label-num { font-size: 3rem; font-weight: 900; color: rgba(0,184,148,0.15); letter-spacing: -2px; line-height: 1; }
.dark .label-num { color: rgba(0,184,148,0.1); }
.label-line { flex: none; width: 40px; height: 2px; background: linear-gradient(90deg, #00B894, transparent); }
.label-text { font-size: 0.78rem; font-weight: 700; letter-spacing: 0.12em; color: #00B894; }

/* ════════════ LAYOUT */
.svc-layout {
  display: grid;
  grid-template-columns: 1fr 360px;
  gap: 5rem;
  align-items: start;
  opacity: 0; transform: translateY(40px);
  transition: opacity 0.8s 0.1s cubic-bezier(0.16,1,0.3,1),
              transform  0.8s 0.1s cubic-bezier(0.16,1,0.3,1);
}
.svc-layout.visible { opacity: 1; transform: translateY(0); }
@media (max-width: 960px) { .svc-layout { grid-template-columns: 1fr; gap: 3rem; } }

/* ════════════ CARD STACK */
.svc-left { display: flex; flex-direction: column; }
.pkg-stack { display: flex; flex-direction: column; gap: 1.1rem; }

/* ── Base card ── */
.pkg-card {
  position: relative;
  background: #fff;
  border: 1.5px solid rgba(26,43,76,0.09);
  border-radius: 22px;
  overflow: hidden;
  opacity: 0; transform: translateY(36px) scale(0.97);
  transition:
    opacity  0.65s cubic-bezier(0.16,1,0.3,1),
    transform 0.65s cubic-bezier(0.16,1,0.3,1),
    box-shadow 0.35s, border-color 0.35s;
}
.dark .pkg-card { background: rgba(26,43,76,0.3); border-color: rgba(255,255,255,0.07); }
.svc-layout.visible .pkg-card { opacity: 1; transform: translateY(0) scale(1); }
.pkg-card:hover { box-shadow: 0 18px 44px rgba(26,43,76,0.1); border-color: rgba(0,184,148,0.3); }

/* Top accent */
.card-top-line {
  height: 3px;
  background: linear-gradient(90deg, transparent, rgba(0,184,148,0.5), transparent);
}
.card-top-line--premium {
  background: linear-gradient(90deg, transparent, #55E6C1, transparent);
}

.card-inner { padding: 1.6rem 1.75rem 1.75rem; }

/* ── Featured (green) ── */
.pkg-card--featured {
  background: #00B894;
  border-color: #00a37a;
  box-shadow: 0 0 0 1px rgba(0,163,122,0.5), 0 20px 48px rgba(0,184,148,0.28);
}
.pkg-card--featured:hover {
  box-shadow: 0 0 0 1px rgba(0,163,122,0.7), 0 28px 56px rgba(0,184,148,0.38) !important;
  border-color: #00a37a !important;
}
.dark .pkg-card--featured {
  background: #0d1f3c;
  border-color: rgba(0,184,148,0.3);
}
.featured-glow {
  position: absolute; inset: 0; pointer-events: none; border-radius: inherit;
  background: radial-gradient(ellipse at 50% 0%, rgba(255,255,255,0.2), transparent 55%);
}
.dark .featured-glow {
  background: radial-gradient(ellipse at 50% 0%, rgba(0,184,148,0.15), transparent 60%);
}
.featured-ribbon {
  position: absolute; top: 14px; left: 50%; transform: translateX(-50%);
  background: rgba(255,255,255,0.22); border: 1px solid rgba(255,255,255,0.4);
  color: white; font-size: 0.62rem; font-weight: 800; letter-spacing: 0.1em;
  padding: 0.2rem 0.85rem; border-radius: 100px; white-space: nowrap; z-index: 2;
}
.dark .featured-ribbon {
  background: linear-gradient(135deg, #00B894, #009e7a); border: none;
  box-shadow: 0 4px 12px rgba(0,184,148,0.4);
}

/* ── Premium (dark navy) ── */
.pkg-card--premium {
  background: #1A2B4C;
  border-color: #253b63;
  box-shadow: 0 8px 32px rgba(26,43,76,0.28);
}
.pkg-card--premium:hover {
  border-color: rgba(85,230,193,0.4) !important;
  box-shadow: 0 20px 48px rgba(26,43,76,0.38) !important;
}
.dark .pkg-card--premium {
  background: rgba(44,62,107,0.25);
  border-color: rgba(126,168,232,0.15);
}

/* ════════════ HEAD */
.pkg-head {
  display: flex; align-items: flex-start; gap: 1rem;
  padding-top: 1rem; margin-bottom: 1.5rem;
}

.pkg-icon-wrap {
  flex-shrink: 0; width: 46px; height: 46px; border-radius: 13px;
  display: flex; align-items: center; justify-content: center;
}
.pkg-icon-wrap--basic   { background: rgba(0,184,148,0.1);   color: #00B894; border: 1.5px solid rgba(0,184,148,0.2); }
.pkg-icon-wrap--featured{ background: rgba(255,255,255,0.2); color: white;   border: 1.5px solid rgba(255,255,255,0.35); }
.pkg-icon-wrap--premium { background: rgba(255,255,255,0.08);color: #7ea8e8; border: 1.5px solid rgba(255,255,255,0.15); }
.dark .pkg-icon-wrap--featured { background: rgba(0,184,148,0.2); color: #55E6C1; border-color: rgba(0,184,148,0.4); }

.pkg-head-info { display: flex; flex-direction: column; }

.pkg-badge {
  display: inline-block; font-size: 0.58rem; font-weight: 800;
  letter-spacing: 0.12em; padding: 0.12rem 0.55rem;
  border-radius: 100px; margin-bottom: 0.3rem;
}
.pkg-badge--basic   { background: rgba(0,184,148,0.1);   color: #00B894; border: 1px solid rgba(0,184,148,0.2); }
.pkg-badge--featured{ background: rgba(255,255,255,0.2); color: white;   border: 1px solid rgba(255,255,255,0.35); }
.pkg-badge--premium { background: rgba(255,255,255,0.1); color: #7ea8e8; border: 1px solid rgba(255,255,255,0.18); }
.dark .pkg-badge--featured { background: rgba(0,184,148,0.2); color: #55E6C1; border-color: rgba(0,184,148,0.35); }

.pkg-name {
  font-size: 1.05rem; font-weight: 900; color: #1A2B4C;
  letter-spacing: -0.3px; margin-bottom: 0.2rem;
}
.dark .pkg-name { color: #f0f4ff; }
.pkg-name--light { color: white !important; }

.pkg-tagline { font-size: 0.74rem; color: #8a9ab5; font-weight: 500; line-height: 1.4; }
.pkg-tagline--featured { color: rgba(255,255,255,0.72) !important; }
.pkg-tagline--premium  { color: rgba(255,255,255,0.45) !important; }

/* ════════════ PRICE */
.pkg-price-block {
  display: flex; align-items: flex-end; gap: 0.4rem; margin-bottom: 1.25rem;
}
.pkg-price {
  font-size: 2.8rem; font-weight: 900; letter-spacing: -2px; line-height: 1;
  background: linear-gradient(135deg, #00B894, #55E6C1);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
.pkg-price--featured {
  font-size: 3rem;
  background: none !important; -webkit-text-fill-color: white; color: white;
}
.dark .pkg-price--featured {
  background: linear-gradient(135deg, #00B894, #55E6C1) !important;
  -webkit-background-clip: text !important; -webkit-text-fill-color: transparent !important;
  background-clip: text !important;
}
.pkg-price--premium {
  background: linear-gradient(135deg, #55E6C1, #7ea8e8);
  -webkit-background-clip: text; background-clip: text;
}
.pkg-price--text {
  font-size: 1.6rem !important;
  letter-spacing: -0.5px !important;
}
.pkg-price-meta { display: flex; flex-direction: column; padding-bottom: 0.45rem; }
.pkg-currency { font-size: 0.82rem; font-weight: 700; color: #8a9ab5; }
.pkg-currency--light { color: rgba(255,255,255,0.65); }
.pkg-period { font-size: 0.7rem; color: #8a9ab5; font-weight: 500; }
.pkg-period--light { color: rgba(255,255,255,0.5); }

/* ════════════ DIVIDER */
.pkg-divider { height: 1px; background: rgba(26,43,76,0.08); margin-bottom: 1.1rem; }
.dark .pkg-divider { background: rgba(255,255,255,0.06); }
.pkg-divider--featured { background: rgba(255,255,255,0.22); }
.pkg-divider--premium  { background: rgba(255,255,255,0.1); }

/* ════════════ SPEC ROWS */
.pkg-rows {
  display: flex; flex-direction: column; gap: 0.55rem; margin-bottom: 1.1rem;
}
.pkg-row {
  display: flex; align-items: flex-start;
  justify-content: space-between; gap: 1rem; font-size: 0.8rem;
}
.row-label { color: #8a9ab5; font-weight: 500; flex-shrink: 0; }
.row-label--featured { color: rgba(255,255,255,0.6); }
.row-label--premium  { color: rgba(255,255,255,0.42); }
.row-val { font-weight: 700; color: #1A2B4C; text-align: left; }
.dark .row-val { color: #e2e8f0; }
.row-val--featured { color: white; }
.row-val--premium  { color: rgba(255,255,255,0.88); }

/* ════════════ FEATURES */
.pkg-features {
  list-style: none; padding: 0; margin: 0 0 1.5rem;
  display: flex; flex-direction: column; gap: 0.5rem;
}
.pkg-features li,
.feat-li--featured,
.feat-li--premium {
  display: flex; align-items: flex-start; gap: 0.5rem;
  font-size: 0.81rem; font-weight: 500; color: #374151; line-height: 1.4;
}
.dark .pkg-features li { color: #d1d5db; }
.feat-li--featured { color: rgba(255,255,255,0.88) !important; }
.feat-li--premium  { color: rgba(255,255,255,0.78) !important; }

.feat-icon {
  flex-shrink: 0; width: 17px; height: 17px; border-radius: 50%; margin-top: 1px;
  display: flex; align-items: center; justify-content: center;
}
.feat-icon--basic   { background: rgba(0,184,148,0.12); color: #00B894; }
.feat-icon--featured{ background: rgba(255,255,255,0.25); color: white; }
.feat-icon--premium { background: rgba(85,230,193,0.15); color: #55E6C1; }
.dark .feat-icon--featured { background: rgba(0,184,148,0.25); color: #55E6C1; }

/* ════════════ BUTTONS */
.pkg-btn {
  position: relative; overflow: hidden;
  display: flex; align-items: center; justify-content: center; gap: 0.5rem;
  width: 100%; padding: 0.82rem 1rem; border-radius: 12px;
  font-family: 'Tajawal', sans-serif; font-size: 0.9rem; font-weight: 700;
  text-decoration: none; text-align: center;
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
}
.pkg-btn:hover { transform: translateY(-2px); }

/* Basic */
.pkg-btn--basic {
  background: transparent; color: #00B894;
  border: 1.5px solid rgba(0,184,148,0.35);
}
.pkg-btn--basic:hover { box-shadow: 0 6px 20px rgba(0,184,148,0.15); border-color: #00B894; }
.pkg-btn-bg {
  position: absolute; inset: 0; border-radius: inherit;
  background: linear-gradient(135deg, #00B894, #009e7a);
  transform: scaleX(0); transform-origin: right;
  transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
}
.pkg-btn--basic:hover .pkg-btn-bg { transform: scaleX(1); }
.pkg-btn--basic:hover .pkg-btn-content,
.pkg-btn--basic:hover .pkg-btn-arrow { color: white; }

/* Featured */
.pkg-btn--featured {
  background: white; color: #00B894;
  box-shadow: 0 4px 18px rgba(0,0,0,0.1);
}
.pkg-btn--featured:hover { box-shadow: 0 8px 28px rgba(0,0,0,0.18); }
.dark .pkg-btn--featured { background: rgba(0,184,148,0.9); color: white; }
.pkg-btn-shine {
  position: absolute; top: 0; left: -80px; bottom: 0; width: 60px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
  transform: skewX(-20deg);
  animation: shine 3s ease-in-out infinite 1.5s;
}
@keyframes shine { 0%{left:-80px;} 40%,100%{left:110%;} }

/* Premium */
.pkg-btn--premium {
  background: rgba(255,255,255,0.08); color: white;
  border: 1.5px solid rgba(255,255,255,0.28);
}
.pkg-btn--premium .pkg-btn-bg {
  background: linear-gradient(135deg, #00B894, #009e7a);
}
.pkg-btn--premium:hover { box-shadow: 0 6px 20px rgba(0,0,0,0.2); border-color: rgba(255,255,255,0.55); }
.pkg-btn--premium:hover .pkg-btn-bg { transform: scaleX(1); }
.pkg-btn--premium:hover .pkg-btn-content,
.pkg-btn--premium:hover .pkg-btn-arrow { color: white; }

.pkg-btn-content { position: relative; z-index: 1; }
.pkg-btn-arrow   { position: relative; z-index: 1; transition: transform 0.3s; }
.pkg-btn:hover .pkg-btn-arrow { transform: translateX(-4px); }

/* ════════════ RIGHT SIDE */
.svc-right { display: flex; flex-direction: column; position: sticky; top: 6rem; }

.icon-wrap {
  position: relative; width: 64px; height: 64px; border-radius: 20px;
  background: linear-gradient(135deg, #2C3E6B, #1A2B4C);
  display: flex; align-items: center; justify-content: center;
  color: #7ea8e8; margin-bottom: 2rem;
  box-shadow: 0 8px 28px rgba(44,62,107,0.4);
}
.icon-glow {
  position: absolute; inset: -8px; border-radius: 26px;
  background: radial-gradient(circle, rgba(44,62,107,0.2), transparent 70%);
  animation: glowPulse 2.5s ease-in-out infinite;
}
@keyframes glowPulse { 0%,100%{opacity:.5;transform:scale(1)} 50%{opacity:1;transform:scale(1.1)} }

.svc-title {
  font-size: clamp(2.6rem, 4.5vw, 3.8rem); font-weight: 900;
  color: #1A2B4C; letter-spacing: -2px; line-height: 1.05; margin-bottom: 1.25rem;
}
.dark .svc-title { color: #f0f4ff; }

.svc-desc { font-size: 0.95rem; color: #5a6a85; line-height: 1.8; margin-bottom: 2.5rem; }
.dark .svc-desc { color: #9ca3af; }

.big-stat {
  display: flex; align-items: center; gap: 1rem;
  background: linear-gradient(135deg, rgba(44,62,107,0.07), rgba(44,62,107,0.03));
  border: 1.5px solid rgba(44,62,107,0.12); border-radius: 16px;
  padding: 1.1rem 1.5rem; margin-bottom: 1.75rem; width: fit-content;
}
.dark .big-stat { background: rgba(44,62,107,0.1); border-color: rgba(126,168,232,0.15); }
.bs-num {
  font-size: 2.6rem; font-weight: 900; letter-spacing: -2px;
  background: linear-gradient(135deg, #2C3E6B, #4a7ab5);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  line-height: 1;
}
.dark .bs-num {
  background: linear-gradient(135deg, #7ea8e8, #55E6C1);
  -webkit-background-clip: text; background-clip: text;
}
.bs-meta { display: flex; flex-direction: column; }
.bs-label { font-size: 1rem; font-weight: 800; color: #1A2B4C; }
.dark .bs-label { color: #f0f4ff; }
.bs-sub { font-size: 0.75rem; color: #8a9ab5; }

.prog-row { display: flex; justify-content: space-between; margin-bottom: 0.5rem; }
.prog-label { font-size: 0.8rem; color: #5a6a85; }
.dark .prog-label { color: #9ca3af; }
.prog-val { font-size: 0.8rem; font-weight: 700; color: #2C3E6B; }
.dark .prog-val { color: #7ea8e8; }
.prog-track {
  height: 5px; border-radius: 5px; background: rgba(44,62,107,0.1);
  overflow: hidden; margin-bottom: 2.5rem;
}
.prog-fill {
  height: 100%; border-radius: 5px;
  background: linear-gradient(90deg, #2C3E6B, #4a7ab5);
  width: 0; transition: width 1.4s cubic-bezier(0.16,1,0.3,1) 0.5s;
}
.dark .prog-fill { background: linear-gradient(90deg, #4a7ab5, #7ea8e8); }

.cta-row { display: flex; align-items: center; gap: 1.5rem; }
.btn-main {
  position: relative; display: inline-flex; align-items: center; gap: 0.6rem;
  background: #2C3E6B; color: white; padding: 0.8rem 1.7rem; border-radius: 12px;
  font-family: 'Tajawal', sans-serif; font-size: 0.95rem; font-weight: 700;
  text-decoration: none; overflow: hidden;
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
  box-shadow: 0 4px 18px rgba(44,62,107,0.3);
}
.dark .btn-main { background: rgba(255,255,255,0.07); border: 1px solid rgba(255,255,255,0.1); }
.btn-main:hover { transform: translateY(-3px); box-shadow: 0 10px 28px rgba(44,62,107,0.35); }
.btn-bg {
  position: absolute; inset: 0; border-radius: inherit;
  background: linear-gradient(135deg, #00B894, #009e7a);
  transform: scaleX(0); transform-origin: right;
  transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
}
.btn-main:hover .btn-bg { transform: scaleX(1); }
.btn-text { position: relative; z-index: 1; display: flex; align-items: center; gap: 0.5rem; }
.btn-arr  { position: relative; z-index: 1; transition: transform 0.3s; }
.btn-main:hover .btn-arr { transform: translateX(-4px); }

.link-more {
  font-size: 0.85rem; font-weight: 600; color: #2C3E6B;
  text-decoration: none; border-bottom: 1px dashed rgba(44,62,107,0.3);
  padding-bottom: 1px; transition: opacity 0.2s;
}
.dark .link-more { color: #7ea8e8; border-bottom-color: rgba(126,168,232,0.3); }
.link-more:hover { opacity: 0.7; }
</style>