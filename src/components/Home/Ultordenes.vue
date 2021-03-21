<template>
  <div>
    <h2>Últimas Órdenes</h2>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">N° Orden</th>
            <th class="text-left">Cliente</th>
            <th class="text-left">Fecha Entrega</th>
            <th class="text-left">Estado</th>
            <th class="text-left"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="ordenes in ultiordenes" :key="ordenes.num_orden ">
            <td>{{ ordenes.num_orden }}</td>
            <td>{{ ordenes.cliente }}</td>
            <td>{{ ordenes.fecha_entrega }}</td>
            <td>{{ ordenes.estado }}</td>
            <td><v-btn x-small color="info">Ver detalles</v-btn></td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      ultiordenes: [],
    };
  },
  methods: {
    fetchUltiOrdenes() {
      axios.get("http://localhost:8080/api/ultordenes.json")
        .then((resp) => {
          console.log(resp);
          this.ultiordenes = resp.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  created() {
    this.fetchUltiOrdenes();
  },
};
</script>


<style scoped></style>