<template>
    <v-container fluid>
        <v-layout row wrap>
            <v-flex xs12 sm6 offset-sm3 mt-5>
            <form>
                <v-select
                    :items='districts'
                    v-model='district'
                    label='District'
                    @input='test'                   
                ></v-select>
                <v-select
                    :items='locales'
                    v-model='locale'
                    label='Locale'
                ></v-select>
            </form>
        Preview
        <hr>
        <p>Locale: {{ locale }}</p>
            </v-flex>
        </v-layout>

    </v-container>
</template>

<script>
  export default {
    data () {
      return {
        alert: true,
        districts: [
            {text: 'Abra', value: 1},
            {text: 'Cagayan South', value: 2},
            {text: 'Benguet', value: 3}
        ],
        district: '',
        localemaster: [
            {
                localeid: 1,
                localename: 'Baguio',
                districtid: 3
            },
            {
                localeid: 2,
                localename: 'Tuguegarao',
                districtid: 2
            },
            {
                localeid: 3,
                localename: 'Ilocos',
                districtid: 1
            },
            {
                localeid: 4,
                localename: 'Kias',
                districtid: 3
            },
            {
                localeid: 5,
                localename: 'Balatoc',
                districtid: 3
            }
        ],
        locales: [],
        locale: ''
    }
    },
    methods: {
        test() {
           let locales = this.localemaster.filter(locale => {
               return locale.districtid === this.district
           })
           let newlocale = []
           locales.forEach((locale, index) => {
               newlocale[index] = {text: locale.localename, value: locale.localeid}
           })
           this.locales = newlocale
        }
    }
  }
</script>