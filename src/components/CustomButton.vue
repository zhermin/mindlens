<script setup lang="ts">
type Theme = "info" | "error" | "warning" | "success";
type ButtonType = "primary" | "secondary";
type IconType = "left" | "right" | "none";

defineProps<{
  theme: Theme;
  type: ButtonType;
  icon?: IconType;
}>();

const arrowRight = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  viewBox="0 0 24 24"
  stroke-width="1.5"
  fill="none"
  stroke-linecap="round"
  stroke-linejoin="round"
>
  <path stroke="none" d="M0 0h24v24H0z" fill="none" />
  <line x1="3" y1="12" x2="22" y2="12" />
  <line x1="16" y1="18" x2="22" y2="12" />
  <line x1="16" y1="6" x2="22" y2="12" />
</svg>
`;

const arrowLeft = () => `
<svg
  xmlns="http://www.w3.org/2000/svg"
  width="24"
  height="24"
  viewBox="0 0 24 24"
  stroke-width="1.5"
  fill="none"
  stroke-linecap="round"
  stroke-linejoin="round"
>
  <path stroke="none" d="M0 0h24v24H0z" fill="none" />
  <polyline points="15 6 9 12 15 18" />
</svg>
`;
</script>

<template>
  <button
    :class="[`button-${theme}-${type}`, `${!$slots.default && 'icon-only'}`]"
  >
    <template v-if="$slots.default && icon === 'left'">
      <div v-if="type === 'primary'" v-html="arrowRight()" />
      <div v-if="type === 'secondary'" v-html="arrowLeft()" />
      <slot />
    </template>
    <template v-if="$slots.default && icon === 'right'">
      <slot />
      <div v-html="arrowRight()" />
    </template>
    <template v-if="$slots.default && icon === 'none'">
      <slot />
    </template>
    <template v-if="!$slots.default">
      <div v-html="arrowRight()" />
    </template>
  </button>
</template>

<style scoped>
button {
  display: flex;
  place-items: center;
  place-content: center;
  border-radius: 8px;
  padding: 8px 24px;
  gap: 8px;

  font-size: 16px;
  line-height: 24px;
  font-weight: 600;
  text-align: center;

  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

button:hover {
  box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
}

button div {
  display: flex;
}
.icon-only {
  padding: 8px;
}

.button-info-primary {
  background: var(--info);
  border: none;
  stroke: #000000;
  color: #0c0d0d;
}

.button-info-primary:hover {
  background: var(--info-dark);
}

.button-info-secondary {
  background: #ffffff;
  border: 1px solid var(--warning);
  stroke: var(--warning);
  color: var(--warning);
}

.button-error-primary {
  background: var(--error);
  border: none;
  stroke: #ffffff;
  color: #ffffff;
}

.button-error-primary:hover {
  background: var(--error-dark);
}

.button-error-secondary {
  background: #ffffff;
  border: 1px solid var(--error);
  stroke: var(--error);
  color: var(--error);
}

.button-warning-primary {
  background: var(--warning);
  border: none;
  stroke: #ffffff;
  color: #ffffff;
}

.button-warning-primary:hover {
  background: var(--warning-dark);
}

.button-warning-secondary {
  background: #ffffff;
  border: 1px solid var(--warning);
  stroke: var(--warning);
  color: var(--warning);
}

.button-success-primary {
  background: var(--success);
  border: none;
  stroke: #ffffff;
  color: #ffffff;
}

.button-success-primary:hover {
  background: var(--success-dark);
}

.button-success-secondary {
  background: #ffffff;
  border: 1px solid var(--success);
  stroke: var(--success);
  color: var(--success);
}
</style>
