<template>
  <div class="container">
    <b-list-group v-for="project in projects" :key="project.id">
      <b-list-group-item
        :to="{ name:'Project', params:{id: project.id}}"
        event="click"
        class="project-item h-100 d-flex justify-content-between">
            <span class="">{{project.name}}</span>
          <p>Fecha: {{project.dateCreated}}</p>
 
          <h6>{{project.description}}</h6>
      </b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        {
          id: "1",
          name: "Project 1",
          description: "A project example",
          dateCreated: new Date().toLocaleDateString("en-US"),
          author: "Autor of project 1"
        },
        {
          id: "2",
          name: "Project 2",
          description: "A project example",
          dateCreated: new Date().toLocaleDateString("en-US"),
          author: "Autor of project 2"
        },
        {
          id: "3",
          name: "Project 3",
          description: "A project example",
          dateCreated: new Date().toLocaleDateString("en-US"),
          author: "Autor of project 3"
        }
      ]
    };
  }
};
</script>

<style>
.layout{

}
.project-item {
  height: 5rem;
}
</style>