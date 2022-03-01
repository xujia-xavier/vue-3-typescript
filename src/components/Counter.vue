<script setup lang="ts">
import { ref, onMounted } from "vue";
import fetchCount from "../services/fetchCount";
import ControlBar from './ControlBar.vue'
interface Props {
  limit: number
  alertMessageOnLimit?: string
}
const props = withDefaults(defineProps<Props>(),{
  alertMessageOnLimit: 'Can Not Go Any Higher'
});

const count = ref<number | null>(null);

onMounted(() => {
  fetchCount((initialCount) => {
    count.value = initialCount;
  });
});

function addCount(num: number) {
  if (count.value !== null) {
    if (count.value >= props.limit) {
      alert(props.alertMessageOnLimit)
    }
    else {
      count.value += num
    }
  }
}
</script>

<template>
  <p>{{ count  }} Times </p>
  <ControlBar
  @add-count="addCount"
  @reset-count="Count = 0"
  ></ControlBar>
</template>