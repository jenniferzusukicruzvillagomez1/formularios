<template>
    <hr>
    <h3 class="text-center">Total de proyectos : {{this.proyectos.length}}</h3>
    <div class="table-responsive">
      <table class="table table-dark text-center">
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
                  <th>{{index + 1}}</th>
                  <td>{{proyecto.proyecto}}</td>
                  <td>{{proyecto.tipo}}</td>
                  <td @click="cambiarEstado(index)"
                  :class="proyecto.urgente ? 'bg-danger bg-danger' : 'bg-success bg-success'">{{proyecto.urgente ? "Si" : "No"}}</td>
                  
              </tr>
          </tbody>
      </table>
    </div>
</template>
<script>

export default{
    props:[
        'numeroProyectos',
        'proyectos',
        'cambiarEstado'
    ],
}
</script>