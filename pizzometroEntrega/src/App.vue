<template>
  <h2> Pizzaria do seu tadeu </h2>
  <div class='pessoas'>
        <h1>Quantidade de adultos</h1>
        <input type="number" placeholder="Digite a quantidade de adultos" v-model='adultos'>
        <h1>Quantidade de crianças</h1>
        <input type="number" placeholder="Digite a quantidade de crianças" v-model="criancas">
   </div>
  <button v-on:click="calcular()">Calcular</button>
  <p>
    Quantidade de pizzas gigantes(12):{{quantidadeDePizza12}} 
  </p>
  <p>
    Quantidade de pizzas média(10):{{quantidadeDePizza10}} 
  </p>
  <p>
    Quantidade de pizzas pequena(8):{{quantidadeDePizza8}} 
  </p>
  
</template>
<script>
  export default {
    name: 'App',
    data(){
        return{
            adultos: 0,
            criancas: 0,
            quantidadeDePedacosAdulto:0,
            quantidadeDePedacosCrianca:0,
            quantidadeDePizza12 : 0,
            quantidadeDePizza10 : 0,
            quantidadeDePizza8 : 0,
        }
    },
    methods : {
        calcular(){
            let resto;
            
            this.quantidadeDePedacosAdulto = this.adultos * 3;
            this.quantidadeDePedacosCrianca = this.criancas * 2;
            let totalDePedacos = (this.quantidadeDePedacosAdulto) + (this.quantidadeDePedacosCrianca);


            this.quantidadeDePizza12 = parseInt(totalDePedacos / 12);
            resto = totalDePedacos % 12;
            this.quantidadeDePizza10 = parseInt(resto / 10);
            resto = resto % 10;
             this.quantidadeDePizza8 = parseInt(resto / 8);
            resto = resto % 8;

            if(resto > 0){
                this.quantidadeDePizza8++;
            }
        }
    }

  }
 

</script>
<style scoped>

  h2{
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    background-image: linear-gradient(to right, #08fa91, #0b51f5);
    text-align: center;
    color: #ffffff;
  }
  button{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    margin-left: 20px;
    margin-right: 20px;
    padding: 20px;
    width: 100px;
    border: 1px solid #08fa91;
    border-radius: 5px;
   background-color: aqua;
    color: #ffffff;
    font-size: 15px;
    font-weight: bold;
  }
   .pessoas{
        display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
        margin-top: 20px;
        margin-left: 20px;
        margin-right: 20px;
        padding: 20px;
        width: 50vw;
        border: 1px solid #08fa91;
        border-radius: 10px;
    }
    .pessoas h1{
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        text-align: center;
        color: #0a1ed4;
    }
    .pessoas input{
        width: 100%;
        height: 40px;
        border: 1px solid #08fa91;
        border-radius: 10px;
        padding: 10px;
        font-size: 20px;
    }

</style>
