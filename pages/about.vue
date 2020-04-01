<template>
 <div class="container">
   <div>
     <p>About Page</p>

     <n-link to="/">
       Home
     </n-link>
     <nuxt-link to="/">
       Home
     </nuxt-link>
   </div>
 </div>
</template>

<script>


export default {
  middleware:'test',
 head(){
   return{
     meta:[
       {
         hid:'description',
       name:'description',
       content:'about descriptionnnnnnnnnnnnnnnnn'
       }
     ]
   }
 }
 
}
</script>
