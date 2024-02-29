<script setup>
  import SvgIcon from './SvgIcon.vue'
  defineProps(['accordionItem'])
  const emit = defineEmits(['toggleDescription']) // defining events to emit
  const handleClick = id => emit('toggleDescription', id) // emitting toggleDescription event with id attribute.
</script>

<template>
  <div :class="['accordion-item', {open: accordionItem.isOpen}]" @click="() => handleClick(accordionItem.id)">
    <!-- Content for Accordion item -->
  </div>
</template>

<style>

</style>