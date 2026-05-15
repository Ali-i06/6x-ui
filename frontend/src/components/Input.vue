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
  ---------------------------------------------------------------
*/

/* ── متغیرهای پایه ── */
:root {
  --xui-radius: 10px;
  --xui-ease: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --xui-duration: 0.28s;
  --xui-transition:
    border-color   var(--xui-duration) var(--xui-ease),
    box-shadow     var(--xui-duration) var(--xui-ease),
    background     var(--xui-duration) var(--xui-ease);

  /* light mode */
  --xui-border-idle:  rgba(0, 0, 0, 0.12);
  --xui-border-hover: rgba(22, 119, 255, 0.45);
  --xui-border-focus: rgba(22, 119, 255, 0.70);
  --xui-bg-idle:      rgba(255, 255, 255, 1);
  --xui-bg-hover:     rgba(250, 252, 255, 1);
  --xui-focus-shadow:
    0 0 0 3px rgba(22, 119, 255, 0.12),
    0 2px 8px  rgba(22, 119, 255, 0.08);
}

/* ── dark mode ── */
body.dark {
  --xui-border-idle:  rgba(255, 255, 255, 0.10);
  --xui-border-hover: rgba(64, 150, 255, 0.45);
  --xui-border-focus: rgba(64, 150, 255, 0.65);
  --xui-bg-idle:      rgba(255, 255, 255, 0.04);
  --xui-bg-hover:     rgba(255, 255, 255, 0.06);
  --xui-focus-shadow:
    0 0 0 3px rgba(64, 150, 255, 0.14),
    0 2px 10px rgba(64, 150, 255, 0.06);
}

/* ─── Simple input & textarea ─── */
input.xui-input.ant-input,
textarea.xui-input.ant-input {
  border-radius: var(--xui-radius) !important;
  border-color:  var(--xui-border-idle) !important;
  background:    var(--xui-bg-idle) !important;
  transition:    var(--xui-transition) !important;
}
input.xui-input.ant-input:hover,
textarea.xui-input.ant-input:hover {
  border-color: var(--xui-border-hover) !important;
  background:   var(--xui-bg-hover) !important;
}
input.xui-input.ant-input:focus,
textarea.xui-input.ant-input:focus {
  border-color: var(--xui-border-focus) !important;
  box-shadow:   var(--xui-focus-shadow) !important;
  background:   var(--xui-bg-idle) !important;
}

/* ─── Affix wrapper (prefix/suffix, password) ─── */
.xui-input.ant-input-affix-wrapper,
.xui-input.ant-input-affix-wrapper.ant-input-password {
  border-radius: var(--xui-radius) !important;
  border-color:  var(--xui-border-idle) !important;
  background:    var(--xui-bg-idle) !important;
  transition:    var(--xui-transition) !important;
}
.xui-input.ant-input-affix-wrapper:hover,
.xui-input.ant-input-affix-wrapper.ant-input-password:hover {
  border-color: var(--xui-border-hover) !important;
  background:   var(--xui-bg-hover) !important;
}
.xui-input.ant-input-affix-wrapper-focused,
.xui-input.ant-input-affix-wrapper:focus-within {
  border-color: var(--xui-border-focus) !important;
  box-shadow:   var(--xui-focus-shadow) !important;
  background:   var(--xui-bg-idle) !important;
}

/* داخل affix wrapper — بدون border/radius مجزا */
.xui-input.ant-input-affix-wrapper .ant-input {
  border-radius: 0 !important;
  box-shadow:    none !important;
  background:    transparent !important;
  border-color:  transparent !important;
}

/* ─── Number input ─── */
.xui-input.ant-input-number,
.xui-input.ant-input-number-affix-wrapper {
  border-radius: var(--xui-radius) !important;
  border-color:  var(--xui-border-idle) !important;
  background:    var(--xui-bg-idle) !important;
  transition:    var(--xui-transition) !important;
}
.xui-input.ant-input-number:hover,
.xui-input.ant-input-number-affix-wrapper:hover {
  border-color: var(--xui-border-hover) !important;
  background:   var(--xui-bg-hover) !important;
}
.xui-input.ant-input-number-focused,
.xui-input.ant-input-number:focus-within,
.xui-input.ant-input-number-affix-wrapper-focused {
  border-color: var(--xui-border-focus) !important;
  box-shadow:   var(--xui-focus-shadow) !important;
}
</style>
