<!-- eslint-disable prettier-vue/prettier -->
<!-- eslint-disable prettier-vue/prettier -->
<!-- eslint-disable prettier-vue/prettier -->
<script setup lang="ts">
import { computed, ref } from 'vue';
import BaseInput from '@/components/atoms/BaseInput.vue';
import { useRoute, RouterLink } from 'vue-router';
import { useCalStore } from '../stores/calendar';
const route = useRoute();
const calStore = useCalStore(); 
const eventList= calStore.events
</script>

<template>
    <div class="p-12">
    <p class="text-[32px]">活動行事曆</p>
    
    <div class="py-12">
    <ul v-for="item in eventList" :key="item.id">
        <li>
            <img :src="item.img" alt="event image" class="w-10 h-10 object-cover">
          <p class="ml-1rem font-bold text-cyan-500">{{ item.title }}</p>
            <p class="text-">{{item.date}}</p>
            <div class="">
                <a class="bg-slate-400 rounded-md w-flex h-0.3 text-center ml-0.5 mr-0.5":style="{ width: `calc(${item.tag[0].length * 0.75}rem + 0.5rem)` }">{{item.tag[0]}}</a>
                <a class="bg-slate-400 rounded-md w-flex h-0.3 text-center ml-0.5 mr-0.5":style="{ width: `calc(${item.tag[0].length * 0.75}rem + 0.5rem)` }">{{item.tag[1]}}</a>
                <a class="bg-slate-400 rounded-md w-flex h-0.3 text-center ml-0.5 mr-0.5":style="{ width: `calc(${item.tag[0].length * 0.75}rem + 0.5rem)` }">{{item.tag[2]}}</a>
            </div>
        </li>
    </ul>
    </div>
</div>
</template>