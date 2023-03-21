<template>
  <div class="wrapper">
    <Mats v-if="currentMats === 0" @stepMats="currentMats = 1"/>
    <ColorMats @stepMats="currentMats = 2" @backMats="currentMats = 0"  v-if="currentMats === 1"/>
    <KitSelection @stepMats="currentMats = 3" @backMats="currentMats = 1" v-if="currentMats === 2"/>
    <ContactFrom @stepMats="currentMats = 4" @backMats="currentMats = 2" v-if="currentMats === 3"/>
  </div>
</template>
<script>
  import ColorMats from '@/components/ColorMats.vue'
  import Mats from '@/components/Mats.vue'
  import ContactFrom from '@/components/ContactForm.vue'
  import KitSelection from '@/components/KitSelection.vue'
export default {
  name: "App",

  components: {
    ColorMats,
    Mats,
    ContactFrom,
    KitSelection,
  },

  data() {
    return {
      currentMats: 0
    }
  },
};

</script>

<style>

</style>






