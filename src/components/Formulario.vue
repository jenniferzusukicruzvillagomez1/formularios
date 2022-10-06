<template>
<!-- bootstrap form -->
<form @submit.prevent="registrarproyecto">
    <div class="cl-3">
      <label for="" class="form-label">Proyecto</label>
      <input v-model.trim="proyecto" type="text" class="form-control" required>
    </div>
    <div class="cl-3">
        <label for="" class="form-label">Actividad</label>
        <select class="form-select" required  v-model.trim="tipo">
            <option disabled selected value="">Seleccione tipo de actividad</option>
            <option value="1">Aplicaciones Web con Vue.JS</option>
            <option value="2">Backend Service con Node.js</option>
            <option value="3">App Movil con React Native</option>
        </select>
    </div>
    <div class="cl-3">
        <label class="form-check-label m-1">Urgente</label>
        <input type="checkbox" class="form-check-input m-2" v-model.trim="urgente">
    </div>
    <button type="submit" class="btn btn-primary">Guardar</button>
  </form>
  <hr>
  <div class="table-responsive">
    <table class="table table-primary text-center">
        <thead>
            <tr>
                <th>#</th>
                <th>Proyecto</th>
                <th>Tipo</th>
                <th>Urgente</th>
            </tr>
        </thead>
        <tbody v-for="(proyecto,index) in proyectos" :key="index">
            <tr class="table-light">
                <td>{{index + 1}}</td>
                <td>{{proyecto.proyecto}}</td>
                <td>{{proyecto.tipo}}</td>
                <td :class="proyecto.urgente ? 'bg-success' : 'bg-danger'">{{proyecto.urgente ? "Si" : "No"}}</td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
    export default{
      data:()=>({
        proyecto:"",
        tipo:"",
        urgente:false,
        proyectos:[]
      }),
      methods:{
        registrarproyecto(){
            const proyecto = {
                proyecto: this.proyecto,
                tipo : this.tipo,
                urgente : this.urgente
            };

        this.proyectos.push(proyecto);
        this.proyecto = "",
        this.tipo = "",
        this.urgente = false,
          console.log(this.proyectos)
        }
      },
    };
  
  </script>