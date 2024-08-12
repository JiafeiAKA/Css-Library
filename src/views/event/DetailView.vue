<script setup lang="ts">
import { toRefs, defineProps } from 'vue';
import { type Event } from '@/types'

const props = defineProps<{
  event: Event
  id: Event
}>()
const { event } = toRefs(props)
</script>
<template>
<p class="mt-8">{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
<p class="m-2">{{ event.description }}</p>
</template>