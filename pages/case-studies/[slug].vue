<script setup lang="ts">
const { params } = useRoute();
const slug = computed(() => params.slug as string);
</script>

<template>
	<ResourcePage :slug="slug" type="case-studies" />
</template>
