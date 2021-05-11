<!--  -->
<template>
  <div class="dropdown" ref="dropdownRef">
    <a
      @click.prevent="toggleOption"
      href="#"
      class="btn btn-outline-light my-2 dropdown-toggle"
      >{{ title }}</a
    >
    <ul class="dropdown-menu" :style="{ display: 'block' }" v-if="isOpen">
      <slot></slot>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, onUnmounted, ref } from "vue";

export default defineComponent({
  name: "Dropdown",
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup() {
    const isOpen = ref(false);
    const dropdownRef = ref<null | HTMLElement>(null);
    const toggleOption = () => {
      isOpen.value = !isOpen.value;
    };
    const wwhandler = (e: MouseEvent) => {
      if (dropdownRef.value) {
        if (dropdownRef.value.contains(e.target as HTMLElement)) {
        }
        console.log("dropdownRef.value", dropdownRef.value);
      }
      return "";
    };
    onMounted(() => {
      document.addEventListener("click", wwhandler);
    });
    onUnmounted(() => {
      document.removeEventListener("click", wwhandler);
    });
    return {
      isOpen,
      toggleOption,
      dropdownRef
    };
  }
});
</script>
<style scoped></style>
