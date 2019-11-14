<template>
  <div>
    <div class="container">
      <h1>{{project.name}}</h1>
    </div>
    <div class="container">
      <div>
        <b-tabs content-class="mt-3">
          <b-tab title="Presentacion" active>
            <p>Presentacion del proyecto</p>
          </b-tab>
          <b-tab title="BMO">
            <table class="table table-bordered">
              <thead class="thead-dark">
                <tr>
                  <th scope="col">Piso</th>
                  <th v-for="service in project.services" :key="service" scope="col">{{service}}</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="index in project.levels" :key="index">
                  <th scope="row">Piso {{index}}</th>
                  <td
                    @click="execute"
                    cursos
                    class="cell"
                    v-for="index in project.services.length"
                    :key="index"
                  >
                    <a href></a>
                  </td>
                </tr>
              </tbody>
            </table>
          </b-tab>
          <b-tab title="Info">
            <p>Info adicional de proyecto</p>
          </b-tab>
        </b-tabs>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      project: {
        id: this.$route.params.id,
        name: "Project name",
        description: "Project description",
        levels: 5,
        services: ["AFC", "ELE", "GAS", "CLC", "ETH"],
        completed: "",
        progress: ""
      }
    };
  },
  methods: {
    execute() {
      alert("Opening software");
    }
  }
};
</script>

<style>
.cell {
  cursor: pointer;
  background-color: rgb(163, 177, 207);
}
.cell:hover {
  cursor: pointer;
  background-color: rgb(75, 125, 226);
}
</style>