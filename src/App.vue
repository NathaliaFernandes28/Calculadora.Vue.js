<template>
  <div class="calculator">
    <h1>{{ title }}</h1>
    <!--Vamos usar o v-model para ligar o input, criado no form, com o numeroAtual.-->
    <Form :valor="displayValue"></Form>
    <Number
    @numero="exibirNumero"
    @operacao="exibirOperacao"
    @limpar="resetarNumero"></Number>
  </div>
  
</template>

<script>
import Form from "./components/Form.vue"
import Number from "./components/Number.vue"

export default {
  data(){
    return {
      title: "Calculadora",
      numeroAnterior: null,
      operacaoAtual: null,
      numeroAtual: "",
      resultado: null,
    }
  },
  computed: {
    displayValue(){
      return this.numeroAnterior !== null && this.operacaoAtual
      ? `${this.numeroAnterior} ${this.operacaoAtual} ${this.numeroAtual}` : this.numeroAtual
    }
  },
  methods: {
    exibirNumero(numero){
      this.numeroAtual += numero.toString()
    },
    exibirOperacao(operacao){
      if(operacao === "="){
        this.calcularResultado()
      } else {
        this.numeroAnterior = parseFloat(this.numeroAtual);
        this.operacaoAtual = operacao;
        this.numeroAtual = ""; //Reseta o número atual para a entrada do próximo número//
      }
    },
    calcularResultado(){
      const numeroAtual = parseFloat(this.numeroAtual);

      if(this.operacaoAtual === "+"){
        this.resultado = this.numeroAnterior + numeroAtual;
      } else if(this.operacaoAtual === "-") {
        this.resultado = this.numeroAnterior - numeroAtual;
      } else if(this.operacaoAtual === "x"){
        this.resultado = this.numeroAnterior * numeroAtual;
      } else if(this.operacaoAtual === "/"){
        if(numeroAtual === 0){
          alert("Divisão por zero não é possível!");
          return;
        }
        this.resultado = this.numeroAnterior / numeroAtual;
      }
      this.numeroAtual = this.resultado.toString();
      this.numeroAnterior = null;
      this.operacaoAtual = null;
    },
    resetarNumero(limpar){
      this.numeroAnterior = null;
      this.operacaoAtual = null;
      this.numeroAtual = "";
      this.resultado = null;
    }
  },
  components: {Form, Number}
}
</script>


<style scoped>
h1{
  text-align: center;
  color: white;
  margin-top: 0.7em;
  font-size: 4em;
}

</style>

