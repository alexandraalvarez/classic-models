<template>
  <v-toolbar dense :dark="true">
    <v-app-bar-nav-icon></v-app-bar-nav-icon>

    <v-toolbar-title>Company</v-toolbar-title>
    <v-btn depressed color="default" @click="$router.push('/*')">
      Home
    </v-btn>
    <v-btn depressed color="default" @click="$router.push('/ordenes')">
      Ordenes
    </v-btn>
    <v-btn depressed color="default" @click="$router.push('/*')">
      Inventario
    </v-btn>
    <v-spacer></v-spacer>

    
    <v-btn depressed color="default" @click="$router.push('/*')">
      Perfil
    </v-btn>
    <v-btn depressed color="default" @click="$router.push('/login')">
      Cerrar Sesión
    </v-btn>
  </v-toolbar>
</template>

<script>

</script>

<style></style>