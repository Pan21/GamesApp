<template>
<div>
    <h1>Games App</h1>
    <button v-on:click="getGamesData">Load game Data</button>
    <div v-for="gameData in gameDataList" :key="gameData.id" class="games-data">
    <div class="games-stats">

    <div class="games-icon">
        <img :src="`${ gameData.logo }`">
      </div>

      <div class="textContain">
      
      <div>
      <h1>Useful Facts about {{gameData.developer}}</h1>

      <p>{{gameData.developer}} was established in the year {{gameData.year}}</p>
      
      <p>Their headquarters is located in {{gameData.location}}</p>
      </div>

      </div>
        <div>
        </div>
      </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "games",
  data() {
    return {
      gameDataList: []
    };
  },
  methods: {
    getGamesData() {
      fetch("data.json")
        .then(response => response.json())
        .then(data => (this.gameDataList = data));
    }
  }
};
</script>

<style scoped>
.games-data {
  
  width: 30%;
  display: flex;
  margin: 0 auto;
  background-color: lightgray;
  
  border: 10px solid black;
  padding: 20px;
  margin-bottom: 20px;

}

.textContain{
margin: 0 auto;
width: 300px;
height: 400px;
background-color: teal;
}

.games-icon {
  flex-grow: 3;
  justify-content: center;
}

.games-stats {
  flex-grow: 8;

  margin: 0 auto;
}


img {
  width:40%;
  border-radius: 100px;
}

button {
    padding:10px;
    background-color: #1aa832;
    color: white;
    border: 1px solid #ccc;
}
</style>