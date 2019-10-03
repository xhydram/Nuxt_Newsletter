<template>
  <div class="card">
    <div class="card-body">
      <h5 class="card-title">{{titulo}}</h5>
      <div class="card-img d-flex justify-content-center align-items-center position-relative">
        <img
          src="https://images.pexels.com/photos/2942361/pexels-photo-2942361.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500"
          class="card-img-top"
          alt="..."
          :style=" 'width:' + ancho + 'px; height: ' + alto + 'px;'"
        />
      </div>
    </div>
    <a href="#" class="btn btn-primary btn-styles">Get in Touch</a>
  </div>
</template>

<script>
export default {
  name: "TouchCard",
  props: {
    titulo: String,
    ancho: String,
    alto: String
  }
};
</script>


<style scoped>
.card {
  width: calc((100% / 4) - 20px);
  margin-bottom: 50px;
  border: none;
}

.card-title {
  font-weight: bold;
}

.tomato {
  color: tomato;
}

.btn-styles {
  width: 100%;
  background: tomato;
  border: 3px solid rgba(0, 0, 0, 0.15);
  color: white;
  font-size: 1rem;
  line-height: 1.5rem;
  font-weight: bold;
}

.btn-styles:hover {
  color: rgba(0, 0, 0, 0.4);
  background: rgba(245, 80, 51, 0.7);
}

.card-img {
  width: 100%;
}

img {
  border-radius: 50%;
  width: 100px;
  height: 100px;
}

.p-styles {
  color: rgba(0, 0, 0, 0.7);
  font-size: 0.95rem;
  line-height: 1.35rem;
}
</style>

