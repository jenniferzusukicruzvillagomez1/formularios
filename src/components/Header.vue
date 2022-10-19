<template>
  <div class="row">
    <div class="col-12 col-md-6">
      <h1>App - Proyectos</h1>
    
    </div>
    <div class="col-12 col-md-6">
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
<style>
@font-face {
font-family: 'Oswald', sans-serif;
src: url("https://fonts.gstatic.com");
}
h1{
font-family: Oswald;
font-variant: small-caps;
}

</style>