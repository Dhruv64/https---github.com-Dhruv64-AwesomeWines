<template>
<div>
<v-container fluid class="py-16">
  <v-layout justify-center align-center>
    <v-flex shrink>
      <div class="py-16">
<v-img 
src="@/assets/logo.png"
max-width="800"
class="mx-auto"
/>
</div>
    </v-flex>
  </v-layout>
</v-container>

<v-container fluid class="py-16">
  <v-layout justify-center align-center>
    <v-flex shrink>
      <div >
        <v-btn
        depressed 
        color="success"
        router to="/store"
        large
        >Shop now</v-btn>
</div>
    </v-flex>
  </v-layout>
</v-container>
</div>
</template>

<script>
  export default {
    name: 'Home-vue',

    components: {
      
    },
  }
</script>
