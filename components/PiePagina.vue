<template>
    <footer class="d-flex flex-column justify-content-center align-items-center">
        <span><span class="grey">Developed by: </span><a href="https://github.com/xhydram" target="_blank" class="tomato">Aybson Mercado</a></span>
        <span>Derechos Reservados &reg;</span>
    </footer>
</template>

<script>
export default {
    name: "PiePagina"
}
</script>


<style scoped>


footer{
    background: #eee;
    height: 50px;
    padding: 40px 0;
    color: rgba(100,100,100,0.5);
    bottom: 0;
}

.tomato{
    color: tomato;
}

.grey{
    color: rgba(120,120,120,0.8);
}


</style>