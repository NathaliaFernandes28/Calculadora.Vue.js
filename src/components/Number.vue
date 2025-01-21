<template>
    <div class="calculator">
      <div class="buttons">
        <div class="row">
            <button @click="limparNumero(0)">C</button>
            <button @click="emitirNumero(7)">7</button>
            <button @click="emitirNumero(8)">8</button>
            <button @click="emitirNumero(9)">9</button>
            <button @click="emitirOperacao('+')">+</button>
        </div>
        <div class="row">
            <button @click="emitirNumero(4)">4</button>
            <button @click="emitirNumero(5)">5</button>
            <button @click="emitirNumero(6)">6</button>
            <button @click="emitirOperacao('-')">-</button>
            <button @click="emitirNumero('()')">( )</button>
        </div>
        <div class="row">
            <button @click="emitirNumero(1)">1</button>
            <button @click="emitirNumero(2)">2</button>
            <button @click="emitirNumero(3)">3</button>
            <button @click="emitirOperacao('x')">x</button>
            <button @click="emitirNumero('%')">%</button>
        </div>
        <div class="row">
            <button @click="emitirNumero(0)">0</button>
            <button @click="emitirOperacao('.')">.</button>
            <button @click="emitirOperacao('=')">=</button>
            <button @click="emitirOperacao('/')">/</button>
            <button @lick="emitirOperacao('00')">00</button>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    data(){
        return {

        }
    }, 
    methods: {
        emitirNumero(numero){
            this.$emit("numero", numero)
        },
        //Vamos chamar o evento emitirOperacao como metodo e vamos colocar como parametro a palavra 'operacao',
        //que vai fazer referencia ao parametro ('/')do evento enviado @click="emitirOperacao('/').
        emitirOperacao(operacao){
            this.$emit("operacao", operacao)
        },
        limparNumero(limpar){
            this.$emit("limpar", limpar)
        }
    }
}
</script>

<style scoped>
.calculator {
text-align: center;
margin-top: 0.2em;
};
.buttons{
    display: flex;
    flex-direction: column;
}
.row{
    display: flex;
    justify-content: center;
    gap: 1em;
    padding: 0.5em;
}
button {
    padding: 1.5em;
    font-size: 1.5em;
    border: 2px solid #333;
    border-radius: 0.3em;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
    color: #038C73;
}

button:active{
    transform: scale(0.92);
}

</style>