<template>
  <table class="stats">
    <tr>
      <th>Nombre de livres</th>
      <th>Nombre de sorts</th>
      <th>Nombre d'écoles</th>
      <th>Nombre de branches</th>
      <th>Nombre de classes</th>
    </tr>
    <tr>
      <td>{{statistiqueNbLivreDiff}}</td>
      <td>{{ data.length }}</td>
      <td>{{statistiqueNbEcoleDiff}}</td>
      <td>{{statistiqueNbBranchesDiff}}</td>
      <td>{{statistiqueNbClassesDiff}}</td>
    </tr>
  </table>
</template>


<script>
export default {
  name: "spellStats",
  props: ["data"],
  methods: {
    getOccurenceElement(key) { 
      let tousLesElements = this.data.map(table => table[key]); 
      let tableauElementsUnique = [...new Set(tousLesElements)]; 
      return tableauElementsUnique.length; 
    },
  },
  computed: {
    statistiqueNbLivreDiff() {
      return this.getOccurenceElement(0);
    },
    statistiqueNbEcoleDiff() {
      return this.getOccurenceElement(2);
    },
    statistiqueNbBranchesDiff() {
      let tousLesElements = this.data.map(table => table[3]);

      let concat = [];
      tousLesElements.forEach(elem => {
        concat = concat.concat(elem);
      })
      return [...new Set(concat)].length;
    },
    statistiqueNbClassesDiff() {
      let count = 0;
      let countArrayClasse = [];
      for (const vFor of this.data) {
        if (vFor[3].length != 0) {
          for (const classe of vFor[4]) {
            if (!countArrayClasse.includes(classe[0])) {
              count++;
              countArrayClasse.push(classe[0]);
            }
          }
        }
      }
      return count;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
table {
  margin-top: 20px;
  margin-left: auto;
  margin-right: auto;
}

.stats {
  width: 100%;
  border-collapse: collapse;
  border: 2px solid black;
}
th {
  padding: 5px;
}
</style>