<script setup lang="ts">
// Download link for a file in public/data/.
// Uses the build's base path, so it works locally and on GitHub Pages.
const props = defineProps<{ file: string }>()
const href = `${import.meta.env.BASE_URL}data/${props.file}`
</script>

<template>
  <a :href="href" download class="data-file">
    <carbon:download class="data-file-icon" />
    <span><slot>{{ file }}</slot></span>
  </a>
</template>

<style scoped>
.data-file {
  display: inline-flex;
  align-items: center;
  gap: 0.4em;
  padding: 0.2em 0.65em;
  border: 1.5px solid var(--gl-teal);
  border-radius: 6px;
  color: var(--gl-teal);
  font-family: var(--slidev-code-font-family, ui-monospace, monospace);
  font-size: 0.82em;
  text-decoration: none;
  border-bottom: 1.5px solid var(--gl-teal);
}
.data-file:hover {
  background: var(--gl-teal);
  color: #fff;
}
.data-file-icon {
  flex: none;
}
</style>
