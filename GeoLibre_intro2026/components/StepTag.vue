<script setup lang="ts">
// Progress marker for the hands-on slides: which step we are on, and how long it takes.
withDefaults(defineProps<{ n: number, total?: number, min?: number }>(), { total: 6 })
</script>

<template>
  <div class="step-tag">
    <span class="step-label">Step {{ n }} of {{ total }}</span>
    <span class="step-bar" aria-hidden="true">
      <i v-for="i in total" :key="i" :class="{ done: i < n, now: i === n }" />
    </span>
    <span v-if="min" class="step-min">{{ min }} min</span>
  </div>
</template>

<style scoped>
.step-tag {
  position: absolute;
  top: 1.5rem;
  right: 3.5rem;
  display: flex;
  align-items: center;
  gap: 0.7rem;
  font-size: 0.8rem;
  color: var(--gl-ink-soft);
}
.step-label {
  font-weight: 600;
  color: var(--gl-teal);
}
.step-bar {
  display: flex;
  gap: 4px;
}
.step-bar i {
  width: 18px;
  height: 5px;
  border-radius: 3px;
  background: #d5dde0;
}
.step-bar i.done {
  background: var(--gl-teal);
  opacity: 0.45;
}
.step-bar i.now {
  background: var(--gl-orange);
}
</style>
