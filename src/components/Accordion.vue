<script setup>
  import { ref } from 'vue'
  import AccordionItem from './AccordionItem.vue'
  const data = [
    { id: 1,
      title: 'Click to open and close',
      description: 'Content Goes Here' },
    { id: 2,
      title: 'Click to open and close',
      description: 'Content Goes Here' }
  ]
  const accordionItems = ref(data) // data is above array for Accordion content
  const toggleDescription = id => {
    accordionItems.value = accordionItems.value.map(accordionItem => accordionItem.isOpen && accordionItem.id !== id ? {...accordionItem, isOpen: false} : accordionItem)
    accordionItems.value = accordionItems.value.map(accordionItem => accordionItem.id === id ? {...accordionItem, isOpen: !accordionItem.isOpen} : accordionItem)
  }
</script>

<template>
  <div>
    <AccordionItem
      v-for="accordionItem in accordionItems"
      :key="accordionItem.id"
      :accordionItem="accordionItem"
      @toggle-description="toggleDescription"
    />
  </div>
</template>
 
<style scoped>

</style>