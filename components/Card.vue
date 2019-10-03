<template>
  <div class="card">
    <div class="card-img d-flex justify-content-center align-items-center position-relative">
      <img :src="ruta" class="card-img-top" alt="..." />
      <span class="tag position-absolute">DAILY</span>
    </div>
    <div class="card-body">
      <h5 class="card-title">{{ titulo }}</h5>
      <p class="card-text text-justify p-styles">{{ descripcion }}</p>
    </div>
    <a
      href="#"
      class="btn btn-primary btn-styles d-flex justify-content-center align-items-center position-relative"
      @click.prevent="register(ruta, titulo, descripcion)"
    >
      <i class="fas fa-envelope tomato position-absolute left"></i>
      <span>Subscribe</span>
      <i class="fas fa-chevron-right position-absolute right"></i>
    </a>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    titulo: String,
    ruta: String,
    descripcion: String,
    news_id: String
  },

  data: () =>{
    return {
      correo : "",
      subscribed_info: {
        email : '',
        newsletter_id : 0
      }
    }
  },

  methods: {
    register(i, t, d) {
      const html_var = `
                     
                <div class="alert-container">
                    <div class="image-container">
                            <img src="${i}" class="image-style" style="border-radius: 50%;"/>
                    </div>
                    <div class="description-container">
                        <h3 class="tittle">${t}</h3>
                        <p class="content">
                                ${d}
                        </p>
                    </div>
                </div>
            `;

      (async () => {
        const { value: email } = await Swal.fire({
          input: "email",
          html: html_var,
          inputPlaceholder: "Ingresa tu correo electronico",
          confirmButtonColor: "tomato",
          confirmButtonText: "Subscribe"
        });

        if (email) {
          Swal.fire(email + " subscribed to : " + t);
          this.subscribed_info.email = email;
          this.subscribed_info.newsletter_id = Number(this.news_id);
          console.log(this.subscribed_info);


          const url = process.env.VUE_APP_API + '/users';
          
          axios.post(url,this.subscribed_info)
            .then(response => {
              console.log(response.data);
            })
            .catch(error => {
              console.log("Hubo un error en la conexion a la API");
            })


        }
      })()
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

.tomato {
  color: tomato;
}

.left {
  left: 0;
  padding-left: 15px;
}

.right {
  right: 0;
  padding-right: 15px;
}

.btn-styles {
  width: 100%;
  background: transparent;
  border: 3px solid rgba(0, 0, 0, 0.15);
  color: rgba(0, 0, 0, 0.5);
  font-size: 1rem;
  line-height: 1.5rem;
}

.btn-styles:hover {
  color: white;
  background: rgba(0, 0, 0, 0.15);
}

.card-img {
  width: 100%;
}

.tag {
  right: 0;
  top: 0;
  background: rgba(255, 204, 188, 0.5);
  padding: 5px;
  font-size: 0.7rem;
  border-radius: 5px;
  color: tomato;
  font-weight: bold;
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

