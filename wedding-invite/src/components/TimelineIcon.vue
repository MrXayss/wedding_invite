<template>
  <svg
    v-if="name === 'glasses'"
    viewBox="0 0 24 24"
    class="timeline-icon"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    >
    <path d="M7 4H12L10.8 10.2C10.5 11.9 9.1 13.1 7.4 13.1C5.7 13.1 4.3 11.9 4 10.2L3 4H7Z" />
    <path d="M12 4H17L18 10.2C18.3 11.9 16.9 13.1 15.2 13.1C13.5 13.1 12.1 11.9 11.8 10.2L10.6 4H12Z" />
    <path d="M7.4 13.1V18" />
    <path d="M15.2 13.1V18" />
    <path d="M5.2 18H9.6" />
    <path d="M13 18H17.4" />
    <path d="M4.3 7H11.4" />
    <path d="M11.4 7H17.7" />
    </svg>

  <svg
  v-else-if="name === 'rings'"
  viewBox="0 0 24 24"
  class="timeline-icon"
  fill="none"
  xmlns="http://www.w3.org/2000/svg"
>
  <circle cx="8.7" cy="14.3" r="4.3" />
  <circle cx="14.1" cy="14.3" r="4.3" />

  <path
  d="M11.8 7.4C11.8 6.4 12.5 5.8 13.4 5.8C14 5.8 14.5 6.1 14.8 6.6C15.1 6.1 15.6 5.8 16.2 5.8C17.1 5.8 17.8 6.4 17.8 7.4C17.8 9 15.8 10.2 14.8 11C13.8 10.2 11.8 9 11.8 7.4Z"
/>
</svg>

  <svg
  v-else-if="name === 'dinner'"
  viewBox="0 0 24 24"
  class="timeline-icon"
  fill="none"
  xmlns="http://www.w3.org/2000/svg"
>
  <circle cx="12" cy="12.5" r="5.2" />
  <circle cx="12" cy="12.5" r="2.4" />
  <path d="M4.2 5V12" />
  <path d="M2.8 5V8.4" />
  <path d="M5.6 5V8.4" />
  <path d="M2.8 8.4H5.6" />
  <path d="M4.2 12V19" />
  <path d="M19.4 5C18.2 6.4 17.7 8 17.7 10.1V12.3H20.5" />
  <path d="M20.5 5V19" />
</svg>

  <svg
  v-else-if="name === 'fireworks'"
  viewBox="0 0 24 24"
  class="timeline-icon"
  fill="none"
  xmlns="http://www.w3.org/2000/svg"
>
  <path d="M8 6V8.5" />
  <path d="M8 13.5V16" />
  <path d="M3 11H5.5" />
  <path d="M10.5 11H13" />
  <path d="M4.5 7.5L6.3 9.3" />
  <path d="M9.7 12.7L11.5 14.5" />
  <path d="M11.5 7.5L9.7 9.3" />
  <path d="M6.3 12.7L4.5 14.5" />

  <path d="M17 4V5.8" />
  <path d="M17 10.2V12" />
  <path d="M13 8H14.8" />
  <path d="M19.2 8H21" />
  <path d="M14.2 5.2L15.5 6.5" />
  <path d="M18.5 9.5L19.8 10.8" />
  <path d="M19.8 5.2L18.5 6.5" />
  <path d="M15.5 9.5L14.2 10.8" />

  <path d="M15 16.5L15.6 17.7L16.8 18.3L15.6 18.9L15 20.1L14.4 18.9L13.2 18.3L14.4 17.7L15 16.5Z" />
</svg>

  <svg
    v-else
    viewBox="0 0 24 24"
    class="timeline-icon"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
  >
    <circle cx="12" cy="12" r="5" />
  </svg>
</template>

<script setup>
defineProps({
  name: {
    type: String,
    default: '',
  },
})
</script>

<style scoped>
.timeline-icon {
  width: 24px;
  height: 24px;
  stroke: currentColor;
  stroke-width: 1.4;
  stroke-linecap: round;
  stroke-linejoin: round;
}
</style>