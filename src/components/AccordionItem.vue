<script setup>
  defineProps(['accordionItem'])
  const emit = defineEmits(['toggleDescription']) // defining events to emit
  const handleClick = id => emit('toggleDescription', id) // emitting toggleDescription event with id attribute.
</script>

<template>
  <div :class="['accordion-item', {open: accordionItem.isOpen}]" @click="() => handleClick(accordionItem.id)">
    <div :class="['header', {open: accordionItem.isOpen}]">
      <h2>{{ accordionItem.title }}</h2>
    </div>
    <div :class="['description', {open: accordionItem.isOpen}]">
      <div v-html="accordionItem.description" />
    </div>
  </div>
</template>

<style lang="less">
.accordion-item {
  .header {
    h2 {
      font-size: 16px;
    }
    cursor: pointer;
    &.open {
      font-weight: bold;
    }
  }
  .description {
    max-height: 0;
    padding: 0 25px;
    overflow-y: scroll;
    &.open {
      padding: 25px;
      max-height: 400px;
    }
  }
}
</style>