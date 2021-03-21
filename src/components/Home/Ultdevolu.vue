<template>
  <div>
    <h2>Últimas Devoluciones</h2>
    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">N° Orden</th>
            <th class="text-left">Cliente</th>
            <th class="text-left">Fecha Devolución</th>
            <th class="text-left"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="devoluciones in ultidevoluciones" :key="devoluciones.num_orden ">
            <td>{{ devoluciones.num_orden }}</td>
            <td>{{ devoluciones.cliente }}</td>
            <td>{{ devoluciones.fecha_entrega }}</td>
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
      ultidevoluciones: [],
    };
  },
  methods: {
    fetchUltidevoluciones() {
      axios.get("http://localhost:8080/api/ultdevolu.json")
        .then((resp) => {
          console.log(resp);
          this.ultidevoluciones = resp.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  created() {
    this.fetchUltidevoluciones();
  },
};
</script>


<style scoped></style>