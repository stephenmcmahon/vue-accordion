<script setup>
  defineProps(['accordionItem'])
  const emit = defineEmits(['toggleDescription']) // defining events to emit
  const handleClick = id => emit('toggleDescription', id) // emitting toggleDescription event with id attribute.
</script>

<template>
  <div :class="['accordion-item', {open: accordionItem.isOpen}]" @click="() => handleClick(accordionItem.id)">
    <div :class="['header', {open: accordionItem.isOpen}]">
      <p>{{ accordionItem.title }}</p>
    </div>
    <div :class="['description', {open: accordionItem.isOpen}]">
      <div v-html="accordionItem.description" />
    </div>
  </div>
</template>

<style lang="less">
.accordion-item {
  .header {
    background-color: #9cc0d0;
    padding: 5px 10px;
    margin-top: 15px; 
    cursor: pointer;
    transition: all 0.25s ease-in-out;
    &.open {
      background-color: #9cd0b2;      
      font-weight: bold;
    }
    p {
      font-size: 16px;
    }
  }
  .description {
    max-height: 0;
    background-color: #e7e7e7;
    padding: 0 25px;
    overflow-y: scroll;
    transition: all 0.25s ease-in-out;
    &.open {
      padding: 25px;
      max-height: 400px;
    }
  }
}
</style>