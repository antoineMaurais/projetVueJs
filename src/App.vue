<template>
  <HelloWorld msg="Sorts :" />

  <h1>Wiki des sorts</h1>
  <menuHeader />
  <table>
    <th></th>
    <tr>
      <checkBoxSelect @spellSearch="updateSearch" />
    </tr>
  </table>
  <br />
  <!--  Utiliser v-if pour afficher different pnglet -->
  <div>
    <spellStats :tableauSpells="spellSearch" />
  </div>
  <!--
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
-->
  <table>
    <tr>
      <th>Livre</th>
      <th>Nom</th>
      <th>Ecole</th>
      <th>Branche</th>
      <th>Classe</th>
    </tr>
    <!-- On boucle des lignes de tableau
          Chaque entité de spellSearch va être stocké dans spellFor
          Puis on met une clé pour dire sur quoi on boucle, ici le nom, mais c'est inutile dans notre cas
    -->

    <tr v-for="spellFor in spellSearch" :key="spellFor[1]">
      <!--On appel l'élément spell de spellView et on lui donne la valeur de spellFor pour qu'il travaille avec -->
      <spellView :spell="spellFor" />
    </tr>
  </table>
</template>

<script>
import spellView from "./components/formSpellView.vue";
import checkBoxSelect from "./components/formCheckBoxSelect.vue";
import spellStats from "./components/formSpellStats.vue";
import menuHeader from "./components/formHeader.vue";
import data from "./assets/data.min.js"; // Lien vers toutes les données

export default {
  name: "App",
  components: {
    checkBoxSelect,
    spellView,
    spellStats,
    menuHeader,
  },
  data: function () {
    return { searchName: "", searchNameBox: "" };
  },
  computed: {
    spellSearch() {
      /*On récupère les data de la base JS qu'on importe,
        On filtre toutes les valeurs
        On encapsule chaque valeur de nom, ici 'spell[1]' dans une variable 'spell'
        Qui commence par les valeurs rentrés dans la zone de texte de l'input */
      console.log(this.searchNameBox);
      console.log(data);

      if (this.searchNameBox)
        return data.filter((spell) => spell[1].startsWith(this.searchName));
      else return [];
    },
    statistiqueSort() {
      if (this.searchNameBox) {
        let value = data.filter((spell) =>
          spell[1].startsWith(this.searchName)
        );
        return value.length;
      } else return 0;
    },
    statistiqueNbLivreDiff() {
      if (this.searchNameBox) {
        let value = data.filter((spell) =>
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
      if (this.searchNameBox) {
        let value = data.filter((spell) =>
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
      if (this.searchNameBox) {
        let value = data.filter((spell) =>
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
      if (this.searchNameBox) {
        let value = data.filter((spell) =>
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
  methods: {
    updateSearch(searchName, searchNameBox) {
      this.searchName = searchName;
      this.searchNameBox = searchNameBox;
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
