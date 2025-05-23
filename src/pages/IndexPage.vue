<template>
      <header><p class="text-h2" style="text-align: center; margin-top: 1vw;">Quasar with Vue 3</p>
      <h5 style="text-align: center;">by Felipe Felix</h5></header>
  <q-page class="q-pa-md">
    <div class="row justify-center q-gutter-md" style="margin: 0 auto;">
      <div 
        v-for="user in users" 
        :key="user.id" 
        class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl-2"
        style="min-width: 250px; max-width: 300px; margin-left: 4vw; margin-right: 4vw;"
      >
        <UserCard 
          :user="user" 
          @ver-detalhes="openDetails" 
        />
      </div>
    </div>

    <q-dialog v-model="showDialog" persistent>
      <UserDetailsCard
        v-if="selectedUser"
        :user="selectedUser"
        @close="showDialog = false"
      />
    </q-dialog>
  </q-page>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

import UserCard from 'src/components/UserCard.vue'
import UserDetailsCard from 'src/components/UserDetailsCard.vue'

const users = ref([])
const showDialog = ref(false)
const selectedUser = ref(null)

function openDetails(user) {
  selectedUser.value = user
  showDialog.value = true
}

async function loadUsers() {
  try {
    const res = await axios.get('https://jsonplaceholder.typicode.com/users')
    users.value = res.data
  } catch (error) {
    console.error('Erro ao carregar usuários:', error)
  }
}

onMounted(() => {
  loadUsers()
})
</script>