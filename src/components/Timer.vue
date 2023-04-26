<template>
  <div class="column is-flex is-align-items-center">
    <!-- o : serve para que haja uma conexão de propriedade entre o elemento pai e o filho 
    agora o @: é utilizado para adicionar um ouvinte de evento no componente filho-->
    <StopWacth :timeSeconds="timeSeconds" />
    <button type="button" class="button btn-timer" @click="start" :disabled="checker">
      <i class="fas fa-play"></i>Start
    </button>
    <button type="button" class="button btn-timer" @click="end" :disabled="!checker">
      <i class="fas fa-pause"></i>Stop
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopWacth from "./StopWacth.vue";
export default defineComponent({
  name: "Timer-Component",
  components: { StopWacth },
  //esse atributo emite um evento, ou seja, avisa ao elemento pai que algo occoreu
  emits: ["finishedTimer"],
  data() {
    return {
      watcher: 0,
      timeSeconds: 0,
      checker: false,
    };
  },
  methods: {
    start() {
      this.checker = !this.checker;
      this.watcher = setInterval(() => {
        this.timeSeconds += 1;
      }, 1000);
    },
    end() {
      this.checker = !this.checker;
      clearInterval(this.watcher);
      this.$emit("finishedTimer", this.timeSeconds);
      this.timeSeconds = 0;
    },
  },
});
</script>

<style>
p {
  color: #1b2552;
}
.btn-timer {
  margin-right: 10px;
  background-color: #1b2552;
  color: #e2ecf4;
}
.btn-timer:hover {
  color: var(--text-color-secondary);
}

.btn-timer:active {
  color: var(--text-color-secondary);
}
.btn-timer:focus {
  color: var(--text-color-secondary);
}

btn-timer i {
  color: #e2ecf4;
  margin-right: 5px;
}
</style>
