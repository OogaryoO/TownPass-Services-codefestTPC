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
  <div v-if="curEvent != null">
    <!-- put in event itself  -->
    <div class="flex-nowrap bg-slate-100 justify-center">
        <img :src="curEvent.img" alt="event image" class="w-full h-fit object-cover" />
      <div class="w-fit">
        <p class="text-4xl">{{ curEvent.title }} ({{ curEvent.date }})</p>
        <hr class="w-full border-2 border-primary-200" />
        <a :href="'//' + curEvent.link" target="_blank" class="text-xl ">
          活動詳細資訊
        </a>
        <hr class="w-full border-2 border-primary-200" />
        <p class="text-xl">{{ curEvent.description }}</p>
        <hr class="w-full border-2 border-primary-200" />
        <ul class="flex py-2 text-lg">
            <li>
              <RouterLink :to="{
                name: 'event-calendar',
              query: {
                  tag: curEvent.tag[0]
              }
              }" class="bg-slate-400 rounded-md h-fit w-fit text-center ml-1 mr-0.5 truncate"
              >{{ curEvent.tag[0] }}
              </RouterLink>
            </li>
            <li>
            <RouterLink :to="{
              name: 'event-calendar',
              query: {
                tag: curEvent.tag[1]
              }
            }" class="bg-slate-400 rounded-md h-fit w-fit text-center ml-1 mr-0.5 truncate"
              >{{ curEvent.tag[1] }}
            </RouterLink>
            </li>
            <li>
            <RouterLink :to="{
              name: 'event-calendar',
              query: {
                tag: curEvent.tag[2]
              }
            }" class=" flex-grow bg-slate-400 rounded-md h-fit w-fit text-center ml-1 mr-0.5 truncate"
              >{{ curEvent.tag[2] }}
            </RouterLink>
            </li>
          </ul>
      </div>
    </div>
  </div>
  <div v-else>
    <!-- test, should be cleaned b4 release  -->
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