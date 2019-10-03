<template>
  <div class="card d-flex flex-row flex-wrap">
    <div class="card-img d-flex justify-content-center">
      <img
        :src="ruta"
        class="card-img-top"
        alt="..."
      />
    </div>
    <div class="card-body">
      <h5 class="card-title"> {{ titulo }} </h5>
      <p
        class="card-text text-justify p-styles"
      >{{ descripcion }}</p>
    </div>
    <a href="#" class="btn btn-primary btn-styles d-flex justify-content-center align-items-center position-relative">
        <i class="fas fa-envelope tomato position-absolute left"></i>
        <span>Vote</span>
        <i class="fas fa-chevron-right position-absolute right"></i>
    </a>
    <div class="range">
        <div class="range-value" :style="range(Number(votos), Number(objetivo))"></div>
    </div>
    <div class="info-range d-flex justify-content-between">
        <span class="subs">{{votos}} <br> SUBSCRIBED</span>
        <span class="targ"> {{objetivo}} <br> TARGET </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "VoteCard",
  props: {
      titulo: String,
      ruta: String,
      descripcion: String,
      votos: String,
      objetivo: String
  },
  methods: {
      range(valor_actual, valor_objetivo){
          var porcentaje = ( (valor_actual * valor_objetivo) / valor_objetivo );
          console.log("width: " + porcentaje + "%;");
          return ("width: " + porcentaje + "%;");
      }
  }
};
</script>


<style scoped>
.card {
  width: calc((100% / 4) - 20px);
  margin-bottom: 50px;
  background: transparent;
  border: none;
}

.tomato{
    color: tomato;
}

.left{
    left: 0;
    padding-left: 15px;
}

.right{
    right: 0;
    padding-right: 15px; 
}

.btn-styles{
    width: 100%;
    background: transparent;
    border: 3px solid rgba(0,0,0,0.15);
    color: rgba(0, 0, 0, 0.5);
    font-size: 1rem;
    line-height: 1.5rem;
}

.btn-styles:hover{
    color: white;
    background: rgba(0,0,0,0.15);
}

.card-img {
  width: 20%;
}


img {
  border-radius: 50%;
  width: 70px;
  height: 70px;
}

.p-styles {
  color: rgba(0, 0, 0, 0.7);
  font-size: 0.90rem;
  line-height: 1.3rem;
}

.card-body{
    width: 50%;
    padding: 10px;
}

.range{
    background: rgb(199, 187, 187, 0.7);
    border-radius: 30px;
    width: 100%;
    height: 15px;
    margin-top: 20px;
    overflow: hidden;
    margin-bottom: 10px;
}

.range-value{
    background: tomato;
    width: 0;
    height: 100%;
    border-radius: 30px;
}

.info-range{
    width: 100%;
    font-size: 0.75rem;
    font-weight: bold;
}


</style>

