
<template>
  <header>
    <nav id="nav">
      <RouterLink to="/" class="logo-url"
        ><img :src="logo" :alt="alt" id="logo"
      /></RouterLink>
      <RouterLink to="/">Home</RouterLink> |
      <RouterLink to="/pedidos">
          Pedidos
      </RouterLink>
      <div class="pedido">{{ quantidade }}</div>
    </nav>
  </header>
</template>

<script>
export default {
  props: ["logo", "alt"],
  data(){
    return {
      quantidade: 0
    }
  },
  methods: {
    async getPedidos(){
      const req = await fetch("http://localhost:3000/burgers")
      const data = await req.json()
      this.quantidade = data.length
    }
  },
  mounted(){
    this.getPedidos()
  }
};
</script>

<style scoped>
#nav {
  background-color: #222;
  border-bottom: 2px solid #FCBA03;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav .logo-url {
  margin: auto;
  margin-left: 0;
}

#logo {
  width: 40px;
  height: 40px;
}

#nav a {
  color: #fcba03;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
}

#nav a:hover {
  color: #fff;
}

.pedido {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 4px 4px;
  background-color: #222;
  border: 2px solid #FCBA03;
  width: 30px;
  height: 30px;
  color: #fff;
}

</style>
