<template>
  <header class="sideBar is-flex is-flex-direction-column is-align-items-center">
    <img src="../assets/logo-tarefando.png" alt="Logo Tarefando" />
    <p>
      Lembre-se que seu cerébro também precisa descansar, por isso é importante aplicar pausas
      regulares durante suas tarefas!
    </p>
    <button type="button" class="button btn-mode" @click="changeTheme">
      <i class="fa-solid fa-sun" v-if="setMode"></i><i class="fa-sharp fa-solid fa-moon" v-else></i
      >{{ textButton }}
    </button>
    <button type="button" class="button btn-reload" @click="reloadPage">
      <i class="fa-solid fa-rotate"></i>Recarregar
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent({
  name: "Side-Bar",
  emits: ["changedTheme"],
  data() {
    return {
      setMode: false,
    };
  },
  computed: {
    textButton(): string {
      if (this.setMode) {
        return "Modo Claro";
      }
      return "Modo Escuro";
    },
  },
  methods: {
    changeTheme() {
      this.setMode = !this.setMode;
      this.$emit("changedTheme", this.setMode);
    },
    reloadPage() {
      const check = window.confirm(
        "Deseja recarregar a página? Todas as suas tarefas serão perdidas"
      );
      if (check) {
        location.reload();
      }
    },
  },
});
</script>

<style>
.sideBar {
  padding: 1rem;
  background-color: #1b2552;
  width: 100%;
  height: 100vh;
}
.sideBar img {
  width: 300px;
}
.sideBar p {
  margin: 20px;
  font-size: 14px;
  font-weight: 600;
  font-family: "Roboto", sans-serif;
  color: #e2ecf4;
  text-align: center;
  display: inline-block;
  width: 300px;
  height: 58px;
}
i {
  margin-right: 5px;
}
.btn-mode {
  margin: 15px;
  background-color: #e2ecf4;
  color: #9fbfe1;
}
.btn-mode:hover {
  color: #11193d;
}

.btn-mode:active {
  color: #9fbfe1;
  background-color: #11193d;
}
.btn-mode:focus {
  color: #9fbfe1;
  background-color: #11193d;
}

.btn-reload {
  background-color: transparent;
  border-color: #9fbfe1;
  color: #9fbfe1;
  width: 144px;
}
.btn-reload:hover {
  background-color: #9fbfe1;
  color: #131aa3;
}
.btn-reload:active {
  color: #131aa3;
  background-color: #9fbfe1;
}
.btn-reload:focus {
  color: #131aa3;
  background-color: #9fbfe1;
}
</style>
