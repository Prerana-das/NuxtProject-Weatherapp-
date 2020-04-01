<template>
  <div>
      <h6>I am a blog post</h6>

      <p>{{slug}}</p>
      <p>{{slug.blog}} <span>'Only validate for digit'</span></p>
  </div>
</template>

<script>
export default {
  validate({params}){
    // return true
    return /^\d+$/.test(params.blog)
  },
  data(){
    return{
      slug:this.$route.params
    }
  },
  created(){
    console.log(this.$route.params)
  }
}
</script>

<style>

</style>