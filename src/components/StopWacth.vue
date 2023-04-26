<template>
  <div class="stopwatch">
    <p>{{ elapsedTime }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "StopWacth-Component",
  props: {
    timeSeconds: {
      type: Number,
      default: 0,
    },
  },
  //com base numa informação ele vai monitorá-la, verificando se houve alteração
  computed: {
    elapsedTime(): string {
      const cont = new Date(this.timeSeconds * 1000);
      const formatter = new Intl.DateTimeFormat("pt-BR", {
        hour: "2-digit",
        minute: "2-digit",
        second: "2-digit",
        timeZone: "UTC",
      });
      return formatter.format(cont);
      //return new Date(this.timeSeconds * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style>
.stopwatch {
  font-family: "Roboto";
  font-weight: 500;
  margin-right: 15px;
}
</style>
