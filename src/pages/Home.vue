<template>
  <div class="home">
    <v-carousel height="700">
      <v-carousel-item
        v-for="(image, i) in images"
        :key="i"
        :src="image"
      ></v-carousel-item>
    </v-carousel>
    <v-card class="py-3 text-center">
      <countdown :date="date" title="The Celebration Begins In" />
      <v-btn class="my-2" @click="showRSVP" depressed>RSVP</v-btn>
    </v-card>
    <gmap-map
      :center="{ lat: 37.2078854, lng: -93.2930151 }"
      :zoom="20"
      style="width: 100%; height: 600px" />
    <v-card class="py-3 text-center">
      <v-dialog v-model="directions" max-width="500px" :fullscreen="$vuetify.breakpoint.xsOnly">
        <v-btn slot="activator" depressed>Get Directions</v-btn>
        <v-card class="rsvp">
          <v-card-title class="fancy-title">
            <span class="text-center">Directions</span>
          </v-card-title>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn flat @click.native="directions = false">Close</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-card>
  </div>
</template>

<script>
import countdown from '@/components/countdown.vue';
import p1 from '@/assets/img/photo1.jpg';
import p2 from '@/assets/img/photo2.jpg';
import p3 from '@/assets/img/photo3.jpg';
import p4 from '@/assets/img/photo4.jpg';
import p5 from '@/assets/img/photo5.jpg';
import p6 from '@/assets/img/photo6.jpg';

export default {
  name: 'home',
  components: { countdown },
  data: () => ({
    directions: false,
    date: 'December 16, 2018 03:00:00',
    images: [
      p1, p2, p3, p4, p5, p6,
    ],
  }),
  methods: {
    showRSVP() {
      this.$store.commit('SET_SHOW_RSVP', true);
    },
  },
};
</script>
