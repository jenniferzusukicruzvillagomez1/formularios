<template>

  <div class="row">
    <div class="col-12 col-md-4">
      <h3 class="text-center" :class="proyecto.urgente ? 'text-success' : 'text-info' "   >Progreso {{porcentaje}}</h3>

      <!-- progress bar -->
      <div class="progress">
        <div class="progress-bar progress-bar-striped progress-bar-animated bg-success"
        role="progressbar"
        :aria-valuenow="porcentaje"
        aria-valuemin="0"
        aria-valuemax="100"
        :style="`width:${porcentaje}%`">

        </div>
      </div>
       <!-- progress bar -->

      <!-- bootstrap form -->
<form @submit.prevent="registrarproyecto">
  <div class="mb-3">
    <label for="" class="form-label">Proyecto</label>
    <input v-model.trim="proyecto" type="text" class="form-control" required>
  </div>
  <div class="mb-3">
      <label for="" class="form-label">Actividad</label>
      <select class="form-select" required  v-model.trim="tipo">
          <option disabled selected value="">Seleccione tipo de actividad</option>
          <option value="1">Aplicaciones Web con Vue.JS</option>
          <option value="2">Backend Service con Node.js</option>
          <option value="3">App Movil con React Native</option>
      </select>
  </div>
  <div class="mb-3">
      <label class="form-check-label m-1">Urgente</label>
      <input type="checkbox" class="form-check-input m-2" v-model.trim="urgente">
  </div>
  <button type="submit" class="btn btn-primary">Guardar</button>
</form>

    </div>
    <div class="col-12 col-md-8">
      <total-proyectos :numeroProyectos="numeroProyectos" :proyectos="proyectos" :cambiarEstado="cambiarEstado"/>
    </div>
  
  </div>
</template>

<script>
  import TotalProyectos from './TotalProyectos.vue';
    export default{
      components:{
        TotalProyectos
      },
      data:()=>({
        proyecto:"",
        tipo:"",
        urgente:false,
        proyectos:[],
        numeroProyectos:0,
      }),
      methods:{
        registrarproyecto(){
            const proyecto = {
                proyecto: this.proyecto,
                tipo : this.tipo,
                urgente : this.urgente
            };
          
        this.proyectos.push(proyecto),
        this.proyecto = "",
        this.tipo = "",
        this.urgente = false,
          console.log(this.proyectos)
        },
        cambiarEstado(id){
          //this.urgente = !this.urgente;
          this.proyectos[id].urgente = !this.proyectos[id].urgente;
        }

      },
      computed:{
        numeroProyectos(){
          return this.proyectos.length;
        },
        porcentaje(){
          let completados = 0;
          
          this.proyectos.map(proyectos =>{
            if (proyectos.i) {
              completados++;
            }
            return (completados *100) / this.numeroProyectos || 10;
          });
        }
      },
      
    };
  
  </script>