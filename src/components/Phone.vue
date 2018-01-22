<template>
  <div class="layout-padding row justify-center">
    <div style="display: flex;">

      <div style="display: flex; margin-top: 25px; margin-left: -40px;">
           <s-flags></s-flags>
        <div>
          <q-input float-label="Phone" style="width: 215px; margin-left: 10px;"/>
        </div>
        <div style="width: 215px; max-width: 90vw; margin-left: 10px;">
          <q-input id="label" color="primaryy" v-model="terms" float-label="Label">
              <q-autocomplete @search="search" :min-characters="1" @selected="selected" :static-data="{field: 'value', list: label}"/>
          </q-input>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import {
  QAutocomplete,
  QSearch,
  QInput,
  uid,
  filter,
  Toast,
  QSelect,
  QIcon
} from 'quasar'
import SFlags from './Flags.vue'

export default {
  name: 's-phone',
  components: {
    QAutocomplete,
    QSearch,
    QInput,
    QSelect,
    QIcon,
    SFlags
  },
  props: {
    customLabel: {
      type: Boolean,
      default: false,
      required: false
    },
    isConfirmed:{
      type: Boolean,
      default: true,
      required: true
    },
    hasWhatsapp:{
      type: Boolean,
      default: true,
      required: true
    }
  },
  data () {
    return {
      terms: '',
        options: [
          {
            value: 'Residential', // The value given, when selected
            label: 'Residential', // The value displayed as main label for this suggested selection
          },
          {
            value: 'Commercial', // The value given, when selected
            label: 'Commercial', // The value displayed as main label for this suggested selection
          },
          {
            value: 'Cell Phone', // The value given, when selected
            label: 'Cell Phone', // The value displayed as main label for this suggested selection
          },
          {
            value: 'Other', // The value given, when selected
            label: 'Other', // The value displayed as main label for this suggested selection
          }
        ],
    }
  },
  methods: {
    search (terms, done) {
      setTimeout(() => {
        done(filter(terms, {field, list}))
      }, 100)
    },
  },
  computed: {
    label() {
      return this.options.map((option)=> {
        return {
          label: option.label,
          value: option.value,
        }
      })
    }
  }
}
</script>
