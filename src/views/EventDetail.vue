<script setup lang="ts">
import { computed, ref } from 'vue';
import BaseInput from '@/components/atoms/BaseInput.vue';
import { useRoute, RouterLink } from 'vue-router';
import { useCalStore } from '../stores/calendar';
const route = useRoute();
const calStore = useCalStore();
const eventList = calStore.events;
const curEvent = eval('eventList[' + "route.query.evnt" + ']')  ;
</script>

<template>
  <div class="bg-primary-500 block h-20 text-lg">
    <a @click="$router.back()" class="inline-block align-middle"> go back go back</a>
  </div>
  <div v-if="curEvent != null">
    <!-- put in event itself  -->
    <div class="flex justify-center">
      <div class="w-1/2">
        <img :src="curEvent.img" alt="event image" class="w-full h-96 object-cover" />
      </div>
      <div class="w-1/2">
        <p class="text-4xl">{{ curEvent.title }}</p>

        <div class="flex">
          <RouterLink
            :to="{ name: 'event-calendar', query: { tag: curEvent.tag[0] } }"
            class="bg-slate-400 rounded-md w-20 h-8 text-center ml-1 mr-0.5"
            >{{ curEvent.tag[0] }}
          </RouterLink>
          <RouterLink
            :to="{ name: 'event-calendar', query: { tag: curEvent.tag[1] } }"
            class="bg-slate-400 rounded-md w-20 h-8 text-center ml-1 mr-0.5"
            >{{ curEvent.tag[1] }}
          </RouterLink>
          <RouterLink
            :to="{ name: 'event-calendar', query: { tag: curEvent.tag[2] } }"
            class="bg-slate-400 rounded-md w-20 h-8 text-center ml-1 mr-0.5"
            >{{ curEvent.tag[2] }}
          </RouterLink>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <!-- put in test itself  -->
    <div class="flex justify-center">
      <div class="w-1/2">
        <img :src="curEvent.img" alt="event image" class="w-full h-96 object-cover" />
      </div>
      <div class="w-1/2">
        <p class="text-4xl">{{ curEvent.title }}</p>
        <p class="text-xl">{{ curEvent.description }}</p>
        <div class="flex">
          <RouterLink
            :to="{ name: 'event-calendar', query: { tag: curEvent.tag[0] } }"
            class="bg-slate-400 rounded-md w-20 h-8 text-center ml-1 mr-0.5"
            >{{ curEvent.tag[0] }}
          </RouterLink>
          <RouterLink
            :to="{ name: 'event-calendar', query: { tag: curEvent.tag[1] } }"
            class="bg-slate-400 rounded-md w-20 h-8 text-center ml-1 mr-0.5"
            >{{ curEvent.tag[1] }}
          </RouterLink>
          <RouterLink
            :to="{ name: 'event-calendar', query: { tag: curEvent.tag[2] } }"
            class="bg-slate-400 rounded-md w-20 h-8 text-center ml-1 mr-0.5"
            >{{ curEvent.tag[2] }}
          </RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>