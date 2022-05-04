<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <ModalDetail :open="open" :data="dataModal" @showModal="
          (value) => {
            this.open = value;
          }"/>
  <div class="mt-8 flex flex-col m-6">
    <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="inline-block w-full py-2 align-middle md:px-6 lg:px-8">
        <div
          class="
            overflow-hidden
            shadow
            ring-1 ring-black ring-opacity-5
            md:rounded-lg
          "
        >
          <!--<h2>Nombre de livre : {{ spellData.length }}</h2>-->
          <table class="w-full divide-y divide-gray-300">
            <thead class="bg-gray-50">
              <tr>
                <th
                  scope="col"
                  class="
                    whitespace-nowrap
                    py-3.5
                    pt-0
                    pl-4
                    pr-3
                    text-center text-sm
                    font-semibold
                    text-gray-900
                    sm:pl-6
                  "
                >
                  Livre
                </th>
                <th
                  scope="col"
                  class="
                    whitespace-nowrap
                    px-2
                    py-3.5
                    pt-0
                    text-center text-sm
                    font-semibold
                    text-gray-900
                  "
                >
                  Nom
                </th>
                <th
                  scope="col"
                  class="
                    whitespace-nowrap
                    px-2
                    py-3.5
                    pt-0
                    text-center text-sm
                    font-semibold
                    text-gray-900
                  "
                >
                  Ecole
                </th>
                <th
                  scope="col"
                  class="
                    whitespace-nowrap
                    px-2
                    py-3.5
                    pt-0
                    text-center text-sm
                    font-semibold
                    text-gray-900
                  "
                >
                  Branche
                </th>
                <th
                  scope="col"
                  class="
                    whitespace-nowrap
                    px-2
                    py-3.5
                    pt-0
                    text-center text-sm
                    font-semibold
                    text-gray-900
                  "
                >
                  Classe
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <tr
                class="spellTab"
                v-for="spellFor in spellAfficher"
                :key="spellFor[1]"
                v-on:click="afficherDetail(spellFor)"
              >
                <!--On appel l'élément spell de spellView et on lui donne la valeur de spellFor pour qu'il travaille avec -->
                <spellView :spell="spellFor" />
              </tr>
              <!-- More transactions... -->
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import spellView from "./formSpellView.vue";
import ModalDetail from "./formModalDetail.vue";
//import spellDetail from "./formSpellDetail.vue";

export default {
  name: "spellTable",
  props: ["spellAfficher"],
  components: {
    spellView,
    ModalDetail
  },
  data () {
    return {
      open: false,
      dataModal: []
    }
  },
  methods: {
    afficherDetail(data) {
      this.open = true;
      this.dataModal = data;
      console.log(data);
    },
    setDataModal() {

    }
  },
};
</script>

<style>
.spellTab:hover {
  color: white;
  background-color: #791cf8;
}
</style>
