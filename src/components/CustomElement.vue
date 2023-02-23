<template>
  <component :is="tag" v-bind="$attrs">
   <slot></slot>
  </component>
</template>

<script lang="ts">
import { defineComponent, h, VNode } from 'vue'

export default defineComponent({
  props: {
    tag: {
      type: String,
      default: 'input'
    }
  },
  setup(props, { attrs, slots }): () => VNode {
    return () => h(props.tag, attrs, slots.default?.())
  }
})
</script>