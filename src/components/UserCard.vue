<template>
  <q-card class="my-card q-ma-sm" style="width: 300px; border-left: 6px solid lightskyblue; ">
    <q-card-section>
      <div class="text-h6">{{ user.name }}</div>
      <div class="text-subtitle2">{{ user.email }}</div>
      <div class="text-subtitle2">Cidade: {{ user.address.city }}</div>
    </q-card-section>
    <hr>
    <q-card-actions align="right">
      <q-btn color = "primary" label="Ver Detalhes" @click="$emit('ver-detalhes', user)" />
    </q-card-actions>
  </q-card>
</template>

<script setup>
defineProps({
  user: Object
})
</script>