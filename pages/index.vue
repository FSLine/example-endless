<template>
  <LoopScroll>

    <v-card
      class="mt-10 mx-5"
      elevation="2"
      v-for="n in 6"
      :key="n"
      @click="log(n)"
    >
    <v-card-title>{{n}}</v-card-title>
    </v-card>
  </LoopScroll>
</template>


<script>
export default {


    methods: {

	    log(n) {

            console.log('n'+n)

        }

    }
}
</script>