<template>
  <div class="menu-container">
    <nav class="navbar navbar-light bg-transparent">
      <a class="navbar-brand d-flex logo-styles" href="#">
        <i class="far fa-newspaper"></i>[ INSIDE ]
      </a>
    </nav>
    <ul class="nav">
      <li class="nav-item">
        <nuxt-link
          to="/"
          class="nav-link item-styles"
          :class="clicked == 'todas' ? 'selection' : ''"
          @click.native="selected('todas')"
        >Todas</nuxt-link>
      </li>
      <li class="nav-item" v-for="a in tags" :key="a.id">
        <nuxt-link
          :to="'/categorie/' + a.slug"
          class="nav-link item-styles"
          @click.native="selected(a.id)"
          :class="clicked == a.id ? 'selection' : ''"
        >{{ a.name }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>


<script>
import axios from 'axios'
export default {
	name: 'Menu',

  data: () =>{
    return {
      tags: [],
      clicked: "todas"
    }
  },

  methods: {

    getData(){

      const url = 'https://newsletters.academlo.com/api/v1/tags'
      axios.get(url)
        .then(response => {
          this.tags = response.data
        })
        .catch(() =>{
          console.log("Error con la API")
        })

	},
	
	selected(selectedItem){
		this.clicked = selectedItem;
	}

  },

  created(){
    this.getData()
  }

}
</script>


<style scoped>
a.logo-styles {
  font-family: "Merriweather", serif;
  font-weight: bold;
  font-size: 1.45rem;
  color: tomato;
}

i {
  color: tomato;
  font-size: 2rem;
  margin-right: 10px;
}

.menu-container {
  border: 1px solid rgba(0, 0, 0, 0.1);
}

.item-styles {
  color: rgb(120, 120, 120);
}

.item-styles:hover {
  background: rgba(252, 228, 236, 0.5);
  color: black;
}

.selection {
  background: rgba(252, 228, 236, 0.5);
  color: black;
}
</style>