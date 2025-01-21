<template>
    <div class="calculator">
        <!--Ajusta o form.vue a receber o valor do numeroAtual através do propt chamada valor e exibi-lo no input usando v-bind-->
        <input type="text" :value="valor" readonly>
    </div>
</template>

<script>
export default {
   props: {
    valor: {
        type: String,
        Required: true,
    }
   }
   
   
}
</script>

<style scoped>
input {
width: 25.9%;
padding: 0.8em;
font-size: 1.5em;
font-weight: 600;
margin-left: 27em;
color: #038C73;
}
</style>

