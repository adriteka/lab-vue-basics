<template>
  <div class="card">
    <p class="title is-5">
      {{ props.title }}
    </p>
    <p class="subtitle is-6">
      {{ props.description }}
    </p>

    <hr />
    <p class="content">
      {{ props.content }}
    </p>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  title: {
    type: String,
    required: true,
    default: "Missing title",
  },
  description: {
    type: String,
  },
  content: {
    type: String,
    required: true,
    default: "Missing content",
  },
});
</script>

<style scoped>
.card {
  padding: 1rem;
}
.card > * {
  text-align: left;
}

hr {
  margin: 0.5rem 0;
}
</style>
