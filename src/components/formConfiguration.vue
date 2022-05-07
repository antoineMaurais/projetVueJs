<template>
  <div class="flex justify-center m-8">
    <section class="font-semibold">
      <h1>Configuration :</h1>
      <ul>
        Modifier les options de recherche :
        <li>Ecole <input @click="event => updateChoice('ecole', event.target.checked)" type="checkbox" v-model="config.ecole" /></li>
        <li>Classe <input @click="event => updateChoice('classes', event.target.checked)" type="checkbox" v-model="config.classes" /></li>
        <li>Branche <input @click="event => updateChoice('branche', event.target.checked)" type="checkbox" v-model="config.branche" /></li>
        <li>Niveau <input @click="event => updateChoice('niveau', event.target.checked)" type="checkbox" v-model="config.niveau" /></li>
      </ul>
    </section>
  </div>
</template>


<script>
export default {
  name: "ongletConfiguration",
  data: function () {
    return {
      config: JSON.parse(localStorage.getItem("config"))
    }
  },
  methods: {
    updateChoice(name, value) {
      let config = JSON.parse(localStorage.getItem("config"));
      
      switch (name) {
        case "ecole":
          config.ecole = value;
          break;
        case "branche":
          config.branche = value;
          break;
        case "classes":
          config.classes = value;
          break;
        case "niveau":
          config.niveau = value;
          break;
      }
      localStorage.setItem("config", JSON.stringify(config));
    },
  }
};

</script>