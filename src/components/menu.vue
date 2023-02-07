<template>
  <q-drawer
        v-model="drawer"
        show-if-above
        bordered
        :mini="!drawer || miniState"
        :width="250"
        :mini-width="70"
        :breakpoint="500"
        class="bg-grey-1 text-secondary fontInter"
        style="font-size: 16px"
      >

      <template v-slot:mini>

        <div class="absolute" style="top: 40vh; right: -25px">

          <q-btn
            dense
            outline
            square
            color="grey-4"
            class="drawer_btn"
            @click="miniState = false"
          >
            <q-icon
                :name="miniState ? 'chevron_right' : 'chevron_left'"
                color="secondary"
              />

              <q-tooltip class="bg-secondary" anchor="center right" self="center left" :offset="[10, 10]">
                Expandir Menu
              </q-tooltip>

          </q-btn>
        </div>

        <q-scroll-area style="height: calc(100% - 70px);" :horizontal-thumb-style="{ opacity: 0 }">
          <div class="q-py-lg">
              <div class="text-center">
                <q-icon size="xs" name="mdi-home-variant-outline" class="cursor-pointer q-mb-sm"/>
                <div
                  v-for="m in menu"
                  :key="m.label"
                >
                <div class="text-grey-7">
                  {{ m.label.substr(0,1) }}
                  <q-tooltip class="bg-grey-7" anchor="center right" self="center left" :offset="[10, 10]">
                    {{ m.label }}
                  </q-tooltip>
                </div>

                <div
                    v-for="menus in m.subMenu"
                    :key="menus.label"
                    class="q-my-xs"
                    v-ripple
                >

                  <q-icon
                    size="xs"
                    :name="menus.icon"
                    class="cursor-pointer"
                  >
                    <q-tooltip class="bg-secondary" anchor="center right" self="center left" :offset="[10, 10]">
                      {{ menus.label }}
                    </q-tooltip>
                  </q-icon>

                </div>


                </div>
              </div>
          </div>
        </q-scroll-area>

        <div class="text-center full-width">
          <q-avatar size="lg" style="border-radius: 100%;">
            <img src="https://media.licdn.com/dms/image/C4E03AQE7FNMTez-spQ/profile-displayphoto-shrink_800_800/0/1648867644170?e=1681344000&v=beta&t=uTI9BJ1hMHazEFkJWS5YXgRTFZYDji3S3jAs8XS3Vq4">
          </q-avatar>
        </div>



      </template>

        <q-scroll-area style="height: calc(100% - 70px);" :horizontal-thumb-style="{ opacity: 0 }">
          <q-list padding>

            <q-item clickable dense v-ripple class="q-mx-md">

              <q-item-section avatar >
                <div class="flex items-center justify-center">
                  <q-icon size="xs" name="mdi-home-variant-outline" />
                  <span class="q-ml-md">Home</span>
                </div>

              </q-item-section>

            </q-item>

            <q-expansion-item
              clickable
              dense
              expanded-icon="mdi-minus"
              expand-icon="mdi-plus"
              expand-icon-class="text-grey-6 icon-size"
              icon="mdi-plus"
              v-for="m in menu"
              :key="m.label"
            >

                <template v-slot:header>
                    <q-item-section style="font-size: 14px" class="text-grey-7">{{ m.label }}</q-item-section>
                </template>

                <template v-slot:append>
                  <q-icon name="search" color="red"></q-icon>
                </template>

                <q-item
                  clickable
                  dense
                  v-ripple
                  v-for="menus in m.subMenu"
                  :key="menus.label"
                  class="q-mx-md text-secondary"
                >

                  <q-item-section avatar >
                    <div class="flex items-center justify-center">
                      <q-icon size="xs" :name="menus.icon" />
                      <span class="q-ml-md">{{ menus.label }}</span>
                    </div>
                  </q-item-section>
                </q-item>


            </q-expansion-item>
          </q-list>
        </q-scroll-area>

        <div style="height: 70px" class="q-pa-sm">
          <q-card flat class="bg-primary fit q-pa-sm items-center justify-around flex">

            <q-avatar size="lg" style="border-radius: 100%;">
              <img src="https://media.licdn.com/dms/image/C4E03AQE7FNMTez-spQ/profile-displayphoto-shrink_800_800/0/1648867644170?e=1681344000&v=beta&t=uTI9BJ1hMHazEFkJWS5YXgRTFZYDji3S3jAs8XS3Vq4">
            </q-avatar>

            <div class="text-white fontInter">
              <div class="fontInter" style="font-size: 16px">
                Yuri Grando
              </div>
              <div class="fontInterLight" style="font-size: 11px">
                Spark Intralogistica
              </div>
            </div>

            <q-icon
              name="mdi-cog-outline"
              size="sm"
              color="white"
              class="cursor-pointer q-ml-md"
            />


          </q-card>
        </div>


        <div class="absolute" style="top: 40vh; right: -25px">

          <q-btn
            dense
            outline
            square
            color="grey-4"
            class="drawer_btn"
            @click="miniState = true"
          >
            <q-icon

                :name="miniState ? 'chevron_right' : 'chevron_left'"
                color="secondary"
              />

              <q-tooltip class="bg-secondary" anchor="center right" self="center left" :offset="[10, 10]">
                Ocultar Menu
              </q-tooltip>

          </q-btn>
        </div>
      </q-drawer>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'myMenu',
  data () {
    const miniState = ref(false);

    const menu = ref([

      {
        label: 'Emitente',
        icon: 'mdi-home-variant-outline',
        subMenu: [
          {
            label: 'Volume',
            icon: 'mdi-package-variant-closed'
          },
          {
            label: 'Remessa',
            icon: 'mdi-inbox-multiple-outline'
          }
        ]
      },
      {
        label: 'Transportador',
        icon: 'mdi-home-variant-outline',
        subMenu: [
          {
            label: 'Montar Carga',
            icon: 'mdi-truck-check-outline'
          },
          {
            label: 'Visualizar Carga',
            icon: 'mdi-truck-outline'
          },
          {
            label: 'Editar Carga',
            icon: 'mdi-pencil-outline'
          }
        ]
      },
      {
        label: 'Análise',
        icon: 'mdi-home-variant-outline',
        subMenu: [
          {
            label: 'Operacional',
            icon: 'mdi-note-search-outline'
          },
          {
            label: 'Rastreamento',
            icon: 'mdi-map-marker-outline'
          },
          {
            label: 'Métricas',
            icon: 'mdi-chart-box-outline'
          }
        ]
      },
      {
        label: 'Cadastros',
        icon: 'mdi-home-variant-outline',
        subMenu: [
          {
            label: 'Empresas',
            icon: 'mdi-account-group-outline'
          },
          {
            label: 'Usuários',
            icon: 'mdi-account-outline'
          },
          {
            label: 'Veículos',
            icon: 'mdi-truck-fast-outline'
          }
        ]
      },
      {
        label: 'Destinatário',
        icon: 'mdi-home-variant-outline',
        subMenu: [
          {
            label: 'Pedidos',
            icon: 'mdi-package-variant'
          }
        ]
      }
    ])

    return {
      drawer: ref(false),
      miniState,
      menu,





      drawerClick (e) {
        // if in "mini" state and user
        // click on drawer, we switch it to "normal" mode
        if (miniState.value) {
          miniState.value = false

          // notice we have registered an event with capture flag;
          // we need to stop further propagation as this click is
          // intended for switching drawer to "normal" mode only
          e.stopPropagation()
        }
      }
    }
  }
}
</script>

<style style="sass">

.drawer_btn {
  width: 25px;
  height: 50px;
  border-color: black;
  border: 1rem;
}

.icon-size i.q-icon{
  font-size: 15px
}

</style>
