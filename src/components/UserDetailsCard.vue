<template>
  <q-card style="min-width: 400px; max-width: 600px;">
    <q-card-section>
      <div class="text-h6">{{ user.name }}</div>
      <div><strong>Usuário:</strong> {{ user.username }}</div>
      <div><strong>Email:</strong> {{ user.email }}</div>
      <div>
        <strong>Endereço:</strong>
        {{ user.address.street }},{{ user.address.city }}
      </div>
      <div><strong>Telefone:</strong> {{ user.phone }}</div>
      <div><strong>Website:</strong> {{ user.website }}</div>
      <div><strong>Empresa:</strong> {{ user.company.name }}</div>
    </q-card-section>

    <q-card-actions align="right">
      <q-btn flat label="Fechar" color="primary" @click="$emit('close')" />
    </q-card-actions>
  </q-card>
</template>

<script setup>
defineProps({
  user: Object
});
</script>
