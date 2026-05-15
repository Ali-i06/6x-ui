<!--
  XInput — یک wrapper یکپارچه برای تمام input های پروژه
  type: 'text' (default) | 'password' | 'number' | 'textarea'
  تمام props و slots به Ant Design منتقل می‌شند.
-->
<script setup>
defineOptions({ inheritAttrs: false });

defineProps({
  type: {
    type: String,
    default: 'text',
  },
});
</script>

<template>
  <!-- Password -->
  <a-input-password
    v-if="type === 'password'"
    v-bind="$attrs"
    class="xui-input"
  >
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </a-input-password>

  <!-- Textarea -->
  <a-textarea
    v-else-if="type === 'textarea'"
    v-bind="$attrs"
    class="xui-input"
  >
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </a-textarea>

  <!-- Number -->
  <a-input-number
    v-else-if="type === 'number'"
    v-bind="$attrs"
    class="xui-input"
  >
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </a-input-number>

  <!-- Text (default) -->
  <a-input
    v-else
    v-bind="$attrs"
    class="xui-input"
  >
    <template v-for="(_, name) in $slots" #[name]="slotProps">
      <slot :name="name" v-bind="slotProps ?? {}" />
    </template>
  </a-input>
</template>

<style>
/*
  ---------------------------------------------------------------
  XUI Input — استایل‌های گلوبال (بدون scoped)
  برای تغییر شکل همه input های پروژه، فقط همین فایل رو ویرایش کن.
  ---------------------------------------------------------------
*/

/* ── متغیرهای پایه ── */
:root {
  --xui-radius: 10px;
  --xui-transition: border-color 0.22s cubic-bezier(0.4, 0, 0.2, 1),
                    box-shadow   0.22s cubic-bezier(0.4, 0, 0.2, 1),
                    background   0.22s cubic-bezier(0.4, 0, 0.2, 1),
                    transform    0.18s cubic-bezier(0.4, 0, 0.2, 1);
  --xui-focus-shadow: 0 0 0 3px rgba(22, 119, 255, 0.16);
  --xui-hover-lift: translateY(-1px);
}

/* ── Simple input & textarea ── */
input.xui-input.ant-input,
textarea.xui-input.ant-input {
  border-radius: var(--xui-radius) !important;
  transition: var(--xui-transition) !important;
}

input.xui-input.ant-input:hover,
textarea.xui-input.ant-input:hover {
  transform: var(--xui-hover-lift);
}

input.xui-input.ant-input:focus,
textarea.xui-input.ant-input:focus {
  border-radius: var(--xui-radius) !important;
  box-shadow: var(--xui-focus-shadow) !important;
  transform: var(--xui-hover-lift);
}

/* ── Affix wrapper (prefix/suffix, password) ── */
.xui-input.ant-input-affix-wrapper,
.xui-input.ant-input-affix-wrapper.ant-input-password {
  border-radius: var(--xui-radius) !important;
  transition: var(--xui-transition) !important;
}

.xui-input.ant-input-affix-wrapper:hover,
.xui-input.ant-input-affix-wrapper.ant-input-password:hover {
  transform: var(--xui-hover-lift);
}

.xui-input.ant-input-affix-wrapper-focused,
.xui-input.ant-input-affix-wrapper:focus-within {
  border-radius: var(--xui-radius) !important;
  box-shadow: var(--xui-focus-shadow) !important;
  transform: var(--xui-hover-lift);
}

/* داخل affix wrapper، خود input نباید border و radius مجزا داشته باشه */
.xui-input.ant-input-affix-wrapper .ant-input {
  border-radius: 0 !important;
  box-shadow: none !important;
}

/* ── Number input ── */
.xui-input.ant-input-number,
.xui-input.ant-input-number-affix-wrapper {
  border-radius: var(--xui-radius) !important;
  transition: var(--xui-transition) !important;
}

.xui-input.ant-input-number:hover,
.xui-input.ant-input-number-affix-wrapper:hover {
  transform: var(--xui-hover-lift);
}

.xui-input.ant-input-number-focused,
.xui-input.ant-input-number:focus-within,
.xui-input.ant-input-number-affix-wrapper-focused {
  border-radius: var(--xui-radius) !important;
  box-shadow: var(--xui-focus-shadow) !important;
  transform: var(--xui-hover-lift);
}

/* ── Dark theme focus shadow ── */
body.is-dark .xui-input.ant-input:focus,
body.is-dark .xui-input.ant-input-affix-wrapper-focused,
body.is-dark .xui-input.ant-input-affix-wrapper:focus-within,
body.is-dark .xui-input.ant-input-number-focused,
body.is-dark .xui-input.ant-input-number:focus-within {
  --xui-focus-shadow: 0 0 0 3px rgba(64, 150, 255, 0.20);
}
</style>
