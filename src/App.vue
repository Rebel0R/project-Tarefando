<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': setModeActive }">
    <div class="column is-one-quarter">
      <SideBar @changedTheme="changingTheme" />
    </div>
    <div class="column is-three-quarter content">
      <Forms placeholder="Qual tarefa você vai começar agora? 😏" @savingTask="saveTask" />
      <div class="list">
        <Task v-for="(task, index) in tasks" :key="index" :completedTask="task" />
        <div v-if="tasksEmpty">
          <NoTask />
        </div>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import Forms from "./components/Forms.vue";
import Task from "./components/Task.vue";
import TaskInterface from "./interface/TaskInterface";
import NoTask from "./components/NoTask.vue";

export default defineComponent({
  name: "App",
  data() {
    return {
      tasks: [] as TaskInterface[],
      setModeActive: false,
    };
  },
  computed: {
    tasksEmpty(): boolean {
      return this.tasks.length === 0;
    },
  },
  components: { SideBar, Forms, Task, NoTask },
  methods: {
    saveTask(task: TaskInterface) {
      this.tasks.push(task);
    },
    changingTheme(stage: boolean) {
      this.setModeActive = stage;
    },
  },
});
</script>

<style>
main {
  --bg-primary: #e2ecf4;
  --text-color-primary: #1b2552;
  --text-color-secondary: #52f28a;
}

main.dark-mode {
  --bg-primary: #1b2b76;
  --text-color-primary: #e2ecf4;
  --text-color-secondary: #52f28a;
}

.content {
  background-color: var(--bg-primary);
}
</style>
