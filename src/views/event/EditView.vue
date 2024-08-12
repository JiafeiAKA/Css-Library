<script setup lang="ts">
import { ref, toRefs } from 'vue';
import { useRouter } from 'vue-router';
import { useMessageStore } from '@/stores/message';
import { type Event } from '@/types';

const props = defineProps<{ 
  event: Event
  id: String
}>()
// eslint-disable-next-line @typescript-eslint/no-unused-vars
const { event } = toRefs(props);
const router = useRouter();
const store = useMessageStore();
const showMessage = ref(false);
const flashMessage = ref('');

const editEvent = () => {
  store.updateMessage('The data has been updated');
  setTimeout(() => {
    store.resetMessage();
  }, 3000);
  router.push({ name: 'event-detail-view', params: { id: props.event.id }});
};
</script>
<template>
    <div>
    <p class="mt-8">Edit event here</p>
    <button class="m-8 rounded-md ring ring-green-500 ring-offset-2 hover:scale-101 hover:shadow-sp" @click="edit">Edit here!</button>
    <div v-if="showMessage">
      {{ flashMessage }}
    </div>
  </div>
</template>