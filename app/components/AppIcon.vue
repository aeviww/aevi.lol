<script setup lang="ts">
// Hand-picked inline glyphs. Inline SVG keeps the sheet dependency-free,
// renders on first paint and inherits `currentColor` everywhere.
const paths: Record<string, string> = {
  "arrow-up-right": "M7 17 17 7M9 7h8v8",
  "arrow-down": "M12 5v14M5 12l7 7 7-7",
  "arrow-left": "M19 12H5m6-7-7 7 7 7",
  github:
    "M9 19c-4 1.5-4-2.5-6-3m12 5v-3.9a3.4 3.4 0 0 0-.9-2.6c3-.3 5.9-1.5 5.9-6.6a5.1 5.1 0 0 0-1.4-3.5 4.8 4.8 0 0 0-.1-3.6s-1.4-.4-4.5 1.7a12.3 12.3 0 0 0-6 0C4.9 1.4 3.5 1.8 3.5 1.8a4.8 4.8 0 0 0-.1 3.6A5.1 5.1 0 0 0 2 8.9c0 5.1 2.9 6.3 5.9 6.6A3.4 3.4 0 0 0 7 18v3",
  discord:
    "M18.9 5.6A16.7 16.7 0 0 0 14.8 4.4l-.3.7a12.4 12.4 0 0 1 3.7 1.2 12 12 0 0 0-9.3-.5 15.4 15.4 0 0 1 2.4-.7l-.3-.7a16.7 16.7 0 0 0-4.1 1.2C3.3 9.2 2.6 12.7 3 16.2a16.5 16.5 0 0 0 5 2.5l.6-1a10.6 10.6 0 0 1-1.7-.8l.4-.3a11.8 11.8 0 0 0 10.2 0l.4.3a10.6 10.6 0 0 1-1.7.8l.6 1a16.5 16.5 0 0 0 5-2.5c.5-4-.6-7.5-2.9-10.6ZM9.3 14c-.8 0-1.5-.8-1.5-1.7s.7-1.7 1.5-1.7 1.5.8 1.5 1.7-.7 1.7-1.5 1.7Zm5.4 0c-.8 0-1.5-.8-1.5-1.7s.7-1.7 1.5-1.7 1.5.8 1.5 1.7-.7 1.7-1.5 1.7Z",
  globe: "M12 3a9 9 0 1 0 0 18 9 9 0 0 0 0-18Zm-9 9h18M12 3a14 14 0 0 1 0 18 14 14 0 0 1 0-18Z",
  copy: "M9 9h9v9a2 2 0 0 1-2 2H9a2 2 0 0 1-2-2V9Zm-2 6H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h7a2 2 0 0 1 2 2v1",
  check: "m4 12.5 5 5L20 6.5",
  sun: "M12 4V2m0 20v-2m8-8h2M2 12h2m12.9-4.9 1.5-1.5M5.6 18.4l1.5-1.5m0-9.8L5.6 5.6m12.8 12.8-1.5-1.5M16 12a4 4 0 1 1-8 0 4 4 0 0 1 8 0Z",
  moon: "M20 14.5A8.5 8.5 0 0 1 9.5 4a8.5 8.5 0 1 0 10.5 10.5Z",
  command:
    "M15 6a3 3 0 1 1 3 3h-3V6Zm0 12a3 3 0 1 0 3-3h-3v3ZM9 6a3 3 0 1 0-3 3h3V6Zm0 12a3 3 0 1 1-3-3h3v3Zm0-9h6v6H9V9Z",
  eye: "M2 12s3.6-6 10-6 10 6 10 6-3.6 6-10 6-10-6-10-6Zm10 2.5a2.5 2.5 0 1 0 0-5 2.5 2.5 0 0 0 0 5Z",
  user: "M12 11a4 4 0 1 0 0-8 4 4 0 0 0 0 8Zm-8 10c0-3.3 3.6-5.5 8-5.5s8 2.2 8 5.5",
  rss: "M4 11a9 9 0 0 1 9 9M4 4a16 16 0 0 1 16 16M5.5 19a.5.5 0 1 0 0-1 .5.5 0 0 0 0 1Z",
  star: "m12 4 2.5 5.2 5.5.8-4 4 .9 5.5-4.9-2.6-4.9 2.6.9-5.5-4-4 5.5-.8L12 4Z",
};

const props = withDefaults(
  defineProps<{ name: string; size?: number | string; strokeWidth?: number }>(),
  { size: 16, strokeWidth: 1.6 },
);

const d = computed(() => paths[props.name] ?? "");
const filled = computed(() => props.name === "discord" || props.name === "command");
</script>

<template>
  <svg
    :width="size"
    :height="size"
    viewBox="0 0 24 24"
    :fill="filled ? 'currentColor' : 'none'"
    :stroke="filled ? 'none' : 'currentColor'"
    :stroke-width="strokeWidth"
    stroke-linecap="square"
    stroke-linejoin="miter"
    aria-hidden="true"
    focusable="false"
  >
    <path :d="d" />
  </svg>
</template>
