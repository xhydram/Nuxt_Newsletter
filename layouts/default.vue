<template>
  <div>
    <link href="https://fonts.googleapis.com/css?family=Merriweather:400,900&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@8"></script>
    <script src="https://kit.fontawesome.com/e11a230b42.js" crossorigin="anonymous"></script>
    <Menu/>
    <div class="fluid-container fluid-styles">
      <nuxt />
    </div>
    <PiePagina/>
  </div>
</template>

<script>
import Menu from '@@/components/Menu'
import PiePagina from '@@/components/PiePagina'

export default {
  
  components: {
    Menu,
    PiePagina
  }

}
</script>


<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

.fluid-styles{
  min-height: 81vh;
}

</style>
