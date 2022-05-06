<template>
  <div
    v-show="open"
    class="relative z-10"
    aria-labelledby="modal-title"
    role="dialog"
    aria-modal="true"
  >
    <div
      class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
    ></div>

    <div class="fixed z-10 inset-0 overflow-y-auto">
      <div
        class="
          flex
          items-end
          justify-center
          min-h-screen
          pt-4
          px-4
          pb-20
          text-center
          sm:block sm:p-0
        "
      >
        <!-- This element is to trick the browser into centering the modal contents. -->
        <span
          class="hidden sm:inline-block sm:align-middle sm:h-screen"
          aria-hidden="true"
          >&#8203;</span
        >

        <div
          class="
            relative
            inline-block
            align-bottom
            bg-white
            rounded-lg
            px-4
            pt-5
            pb-4
            text-left
            overflow-hidden
            shadow-xl
            transform
            transition-all
            sm:my-8 sm:align-middle sm:max-w-lg sm:w-full sm:p-6
          "
        >
          <div>
            <div class="mt-3 text-center sm:mt-5">
              <h1>{{ data[1] }}</h1>
              <ul>
                <li><strong>Livre</strong> : {{ data[0] }}</li>
                <li><strong>Ecole</strong> : {{ data[2] }}</li>
                <ul>
                  <strong>Branches</strong>
                  :
                  <li v-for="branche in data[3]" v-bind:key="branche">
                    {{ branche }}
                  </li>
                </ul>
                <ul>
                  <strong>Classes</strong>
                  :
                  <li v-for="classe in data[4]" v-bind:key="classe">
                    {{ classe.join(", ") }}
                  </li>
                </ul>
                <ul>
                  <strong>Composantes</strong>
                  :
                  <li v-for="composante in data[5]" v-bind:key="composante">
                    {{ composante }}
                  </li>
                </ul>
                <li><strong>Temps d'incantation</strong> : {{ data[6] }}</li>
                <li><strong>Portée</strong> : {{ data[7] }}</li>
                <li><strong>Cible</strong> : {{ data[8] }}</li>
                <li><strong>Durée</strong> : {{ data[9] }}</li>
                <li><strong>Jet de sauvegarde</strong> : {{ data[10] }}</li>
                <li><strong>Résistance à la magie</strong> : {{ data[11] }}</li>
                <li><strong>Description</strong> : {{ data[12] }}</li>
                <li><strong>Nécessaire</strong> : {{ data[13] }}</li>
              </ul>
            </div>
          </div>
          <div class="mt-5 sm:mt-6 flex justify-end">
            <button
              type="button"
              class="
                mt-3
                w-full
                inline-flex
                justify-center
                rounded-md
                border border-gray-300
                shadow-sm
                px-4
                py-2
                bg-white
                text-base
                font-medium
                text-gray-700
                hover:bg-gray-50
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-indigo-500
                sm:mt-0 sm:col-start-1 sm:text-sm
              "
              @click="$emit('showModal', false)"
            >
              Fermer
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "ModalDetail",
  props: ["open", "data"],
};
</script>
