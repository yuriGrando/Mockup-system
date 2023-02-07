<template>

  <q-card bordered class="fontInter text-secondary bg-grey-1">
    <div
      class="q-pa-sm"
      style="width: 320px; height: 410px;"
    >
      <div style="font-size: 18px">
        Apps
      </div>

      <q-separator  spaced class="q-mb-md"/>

      <q-scroll-area style="height: 350px">

        <div class="row q-col-gutter-sm">
          <div
            class="col-4 text-center q-mb-md"
            v-for="app in apps"
            :key="app.name"
          >
            <q-avatar size="lg">
              <img :src="app.src">
            </q-avatar>
            <div>
              {{app.name}}
            </div>
          </div>

        </div>

      </q-scroll-area>

    </div>
  </q-card>

</template>
<script>

export default {
  name: 'appsDropdown',

  data(){
    return {

      apps: [
        {
          name: 'Conta',
          src: 'https://media.licdn.com/dms/image/C4E03AQE7FNMTez-spQ/profile-displayphoto-shrink_800_800/0/1648867644170?e=1681344000&v=beta&t=uTI9BJ1hMHazEFkJWS5YXgRTFZYDji3S3jAs8XS3Vq4'
        },

        {
          name: 'traceBOX',
          src: new URL('../../public/apps/trace.png', import.meta.url).href
        },

        {
          name: 'myControl',
          src: new URL('../../public/apps/mycontrol.png', import.meta.url).href
        },

        {
          name: 'myPonto',
          src: new URL('../../public/apps/myponto.png', import.meta.url).href
        },
        {
          name: 'myWMS',
          src: new URL('../../public/apps/mywms.png', import.meta.url).href
        },
        {
          name: 'sparke',
          src: new URL('../../public/apps/sparke.png', import.meta.url).href
        },
        {
          name: 'myCUBI',
          src: new URL('../../public/apps/mycubi.png', import.meta.url).href
        },
        {
          name: 'myAGV',
          src: new URL('../../public/apps/myagv.png', import.meta.url).href
        },
        {
          name: 'myBI',
          src: new URL('../../public/apps/mybi.png', import.meta.url).href
        },
        {
          name: 'myIDENT',
          src: new URL('../../public/apps/myident.png', import.meta.url).href
        },
        {
          name: 'myCONTAINER',
          src: new URL('../../public/apps/mycontainer.png', import.meta.url).href
        },
        {
          name: 'Ajuda',
          src: new URL('../../public/apps/help.png', import.meta.url).href
        },
      ]

    }
  }
}
</script>
