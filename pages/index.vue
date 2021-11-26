<template>
  <v-card flat class="ma-2">
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="12">
        <v-container>
          <v-img
            lazy-src="https://picsum.photos/id/11/10/6"
            max-height="150"
            max-width="250"
            src="https://w7.pngwing.com/pngs/593/751/png-transparent-avenues-classics-warrensburg-ravioli-dessert-coach-speak-serve-tony-text-breakfast-logo.png"
          />
        </v-container>
      </v-col>

      <v-col cols="12" sm="8" md="12">
        <v-app-bar class="mx-4" color="white" flat>
          <v-btn text> Home</v-btn>
          <v-btn text> Bio</v-btn>
          <v-btn text> Music</v-btn>
          <v-btn text> Videos</v-btn>
          <v-btn text> Shows</v-btn>
          <v-btn text> Merchandize</v-btn>
          <v-btn text> Gallery</v-btn>
          <v-btn text> Contact</v-btn>

          <v-spacer></v-spacer>

          <v-btn icon>
            <v-icon>mdi-facebook</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-twitter</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-instagram</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-youtube</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-spotify</v-icon>
          </v-btn>
        </v-app-bar>
      </v-col>

      <v-carousel cycle hide-delimiters show-arrows-on-hover>
        <v-carousel-item
          v-for="(item, i) in items"
          :key="i"
          :src="item.src"
          reverse-transition="fade-transition"
          transition="fade-transition"
        ></v-carousel-item>
      </v-carousel>

      <v-col cols="12" sm="8" md="12" class="my-10">
        <div class="text-center text-h5" style="font-family: Ubuntu Mono">
          “... the Afropop dynamism of the whole record is infectious”
        </div>

        <div class="text-center my-4">— David Honigmann, Financial Times</div>
      </v-col>

      <v-col cols="12" sm="8" md="12">
        <div class="text-h3 text-center">Keep Up With Us and Our Travels</div>
      </v-col>

      <v-container>
        <v-col cols="12" sm="8" md="12">
          <div class="text-h4">What's New...</div>
        </v-col>

        <v-col cols="12" sm="8" md="12">
          <v-card class="pa-10 my-2" v-for="i in 5" :key="i">
            <v-row>
              <v-col md="1">
                <v-avatar color="primary" size="56">
                  <img
                    src="https://cdn.vuetifyjs.com/images/john.jpg"
                    alt="John" /></v-avatar
              ></v-col>
              <v-col md="11" class="text-h5">
                <a href="#" flat>LA Weekly Feature</a>
              </v-col>
              <v-col md="11" offset-md="1">
                <blockquote>
                  Exciting to be featured in LA Weekly as part of the Fowler
                  Museum's Arts of Africa Festival!
                </blockquote>
              </v-col>

              <v-col md="11" offset-md="1">
                <span>Posted on 12 Nov 2021</span>
                <v-btn small text>
                  <span>Like</span> <v-icon small>mdi-heart</v-icon></v-btn
                >
                <v-btn small text>
                  <span>Share</span> <v-icon small>mdi-share</v-icon></v-btn
                >
                <v-btn small text>
                  <span>Comment</span> <v-icon small>mdi-comment</v-icon></v-btn
                >
              </v-col>
            </v-row>
          </v-card>

          <div class="text-center my-5">
            <v-pagination v-model="page" :length="6"></v-pagination>
          </div>
        </v-col>

        <v-divider />
      </v-container>

      <v-col cols="12" sm="8" md="12">
        <div class="text-h3 text-center">
          Listen and Support Our Music Below!
        </div>
      </v-col>

      <v-col cols="12" sm="8" md="12">
        <v-row class="mx-5">
          <v-col cols="12" sm="12" md="6" v-for="i in 4" :key="i">
            <youtube
              class="mx-1"
              :video-id="videoID"
              ref="youtube"
              @playing="playing"
            />
          </v-col>
        </v-row>
        <v-divider class="my-5" />
      </v-col>

      <v-col cols="12" sm="8" md="12">
        <div class="text-h3 text-center">New upcoming mixes!</div>
      </v-col>

      <v-col cols="12" sm="8" md="12">
        <v-container>
          <v-row>
            <v-col cols="12" sm="12" md="6" v-for="i in 2" :key="i">
              <youtube
                class="mx-1"
                :video-id="videoID"
                width="99%"
                ref="youtube"
                @playing="playing"
              />
            </v-col>
          </v-row>
        </v-container>
      </v-col>

      <v-col cols="12" sm="8" md="12" class="my-10">
        <div class="text-center text-h5" style="font-family: Ubuntu Mono">
          “This very gentle but rhythmically diverse album reaps a multitude of
          rewards - it is both musically and lyrically uplifting.”
        </div>

        <div class="text-center my-4">— Songlines</div>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
import { getIdFromUrl } from "vue-youtube";
export default {
  data() {
    return {
      items: [
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
        },
      ],
      video: {
        url: "https://youtu.be/iWbqJ003XlM?list=PL7DVknAslbBfqJrho20TRnE-grgrEHGpM",
      },
    };
  },
  methods: {
    playVideo() {
      this.player.playVideo();
    },
    playing() {
      console.log("o/ we are watching!!!");
    },
    getId() {
      return getIdFromUrl(this.video.url);
    },
  },
  computed: {
    player() {
      return this.$refs.youtube.player;
    },
    videoID() {
      return this.getId();
    },
  },
};
</script>
<style scoped>
iframe {
  width: 90%;
  max-width: 650px; /* Also helpful. Optional. */
}
</style>