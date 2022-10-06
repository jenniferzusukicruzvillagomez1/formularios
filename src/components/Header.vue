<template>
        <div class="row">
          <div class="cl-12 cls-cl-6">
            <h1>App - Proyectos</h1>
          
          </div>
          <div class="cl-12 cls-cl-6">
            <img width="100" :src="url" :alt="des">
          </div>
          <hr>
        </div>
</template>
<script>
    
    export default{
      data:()=>({
        url:"https://cdn.svgporn.com/logos/vue.svg",
        des:"Vue.Js",
      }),
    };
  
  </script>