<template>
  <v-container class="contenido">
    <v-row>
      <v-col>
        <h3 class="titulo">Cumplimiento Diario de Órdenes</h3>
      </v-col>
    </v-row>
    <v-row class="informacion">
      <v-col>
        <div class="valor">{{porcentaje}}%</div>
        <div class="detalle_valor"><a href="">Ver detalles</a></div>
      </v-col>
      <v-col>
        <div class="valor">{{totales}}</div>
        <div class="detalle_valor">Órdenes Totales</div>
      </v-col>
      <v-col>
        <div class="valor">{{atrasadas}}</div>
        <div class="detalle_valor">Órdenes Atrasadas</div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  name: 'cumplido-dia',
  //props: {}
  data: function(){
      return{
          totales: 0,
          atrasadas: 0,
      }
  },
  computed: {
    porcentaje(){
      let resultado = 0;
      let totales = this.totales;
      let atrasadas = this.atrasadas;
      let total = atrasadas + totales;

      console.log(totales);
      console.log(total);
      
      if(total>0){
        resultado = ( atrasadas * 100) / totales;
        
        console.log(resultado);
      }
      return resultado.toFixed(0);
      
    }
  },
  methods: {
    // -- Metodos
    fetchOrdenes(){
      axios.get('http://localhost:8080/api/kpis.json')
        .then(resp=>{
          console.log(resp.data[1]);
          let atraso = resp.data[1];
          console.log(atraso.totales);
          this.totales = atraso.totales;
          this.atrasadas = atraso.atrasadas;
        })
        .catch(error=>{
          console.log(error)
        })
    }
  },
 created(){
    this.fetchOrdenes();
  }
}
</script>

<style scoped>
  .titulo{
    text-align:center;
    font-weight: bolder;
  }
  .informacion{
    padding: 0 30px;
  }
  .valor{
    text-align: center;
    font-size:20px;
  }
  .detalle_valor{
    text-align: center;
    font-weight: bolder;
  }
  .contenido{
    border: 1px solid grey; 
  }
</style>