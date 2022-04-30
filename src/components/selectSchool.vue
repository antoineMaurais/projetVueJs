<template>
  <div>
    <label>Ecole</label>
    <select v-bind:id="id">
      <option v-for="ecole in ecoles" v-bind:key="ecole" v-bind:ecole="ecole">
        {{ ecole }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SelectSchool",
  props: {
    id: {
      type: String,
      required: true,
    },
    ecole: {
      type: String,
      required: true,
    },
  },
};
</script>
