<template>
  <div class="m-16 mt-0">
  <h3 class="text-lg leading-6 font-medium text-gray-900">Les statistiques</h3>
  <dl class="mt-5 grid grid-cols-1 gap-5 sm:grid-cols-3">
    <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
      <dt class="text-sm font-medium text-gray-500 truncate">Nombre de livres</dt>
      <dd class="mt-1 text-3xl font-semibold text-gray-900">{{statistiqueNbLivreDiff}}</dd>
    </div>

    <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
      <dt class="text-sm font-medium text-gray-500 truncate">Nombre de sorts</dt>
      <dd class="mt-1 text-3xl font-semibold text-gray-900">{{ data.length }}</dd>
    </div>

    <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
      <dt class="text-sm font-medium text-gray-500 truncate">Nombre d'écoles</dt>
      <dd class="mt-1 text-3xl font-semibold text-gray-900">{{statistiqueNbEcoleDiff}}</dd>
    </div>

    <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
      <dt class="text-sm font-medium text-gray-500 truncate">Nombre de branches</dt>
      <dd class="mt-1 text-3xl font-semibold text-gray-900">{{statistiqueNbBranchesDiff}}</dd>
    </div>

    <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
      <dt class="text-sm font-medium text-gray-500 truncate">Nombre de classes</dt>
      <dd class="mt-1 text-3xl font-semibold text-gray-900">{{statistiqueNbClassesDiff}}</dd>
    </div>

  </dl>
</div>

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