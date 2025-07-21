<template>
  <v-container fluid class="pa-6">
    <v-row align="start" dense>

      <!-- FORM DI KIRI -->
      <v-col cols="12" md="5">
        <v-card elevation="8" class="pa-6">
          <v-card-title class="text-h5 font-weight-bold text-center pb-2">
            📋 Form Pendaftaran Siswa
          </v-card-title>

          <v-divider class="mb-4"></v-divider>

          <v-card-text>
            <v-text-field
              v-model="nama"
              label="Nama Lengkap"
              variant="outlined"
              class="mb-3"
            />
            <v-text-field
              v-model="ttl"
              label="Tempat, Tanggal Lahir"
              variant="outlined"
              class="mb-3"
            />
            <v-text-field
              v-model="hobi"
              label="Hobi"
              variant="outlined"
              class="mb-4"
            />

            <v-btn color="primary" block @click="submit">
              Kirim Data
            </v-btn>

            <v-alert
              v-if="submitted"
              type="success"
              class="mt-4"
              border="start"
              colored-border
            >
              ✅ Data siswa berhasil dikirim!
            </v-alert>
          </v-card-text>
        </v-card>
      </v-col>

      <!-- DAFTAR SISWA DI KANAN -->
      <v-col cols="12" md="7" v-if="dataSiswa.length > 0">
        <v-card elevation="4" class="pa-4">
          <v-card-title class="text-h6 font-weight-bold text-center">
            📄 Daftar Siswa
          </v-card-title>
          <v-divider class="mb-3" />

          <v-list>
            <v-list-item v-for="(siswa, index) in dataSiswa" :key="index">
              <v-list-item-content>
                <v-list-item-title class="font-weight-bold">
                  {{ siswa.nama }}
                </v-list-item-title>
                <v-list-item-subtitle>
                  TTL: {{ siswa.ttl }} | Hobi: {{ siswa.hobi }}
                </v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn icon color="error" @click="hapusSiswa(index)">
                  <v-icon>mdi-delete</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list>
        </v-card>
      </v-col>

    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'

const nama = ref('')
const ttl = ref('')
const hobi = ref('')
const submitted = ref(false)
const dataSiswa = ref([])

function submit() {
  if (nama.value && ttl.value && hobi.value) {
    dataSiswa.value.push({
      nama: nama.value,
      ttl: ttl.value,
      hobi: hobi.value,
    })

    nama.value = ''
    ttl.value = ''
    hobi.value = ''
    submitted.value = true

    setTimeout(() => {
      submitted.value = false
    }, 3000)
  }
}

function hapusSiswa(index) {
  dataSiswa.value.splice(index, 1)
}
</script>
