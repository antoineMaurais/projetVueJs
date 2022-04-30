<template>
  <tr>
    <td>
      <div
        class="
          relative
          border border-gray-300
          rounded-md
          px-3
          py-2
          shadow-sm
          focus-within:ring-1
          focus-within:ring-indigo-600
          focus-within:border-indigo-600
        "
      >
        <label
          for="name"
          class="
            absolute
            -top-2
            left-2
            -mt-px
            inline-block
            px-1
            bg-gray-50
            text-xs
            font-medium
            text-gray-900
          "
          >Rechercher un sort</label
        >
        <input
          type="text"
          v-model="searchName"
          @input="
            $emit(
              'spellSearch',
              this.searchName,
              this.searchNameBox,
              this.searchSchool,
              this.searchSchoolBox,
              this.searchBranche,
              this.searchBrancheBox,
              this.searchClasse,
              this.searchClasseBox,
              this.searchLevel,
              this.searchLevelBox
            )
          "
          name="name"
          id="name"
          class="
            block
            w-full
            border-0
            p-0
            text-gray-900
            bg-gray-50
            placeholder-gray-500
            focus:ring-0
            sm:text-sm
          "
        />
      </div>
    </td>

    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchNameBox"
        @input="
          $emit(
            'spellSearch',
            this.searchName,
            this.searchNameBox,
            this.searchSchool,
            this.searchSchoolBox,
            this.searchBranche,
            this.searchBrancheBox,
            this.searchClasse,
            this.searchClasseBox,
            this.searchLevel,
            this.searchLevelBox
          )
        "
      />
    </td>
  </tr>
  <tr>
    <td>
      <form>
        <SelectSchool
          id="ecoles"
          label="Ecole :"
          v-bind:ecoles="schools"
        ></SelectSchool>
      </form>
    </td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchSchoolBox"
        @input="
          $emit(
            'spellSearch',
            this.searchName,
            this.searchNameBox,
            this.searchSchool,
            this.searchSchoolBox,
            this.searchBranche,
            this.searchBrancheBox,
            this.searchClasse,
            this.searchClasseBox,
            this.searchLevel,
            this.searchLevelBox
          )
        "
      />
    </td>
  </tr>
  <tr>
    <td>Branches</td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchBrancheBox"
        @input="
          $emit(
            'spellSearch',
            this.searchName,
            this.searchNameBox,
            this.searchSchool,
            this.searchSchoolBox,
            this.searchBranche,
            this.searchBrancheBox,
            this.searchClasse,
            this.searchClasseBox,
            this.searchLevel,
            this.searchLevelBox
          )
        "
      />
    </td>
  </tr>
  <tr>
    <td>Classes</td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchClasseBox"
        @input="
          $emit(
            'spellSearch',
            this.searchName,
            this.searchNameBox,
            this.searchSchool,
            this.searchSchoolBox,
            this.searchBranche,
            this.searchBrancheBox,
            this.searchClasse,
            this.searchClasseBox,
            this.searchLevel,
            this.searchLevelBox
          )
        "
      />
    </td>
  </tr>
  <tr>
    <td>Niveau</td>
    <td>
      Prendre en compte ?
      <input
        type="checkbox"
        v-model="searchLevelBox"
        @input="
          $emit(
            'spellSearch',
            this.searchName,
            this.searchNameBox,
            this.searchSchool,
            this.searchSchoolBox,
            this.searchBranche,
            this.searchBrancheBox,
            this.searchClasse,
            this.searchClasseBox,
            this.searchLevel,
            this.searchLevelBox
          )
        "
      />
    </td>
  </tr>
</template>

<script>
import SelectSchool from "./selectSchool.vue";
import data from "./../assets/data.min.js"; // Lien vers toutes les données

export default {
  name: "checkBoxSelect",
  components: {
    SelectSchool,
  },
  data: function () {
    return {
      searchName: "",
      searchNameBox: false,
      searchSchool: "",
      searchSchoolBox: false,
      searchBranche: "",
      searchBrancheBox: false,
      searchClasse: "",
      searchClasseBox: false,
      searchLevel: "",
      searchLevelBox: false,
      schools: this.initSchools(),
    };
  },
  emits: [
    "searchName",
    "searchNameBox",
    "searchSchool",
    "searchSchoolBox",
    "searchBranche",
    "searchBrancheBox",
    "searchClasse",
    "searchClasseBox",
    "searchLevel",
    "searchLevelBox",
  ],
  methods: {
    getSchools() {
      let schools = []; // tableau qui contient les différentes écoles
      console.log("GetSchools");
      data.forEach((sort) => {
        if (!schools.includes(sort[2]))
          // évite les doublons
          schools.push(sort[2]);
      });
      return schools;
    },
    initSchools() {
      console.log("InitSchools");
      let schools = JSON.parse(localStorage.getItem("ecoles"));
      console.log(schools);
      if (!schools) {
        console.log("schools22");
        schools = this.getSchools();
        localStorage.setItem("ecoles", JSON.stringify(schools));
      }
      return schools;
    },
  },
};
</script>