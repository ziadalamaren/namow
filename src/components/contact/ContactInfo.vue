<template>
  <div class="ci-wrap" dir="rtl" ref="elRef">

    <!-- ── Intro text ── -->
    <div class="ci-intro" :class="{ visible }">
      <div class="ci-label">معلومات التواصل</div>
      <h2 class="ci-title">نحن هنا<br><em>لمساعدتك</em></h2>
      <p class="ci-desc">
        تواصل معنا عبر أي قناة تناسبك.
        فريقنا متاح من الأحد إلى الخميس خلال ساعات العمل.
      </p>
    </div>

    <!-- ── Contact cards ── -->
    <div class="ci-cards">
      <a
        v-for="(card, i) in cards"
        :key="i"
        :href="card.href"
        :target="card.external ? '_blank' : undefined"
        rel="noopener"
        class="ci-card"
        :class="[`ci-card--${card.type}`, { visible }]"
        :style="{ transitionDelay: `${i * 120 + 200}ms` }"
      >
        <!-- Top accent -->
        <div class="ci-card-accent"></div>

        <div class="ci-card-icon" :style="{ background: card.iconBg, borderColor: card.iconBorder }">
          <component :is="'svg'"
            xmlns="http://www.w3.org/2000/svg"
            width="22" height="22"
            viewBox="0 0 24 24"
            fill="none"
            :stroke="card.iconColor"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
            v-html="card.icon"
          />
        </div>

        <div class="ci-card-body">
          <div class="ci-card-label">{{ card.label }}</div>
          <div class="ci-card-value">{{ card.value }}</div>
          <div v-if="card.note" class="ci-card-note">{{ card.note }}</div>
        </div>

        <div class="ci-card-arrow">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16">
            <path d="M5 12h14M12 5l7 7-7 7"/>
          </svg>
        </div>
      </a>
    </div>

    <!-- ── Location map card ── -->
    <div class="ci-map-card" :class="{ visible }" style="transition-delay: 500ms">
      <div class="ci-map-header">
        <div class="ci-map-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24"
            fill="none" stroke="#00B894" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>
            <circle cx="12" cy="10" r="3"/>
          </svg>
        </div>
        <div>
          <div class="ci-map-title">موقعنا</div>
          <div class="ci-map-sub">إربد، المملكة الأردنية الهاشمية 🇯🇴</div>
        </div>
      </div>

      <!-- Decorative map illustration -->
      <div class="ci-map-visual">
        <!-- Grid lines -->
        <svg class="ci-map-grid" viewBox="0 0 400 200" xmlns="http://www.w3.org/2000/svg">
          <!-- Horizontal lines -->
          <line v-for="y in [40,80,120,160]" :key="`h${y}`" :x1="0" :y1="y" :x2="400" :y2="y" stroke="rgba(0,184,148,0.08)" stroke-width="1"/>
          <!-- Vertical lines -->
          <line v-for="x in [80,160,240,320]" :key="`v${x}`" :x1="x" y1="0" :x2="x" y2="200" stroke="rgba(0,184,148,0.08)" stroke-width="1"/>
          <!-- Streets -->
          <line x1="0" y1="100" x2="400" y2="100" stroke="rgba(255,255,255,0.07)" stroke-width="2"/>
          <line x1="200" y1="0" x2="200" y2="200" stroke="rgba(255,255,255,0.07)" stroke-width="2"/>
          <!-- Pin -->
          <circle cx="200" cy="100" r="28" fill="rgba(0,184,148,0.15)" stroke="rgba(0,184,148,0.3)" stroke-width="1">
            <animate attributeName="r" values="28;38;28" dur="2.5s" repeatCount="indefinite"/>
            <animate attributeName="opacity" values="1;0.3;1" dur="2.5s" repeatCount="indefinite"/>
          </circle>
          <circle cx="200" cy="100" r="8" fill="#00B894"/>
          <circle cx="200" cy="100" r="4" fill="white"/>
        </svg>
        <div class="ci-map-label-city">إربد</div>
      </div>

      <a
        href="https://maps.google.com/?q=Irbid,Jordan"
        target="_blank" rel="noopener"
        class="ci-map-link"
      >
        فتح في خرائط جوجل
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="13">
          <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/>
        </svg>
      </a>
    </div>

    <!-- ── Working hours ── -->
    <div class="ci-hours" :class="{ visible }" style="transition-delay: 600ms">
      <div class="ci-hours-header">
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24"
          fill="none" stroke="#00B894" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
          <circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/>
        </svg>
        ساعات العمل
        <span class="ci-hours-badge">
          <span class="ci-hours-dot"></span>
          متاح الآن
        </span>
      </div>
      <div class="ci-hours-rows">
        <div v-for="row in hours" :key="row.day" class="ci-hours-row">
          <span class="ci-hours-day">{{ row.day }}</span>
          <span class="ci-hours-bar">
            <span class="ci-hours-fill" :style="{ width: row.pct + '%' }"></span>
          </span>
          <span class="ci-hours-time">{{ row.time }}</span>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { useReveal } from "@/composables/useReveal";
const { elRef, visible } = useReveal(0.08);

const cards = [
  {
    type: "whatsapp",
    label: "واتساب",
    value: "+962777210884",
    note: "رد فوري في أوقات العمل",
    href: "https://wa.me/962777210884?text=مرحبًا%20فريق%20نمو%2C%20لدي%20استفسار%20حول%20خدماتكم",
    external: true,
    iconBg: "rgba(37,211,102,0.12)",
    iconBorder: "rgba(37,211,102,0.25)",
    iconColor: "#25D366",
    icon: `<path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5 -.669 -.51 -.173 -.008 -.371 -.01 -.57 -.0１ -.１９８ ０ -.５２ .０７４ -.７９２ .３７２ -.２７２ .２９７ -１ .０１６ -１ .０１６ ２ .４７９ ０ １ .４６２ １ .０６５ ２ .８７５ １ .２１３ ３ .０７４ .１４９ .１９８ ２ .０９６ ３ .２ ５ .０７７ ４ .４８７ .７０９ .３０６ １ .２６２ .４８９ １ .６９４ .６２５ .７１２ .２２７ １ .３６ .１９５ １ .８７１ .１１８ .５７１ -.０８５ １ .７５８ -.７１９ ２ .００６ -₁ .４₁₃ .₂₄₈ -.₆₉₄ .₂₄₈ -₁ .₂₈₉ .₁₇₃ -₁ .₄₁₃ -.₀₇₄ -.₁₂₄ -.₂₇₂ -.₁₉₈ -.５₇ -."/>`,
  },
  {
    type: "email",
    label: "البريد الإلكتروني",
    value: "zeadamaren24@gmail.com",
    note: "للاستفسارات التفصيلية",
    href: "mailto:zeadamaren24@gmail.com",
    external: false,
    iconBg: "rgba(0,184,148,0.12)",
    iconBorder: "rgba(0,184,148,0.25)",
    iconColor: "#00B894",
    icon: `<path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/>`,
  },
  {
    type: "location",
    label: "الموقع",
    value: "إربد، الأردن",
    note: "نعمل عن بُعد مع جميع مدن الأردن",
    href: "https://maps.google.com/?q=Irbid,Jordan",
    external: true,
    iconBg: "rgba(26,43,76,0.08)",
    iconBorder: "rgba(26,43,76,0.15)",
    iconColor: "#1A2B4C",
    icon: `<path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/>`,
  },
];

const hours = [
  { day: "الأحد – الخميس", time: "٩ص – ٦م",  pct: 100 },
  { day: "الجمعة",          time: "٩ص – ١م",  pct: 44 },
  { day: "السبت",           time: "مغلق",      pct: 0 },
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

.ci-wrap {
  font-family: 'Tajawal', sans-serif;
  display: flex; flex-direction: column; gap: 1.5rem;
}

/* ── Intro ── */
.ci-intro {
  opacity: 0; transform: translateY(24px);
  transition: opacity 0.8s cubic-bezier(0.16,1,0.3,1), transform 0.8s cubic-bezier(0.16,1,0.3,1);
  margin-bottom: 0.5rem;
}
.ci-intro.visible { opacity: 1; transform: translateY(0); }

.ci-label {
  display: inline-block; font-size: 0.75rem; font-weight: 700;
  letter-spacing: 0.14em; color: #00B894; text-transform: uppercase;
  margin-bottom: 0.75rem; padding-bottom: 0.4rem;
  border-bottom: 2px solid rgba(0,184,148,0.3);
}
.ci-title {
  font-size: clamp(1.8rem, 4vw, 2.6rem); font-weight: 900;
  color: #1A2B4C; letter-spacing: -1px; line-height: 1.15; margin-bottom: 0.75rem;
}
.ci-title em {
  font-style: normal;
  background: linear-gradient(135deg, #00B894, #55E6C1);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
.ci-desc { font-size: 0.92rem; color: #5a6a85; line-height: 1.8; }

/* ── Cards ── */
.ci-cards { display: flex; flex-direction: column; gap: 0.85rem; }

.ci-card {
  display: flex; align-items: center; gap: 1rem;
  background: white; border: 1.5px solid rgba(26,43,76,0.07);
  border-radius: 18px; padding: 1.25rem 1.5rem;
  text-decoration: none; color: inherit; position: relative; overflow: hidden;
  opacity: 0; transform: translateX(20px);
  transition:
    opacity 0.6s cubic-bezier(0.16,1,0.3,1),
    transform 0.6s cubic-bezier(0.16,1,0.3,1),
    border-color 0.3s, box-shadow 0.3s;
  box-shadow: 0 2px 12px rgba(26,43,76,0.05);
}
.ci-card.visible { opacity: 1; transform: translateX(0); }
.ci-card:hover {
  border-color: rgba(0,184,148,0.3);
  box-shadow: 0 8px 28px rgba(26,43,76,0.1);
  transform: translateX(-4px) !important;
}

.ci-card-accent {
  position: absolute; top: 0; right: 0; bottom: 0; width: 3px;
  background: linear-gradient(180deg, #00B894, #55E6C1);
  opacity: 0; transition: opacity 0.3s;
}
.ci-card:hover .ci-card-accent { opacity: 1; }

.ci-card-icon {
  width: 46px; height: 46px; border-radius: 13px; flex-shrink: 0;
  border: 1.5px solid transparent;
  display: flex; align-items: center; justify-content: center;
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.ci-card:hover .ci-card-icon { transform: scale(1.12) rotate(-5deg); }

.ci-card-body { flex: 1; min-width: 0; }
.ci-card-label { font-size: 0.72rem; color: #9aa3b2; font-weight: 600; text-transform: uppercase; letter-spacing: 0.08em; }
.ci-card-value { font-size: 0.98rem; font-weight: 800; color: #1A2B4C; margin-top: 0.15rem; }
.ci-card-note  { font-size: 0.75rem; color: #9aa3b2; margin-top: 0.15rem; }

.ci-card-arrow {
  color: rgba(26,43,76,0.2); flex-shrink: 0;
  transition: color 0.3s, transform 0.3s;
}
.ci-card:hover .ci-card-arrow { color: #00B894; transform: translateX(-4px); }

/* ── Map card ── */
.ci-map-card {
  background: #1A2B4C; border-radius: 20px; overflow: hidden;
  opacity: 0; transform: translateY(20px);
  transition: opacity 0.7s cubic-bezier(0.16,1,0.3,1), transform 0.7s cubic-bezier(0.16,1,0.3,1);
}
.ci-map-card.visible { opacity: 1; transform: translateY(0); }

.ci-map-header {
  display: flex; align-items: center; gap: 0.85rem;
  padding: 1.5rem 1.5rem 0;
}
.ci-map-icon {
  width: 38px; height: 38px; border-radius: 10px; flex-shrink: 0;
  background: rgba(0,184,148,0.15); border: 1px solid rgba(0,184,148,0.25);
  display: flex; align-items: center; justify-content: center;
}
.ci-map-title { font-size: 0.9rem; font-weight: 800; color: white; }
.ci-map-sub   { font-size: 0.75rem; color: rgba(255,255,255,0.45); margin-top: 0.1rem; }

.ci-map-visual {
  position: relative; margin: 1.25rem 0 0;
  background: rgba(255,255,255,0.03);
  border-top: 1px solid rgba(255,255,255,0.06);
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
.ci-map-grid { width: 100%; height: 130px; display: block; }
.ci-map-label-city {
  position: absolute; top: 50%; left: 50%; transform: translate(-50%, -55%);
  font-size: 0.7rem; font-weight: 700; color: rgba(255,255,255,0.35);
  letter-spacing: 0.1em; text-transform: uppercase;
  margin-top: -18px;
}

.ci-map-link {
  display: flex; align-items: center; gap: 0.5rem; justify-content: center;
  padding: 1rem; color: #00B894; font-size: 0.82rem; font-weight: 700;
  text-decoration: none; transition: background 0.3s;
}
.ci-map-link:hover { background: rgba(255,255,255,0.04); }

/* ── Working hours ── */
.ci-hours {
  background: white; border: 1.5px solid rgba(26,43,76,0.07);
  border-radius: 20px; padding: 1.5rem;
  box-shadow: 0 2px 12px rgba(26,43,76,0.05);
  opacity: 0; transform: translateY(20px);
  transition: opacity 0.7s cubic-bezier(0.16,1,0.3,1), transform 0.7s cubic-bezier(0.16,1,0.3,1);
}
.ci-hours.visible { opacity: 1; transform: translateY(0); }

.ci-hours-header {
  display: flex; align-items: center; gap: 0.6rem;
  font-size: 0.85rem; font-weight: 700; color: #1A2B4C;
  margin-bottom: 1.25rem;
}
.ci-hours-badge {
  display: inline-flex; align-items: center; gap: 0.4rem;
  margin-right: auto;
  background: rgba(0,184,148,0.08); border: 1px solid rgba(0,184,148,0.2);
  color: #00B894; font-size: 0.7rem; font-weight: 700;
  padding: 0.2rem 0.65rem; border-radius: 100px;
}
.ci-hours-dot {
  width: 6px; height: 6px; border-radius: 50%; background: #00B894;
  animation: dotP 2s ease-in-out infinite;
}
@keyframes dotP {
  0%,100%{box-shadow:0 0 0 0 rgba(0,184,148,0.5);} 60%{box-shadow:0 0 0 5px rgba(0,184,148,0);}
}

.ci-hours-rows { display: flex; flex-direction: column; gap: 0.75rem; }
.ci-hours-row  { display: flex; align-items: center; gap: 0.75rem; }
.ci-hours-day  { font-size: 0.78rem; color: #5a6a85; font-weight: 500; min-width: 130px; }
.ci-hours-bar  {
  flex: 1; height: 4px; background: rgba(26,43,76,0.07);
  border-radius: 4px; overflow: hidden;
}
.ci-hours-fill {
  height: 100%; border-radius: 4px;
  background: linear-gradient(90deg, #00B894, #55E6C1);
  transition: width 1s cubic-bezier(0.16,1,0.3,1);
}
.ci-hours-time { font-size: 0.78rem; color: #1A2B4C; font-weight: 700; min-width: 70px; text-align: left; }
</style>