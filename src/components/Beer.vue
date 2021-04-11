<template>
  <div class="main" @click="clickedbeer()">
    <img :src="`${beerData.image_url}`" alt="`image of beer" style="max-height: 200px; max-width: 200px; margin-top: 5px;" />
    <p class="smaller" v-if="this.beerData.image_url === null">
        No Image
    </p>
    <h3 id="beername">{{ beerData.name }}</h3>
    <p class="smaller">{{beerData.abv}}%</p>
    <button id="details" @click="handleDetails()">Details</button>
		<dialog v-if="isClicked" open>
      <button id="close" @click="closetab()">x</button>
      <img :src="`${beerData.image_url}`" alt="`image of beer" style="max-height: 400px; max-width: 400px;" /><br>
      <b>{{beerData.name}}</b><br><br>
      <b>Alcohol by Volume:</b>
      {{beerData.abv}}%<br><br>
      <b>Description:</b><br>
      {{beerData.description}}
      </dialog>
</div>
</template>
<script>
export default {
  components: {
  },
  name: "Beer",
  props: {
    beerData: Object
  },
  data() {
    return {
        isClicked : false
    };
  },

  methods: {
      clickedbeer(){
          console.log(this.beerData.name + " was clicked!");
      },
      handleDetails(){
        this.isClicked = !this.isClicked
      },
      closetab(){
        this.isClicked = false;
      }
  },
};
</script>
<style scoped>
dialog{
  box-shadow: 3px 3px rgba(0,0,0,0.4);
  background-color:rgb(240, 240, 240);
  color:black;
  width: 50%;
  position:fixed;
  top: 120px;
  margin-left: auto;
  margin-right: auto;
  border:none;
  border-radius: 10px;
  justify-content: center;
  align-content: center;
  font-size: 14px;
  font-weight: normal;
}
h3{
  color:black;
  font-size:16px;
  font-weight: bold;
}
.smaller{
    font-size: 12px;
    font-weight: normal;
}

#details{
  margin-bottom: 5px;
}
#close{
  position: absolute;
  top: 0;
  right: 0;
  width: 24px;
  font-weight: bold;
}
</style>