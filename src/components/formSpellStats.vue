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
      <td>{{ statistiqueNbLivreDiff }}</td>
      <td>{{ statistiqueSort }}</td>
      <td>{{ statistiqueNbEcoleDiff }}</td>
      <td>{{ statistiqueNbBranchesDiff }}</td>
      <td>{{ statistiqueNbClassesDiff }}</td>
    </tr>
  </table>
</template>


<script>
export default {
  name: "spellStats",
  props: ["tableauSpells"],
  computed: {
    statistiqueSort() {
      console.log(this.tableauSpells);
      if (this.tableauSpells.length != 0) {
        let value = this.tableauSpells.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        return value.length;
      } else return 0;
    },
    statistiqueNbLivreDiff() {
      if (this.tableauSpells.length != 0) {
        let value = this.tableauSpells.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        let count = 0;
        let countArrayLivre = [];
        for (const vFor of value) {
          if (!countArrayLivre.includes(vFor[0])) {
            count++;
            countArrayLivre.push(vFor[0]);
          }
        }
        return count;
      } else return 0;
    },
    statistiqueNbEcoleDiff() {
      if (this.tableauSpells.length != 0) {
        let value = this.tableauSpells.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        let count = 0;
        let countArraySchool = [];
        for (const vFor of value) {
          if (!countArraySchool.includes(vFor[2])) {
            count++;
            countArraySchool.push(vFor[2]);
          }
        }
        return count;
      } else return 0;
    },
    statistiqueNbBranchesDiff() {
      if (this.tableauSpells) {
        let value = this.tableauSpells.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        let count = 0;
        let countArrayBranche = [];
        for (const vFor of value) {
          if (vFor[3].length != 0) {
            for (const branche of vFor[3]) {
              if (!countArrayBranche.includes(branche)) {
                count++;
                countArrayBranche.push(branche);
              }
            }
          }
        }
        return count;
      } else return 0;
    },
    statistiqueNbClassesDiff() {
      if (this.tableauSpells) {
        let value = this.tableauSpells.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        let count = 0;
        let countArrayClasse = [];
        for (const vFor of value) {
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
      } else return 0;
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