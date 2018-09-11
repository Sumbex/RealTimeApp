<template>
	<v-toolbar>
    	<!-- <v-toolbar-side-icon></v-toolbar-side-icon> -->
    	<v-toolbar-title>Forum</v-toolbar-title>
    	<v-spacer></v-spacer>
    	<div class="hidden-sm-and-down">
      	 <router-link to="/forum">
          <v-btn flat >Forun</v-btn>
        </router-link>

        <router-link to="/quest">
          <v-btn flat >Question</v-btn>
        </router-link>

        <router-link to="/cat">
          <v-btn flat >Category</v-btn>
        </router-link>

        <router-link to="/login">
          <v-btn flat >Login</v-btn>
        </router-link>
    </div>
  </v-toolbar>
</template>

<script>
	export default{

	}
</script>

<style>

</style>