<template>
  <div v-show="affiche">
    <div class="flex items-center">
      <label for="select" class="w-32 text-justify block text-sm font-medium text-gray-700">{{label}}</label>
      <select @change="$emit('eventSelectOption', name, $event.target.value)" id="select" name="select" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md">
        <option v-for="option in options" v-bind:key="option">
        {{ option }}
      </option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "SelectList",
  emits: ["eventSelectOption"],
  props: ["label", "options", "name", "affiche"]
};
</script>
