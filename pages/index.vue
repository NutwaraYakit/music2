<template>
  <div>
    <div class="container">
      <br />
      <br />
      <img id="hm"
      src="https://www.aoos.com/media/catalog/product/cache/d3537c321a700cb9c1fb7a409c881eeb/m/i/microphone_live_music_neon_sign_l187.jpg"
      width="30%">
      <br />
      <h1 id="wc">Welcome to Google Music !</h1><br />
      <b-nav-item id="btt" to="/Search">Search Music</b-nav-item >
      <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {}

</script>

<style>
#hm{
  display: flex;
  justify-content: center;
  margin-left: 370px;
}
#wc{
  display: flex;
  justify-content: center;
  color: rgb(245, 80, 168);
}
#btt{
  display: flex;
  justify-content: center;
  margin-left: 430px;
  border-radius: 15px;
  width: 180px;
  height:50px;
  background-color: rgba(207, 31, 119, 0.863);
  border: 2px solid  rgba(207, 31, 119, 0.863);
  font-size: 20px;
}
</style>
