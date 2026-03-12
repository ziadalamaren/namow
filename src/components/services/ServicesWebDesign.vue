<template>
  <section class="pricing-section" dir="rtl" ref="sectionRef">

    <!-- Background -->
    <div class="bg-dots"></div>
    <div class="bg-orb bg-orb-1"></div>
    <div class="bg-orb bg-orb-2"></div>

    <div class="container">

      <!-- ── Header ── -->
      <div class="section-header" :class="{ visible: visible }">
              <div class="svc-label" :class="{ visible: visible }">
        <span class="label-num">01</span>
        <span class="label-line"></span>
        <span class="label-text">الخدمة الاولي</span>
      </div>
        <div class="eyebrow">
          <span class="eyebrow-line"></span>
          باقات تصميم المواقع
          <span class="eyebrow-line eyebrow-line-r"></span>
        </div>
        <h2 class="section-title">اختر الباقة <em>المناسبة</em> لك</h2>
        <p class="section-sub">ثلاث باقات مصممة لتلائم كل حجم مشروع — من الانطلاقة الأولى إلى التوسع الكبير.</p>
      </div>

      <!-- ── Cards grid ── -->
      <div class="cards-grid">

        <!-- ══ BASIC ══ -->
        <div
          class="pkg-card"
          :class="{ visible: visible }"
          style="transition-delay: 0ms"
          @mouseenter="hovered = 0"
          @mouseleave="hovered = null"
        >
          <div class="card-top-line"></div>
          <div class="card-inner">

            <div class="pkg-head">
              <div class="pkg-icon-wrap pkg-icon-wrap--basic">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24"
                  fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                  <rect x="3" y="3" width="18" height="18" rx="2"/><path d="M3 9h18"/>
                </svg>
              </div>
              <div>
                <div class="pkg-badge pkg-badge--basic">Basic</div>
                <h3 class="pkg-name">الباقة الأساسية</h3>
                <p class="pkg-tagline">للمشاريع الصغيرة والانطلاقات الجديدة</p>
              </div>
            </div>

            <div class="pkg-price-block">
              <span class="pkg-price">250</span>
              <div class="pkg-price-meta">
                <span class="pkg-currency">د.أ</span>
                <span class="pkg-period">دفعة واحدة</span>
              </div>
            </div>

            <div class="pkg-divider"></div>

            <div class="pkg-rows">
              <div v-for="row in basicRows" :key="row.label" class="pkg-row">
                <span class="row-label">{{ row.label }}</span>
                <span class="row-val">{{ row.val }}</span>
              </div>
            </div>

            <ul class="pkg-features">
              <li v-for="f in basicFeatures" :key="f">
                <span class="feat-icon feat-icon--basic">
                  <svg xmlns="http://www.w3.org/2000/svg" width="11" height="11" viewBox="0 0 24 24"
                    fill="none" stroke="currentColor" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                  </svg>
                </span>
                {{ f }}
              </li>
            </ul>

            <a href="https://wa.me/962777210884?text=I%20need%20a%20service" class="pkg-btn pkg-btn--basic">
              <span class="pkg-btn-bg"></span>
              <span class="pkg-btn-content">اطلب الخدمة الآن</span>
              <span class="pkg-btn-arrow">←</span>
            </a>

          </div>
        </div>

        <!-- ══ ADVANCED (featured) ══ -->
        <div
          class="pkg-card pkg-card--featured"
          :class="{ visible: visible }"
          style="transition-delay: 150ms"
          @mouseenter="hovered = 1"
          @mouseleave="hovered = null"
        >
          <div class="featured-glow"></div>
          <div class="featured-ribbon">الأكثر طلباً</div>
          <div class="card-inner">

            <div class="pkg-head">
              <div class="pkg-icon-wrap pkg-icon-wrap--featured">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24"
                  fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                  <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/>
                </svg>
              </div>
              <div>
                <div class="pkg-badge pkg-badge--featured">Advanced</div>
                <h3 class="pkg-name pkg-name--featured">الباقة المتقدمة</h3>
                <p class="pkg-tagline pkg-tagline--featured">للشركات التي تريد حضوراً رقمياً مميزاً</p>
              </div>
            </div>

            <div class="pkg-price-block">
              <span class="pkg-price pkg-price--featured">550</span>
              <div class="pkg-price-meta">
                <span class="pkg-currency pkg-currency--featured">د.أ</span>
                <span class="pkg-period pkg-period--featured">دفعة واحدة</span>
              </div>
            </div>

            <div class="pkg-divider pkg-divider--featured"></div>

            <div class="pkg-rows">
              <div v-for="row in advancedRows" :key="row.label" class="pkg-row pkg-row--featured">
                <span class="row-label row-label--featured">{{ row.label }}</span>
                <span class="row-val row-val--featured">{{ row.val }}</span>
              </div>
            </div>

            <ul class="pkg-features">
              <li v-for="f in advancedFeatures" :key="f" class="feat-li--featured">
                <span class="feat-icon feat-icon--featured">
                  <svg xmlns="http://www.w3.org/2000/svg" width="11" height="11" viewBox="0 0 24 24"
                    fill="none" stroke="currentColor" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                  </svg>
                </span>
                {{ f }}
              </li>
            </ul>

            <a href="https://wa.me/962777210884?text=I%20need%20a%20service" class="pkg-btn pkg-btn--featured">
              <span class="pkg-btn-shine"></span>
              <span class="pkg-btn-content">اطلب الخدمة الآن</span>
              <span class="pkg-btn-arrow">←</span>
            </a>

          </div>
        </div>

        <!-- ══ PREMIUM ══ -->
        <div
          class="pkg-card pkg-card--premium"
          :class="{ visible: visible }"
          style="transition-delay: 300ms"
          @mouseenter="hovered = 2"
          @mouseleave="hovered = null"
        >
          <div class="card-top-line card-top-line--premium"></div>
          <div class="card-inner">

            <div class="pkg-head">
              <div class="pkg-icon-wrap pkg-icon-wrap--premium">
                <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24"
                  fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
                </svg>
              </div>
              <div>
                <div class="pkg-badge pkg-badge--premium">Premium</div>
                <h3 class="pkg-name">الباقة الاحترافية</h3>
                <p class="pkg-tagline">للشركات الكبرى والمتاجر الإلكترونية</p>
              </div>
            </div>

            <div class="pkg-price-block">
              <span class="pkg-price pkg-price--premium">1200+</span>
              <div class="pkg-price-meta">
                <span class="pkg-currency">د.أ</span>
                <span class="pkg-period">حسب المتطلبات</span>
              </div>
            </div>

            <div class="pkg-divider"></div>

            <div class="pkg-rows">
              <div v-for="row in premiumRows" :key="row.label" class="pkg-row">
                <span class="row-label row-label--premium">{{ row.label }}</span>
                <span class="row-val row-val--premium">{{ row.val }}</span>
              </div>
            </div>

            <ul class="pkg-features">
              <li v-for="f in premiumFeatures" :key="f" class="feat-li--premium">
                <span class="feat-icon feat-icon--premium">
                  <svg xmlns="http://www.w3.org/2000/svg" width="11" height="11" viewBox="0 0 24 24"
                    fill="none" stroke="currentColor" stroke-width="3.5" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="20 6 9 17 4 12"/>
                  </svg>
                </span>
                {{ f }}
              </li>
            </ul>

            <div class="premium-btns">
              <a href="https://wa.me/962777210884?text=I%20need%20a%20service" class="pkg-btn pkg-btn--premium-consult">
                <span class="pkg-btn-bg pkg-btn-bg--premium"></span>
                <span class="pkg-btn-content">احجز استشارة مجانية</span>
                <span class="pkg-btn-arrow">←</span>
              </a>
              <a href="https://wa.me/962777210884?text=I%20need%20a%20service" class="pkg-btn pkg-btn--premium-price">
                اطلب السعر
              </a>
            </div>

          </div>
        </div>

      </div>

      <!-- ── Bottom note ── -->
      <div class="bottom-note" :class="{ visible: visible }">
        <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24"
          fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/>
        </svg>
        جميع الباقات تشمل استضافة مجانية لمدة سنة · الأسعار بالدينار الأردني · التواصل لأي استفسار
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const sectionRef = ref(null);
const visible    = ref(false);
const hovered    = ref(null);

let observer;
onMounted(() => {
  observer = new IntersectionObserver(
    ([e]) => { if (e.isIntersecting) visible.value = true; },
    { threshold: 0.1 }
  );
  if (sectionRef.value) observer.observe(sectionRef.value);
});
onUnmounted(() => observer?.disconnect());

// ── Basic ──
const basicRows = [
  { label: "عدد الصفحات",  val: "5 صفحات" },
  { label: "التصميم",       val: "قالب احترافي مخصص" },
  { label: "الدعم الفني",   val: "شهر كامل" },
];
const basicFeatures = [
  "تصميم متجاوب مع الجوال",
  "سرعة تحميل عالية",
  "استضافة سنة مجانية",
  "شعار ومحتوى مخصص",
];

// ── Advanced ──
const advancedRows = [
  { label: "عدد الصفحات",  val: "10 صفحات + مدونة" },
  { label: "التصميم",       val: "مخصص بالكامل" },
  { label: "الدعم الفني",   val: "3 أشهر + تدريب" },
];
const advancedFeatures = [
  "كل مميزات الأساسية",
  "تحسين محركات بحث SEO",
  "سرعة فائقة محسّنة",
  "هوية بصرية للعلامة التجارية",
  "تدريب على إدارة الموقع",
];

// ── Premium ──
const premiumRows = [
  { label: "عدد الصفحات",  val: "غير محدود" },
  { label: "التصميم",       val: "فاخر + هوية بصرية كاملة" },
  { label: "الدعم الفني",   val: "VIP سنة كاملة" },
];
const premiumFeatures = [
  "كل مميزات المتقدمة",
  "متجر إلكتروني متكامل",
  "بوابات دفع إلكتروني",
  "SEO متقدم + تقارير أداء",
  "شعار + خطوط + ألوان",
  "تدريب مكثف لفريق العمل",
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

/* ════════════════════════════════════ BASE */
.pricing-section {
  font-family: 'Tajawal', sans-serif;
  position: relative;
  padding: 7rem 0 8rem;
  background: #F5F6FA;
  overflow: hidden;
  color: #1A2B4C;
}
.dark .pricing-section { background: #0d1526; color: #f0f4ff; }

.bg-dots {
  position: absolute; inset: 0; pointer-events: none;
  background-image: radial-gradient(circle, rgba(0,184,148,0.07) 1px, transparent 1px);
  background-size: 28px 28px;
}
.bg-orb { position: absolute; border-radius: 50%; filter: blur(80px); pointer-events: none; }
.bg-orb-1 {
  width: 600px; height: 600px; top: -200px; right: -150px;
  background: radial-gradient(circle, rgba(0,184,148,0.1), transparent 70%);
}
.bg-orb-2 {
  width: 500px; height: 500px; bottom: -150px; left: -100px;
  background: radial-gradient(circle, rgba(44,62,107,0.12), transparent 70%);
}

.container { position: relative; z-index: 1; max-width: 1200px; margin: 0 auto; padding: 0 2rem; }
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

/* ════════════════════════════════════ HEADER */
.section-header {
  text-align: center; margin-bottom: 5rem;
  opacity: 0; transform: translateY(28px);
  transition: opacity 0.8s cubic-bezier(0.16,1,0.3,1), transform 0.8s cubic-bezier(0.16,1,0.3,1);
}
.section-header.visible { opacity: 1; transform: translateY(0); }

.eyebrow {
  display: inline-flex; align-items: center; gap: 0.75rem;
  font-size: 0.76rem; font-weight: 700; letter-spacing: 0.14em; color: #00B894;
  margin-bottom: 1.25rem;
}
.eyebrow-line { display: block; width: 28px; height: 1.5px; background: linear-gradient(90deg, transparent, #00B894); }
.eyebrow-line-r { background: linear-gradient(90deg, #00B894, transparent); }

.section-title {
  font-size: clamp(2rem, 4.5vw, 3.2rem); font-weight: 900;
  color: #1A2B4C; letter-spacing: -1.5px; line-height: 1.1; margin-bottom: 1rem;
}
.dark .section-title { color: #f0f4ff; }
.section-title em {
  font-style: normal;
  background: linear-gradient(135deg, #00B894, #55E6C1);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
.section-sub { font-size: 1rem; color: #5a6a85; max-width: 480px; margin: 0 auto; line-height: 1.75; }
.dark .section-sub { color: #9ca3af; }

/* ════════════════════════════════════ GRID */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  align-items: start;
}
@media (max-width: 980px) { .cards-grid { grid-template-columns: 1fr; max-width: 500px; margin: 0 auto; } }
@media (min-width: 981px) and (max-width: 1100px) { .cards-grid { gap: 1rem; } }

/* ════════════════════════════════════ BASE CARD */
.pkg-card {
  position: relative;
  background: #fff; border: 1.5px solid rgba(26,43,76,0.09);
  border-radius: 24px; overflow: hidden;
  opacity: 0; transform: translateY(48px) scale(0.97);
  transition:
    opacity 0.7s cubic-bezier(0.16,1,0.3,1),
    transform 0.7s cubic-bezier(0.16,1,0.3,1),
    box-shadow 0.4s, border-color 0.4s;
}
.dark .pkg-card { background: rgba(26,43,76,0.3); border-color: rgba(255,255,255,0.07); }
.pkg-card.visible { opacity: 1; transform: translateY(0) scale(1); }
.pkg-card:hover { box-shadow: 0 20px 50px rgba(26,43,76,0.1); border-color: rgba(0,184,148,0.3); }
.dark .pkg-card:hover { box-shadow: 0 20px 50px rgba(0,0,0,0.3); }

/* Top accent line */
.card-top-line {
  height: 3px; width: 100%;
  background: linear-gradient(90deg, transparent, rgba(0,184,148,0.5), transparent);
}
.card-top-line--premium {
  background: linear-gradient(90deg, transparent, #55E6C1, transparent);
}

.card-inner { padding: 2rem 1.75rem 2rem; }

/* ════════════════════════════════════ FEATURED CARD — green in light, dark in dark */
.pkg-card--featured {
  background: #00B894;
  border-color: #00a37a;
  transform: translateY(48px) scale(0.97);
  box-shadow: 0 0 0 1px rgba(0,163,122,0.5), 0 30px 60px rgba(0,184,148,0.25);
}
.pkg-card--featured.visible { transform: translateY(-12px) scale(1.02); }
.pkg-card--featured:hover {
  transform: translateY(-18px) scale(1.02) !important;
  box-shadow: 0 0 0 1px rgba(0,163,122,0.7), 0 40px 70px rgba(0,184,148,0.35) !important;
}
.dark .pkg-card--featured {
  background: #0d1f3c;
  border-color: rgba(0,184,148,0.3);
  box-shadow: 0 0 0 1px rgba(0,184,148,0.2), 0 30px 60px rgba(13,31,60,0.35);
}

.featured-glow {
  position: absolute; inset: 0; pointer-events: none; border-radius: inherit;
  background: radial-gradient(ellipse at 50% 0%, rgba(255,255,255,0.2), transparent 55%);
}
.dark .featured-glow {
  background: radial-gradient(ellipse at 50% 0%, rgba(0,184,148,0.15), transparent 60%);
}

.featured-ribbon {
  position: absolute; top: 16px; left: 50%; transform: translateX(-50%);
  background: rgba(255,255,255,0.22);
  border: 1px solid rgba(255,255,255,0.4);
  color: white; font-size: 0.7rem; font-weight: 800; letter-spacing: 0.1em;
  padding: 0.25rem 1rem; border-radius: 100px;
  white-space: nowrap;
}
.dark .featured-ribbon {
  background: linear-gradient(135deg, #00B894, #009e7a);
  border: none;
  box-shadow: 0 4px 12px rgba(0,184,148,0.4);
}

/* ════════════════════════════════════ PREMIUM CARD — dark navy in light, subtle in dark */
.pkg-card--premium {
  background: #1A2B4C;
  border-color: #253b63;
  box-shadow: 0 8px 32px rgba(26,43,76,0.25);
}
.pkg-card--premium:hover {
  border-color: rgba(85,230,193,0.4) !important;
  box-shadow: 0 20px 50px rgba(26,43,76,0.35) !important;
}
.dark .pkg-card--premium {
  background: rgba(44,62,107,0.25);
  border-color: rgba(126,168,232,0.15);
  box-shadow: none;
}

/* ════════════════════════════════════ CARD HEADER */
.pkg-head {
  display: flex; align-items: flex-start; gap: 1rem;
  padding-top: 1.25rem;
  margin-bottom: 1.75rem;
}

/* Icon wraps */
.pkg-icon-wrap {
  flex-shrink: 0; width: 48px; height: 48px; border-radius: 14px;
  display: flex; align-items: center; justify-content: center;
}
.pkg-icon-wrap--basic {
  background: rgba(0,184,148,0.1); color: #00B894;
  border: 1.5px solid rgba(0,184,148,0.2);
}
.pkg-icon-wrap--featured {
  background: rgba(255,255,255,0.2); color: white;
  border: 1.5px solid rgba(255,255,255,0.35);
}
.dark .pkg-icon-wrap--featured {
  background: rgba(0,184,148,0.2); color: #55E6C1;
  border-color: rgba(0,184,148,0.4);
}
.pkg-icon-wrap--premium {
  background: rgba(255,255,255,0.08); color: #7ea8e8;
  border: 1.5px solid rgba(255,255,255,0.15);
}

/* Badges */
.pkg-badge {
  display: inline-block; font-size: 0.62rem; font-weight: 800;
  letter-spacing: 0.12em; padding: 0.15rem 0.6rem;
  border-radius: 100px; margin-bottom: 0.3rem;
}
.pkg-badge--basic { background: rgba(0,184,148,0.1); color: #00B894; border: 1px solid rgba(0,184,148,0.2); }
.pkg-badge--featured { background: rgba(255,255,255,0.2); color: white; border: 1px solid rgba(255,255,255,0.35); }
.dark .pkg-badge--featured { background: rgba(0,184,148,0.2); color: #55E6C1; border-color: rgba(0,184,148,0.35); }
.pkg-badge--premium { background: rgba(255,255,255,0.1); color: #7ea8e8; border: 1px solid rgba(255,255,255,0.18); }

.pkg-name { font-size: 1.05rem; font-weight: 900; color: #1A2B4C; letter-spacing: -0.3px; margin-bottom: 0.2rem; }
.dark .pkg-name { color: #f0f4ff; }
.pkg-name--featured { color: white !important; }
.pkg-name--premium { color: white !important; }

.pkg-tagline { font-size: 0.75rem; color: #8a9ab5; font-weight: 500; line-height: 1.4; }
.pkg-tagline--featured { color: rgba(255,255,255,0.75) !important; }
.pkg-tagline--premium { color: rgba(255,255,255,0.5) !important; }

/* ════════════════════════════════════ PRICE BLOCK */
.pkg-price-block {
  display: flex; align-items: flex-end; gap: 0.4rem;
  margin-bottom: 1.5rem;
}
.pkg-price {
  font-size: 3rem; font-weight: 900; letter-spacing: -2px; line-height: 1;
  background: linear-gradient(135deg, #00B894, #55E6C1);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
/* Featured: white price on green bg */
.pkg-price--featured {
  font-size: 3.4rem;
  background: none !important;
  -webkit-text-fill-color: white;
  color: white;
}
.dark .pkg-price--featured {
  background: linear-gradient(135deg, #00B894, #55E6C1) !important;
  -webkit-background-clip: text !important;
  -webkit-text-fill-color: transparent !important;
  background-clip: text !important;
}
/* Premium: light blue on dark bg — good contrast */
.pkg-price--premium {
  background: linear-gradient(135deg, #55E6C1, #7ea8e8);
  -webkit-background-clip: text; background-clip: text;
}
.pkg-price-meta { display: flex; flex-direction: column; padding-bottom: 0.5rem; }
.pkg-currency { font-size: 0.85rem; font-weight: 700; color: #8a9ab5; }
.pkg-currency--featured { color: rgba(255,255,255,0.7); }
.pkg-currency--premium  { color: rgba(255,255,255,0.5); }
.pkg-period { font-size: 0.72rem; color: #8a9ab5; font-weight: 500; }
.pkg-period--featured { color: rgba(255,255,255,0.6); }
.pkg-period--premium  { color: rgba(255,255,255,0.4); }

/* ════════════════════════════════════ DIVIDER */
.pkg-divider { height: 1px; background: rgba(26,43,76,0.08); margin-bottom: 1.25rem; }
.dark .pkg-divider { background: rgba(255,255,255,0.06); }
.pkg-divider--featured { background: rgba(255,255,255,0.25); }
.pkg-divider--premium  { background: rgba(255,255,255,0.1); }

/* ════════════════════════════════════ SPEC ROWS */
.pkg-rows { display: flex; flex-direction: column; gap: 0.6rem; margin-bottom: 1.25rem; }

.pkg-row {
  display: flex; align-items: flex-start; justify-content: space-between; gap: 1rem;
  font-size: 0.8rem;
}
.row-label { color: #8a9ab5; font-weight: 500; flex-shrink: 0; }
.row-label--featured { color: rgba(255,255,255,0.65); }
.row-label--premium  { color: rgba(255,255,255,0.45); }
.row-val { font-weight: 700; color: #1A2B4C; text-align: left; }
.dark .row-val { color: #e2e8f0; }
.row-val--featured { color: white; }
.row-val--premium  { color: rgba(255,255,255,0.9); }

/* ════════════════════════════════════ FEATURES LIST */
.pkg-features {
  list-style: none; padding: 0; margin: 0 0 1.75rem;
  display: flex; flex-direction: column; gap: 0.55rem;
}
.pkg-features li, .feat-li--featured, .feat-li--premium {
  display: flex; align-items: flex-start; gap: 0.55rem;
  font-size: 0.82rem; font-weight: 500; color: #374151; line-height: 1.4;
}
.dark .pkg-features li { color: #d1d5db; }
.feat-li--featured { color: rgba(255,255,255,0.9) !important; }
.feat-li--premium  { color: rgba(255,255,255,0.8) !important; }

.feat-icon {
  flex-shrink: 0; width: 18px; height: 18px; border-radius: 50%; margin-top: 1px;
  display: flex; align-items: center; justify-content: center;
}
.feat-icon--basic    { background: rgba(0,184,148,0.12); color: #00B894; }
.feat-icon--featured { background: rgba(255,255,255,0.25); color: white; }
.feat-icon--premium  { background: rgba(85,230,193,0.15); color: #55E6C1; }
.dark .feat-icon--featured { background: rgba(0,184,148,0.25); color: #55E6C1; }

/* ════════════════════════════════════ BUTTONS */
.pkg-btn {
  position: relative; overflow: hidden;
  display: flex; align-items: center; justify-content: center; gap: 0.5rem;
  width: 100%; padding: 0.85rem 1rem; border-radius: 12px;
  font-family: 'Tajawal', sans-serif; font-size: 0.92rem; font-weight: 700;
  text-decoration: none; text-align: center;
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
}
.pkg-btn:hover { transform: translateY(-3px); }

/* Basic btn */
.pkg-btn--basic {
  background: transparent; color: #00B894;
  border: 1.5px solid rgba(0,184,148,0.35);
}
.pkg-btn--basic:hover { box-shadow: 0 8px 24px rgba(0,184,148,0.15); border-color: #00B894; }
.pkg-btn-bg {
  position: absolute; inset: 0; border-radius: inherit;
  background: linear-gradient(135deg, #00B894, #009e7a);
  transform: scaleX(0); transform-origin: right;
  transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
}
.pkg-btn--basic:hover .pkg-btn-bg { transform: scaleX(1); }
.pkg-btn--basic:hover .pkg-btn-content,
.pkg-btn--basic:hover .pkg-btn-arrow { color: white; }
.pkg-btn-content { position: relative; z-index: 1; }
.pkg-btn-arrow { position: relative; z-index: 1; transition: transform 0.3s; }
.pkg-btn--basic:hover .pkg-btn-arrow { transform: translateX(-4px); }

/* Featured btn */
.pkg-btn--featured {
  background: #00B894; color: white;
  box-shadow: 0 6px 24px rgba(0,184,148,0.4);
}
.pkg-btn--featured:hover { box-shadow: 0 12px 32px rgba(0,184,148,0.55); }
.pkg-btn-shine {
  position: absolute; top: 0; left: -80px; bottom: 0; width: 60px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
  transform: skewX(-20deg);
  animation: shine 3s ease-in-out infinite 1.5s;
}
@keyframes shine { 0%{left:-80px;} 40%,100%{left:110%;} }
.pkg-btn--featured .pkg-btn-content,
.pkg-btn--featured .pkg-btn-arrow { position: relative; z-index: 1; }
.pkg-btn--featured:hover .pkg-btn-arrow { transform: translateX(-4px); }

/* Premium btns */
.premium-btns { display: flex; flex-direction: column; gap: 0.75rem; }

.pkg-btn--premium-consult {
  background: rgba(255,255,255,0.1); color: white;
  border: 1.5px solid rgba(255,255,255,0.3);
}
.pkg-btn--premium-consult:hover { box-shadow: 0 8px 24px rgba(0,0,0,0.2); border-color: rgba(255,255,255,0.6); }
.pkg-btn-bg--premium {
  position: absolute; inset: 0; border-radius: inherit;
  background: linear-gradient(135deg, #00B894, #009e7a);
  transform: scaleX(0); transform-origin: right;
  transition: transform 0.4s cubic-bezier(0.16,1,0.3,1);
}
.pkg-btn--premium-consult:hover .pkg-btn-bg--premium { transform: scaleX(1); }
.pkg-btn--premium-consult:hover .pkg-btn-content,
.pkg-btn--premium-consult:hover .pkg-btn-arrow { color: white; }
.pkg-btn--premium-consult .pkg-btn-content { position: relative; z-index: 1; }
.pkg-btn--premium-consult .pkg-btn-arrow { position: relative; z-index: 1; transition: transform 0.3s; }
.pkg-btn--premium-consult:hover .pkg-btn-arrow { transform: translateX(-4px); }

.pkg-btn--premium-price {
  background: rgba(255,255,255,0.06); color: rgba(255,255,255,0.7);
  border: 1px solid rgba(255,255,255,0.15); font-size: 0.85rem;
  transition: background 0.3s, color 0.3s;
}
.pkg-btn--premium-price:hover { background: rgba(255,255,255,0.14); color: white; transform: translateY(-2px); }

/* ════════════════════════════════════ BOTTOM NOTE */
.bottom-note {
  display: flex; align-items: center; justify-content: center; gap: 0.6rem;
  margin-top: 3.5rem; font-size: 0.8rem; color: #8a9ab5; font-weight: 500;
  opacity: 0; transform: translateY(16px);
  transition: opacity 0.7s 0.6s, transform 0.7s 0.6s cubic-bezier(0.16,1,0.3,1);
}
.bottom-note.visible { opacity: 1; transform: translateY(0); }
.bottom-note svg { color: #00B894; flex-shrink: 0; }
</style>