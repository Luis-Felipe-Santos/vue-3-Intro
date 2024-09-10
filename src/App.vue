<template>
  <div>
    One-way data binding <br />
    Two-way data binding <br />
    v-model -> formulários
  </div>
  <br />
  <div class="traço"></div>
  <h1>Eventos</h1>
  <div>
    <label>Nome</label><br />
    <input v-model="name" type="text" />
    <br />
    {{ name }}
  </div>
  <br />
  <div class="traço"></div>
  <div>
    <label>Sports</label> <br />
    <select v-model="sports">
      <option value="">Escolha</option>
      <option value="Futebol">Futebol</option>
      <option value="Skate">Skate</option>
      <option value="Tenis">Tenis</option>
    </select>
    <br />
    {{ sports }}
  </div>
  <br />
  <div class="traço"></div>
  <div>
    <label>NewsLater</label><br />
    <input v-model="newsLatter" type="radio" value="Sim" /> Sim
    <input v-model="newsLatter" type="radio" value="Não" /> Não <br />
    {{ newsLatter }}
  </div>
  <br />
  <div class="traço"></div>
  <div>
    <label>Contrato</label><br />
    <input v-model="contract" type="checkbox" value="Sim" /> Aceita nossos
    termos...
    <br />
    {{ contract }}
  </div>
  <br />
  <div class="traço"></div>
  <div>
    <label>Cores que você mais gosta</label><br />
    <input v-model="colors" type="checkbox" value="Azul" /> Azul
    <input v-model="colors" type="checkbox" value="Amarelo" /> Amarelo
    <br />
    {{ colors }}
  </div>
  <div class="traço"></div>
  <div>
    <button v-on:click="onClick()">Enviar</button>
  </div>
  <br />
  <div class="traço"></div>
  <div @mouseover="onMouseOver()" @mouseout="onMouseOut()">Mouse over</div>
  <br />
  <div class="traço"></div>
  <form action="https://google.com" @submit.prevent="onSubmit">
    <button type="submit">Enviar</button>
  </form>
  <br />
  <div class="traço"></div>
  <div>
    <h1>Computed</h1>
    {{ fullName }}
    <h2 class="text-">Todos em aberto</h2>
    <div v-for="todo in uncompletedTodos" :key="todo.id">
      {{ todo.title }}
    </div>
    <h2>Todos completas</h2>
    <div v-for="todo in completedTodos" :key="todo.id">
      {{ todo.title }}
    </div>
    <br /><br />
    <h2>Todos</h2>
    <div v-for="todo in todos" :key="todo.id">
      <input v-model="todo.completed" type="checkbox" />
      {{ todo.title }}
    </div>
  </div>
  <br /><br />
  <div class="traço"></div>
  <div>
    <h1>Watch</h1>
    <input v-model="name" type="text" />
    <br />
    {{ name }}
    <br /><br />
    <input v-model="user.first_name" type="text" />
    <input v-model="user.last_name" type="text" />
    <br />
    {{ user.first_name }} {{ user.last_name }} <br /><br />
    <select v-model="pageCount">
      <option value="5">5</option>
      <option value="10">10</option>
      <option value="15">15</option>
    </select>
    <br />
    {{ pageCount }}
  </div>
  <br />
  <div class="traço"></div>
  <div>
    <h1>Life Cycle</h1>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      pageCount: 5,
      user: {
        first_name: "",
        last_name: "",
      },
      todos: [
        {
          userId: 1,
          id: 1,
          title: "delectus aut autem",
          completed: false,
        },
        {
          userId: 1,
          id: 2,
          title: "quis ut nam facilis et officia qui",
          completed: false,
        },
        {
          userId: 1,
          id: 3,
          title: "fugiat veniam minus",
          completed: false,
        },
        {
          userId: 1,
          id: 4,
          title: "et porro tempora",
          completed: true,
        },
        {
          userId: 1,
          id: 5,
          title:
            "laboriosam mollitia et enim quasi adipisci quia provident illum",
          completed: false,
        },
      ],
      name: "",
      sports: "",
      newsLatter: "",
      contract: false,
      colors: [],
    };
  },
  watch: {
    name(vl) {
      if (vl.length >= 3) {
        this.saveUserName();
      }
    },
    pageCount() {
      this.changePage();
    },
    user: {
      handler(user) {
        console.log(
          "Usuario alterado: " + user.first_name + " " + user.last_name
        );
      },
      deep: true,
    },
  },
  computed: {
    fullName() {
      return `${this.user.first_name} ${this.user.last_name}`;
    },
    uncompletedTodos() {
      return this.todos.filter((todo) => !todo.completed);
    },
    completedTodos() {
      return this.todos.filter((todo) => todo.completed);
    },
  },
  methods: {
    changePage() {
      console.log("Ajax changePage");
    },
    saveUserName() {
      console.log("Ajax");
      console.log(this.name);
    },
    onClick() {
      console.log("Clicou");
    },
    onMouseOver() {
      console.log("Mouse over");
    },
    onMouseOut() {
      console.log("Mouse out");
    },
    onSubmit() {
      console.log("submit");
    },
  },
};
</script>

<style>
.traço {
  border: 0;
  border-top: 1px solid #000;
  margin: 20px 0;
}
.todos-items {
  background: #000;
  margin: 0 0 5px 0;
  padding: 3px 6px;
  color: #fff;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px;
}
</style>
