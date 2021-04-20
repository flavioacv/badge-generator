<template>
  <q-page class="flex flex-center">
    <q-card flat bordered class="my-card">
      <q-card-section class="row justify-around">
        <q-input
          class="q-mr-sm"
          filled
          v-model="logo"
          style="width:48%"
          label="Logo"
        />
        <q-input filled v-model="titulo" style="width:48%" label="Titulo" />
      </q-card-section>

      <q-card-section class="row justify-around">
        <q-input
          filled
          v-model="corLogo"
          :rules="['anyColor']"
          hint="Cor da logo"
          :style="'width:48%; border-top: 5px solid ' + corLogo"
        >
          <template v-slot:append>
            <q-icon name="colorize" class="cursor-pointer">
              <q-popup-proxy transition-show="scale" transition-hide="scale">
                <q-color v-model="corLogo" />
              </q-popup-proxy>
            </q-icon>
          </template>
        </q-input>
        <q-input
          filled
          v-model="corFundo"
          :rules="['anyColor']"
          hint="Cor do fundo"
          :style="'width:48%; border-top: 5px solid ' + corFundo"
        >
          <template v-slot:append>
            <q-icon name="colorize" class="cursor-pointer">
              <q-popup-proxy transition-show="scale" transition-hide="scale">
                <q-color v-model="corFundo" />
              </q-popup-proxy>
            </q-icon>
          </template>
        </q-input>
      </q-card-section>

      <q-card-section>
        <q-btn
          class="full-width"
          push
          color="primary"
          label="Atualizar"
          @click="atualizar"
        ></q-btn>
      </q-card-section>

      <q-card-section class="row justify-center">
        <p class="text-h6">PREVIEW</p>
      </q-card-section>

      <q-card-section class="flex" style="flex-direction: column; width: auto">
        <q-scroll-area style="height: 50px; width: auto;">
          <div class="q-py-xs">
            <img :src="link" />
          </div>
        </q-scroll-area>
        <q-btn
          push
          color="primary"
          label="Copiar"
          @click="copy"
        />
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { copyToClipboard } from 'quasar'
export default {
  name: 'Index',
  data () {
    return {
      logo: 'Vue.js',
      titulo: 'Vue js',
      corLogo: '#25CA0F',
      corFundo: '#000000',
      link: ''
    }
  },
  mounted () {
    this.atualizar()
  },
  methods: {
    atualizar () {
      this.link = ''
      setTimeout(() => {
        this.link =
          'https://img.shields.io/badge/-' +
          this.titulo +
          '-' +
          this.corFundo.split('#')[1] +
          '?style=for-the-badge&logo=' +
          this.logo +
          '&logoColor=' +
          this.corLogo.split('#')[1]
      }, 500)
    },
    copy () {
      copyToClipboard(this.link)
        .then(() => {
          // success!
          alert('Copiado')
        })
        .catch(() => {
          // fail
        })
    }
  }
}
</script>
