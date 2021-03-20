<template>
  <div>
    <h2>Últimas Órdenes</h2>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">
              N° Orden
            </th>
            <th class="text-left">
              Cliente
            </th>
            <th class="text-left">
              Fecha Entrega
            </th>
            <th class="text-left">
              Estado
            </th>
            <th class="text-left">
              
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="vendedor in ranking" :key="vendedor.id_vendedor">
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td><v-btn x-small color="info">Ver detalles</v-btn></td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "UltiOrdenes",
  // props: {},
  //data: function() {},
  // computed: {},
  //methods: {},
  //created(){,
  // components: {},
};
</script>

<style scoped></style>