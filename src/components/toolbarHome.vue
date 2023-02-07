<template>
   <q-header bordered class="bg-grey-1 text-white fontInter">
      <q-toolbar class="flex">
        <q-toolbar-title class="flex items-center">
          <q-avatar rounded size="md">
            <img src="../assets/trace.png">
          </q-avatar>
          <span class="q-ml-sm fontInterSemiBold text-secondary" style="font-size: 27px">trace<span class="fontInterBold">BOX</span></span>
        </q-toolbar-title>

        <div class="flex items-center">

          <q-icon
            name="mdi-cog-outline"
            size="sm"
            color="secondary"
            class="cursor-pointer q-mr-md"
          />

          <q-btn
            class="q-mr-md"
            color="secondary"
            icon="mdi-apps"
            flat
          >

          <q-menu>
            <AppsDropDown/>
          </q-menu>

        </q-btn>

          <q-avatar size="md">
            <img src="https://media.licdn.com/dms/image/C4E03AQE7FNMTez-spQ/profile-displayphoto-shrink_800_800/0/1648867644170?e=1681344000&v=beta&t=uTI9BJ1hMHazEFkJWS5YXgRTFZYDji3S3jAs8XS3Vq4">
          </q-avatar>

          <q-icon
            name="mdi-chevron-down"
            color="secondary"
            size="xs"
            class="cursor-pointer q-ml-xs"
          />

        </div>
      </q-toolbar>



    </q-header>
</template>

<script>
import AppsDropDown from './appsDropDown.vue';


  export default {
    name: 'toolbarHome',
    components: {
    AppsDropDown
},

    data(){
      return{

      }
    }
  }
</script>

<style>

</style>
