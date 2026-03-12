<template>
  <div class="cf-form-wrap" dir="rtl" ref="elRef">
    <div class="cf-card" :class="{ visible }">

      <!-- Card header -->
      <div class="cf-card-header">
        <div class="cf-header-icon">
          <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24"
            fill="none" stroke="#00B894" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>
          </svg>
        </div>
        <div>
          <div class="cf-card-title">أرسل لنا رسالة</div>
          <div class="cf-card-sub">سنرد عليك في أقل من 24 ساعة</div>
        </div>
      </div>

      <!-- SUCCESS STATE -->
      <Transition name="success-fade">
        <div v-if="submitted" class="cf-success">
          <div class="cf-success-icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"
              fill="none" stroke="white" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="20 6 9 17 4 12"/>
            </svg>
          </div>
          <h3 class="cf-success-title">وصلت رسالتك! 🎉</h3>
          <p class="cf-success-desc">شكراً لك. سنتواصل معك قريباً على <strong>{{ form.email }}</strong></p>
          <button class="cf-reset-btn" @click="resetForm">إرسال رسالة أخرى</button>
        </div>
      </Transition>

      <!-- FORM -->
      <Transition name="form-fade">
        <form v-if="!submitted" @submit.prevent="handleSubmit" novalidate class="cf-form">

          <!-- Row: Name + Phone -->
          <div class="cf-row">
            <!-- Full Name -->
            <div class="cf-field" :class="fieldClass('name')">
              <label class="cf-label" :class="{ float: form.name || focused.name }">
                الاسم الكامل <span class="cf-required">*</span>
              </label>
              <input
                type="text"
                v-model="form.name"
                class="cf-input"
                @focus="focused.name = true"
                @blur="focused.name = false; touch('name')"
                autocomplete="name"
                dir="rtl"
              />
              <div class="cf-field-line"></div>
              <Transition name="err">
                <span v-if="errors.name" class="cf-error">{{ errors.name }}</span>
              </Transition>
            </div>

            <!-- Phone -->
            <div class="cf-field" :class="fieldClass('phone')">
              <label class="cf-label" :class="{ float: form.phone || focused.phone }">
                رقم الهاتف
              </label>
              <input
                type="tel"
                v-model="form.phone"
                class="cf-input"
                @focus="focused.phone = true"
                @blur="focused.phone = false; touch('phone')"
                autocomplete="tel"
                dir="ltr"
                style="text-align:right"
                placeholder=""
              />
              <div class="cf-field-line"></div>
              <Transition name="err">
                <span v-if="errors.phone" class="cf-error">{{ errors.phone }}</span>
              </Transition>
            </div>
          </div>

          <!-- Email -->
          <div class="cf-field" :class="fieldClass('email')">
            <label class="cf-label" :class="{ float: form.email || focused.email }">
              البريد الإلكتروني <span class="cf-required">*</span>
            </label>
            <input
              type="email"
              v-model="form.email"
              class="cf-input"
              @focus="focused.email = true"
              @blur="focused.email = false; touch('email')"
              autocomplete="email"
              dir="ltr"
              style="text-align:right"
            />
            <div class="cf-field-line"></div>
            <Transition name="err">
              <span v-if="errors.email" class="cf-error">{{ errors.email }}</span>
            </Transition>
          </div>

          <!-- Service dropdown -->
          <div class="cf-field cf-field--select" :class="fieldClass('service')">
            <label class="cf-label" :class="{ float: form.service || focused.service }">
              نوع الخدمة المطلوبة <span class="cf-required">*</span>
            </label>
            <div class="cf-select-wrap">
              <select
                v-model="form.service"
                class="cf-select"
                @focus="focused.service = true"
                @blur="focused.service = false; touch('service')"
                dir="rtl"
              >
                <option value="" disabled hidden></option>
                <option v-for="opt in serviceOptions" :key="opt.value" :value="opt.value">
                  {{ opt.label }}
                </option>
              </select>
              <div class="cf-select-arrow">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16">
                  <path d="M6 9l6 6 6-6"/>
                </svg>
              </div>
            </div>
            <div class="cf-field-line"></div>
            <Transition name="err">
              <span v-if="errors.service" class="cf-error">{{ errors.service }}</span>
            </Transition>
          </div>

          <!-- Message -->
          <div class="cf-field cf-field--textarea" :class="fieldClass('message')">
            <label class="cf-label" :class="{ float: form.message || focused.message }">
              رسالتك <span class="cf-required">*</span>
            </label>
            <textarea
              v-model="form.message"
              class="cf-textarea"
              rows="5"
              maxlength="500"
              @focus="focused.message = true"
              @blur="focused.message = false; touch('message')"
              dir="rtl"
            ></textarea>
            <div class="cf-field-line"></div>
            <div class="cf-textarea-footer">
              <Transition name="err">
                <span v-if="errors.message" class="cf-error">{{ errors.message }}</span>
              </Transition>
              <span class="cf-char-count" :class="{ warn: form.message.length > 400 }">
                {{ form.message.length }} / 500
              </span>
            </div>
          </div>

          <!-- Privacy note -->
          <label class="cf-privacy">
            <input type="checkbox" v-model="form.privacy" class="cf-checkbox" />
            <span class="cf-checkmark">
              <svg viewBox="0 0 12 10" fill="none" stroke="white" stroke-width="2" width="10">
                <polyline points="1 5 4 9 11 1"/>
              </svg>
            </span>
            <span class="cf-privacy-text">
              أوافق على
              <a href="#" class="cf-privacy-link">سياسة الخصوصية</a>
              وأن يتم التواصل معي
            </span>
          </label>
          <Transition name="err">
            <span v-if="errors.privacy" class="cf-error cf-error--privacy">{{ errors.privacy }}</span>
          </Transition>

          <!-- Send error (EmailJS failure) -->
          <Transition name="err">
            <div v-if="sendError" class="cf-send-error">
              <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24"
                fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/>
              </svg>
              {{ sendError }}
            </div>
          </Transition>

          <!-- Submit button -->
          <button
            type="submit"
            class="cf-submit"
            :class="{ loading: isLoading }"
            :disabled="isLoading"
          >
            <Transition name="btn-content" mode="out-in">
              <span v-if="!isLoading" key="text" class="cf-submit-inner">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24"
                  fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/>
                </svg>
                إرسال الرسالة
              </span>
              <span v-else key="loader" class="cf-loader">
                <span class="cf-spinner"></span>
                جاري الإرسال...
              </span>
            </Transition>
            <span class="cf-submit-fill"></span>
          </button>

        </form>
      </Transition>

    </div>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted } from "vue";
import { useReveal } from "@/composables/useReveal";

const { elRef, visible } = useReveal(0.08);


const EMAILJS_SERVICE_ID  = "service_3qzvpod";   
const EMAILJS_TEMPLATE_ID = "template_fdefmeg"; 
const EMAILJS_PUBLIC_KEY  = "geey-NnIRPvEN-FfX";  

onMounted(() => {
  if (window.emailjs) return; // already loaded
  const script    = document.createElement("script");
  script.src      = "https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js";
  script.async    = true;
  script.onload   = () => window.emailjs.init({ publicKey: EMAILJS_PUBLIC_KEY });
  document.head.appendChild(script);
});

// ── Form state ────────────────────────────────
const form = reactive({
  name: "", email: "", phone: "",
  service: "", message: "", privacy: false,
});

const focused   = reactive({ name: false, email: false, phone: false, service: false, message: false });
const touched   = reactive({ name: false, email: false, phone: false, service: false, message: false, privacy: false });
const errors    = reactive({ name: "", email: "", phone: "", service: "", message: "", privacy: "" });
const isLoading = ref(false);
const submitted = ref(false);
const sendError = ref("");   // error message shown below the button

// ── Service options ───────────────────────────
const serviceOptions = [
  { value: "تصميم موقع إلكتروني", label: "تصميم موقع إلكتروني" },
  { value: "إدارة محتوى",         label: "إدارة محتوى" },
  { value: "استشارة رقمية",       label: "استشارة رقمية" },
  { value: "هوية بصرية",          label: "هوية بصرية" },
  { value: "متجر إلكتروني",       label: "متجر إلكتروني" },
  { value: "أخرى",                label: "أخرى" },
];

// ── Validation ────────────────────────────────
function validate() {
  errors.name    = form.name.trim().length < 2                          ? "الاسم مطلوب (٢ أحرف على الأقل)"       : "";
  errors.email   = !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)      ? "بريد إلكتروني غير صحيح"               : "";
  errors.phone   = form.phone && !/^[\d\s+\-()]{7,}$/.test(form.phone) ? "رقم هاتف غير صحيح"                   : "";
  errors.service = !form.service                                        ? "يرجى اختيار الخدمة"                  : "";
  errors.message = form.message.trim().length < 10                      ? "الرسالة مطلوبة (١٠ أحرف على الأقل)"  : "";
  errors.privacy = !form.privacy                                        ? "يرجى الموافقة على سياسة الخصوصية"    : "";
  return !Object.values(errors).some(Boolean);
}

function touch(field) {
  touched[field] = true;
  validate();
}

function fieldClass(field) {
  return {
    focused: focused[field],
    filled:  !!form[field],
    error:   touched[field] && errors[field],
    success: touched[field] && !errors[field] && form[field],
  };
}

// ── Submit via EmailJS ────────────────────────
async function handleSubmit() {
  Object.keys(touched).forEach(k => (touched[k] = true));
  if (!validate()) return;

  isLoading.value = true;
  sendError.value = "";

  try {
    await window.emailjs.send(
      EMAILJS_SERVICE_ID,
      EMAILJS_TEMPLATE_ID,
      {
        from_name:  form.name,
        from_email: form.email,
        phone:      form.phone || "لم يُذكر",
        service:    form.service,
        message:    form.message,
      }
    );
    submitted.value = true;
  } catch (err) {
    console.error("EmailJS error:", err);
    sendError.value = "حدث خطأ أثناء الإرسال. يرجى المحاولة مرة أخرى أو التواصل عبر واتساب.";
  } finally {
    isLoading.value = false;
  }
}

// ── Reset ─────────────────────────────────────
function resetForm() {
  Object.assign(form, { name: "", email: "", phone: "", service: "", message: "", privacy: false });
  Object.keys(touched).forEach(k => (touched[k] = false));
  Object.keys(errors).forEach(k  => (errors[k]  = ""));
  submitted.value = false;
  sendError.value = "";
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800;900&display=swap');

.cf-form-wrap {
  font-family: 'Tajawal', sans-serif;
}

/* ── Card ── */
.cf-card {
  background: white;
  border: 1.5px solid rgba(26,43,76,0.08);
  border-radius: 28px;
  padding: 3rem;
  box-shadow: 0 16px 60px rgba(26,43,76,0.09);
  opacity: 0; transform: translateY(32px);
  transition: opacity 0.8s cubic-bezier(0.16,1,0.3,1), transform 0.8s cubic-bezier(0.16,1,0.3,1);
  position: relative; overflow: hidden;
}
.cf-card.visible { opacity: 1; transform: translateY(0); }
.cf-card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 3px;
  background: linear-gradient(90deg, #00B894, #55E6C1, #00B894);
  background-size: 200%;
  animation: gradShift 4s linear infinite;
}
@keyframes gradShift { to { background-position: 200%; } }

.cf-card-header {
  display: flex; align-items: center; gap: 1rem; margin-bottom: 2.5rem;
  padding-bottom: 2rem; border-bottom: 1px solid rgba(26,43,76,0.07);
}
.cf-header-icon {
  width: 52px; height: 52px; border-radius: 15px; flex-shrink: 0;
  background: rgba(0,184,148,0.1); border: 1.5px solid rgba(0,184,148,0.2);
  display: flex; align-items: center; justify-content: center;
}
.cf-card-title { font-size: 1.2rem; font-weight: 800; color: #1A2B4C; }
.cf-card-sub { font-size: 0.8rem; color: #5a6a85; margin-top: 0.15rem; }

/* ── Form layout ── */
.cf-form { display: flex; flex-direction: column; gap: 1.75rem; }
.cf-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1.25rem; }
@media (max-width: 560px) { .cf-row { grid-template-columns: 1fr; } }

/* ── Field ── */
.cf-field {
  position: relative; padding-top: 1.4rem;
}

/* Floating label */
.cf-label {
  position: absolute; top: 1.75rem; right: 0;
  font-size: 0.92rem; font-weight: 500; color: #9aa3b2;
  pointer-events: none; user-select: none;
  transform-origin: right top;
  transition: transform 0.25s cubic-bezier(0.16,1,0.3,1), color 0.25s, font-size 0.25s;
}
.cf-label.float,
.cf-field.focused .cf-label,
.cf-field.filled .cf-label {
  transform: translateY(-1.5rem) scale(0.82);
  color: #00B894;
}
.cf-field.error .cf-label { color: #e53e3e; }

.cf-required { color: #e53e3e; font-size: 0.8rem; }

/* Input */
.cf-input,
.cf-select,
.cf-textarea {
  width: 100%; border: none; outline: none; background: transparent;
  font-family: 'Tajawal', sans-serif;
  font-size: 0.95rem; font-weight: 500; color: #1A2B4C;
  padding: 0.5rem 0; line-height: 1.5;
  appearance: none; -webkit-appearance: none;
}
.cf-input::placeholder,
.cf-textarea::placeholder { opacity: 0; }

/* Bottom line */
.cf-field-line {
  position: absolute; bottom: 0; right: 0; left: 0;
  height: 1.5px; background: rgba(26,43,76,0.12);
  transition: all 0.3s;
}
.cf-field-line::after {
  content: ''; position: absolute; inset: 0;
  background: linear-gradient(90deg, #00B894, #55E6C1);
  transform: scaleX(0); transform-origin: right;
  transition: transform 0.35s cubic-bezier(0.16,1,0.3,1);
  border-radius: 2px;
}
.cf-field.focused .cf-field-line::after { transform: scaleX(1); }
.cf-field.success .cf-field-line { background: rgba(0,184,148,0.2); }
.cf-field.success .cf-field-line::after { transform: scaleX(1); background: #00B894; }
.cf-field.error .cf-field-line { background: rgba(229,62,62,0.2); }
.cf-field.error .cf-field-line::after { transform: scaleX(1); background: #e53e3e; }

/* Select */
.cf-select-wrap { position: relative; }
.cf-select { cursor: pointer; padding-left: 1.5rem; }
.cf-select option { color: #1A2B4C; background: white; }
.cf-select-arrow {
  position: absolute; left: 0; top: 50%; transform: translateY(-50%);
  pointer-events: none; color: #9aa3b2;
  transition: color 0.3s, transform 0.3s;
}
.cf-field.focused .cf-select-arrow { color: #00B894; transform: translateY(-50%) rotate(180deg); }

/* Textarea */
.cf-textarea {
  resize: vertical; min-height: 120px; padding-top: 0.25rem;
  line-height: 1.7;
}
.cf-textarea-footer {
  display: flex; justify-content: space-between; align-items: center;
  margin-top: 0.35rem;
}
.cf-char-count {
  font-size: 0.72rem; color: #9aa3b2; font-weight: 500; margin-right: auto;
  transition: color 0.3s;
}
.cf-char-count.warn { color: #e88b00; }

/* Error messages */
.cf-error {
  display: block; font-size: 0.73rem; color: #e53e3e;
  font-weight: 600; margin-top: 0.35rem;
}
.cf-error--privacy { margin-top: -1rem; }

/* Privacy checkbox */
.cf-privacy {
  display: flex; align-items: flex-start; gap: 0.75rem; cursor: pointer;
  margin-top: -0.25rem;
}
.cf-checkbox { display: none; }
.cf-checkmark {
  flex-shrink: 0; width: 20px; height: 20px; border-radius: 6px;
  border: 1.5px solid rgba(26,43,76,0.2);
  background: white; margin-top: 1px;
  display: flex; align-items: center; justify-content: center;
  transition: all 0.25s cubic-bezier(0.34,1.56,0.64,1);
}
.cf-checkbox:checked ~ .cf-checkmark {
  background: #00B894; border-color: #00B894;
  transform: scale(1.1);
  box-shadow: 0 0 0 4px rgba(0,184,148,0.15);
}
.cf-privacy-text { font-size: 0.85rem; color: #5a6a85; line-height: 1.5; }
.cf-privacy-link { color: #00B894; font-weight: 600; text-decoration: none; }
.cf-privacy-link:hover { text-decoration: underline; }

/* Send error banner */
.cf-send-error {
  display: flex; align-items: flex-start; gap: 0.6rem;
  background: rgba(229,62,62,0.06);
  border: 1px solid rgba(229,62,62,0.2);
  color: #c53030; font-size: 0.85rem; font-weight: 600;
  padding: 0.85rem 1rem; border-radius: 12px; line-height: 1.5;
}
.cf-send-error svg { flex-shrink: 0; margin-top: 1px; }

/* Submit button */
.cf-submit {
  position: relative; overflow: hidden;
  width: 100%; padding: 1.1rem;
  background: #00B894; color: white; border: none;
  border-radius: 16px; cursor: pointer;
  font-family: 'Tajawal', sans-serif; font-size: 1rem; font-weight: 700;
  box-shadow: 0 8px 30px rgba(0,184,148,0.35);
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s;
  margin-top: 0.5rem;
}
.cf-submit:hover:not(:disabled) {
  transform: translateY(-4px) scale(1.01);
  box-shadow: 0 14px 40px rgba(0,184,148,0.5);
}
.cf-submit:disabled { opacity: 0.8; cursor: not-allowed; }

.cf-submit-fill {
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(255,255,255,0.2), transparent);
  transform: translateX(-100%);
  transition: transform 0.45s;
  border-radius: inherit;
}
.cf-submit:hover:not(:disabled) .cf-submit-fill { transform: translateX(0); }

.cf-submit-inner { display: inline-flex; align-items: center; gap: 0.6rem; justify-content: center; }

/* Loader */
.cf-loader { display: inline-flex; align-items: center; gap: 0.75rem; }
.cf-spinner {
  width: 18px; height: 18px; border-radius: 50%;
  border: 2px solid rgba(255,255,255,0.3);
  border-top-color: white;
  animation: spin 0.7s linear infinite;
  flex-shrink: 0;
}
@keyframes spin { to { transform: rotate(360deg); } }

/* ── Success state ── */
.cf-success {
  display: flex; flex-direction: column; align-items: center;
  text-align: center; padding: 2rem 1rem 1rem;
}
.cf-success-icon {
  width: 72px; height: 72px; border-radius: 50%;
  background: linear-gradient(135deg, #00B894, #55E6C1);
  display: flex; align-items: center; justify-content: center;
  margin-bottom: 1.5rem;
  box-shadow: 0 0 0 12px rgba(0,184,148,0.1);
  animation: popIn 0.6s cubic-bezier(0.34,1.56,0.64,1);
}
@keyframes popIn { from{transform:scale(0);opacity:0;} to{transform:scale(1);opacity:1;} }

.cf-success-title { font-size: 1.6rem; font-weight: 900; color: #1A2B4C; margin-bottom: 0.75rem; }
.cf-success-desc  { font-size: 0.95rem; color: #5a6a85; line-height: 1.7; margin-bottom: 2rem; }
.cf-success-desc strong { color: #1A2B4C; }

.cf-reset-btn {
  background: transparent; border: 1.5px solid rgba(0,184,148,0.3);
  color: #00B894; font-family: 'Tajawal', sans-serif;
  font-size: 0.9rem; font-weight: 700; padding: 0.65rem 1.75rem;
  border-radius: 12px; cursor: pointer;
  transition: all 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.cf-reset-btn:hover { background: rgba(0,184,148,0.08); transform: translateY(-2px); }

/* ── Transitions ── */
.err-enter-active, .err-leave-active { transition: all 0.25s; }
.err-enter-from { opacity: 0; transform: translateY(-4px); }
.err-leave-to   { opacity: 0; }

.success-fade-enter-active, .success-fade-leave-active { transition: all 0.4s cubic-bezier(0.16,1,0.3,1); }
.success-fade-enter-from { opacity: 0; transform: scale(0.95) translateY(10px); }
.success-fade-leave-to   { opacity: 0; transform: scale(0.95); }

.form-fade-enter-active, .form-fade-leave-active { transition: all 0.3s; }
.form-fade-enter-from, .form-fade-leave-to { opacity: 0; }

.btn-content-enter-active, .btn-content-leave-active { transition: all 0.2s; }
.btn-content-enter-from { opacity: 0; transform: translateY(6px); }
.btn-content-leave-to   { opacity: 0; transform: translateY(-6px); }
</style>