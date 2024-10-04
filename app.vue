<script setup lang="ts">
const loading = ref(false);
const selected = ref([]);

async function search(q: string) {
  loading.value = true;

  const users: any[] = await $fetch(
    'https://api.escuelajs.co/api/v1/products',
    { params: { title: q, offset: 0, limit: 10 } }
  );

  loading.value = false;

  return users;
}
</script>

<template>
  <USelectMenu
    v-model="selected"
    :loading="loading"
    :searchable="search"
    placeholder="Search for a user..."
    option-attribute="title"
    multiple
    trailing
    by="id"
  />
</template>
