<template>
  <div>
    One-way data binding <br />
    Two-way data binding <br />
    v-model -> formulários
  </div>
  <br />
  <div class="traço"></div>
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
  <div></div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "",
      sports: "",
      newsLatter: "",
      contract: false,
      colors: [],
    };
  },
  methods: {
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
