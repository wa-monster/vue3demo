<!--  -->
<template>
  <div class="dropdown" ref="dropdownRef">
    <a href="#" class="btn btn-outline-light my-2 dropdown-toggle">{{
      title
    }}</a>
    <ul class="dropdown-menu" :style="{ display: 'block' }" v-if="isOpen">
      <slot></slot>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import useClickOutside from "../hooks/useClickOutside";

export default defineComponent({
  name: "Dropdown",
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup() {
    const dropdownRef = ref<null | HTMLElement>(null);
    const isOpen = useClickOutside(dropdownRef);

    return {
      isOpen,
      dropdownRef
    };
  }
});
</script>
<style scoped></style>
