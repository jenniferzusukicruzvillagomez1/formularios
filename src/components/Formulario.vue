<template>

  <div class="row"> 
    <div class="col-12 mb-4">
      <progress-bar :porcentaje="porcentaje"/>
  </div>
      <!-- bootstrap form -->
      <div class="row">
        <form @submit.prevent="registrarProyecto" class="col-12 col-md-4 mt-3">
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
        <div class="col-12 col-md-8">
          <total-proyectos 
          :numeroProyectos="numeroProyectos" 
          :proyectos="proyectos" 
          :cambiarEstado="cambiarEstado"
          :limpiarData="limpiarData"/>
        </div>
          </div>
  </div>
</template>

<script>
  import TotalProyectos from './TotalProyectos.vue';
  import ProgressBar from './ProgressBar.vue'

    export default{
      components:{
        TotalProyectos,
        ProgressBar
      },
      data:()=>({
        proyecto:"",
        tipo:"",
        urgente:false,
        proyectos:[],
        numeroProyectos:0,
      }),
      methods:{
        registrarProyecto(){
            const proyecto = {
                proyecto: this.proyecto,
                tipo : this.tipo,
                urgente : this.urgente,
                completado : false
            };
          
        this.proyectos.push(proyecto),
        this.numeroProyectos++;
        this.proyecto = "",
        this.tipo = "",
        this.urgente = false,
        console.log(this.proyectos)
        },
        
        
        cambiarEstado(proyecto,campo){
          //this.urgente = !this.urgente;
          //this.proyectos[id].urgente = !this.proyectos[id].urgente;
          proyecto[campo] = !proyecto[campo];
          this.saveData();
        },
        
        limpiarData(){
          this.proyectos = [];
          localStorage.clear();
        },
        saveData(){
          this.proyecto = JSON.stringify(localStorage.getItem("proyectos"))
        }
  
      },

      computed:{
        numeroProyectos(){
          return this.proyectos.length;
        },
        porcentaje(){
          let completados = 0;
          
          this.proyectos.map(proyecto =>{
            if (proyecto.completado) 
              completados++;
            
          });
          return (completados * 100) / this.numeroProyectos || 0;
        },
        mounted(){
        this.proyectos =  JSON.parse(localStorage.getItem("proyectos"))
      }
      },

      
    };
  
  </script>