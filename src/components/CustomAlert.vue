<script setup lang="ts">
import CustomButton from "./CustomButton.vue";

type Theme = "info" | "error" | "warning" | "success";

defineProps<{
  theme: Theme;
}>();

const infoIcon = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  viewBox="0 0 24 24"
  fill="#2C75DD"
  stroke="none"
>
  <path
    d="M12 2C6.4898 2 2 6.4898 2 12C2 17.5102 6.4898 22 12 22C17.5102 22 22 17.5102 22 12C22 6.4898 17.5102 2 12 2ZM12.8163 15.5714C12.8163 15.9796 12.5102 16.3878 12 16.3878C11.4898 16.3878 11.1837 16.0816 11.1837 15.5714V11.4898C11.1837 11.0816 11.4898 10.6735 12 10.6735C12.5102 10.6735 12.8163 10.9796 12.8163 11.4898V15.5714ZM12 9.44898C11.4898 9.44898 10.9796 8.93878 10.9796 8.42857C10.9796 7.91837 11.4898 7.40816 12 7.40816C12.5102 7.40816 13.0204 7.91837 13.0204 8.42857C13.0204 8.93878 12.5102 9.44898 12 9.44898Z"
  />
</svg>
`;

const errorIcon = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  viewBox="0 0 24 24"
  fill="#CC3123"
  stroke="none"
>
  <path
    d="M12,2 C17.523,2 22,6.478 22,12 C22,17.522 17.523,22 12,22 C6.477,22 2,17.522 2,12 C2,6.478 6.477,2 12,2 Z M12.0018002,15.0037242 C11.450254,15.0037242 11.0031376,15.4508407 11.0031376,16.0023869 C11.0031376,16.553933 11.450254,17.0010495 12.0018002,17.0010495 C12.5533463,17.0010495 13.0004628,16.553933 13.0004628,16.0023869 C13.0004628,15.4508407 12.5533463,15.0037242 12.0018002,15.0037242 Z M11.99964,7 C11.4868042,7.00018474 11.0642719,7.38637706 11.0066858,7.8837365 L11,8.00036004 L11.0018003,13.0012393 L11.00857,13.117858 C11.0665141,13.6151758 11.4893244,14.0010638 12.0021602,14.0008793 C12.514996,14.0006946 12.9375283,13.6145023 12.9951144,13.1171428 L13.0018002,13.0005193 L13,7.99964009 L12.9932303,7.8830214 C12.9352861,7.38570354 12.5124758,6.99981552 11.99964,7 Z"
  ></path>
</svg>
`;

const warningIcon = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  viewBox="0 0 24 24"
  fill="#DC5A00"
  stroke="none"
>
  <rect
    width="24"
    height="24"
    transform="rotate(90 12 12)"
    opacity="0"
  />
  <path
    d="M22.56 16.3L14.89 3.58a3.43 3.43 0 0 0-5.78 0L1.44 16.3a3 3 0 0 0-.05 3A3.37 3.37 0 0 0 4.33 21h15.34a3.37 3.37 0 0 0 2.94-1.66 3 3 0 0 0-.05-3.04zM12 17a1 1 0 1 1 1-1 1 1 0 0 1-1 1zm1-4a1 1 0 0 1-2 0V9a1 1 0 0 1 2 0z"
  />
</svg>
`;

const successIcon = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24px"
  height="24px"
  viewBox="0 0 24 24"
  fill="#008700"
  stroke="none"
>
  <path
    d="M12,2A10,10,0,1,0,22,12,10.016,10.016,0,0,0,12,2Zm4.71,8.71-5,5a1.014,1.014,0,0,1-1.42,0l-3-3a1,1,0,1,1,1.42-1.42L11,13.59l4.29-4.3a1,1,0,0,1,1.42,1.42Z"
  />
</svg>
`;

const closeIcon = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  viewBox="0 0 24 24"
  stroke="#566271"
  stroke-width="1.5"
  fill="none"
  stroke-linecap="round"
  stroke-linejoin="round"
>
  <path stroke="none" d="M0 0h24v24H0z" fill="none" />
  <line x1="18" y1="6" x2="6" y2="18" />
  <line x1="6" y1="6" x2="18" y2="18" />
</svg>
`;
</script>

<template>
  <div
    :class="[
      'alert-box',
      `alert-box-${theme}`,
      `${!($slots.title && $slots.content) ? 'alert-box-text-only' : ''}`,
    ]"
  >
    <div class="icon" v-if="theme === 'info'" v-html="infoIcon()" />
    <div class="icon" v-if="theme === 'error'" v-html="errorIcon()" />
    <div class="icon" v-if="theme === 'warning'" v-html="warningIcon()" />
    <div class="icon" v-if="theme === 'success'" v-html="successIcon()" />

    <div class="alert-body">
      <template v-if="$slots.title">
        <h3>
          <slot name="title" />
        </h3>
      </template>
      <template v-if="$slots.content">
        <p>
          <slot name="content" />
        </p>
      </template>
      <template
        v-if="
          $slots.title &&
          $slots.content &&
          $slots.alertButtonSecondaryText &&
          $slots.alertButtonPrimaryText
        "
      >
        <div class="alert-buttons">
          <CustomButton :theme="theme" type="secondary" icon="none">
            <slot name="alertButtonSecondaryText" />
          </CustomButton>
          <CustomButton :theme="theme" type="primary" icon="none">
            <slot name="alertButtonPrimaryText" />
          </CustomButton>
        </div>
      </template>
    </div>

    <div class="close-icon" v-html="closeIcon()" />
  </div>
</template>

<style scoped>
.alert-box {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 12px;
  padding: 24px;
  margin: 12px 0;
  border-radius: 4px;
  color: var(--dark);
}

.alert-body {
  margin: 0;
  font-size: 16px;
  line-height: 24px;
  flex-grow: 1;
}

.alert-box h3 {
  margin: 0 0 8px 0;
  font-weight: 600;
}

.alert-box-text-only {
  align-items: center;
  padding: 12px;
}

.alert-box-text-only h3 {
  margin: 0;
}

.icon {
  display: flex;
  align-items: center;
}

.alert-box-info {
  background-color: var(--primary-light);
  border: 1px solid var(--primary);
  stroke: var(--primary);
}

.alert-box-error {
  background-color: var(--error-light);
  border: 1px solid var(--error);
  stroke: var(--error);
}

.alert-box-warning {
  background-color: var(--warning-light);
  border: 1px solid var(--warning);
  stroke: var(--warning);
}

.alert-box-success {
  background-color: var(--success-light);
  border: 1px solid var(--success);
  stroke: var(--success);
}

.alert-buttons {
  display: flex;
  gap: 16px;
  margin: 16px 0 0 0;
}

.close-icon {
  cursor: pointer;
  display: flex;
}

@media (max-width: 768px) {
  .alert-buttons {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
