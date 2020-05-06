<template>
  <div class="home">
        <div class="card-wrap">
          <div class="card" v-for="(card, index) in cards" :key="index">
            <p>{{card.name}}</p>
            <p>{{card.value}}</p>
            <i v-if="card.arrow" class="fa fa-arrow-up" aria-hidden="true"></i>
            <i v-else class="fa fa-arrow-down" aria-hidden="true"></i>
            <div @click="stopInterval(index)" class="button r" id="button-1">
              <input type="checkbox" class="checkbox">
              <div class="knobs"></div>
              <div class="layer"></div>
            </div>
          </div>
        </div>

  </div>
</template>

<script>

  export default {
    name: "Home",
    data() {
      return {
        cards: [
          {id: 1, name: 'A', value: 3, stop:false, arrow: false},
          {id: 2, name: 'B', value: 3, stop:false, arrow: false},
          {id: 3, name: 'C', value: 3, stop:false, arrow: false},
          {id: 4, name: 'D', value: 3, stop:false, arrow: false},
          {id: 5, name: 'E', value: 3, stop:false, arrow: false},
          {id: 6, name: 'F', value: 3, stop:false, arrow: false},
          {id: 7, name: 'G', value: 3, stop:false, arrow: false},
          {id: 8, name: 'H', value: 3, stop:false, arrow: false},
          {id: 9, name: 'I', value: 3, stop:false, arrow: false},
          {id: 10, name: 'J', value: 3, stop:false, arrow: false}
        ],
        interval: setInterval(this.addition, 2000),
      };
    },
    computed: {
    },
    watch: {

    },
    methods: {
      addition() {
        this.cards.forEach(element => {
          if(!element.stop) {
            const last = element.value
            element.value = Number(Math.round(Math.random() * 1 + 1)
            );
            element.arrow = last < element.value
          }
        })
      },
      stopInterval(index) {
        this.cards[index].stop = !this.cards[index].stop
      },
    },
    mounted() {
      // console.log(this.randomNumber);
    },
  };
</script>
