<template>
  <div class="box task">
    <div class="columns">
      <div class="column is-7 is-flex is-align-items-center">
        <i class="fa-sharp fa-solid fa-thumbtack" style="color: #52f28a"></i>
        <p>{{ completedTask.description }}</p>
      </div>
      <div class="column is-flex is-align-items-center">
        <i class="fa-sharp fa-solid fa-stopwatch" style="color: #52f28a"></i>
        <StopWacth :timeSeconds="completedTask.duration" />
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
import StopWacth from "./StopWacth.vue";
import TaskInterface from "@/interface/TaskInterface";
export default defineComponent({
  name: "Task-Component",
  components: { StopWacth },
  props: {
    completedTask: {
      type: Object as PropType<TaskInterface>,
      required: true,
    },
  },
});
</script>

<style>
.task {
  margin: 0.8rem;
  background-color: var(--text-color-primary);
  font-family: "Roboto";
  font-weight: bold;
  font-size: 18px;
}
.task p {
  color: var(--bg-primary);
  margin-left: 10px;
}
</style>
