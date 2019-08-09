<template>
  <div id="game">
    <h1>{{ msg }}</h1>
    <div>
      <p>{{player.name}}</p>
      <div class="health">
        <div :style="myStyle1">{{ player.health }}%</div>
      </div>
    </div>
    <div>
      <p>{{nps.name}}</p>
      <div class="health">
        <div :style="myStyle2">{{ nps.health }}%</div>
      </div>
    </div>
    <button @click="atask()">atask</button>
  </div>
</template>

<script>
export default {
  name: "game",
  props: {
    msg: String
  },

  data() {
    return {
      text: "Hi!",
      player: {
        health: 100,
        name: "Motherfucker"
      },
      nps: {
        health: 100,
        name: "ill"
      }
    };
  },

  methods: {
    atask() {
      let randMF = 1 - 0.5 + Math.random() * (15 - 1 + 1);
      let randIll = 1 - 0.5 + Math.random() * (15 - 1 + 1);

      if (this.nps.health > 0 && this.player.health > 0) {
        this.nps.health -= Math.round(randMF);
        this.player.health -= Math.round(randIll);
      } else {
        this.nps.health = 100;
        this.player.health = 100;
      }

      if (this.nps.health <= 0) {
        alert("u win");
      } else if (this.player.health <= 0 ) {
        alert("u die");
      }
    }
  },
    computed: {
    myStyle1() {
      return {
        width: this.nps.health + "%",
        height: 100 + "%",
        backgroundColor: "aquamarine"
      };
    },
    myStyle2() {
      return {
        width: this.nps.health + "%",
        height: 100 + "%",
        backgroundColor: "aquamarine"
      };
    }
  },
};
</script>

<style>
#game {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 100%;
  min-width: 600px;
  justify-content: space-between;
}
h1 {
  width: 100%;
}
.health {
  margin: 15px;
  height: 20px;
  width: 250px;
  border: 1px solid black;
}

p {
  width: 100%;
}
</style>

