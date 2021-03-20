<template>
  <div>
    <NavBarAdmin></NavBarAdmin>
    <h3>Home</h3>
    <v-container>
      <v-row>
        <v-col>
          <Jumbo></Jumbo>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <Cumplidia></Cumplidia>
        </v-col>
        <v-col>
          <Ordenatras></Ordenatras>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <Ultordenes></Ultordenes>
        </v-col>
        <v-col>
          <Ultdevolu></Ultdevolu>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import NavBarAdmin from "@/components/AdminNavbar.vue";
import Jumbo from "@/components/Home/Jumbo.vue";
import Cumplidia from "@/components/Home/Cumplidia.vue";
import Ordenatras from "@/components/Home/Ordenatras.vue";
import Ultordenes from '../components/Home/Ultordenes.vue';
import Ultdevolu from '../components/Home/Ultdevolu.vue';

export default {
  name: "Home",
  components: {
    NavBarAdmin,
    Jumbo,
    Cumplidia,
    Ordenatras,
    Ultordenes,
    Ultdevolu,
  },
};
</script>

