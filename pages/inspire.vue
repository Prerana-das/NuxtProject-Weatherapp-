<template>
  <v-layout>
    <v-flex class="text-center">
      <img
        src="/v.png"
        alt="Vuetify.js"
        class="mb-5"
      >

      <v-color-picker></v-color-picker> 

      <h3 class="success"> veutify Color Check</h3>

      <v-btn color="success">Success</v-btn>


      <blockquote class="blockquote">
        &#8220;First, solve the problem. Then, write the code.&#8221;
        <footer>
          <small>
            <em>&mdash;John Johnson</em>
          </small>
        </footer>
      </blockquote>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
    
    layout:'inspireLayout'
}
</script>

<style>

</style>
