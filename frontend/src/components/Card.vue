<!--
  XCard — کارت یکپارچه پروژه
  جایگزین a-card در تمام پیج‌ها.
  تمام slots (title, extra, actions, cover, ...) و attrs
  به صورت شفاف پاس‌ داده می‌شوند.
-->
<script setup>
defineOptions({ inheritAttrs: false });
</script>

<template>
  <a-card
    v-bind="$attrs"
    class="xui-card"
  >
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </a-card>
</template>

<style>
/*
  ---------------------------------------------------------------
  XUI Card — استایل‌های گلوبال (بدون scoped)
  برای تغییر شکل همه کارت‌های پروژه، فقط همین فایل رو ویرایش کن.
  ---------------------------------------------------------------
*/

/* ── متغیرهای پایه ── */
:root {
  --xcard-radius:       14px;
  --xcard-ease:         cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --xcard-duration:     0.30s;

  /* light */
  --xcard-bg:           rgba(255, 255, 255, 0.92);
  --xcard-border:       rgba(0, 0, 0, 0.07);
  --xcard-border-hover: rgba(22, 119, 255, 0.22);
  --xcard-shadow:
    0 1px  3px rgba(0, 0, 0, 0.06),
    0 4px 12px rgba(0, 0, 0, 0.05);
  --xcard-shadow-hover:
    0 4px  16px rgba(22, 119, 255, 0.10),
    0 8px  32px rgba(0,   0,   0,   0.08);
  --xcard-header-border: rgba(0, 0, 0, 0.06);
}

/* ── dark mode ── */
body.dark {
  --xcard-bg:           rgba(37, 37, 38, 0.95);
  --xcard-border:       rgba(255, 255, 255, 0.07);
  --xcard-border-hover: rgba(64, 150, 255, 0.24);
  --xcard-shadow:
    0 1px  4px rgba(0, 0, 0, 0.25),
    0 4px 14px rgba(0, 0, 0, 0.20);
  --xcard-shadow-hover:
    0 4px  18px rgba(64, 150, 255, 0.10),
    0 8px  32px rgba(0,   0,   0,  0.30);
  --xcard-header-border: rgba(255, 255, 255, 0.06);
}

/* ── ultra-dark ── */
html[data-theme="ultra-dark"] body.dark {
  --xcard-bg:           rgba(12, 14, 18, 0.96);
  --xcard-border:       rgba(255, 255, 255, 0.05);
  --xcard-border-hover: rgba(64, 150, 255, 0.20);
  --xcard-shadow:
    0 1px  4px rgba(0, 0, 0, 0.50),
    0 4px 16px rgba(0, 0, 0, 0.40);
  --xcard-shadow-hover:
    0 4px  20px rgba(64, 150, 255, 0.08),
    0 10px 36px rgba(0,   0,   0,  0.50);
  --xcard-header-border: rgba(255, 255, 255, 0.04);
}

/* ─── بدنه کارت ─── */
.xui-card.ant-card {
  border-radius:  var(--xcard-radius) !important;
  border:         1px solid var(--xcard-border) !important;
  background:     var(--xcard-bg) !important;
  box-shadow:     var(--xcard-shadow) !important;
  backdrop-filter: blur(2px);
  transition:
    border-color var(--xcard-duration) var(--xcard-ease),
    box-shadow   var(--xcard-duration) var(--xcard-ease),
    transform    var(--xcard-duration) var(--xcard-ease) !important;
  will-change: transform, box-shadow;
}

/* hoverable — خیلی ملایم‌تر از حالت قبل */
.xui-card.ant-card-hoverable:hover {
  border-color: var(--xcard-border-hover) !important;
  box-shadow:   var(--xcard-shadow-hover) !important;
  transform:    translateY(-2px) !important;
}

/* ─── هدر ─── */
.xui-card.ant-card .ant-card-head {
  border-bottom:    1px solid var(--xcard-header-border) !important;
  border-radius:    var(--xcard-radius) var(--xcard-radius) 0 0 !important;
  background:       transparent !important;
  padding-inline:   20px;
  min-height:       48px;
  font-weight:      600;
  letter-spacing:   0.01em;
}

/* ─── بدنه محتوا ─── */
.xui-card.ant-card .ant-card-body {
  padding: 20px;
}

/* ─── فوتر (actions) ─── */
.xui-card.ant-card .ant-card-actions {
  border-top:    1px solid var(--xcard-header-border) !important;
  border-radius: 0 0 var(--xcard-radius) var(--xcard-radius) !important;
  background:    transparent !important;
}

.xui-card.ant-card .ant-card-actions > li {
  margin: 10px 0;
}

/* ─── گوشه‌های داخلی ─── */
.xui-card.ant-card .ant-card-actions > li:first-child {
  border-radius: 0 0 0 var(--xcard-radius) !important;
}
.xui-card.ant-card .ant-card-actions > li:last-child {
  border-radius: 0 0 var(--xcard-radius) 0 !important;
}
</style>
