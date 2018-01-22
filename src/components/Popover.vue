<template>
  <div class="layout-padding row justify-center">
    <div>
      <div>
        <q-btn color="primary" >
          <q-icon name="assignment" />
          <q-popover ref="popover1">
            <q-list link separator class="scroll" style="min-width: 150px" >
              <q-btn @click="inputCountry" standard flat>
                <img src="../assets/flags/4x3/br.svg" >
                <aside style="margin-left: 20px;">Brasil</aside>
                  <sub style="margin-left: 20px; margin-top: 2px;">+55</sub>
              </q-btn><br>
              <q-btn @click="inputCountry" standard flat>
                <img src="../assets/flags/4x3/ad.svg" >
                <aside style="margin-left: 20px;">Andorra</aside>
                  <sub style="margin-left: 20px; margin-top: 2px;">+1</sub>
              </q-btn><br>
              <q-btn @click="inputCountry" standard flat>
                <img src="../assets/flags/4x3/ar.svg" >
                <aside style="margin-left: 20px;">Argentina</aside>
                  <sub style="margin-left: 20px; margin-top: 2px;">+46</sub>
              </q-btn>
            </q-list>
          </q-popover>
        </q-btn>
           <q-field v-if="selected">
                    <q-input type="number" :prefix="+55"/>
                  </q-field>
      </div>
    </div>
  </div>


</template>

<script>
import {
  Toast,
  QBtn,
  QPopover,
  QList,
  QItem,
  QItemMain,
  QIcon,
  QRadio,
  QCard,
  QCardTitle,
  QCardMain,
  QChip,
  QFixedPosition,
  QInput,
  QField
} from 'quasar'
export default {
  name: 's-popover',
  components: {
    QInput,
    QBtn,
    QPopover,
    QList,
    QItem,
    QItemMain,
    QIcon,
    QRadio,
    QCard,
    QCardTitle,
    QCardMain,
    QChip,
    QFixedPosition,
    QField
  },
  data () {
    return {
      anchorOrigin: {vertical: 'bottom', horizontal: 'left'},
      selfOrigin: {vertical: 'top', horizontal: 'left'},
      selected: false
    }
  },
  methods: {
    inputCountry() {
      this.selected = !this.selected;
      toggle();
    }
  },
  computed: {
    anchor () {
      return `${this.anchorOrigin.vertical} ${this.anchorOrigin.horizontal}`
    },
    self () {
      return `${this.selfOrigin.vertical} ${this.selfOrigin.horizontal}`
    }
  }
}
</script>

<style>
  img {
    width: 15px;
    height: 15px;
  }
</style>
