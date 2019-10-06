<template>
  <div class="content-styles">
    <form>
      <span class="logo d-flex justify-content-center align-items-center">
        <i class="fab fa-adn"></i>
      </span>
      <input
        type="email"
        class="form-control"
        id="exampleInputEmail1"
        aria-describedby="emailHelp"
        placeholder="Enter email"
      />
      <input type="password" class="form-control" id="exampleInputPassword1" placeholder="Enter password" />
      <button type="submit" class="btn btn-primary" @:onclic.prevent="">Verify Account</button>
    </form>
  </div>
</template>

<script>
export default {
  layout: "login"
};
</script>


<style scoped>
.content-styles {
  background: transparent;
  width: 35%;
  min-height: 100vh;
  margin: 0 auto;
  padding-top: 250px;
}

form {
  background: rgba(48, 63, 159, 0.75);
  text-align: center;
  padding-top: 15px;
  border-radius: 5px;
}

.logo{
  font-size: 5rem;
  margin-bottom: 20px; 
}

.logo i{
  color: white;
}

input {
  margin-bottom: 25px;
  width: calc(100% - 140px);
  margin-right: 70px;
  margin-left: 70px;
  height: 50px;
}

button{
  margin-top: 20px;
  width: 100%;
  height: 50px;
  border: none;
  border-radius: 0 0 5px 5px;
  background: rgb(86, 190, 21);
  font-size: 1.3rem;
  text-transform: uppercase;
}
</style>