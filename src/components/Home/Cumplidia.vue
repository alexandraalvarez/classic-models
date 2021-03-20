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
        <div class="valor">{{entregadas}}</div>
        <div class="detalle_valor">Órdenes Entregadas</div>
      </v-col>
      <v-col>
        <div class="valor">{{pendientes}}</div>
        <div class="detalle_valor">Órdenes Pendientes</div>
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
          entregadas: 0,
          pendientes: 0,
      }
  },
  computed: {
    porcentaje(){
      let resultado = 0;
      let entregadas = this.entregadas;
      let pendientes = this.pendientes;
      let total = parseInt(entregadas) + parseInt(pendientes);
      
      if(total>0){
        resultado = ( entregadas * 100) / total;
        
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
          
          let cumplo = resp.data[0];
          console.log(cumplo.entregadas);
          this.entregadas = cumplo.entregadas;
          this.pendientes = cumplo.pendientes;
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