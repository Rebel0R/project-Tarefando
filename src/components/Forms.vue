<template>
  <div class="box forms">
    <div class="columns" role="form" aria-label="Input para recebimento de tarefas">
      <div class="column is-8">
        <input
          type="text"
          class="input form-input"
          :placeholder="placeholder"
          v-model="descriptionTask"
        />
      </div>
      <Timer @finishedTimer="endTask" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Timer from "./Timer.vue";
export default defineComponent({
  name: "Form-Component",
  components: { Timer },
  emits: ["savingTask"],
  data() {
    return {
      descriptionTask: "",
    };
  },
  props: {
    placeholder: {
      type: String,
      required: true,
    },
  },
  methods: {
    endTask(timeTotal: number): void {
      this.$emit("savingTask", {
        duration: timeTotal,
        description: this.descriptionTask,
      });
      const task: { description: string; duration: number } = {
        description: this.descriptionTask,
        duration: timeTotal,
      };
      const tasks: { description: string; duration: number }[] = JSON.parse(
        localStorage.getItem("tasks") ?? "[]"
      );
      tasks.push(task);
      localStorage.setItem("tasks", JSON.stringify(tasks));
      this.descriptionTask = "";
    },
  },
});
</script>

<style>
.forms {
  margin: 0.8rem;
  background-color: #e2ecf4;
}

.form-input {
  background-color: #e2ecf4;
  border-color: #9fbfe1;
}
.form-input::placeholder {
  color: #9fbfe1;
}
</style>
