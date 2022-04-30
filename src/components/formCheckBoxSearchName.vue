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
          @input="$emit('spellSearch', this.searchName, this.searchNameBox)"
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
        @input="$emit('spellSearch', this.searchName, this.searchNameBox)"
      />
    </td>
  </tr>
</template>


<script>
export default {
  name: "checkBoxSearchName",
  data: function () {
    return {
      searchName: "",
      searchNameBox: false,
    };
  },
  emits: ["searchName", "searchNameBox"],
};
</script>