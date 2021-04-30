<template>
  <div class="row">
    <div class="col-4 mb-4" v-for="col in columnList" :key="col.id">
      <div class="card h-100 shadow-sm">
        <div class="card-body text-center">
          <img
            class="rounded-circle border border-light w-25 my-"
            :src="col.avatar"
            :alt="col.title"
          />

          <h5 class="card-title">{{ col.title }}</h5>
          <h5 class="card-text text-left">{{ col.description }}</h5>
          <a href="#" class="btn btn-outline-primary">进入专栏</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";

export interface ColumnProps {
  id: number;
  title: string;
  avatar?: string;
  description: string;
}

export default defineComponent({
  name: "ColumnList",
  props: {
    list: {
      type: Array as PropType<ColumnProps[]>,
      required: true
    }
  },
  setup(props) {
    const columnList = computed(() => {
      return props.list.map(v => {
        if (!v.avatar) {
          v.avatar = require("@/assets/avatar.jpg");
        }
        return v;
      });
    });
    return {
      columnList
    };
  }
});
</script>
