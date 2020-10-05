<template>
  <div>
    <div class="container">
      <br />
      <img id="lg"
        src="https://www.aoos.com/media/catalog/product/cache/d3537c321a700cb9c1fb7a409c881eeb/m/i/microphone_live_music_neon_sign_l187.jpg"
        width="15%"
      />
      <h1 id="gm">Google Music</h1>
      <b-row id="cc">
        <b-col cols="8">
          <div>
            <b-card style="background-color: black">
              <b-card-body>
                <input
                  id="b1"
                  v-model="textSearch"
                  type="text"
                  placeholder="  Search..."
                />
                <button id="b2" @click="searchData()">Search</button>
              </b-card-body>
            </b-card>
          </div>
        </b-col>
        <b-col cols="9">
          <div v-for="list in playList" :key="list.trackId" class="mt-4">
            <b-card
              no-body
              class="overflow-hidden"
              style="width: 100%"
              border-variant="info"
            >
              <b-row no-gutters>
                <b-col md="2">
                  <b-card-img
                    :src="list.artworkUrl100"
                    :alt="list.artistName"
                    class="rounded-0"
                  />
                  <router-link
                    :to="{
                      name: 'MureInfo',
                      params: {
                        TrackName: list.trackName,
                        ArtistName: list.artistName,
                        CollectionName: list.collectionName,
                        TrackNumber: list.trackNumber,
                        ReleaseDate: list.releaseDate,
                        TrackCount: list.trackCount,
                        CollectionPrice: list.collectionPrice,
                        Currency: list.currency,
                        TrackPrice: list.trackPrice,
                        CollectionViewUrl: list.collectionViewUrl,
                        ArtworkUrl100: list.artworkUrl100,
                        PreviewUrl: list.previewUrl,
                        ArtistViewUrl: list.artistViewUrl,
                      },
                    }"
                  >
                    <b-button style="border: 2px solid rgba(255, 255, 255, 0.863);background-color: rgb(240, 77, 164)" variant="info">รายละเอียดเพิ่มเติม</b-button>
                  </router-link>
                </b-col>
                <b-col id="ta" md="10">
                  <b-card-body :title="list.trackName">
                    <div>Artist : {{ list.artistName }}</div>
                    <div>Collection : {{ list.collectionName }}</div>
                    <b-card-text>
                      <audio controls>
                        <source :src="list.previewUrl" type="audio/mpeg" />
                      </audio>
                    </b-card-text>
                  </b-card-body>
                </b-col>
              </b-row>
            </b-card>
          </div>
        </b-col>
      </b-row>
      <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      playList: null,
      textSearch: "",
    };
  },

  methods: {
    searchData() {
      axios
        .get(
          "https://itunes.apple.com/search?term=+" +
            this.textSearch +
            "&limit=100"
        )
        .then((response) => {
          this.playList = response.data.results.slice(1, 15);
        })
        .catch((err) => {
          // eslint-disable-next-line no-console
          console.log(err);
        });
    },
  },
};
</script>

<style>
#text {
  font-size: 20px;
  color: rgb(0, 0, 0);
}
#lg{
    display: flex;
  justify-content: center;
    margin-left: 450px;
}
#te {
  font-size: 40px;
  text-align: center;
}
#ta {
  text-align: center;
  background-color: rgb(211, 145, 180);
}
#cc {
  display: flex;
  justify-content: center;
  margin-left: 50px;
}
#b1 {
  border-radius: 15px;
  width: 350px;
  height: 50px;
  margin: 6px;
  background-color: rgb(235, 235, 235);
  border: 2px solid rgb(235, 235, 235);
}
#b2 {
  border-radius: 15px;
  width: 100px;
  height: 50px;
  background-color: rgba(207, 31, 119, 0.863);
  border: 2px solid rgba(207, 31, 119, 0.863);
  color: aliceblue;
}
#gm{
display: flex;
  justify-content: center;
  margin-right: 50px;
  font-size: 35px;
  color: rgb(240, 77, 164);
}

</style>
