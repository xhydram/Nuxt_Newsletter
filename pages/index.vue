<template>
  <div class="main-container text-center">
    <h3>Noticias reales, para humanos reales</h3>
    <span>Todas las categorias existentes para que siempre estes actualizado y en constante aprendizaje.</span>

    <div class="card-container d-flex flex-wrap justify-content-around">
      <Card
        v-for="a in data"
        v-if="a.subscribed >= Number(a.target)"
        :key="a.id"
        :titulo="a.title"
        :ruta="a.image"
        :descripcion="a.description"
        :news_id="a.id"
      ></Card>
      <TouchCard titulo="Interested in sponsoring a newsletter?" ancho="130" alto="130"></TouchCard>
    </div>

    <hr />
    <br />

    <h3>Proximas Categorias</h3>
    <span>Si deseas que agreguemos una categoria porque es de ayuda para ti, vota por tus favoritas</span>

    <div class="card-container d-flex flex-wrap justify-content-around">
      <VoteCard
        v-for="a in data"
        v-if="a.subscribed < Number(a.target)"
        :key="a.id"
        :titulo="a.title"
        :ruta="a.image"
        :descripcion="a.description"
        :votos="a.subscribed"
        :objetivo="a.target"
      ></VoteCard>
      <TouchCard titulo="Have an idea for a newsletter?" ancho="90" alto="90"></TouchCard>
    </div>


  </div>
</template>


<script>
import axios from 'axios'
import Card from '@@/components/Card'
import VoteCard from '@@/components/VoteCard'
import TouchCard from '@@/components/TouchCard'

export default {
  components: {
    Card,
    VoteCard,
    TouchCard
  },

  methods: {
    getData() {
      const url = "https://newsletters.academlo.com/api/v1/newsletters";
      axios
        .get(url)
        .then(response => {
          this.data = response.data;
        })
        .catch(() => {
          alert("Hubo un error");
        });
    }
  },

  data: () => {
    return {
      data: []
    };
  },

  created() {
    this.getData();
  }
}
</script>


<style scoped>
.main-container {
  width: 80%;
  min-height: 100vh;
  margin: 0 auto;
  padding-top: 50px;
}

.card-container {
  margin-top: 30px;
  width: 100%;
}
</style>