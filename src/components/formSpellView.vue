<template>
  <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-900">
    {{ spell[0] }}
  </td>
  <td class="whitespace-nowrap px-2 py-2 text-xs text-gray-900">
    {{ spell[1] }}
  </td>
  <td class="whitespace-nowrap px-2 py-2 text-xs text-gray-900">
    {{ spell[2] }}
  </td>
  <td class="whitespace-nowrap px-2 py-2 text-xs text-gray-900">
    {{ spell[3].join(", ") }}
  </td>
  <td class="whitespace-nowrap px-2 py-2 text-xs text-gray-900">
    {{ spell[4].join(", ") }}
  </td>
</template>


<script>
export default {
  name: "spellView",
  props: ["spell"],
};
</script>