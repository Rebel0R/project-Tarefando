<template>
  <div class="noTask is-flex is-flex-direction-column is-align-items-center">
    <img class="banner" src="../assets/banner-noTask.svg" alt="Banner de Tarefas não realizadas" />
    <p class="noTask-text">Parece que você não está sendo muito produtivo hoje! 😥</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "No-Task",
});
</script>

<style scoped>
.banner {
  width: 38%;
}

.noTask-text {
  display: inline-block;
  color: var(--text-color-primary);
  font-family: "Roboto";
  font-size: 22px;
  font-weight: 500;
  position: relative;
  top: -10px;
}
</style>
