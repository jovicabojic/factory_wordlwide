<template>
  <div class="home">
        <div class="card-wrap">
          <div class="card" v-for="(card, index) in cards" :key="index">
            <p>{{card.name}}</p>
            <p>{{card.value}}</p>
            <i v-if="card.arrow" class="fa fa-arrow-up" aria-hidden="true"></i>
            <i v-else class="fa fa-arrow-down" aria-hidden="true"></i>
            <div @click="stopInterval(index)" class="button rounded" id="button">
              <input type="checkbox" class="checkbox">
              <div class="circle"></div>
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
        signs: ['+', '-'],
        logs: [
          {id: 1, name: 'A', val: []},
          {id: 2, name: 'B', val: []},
          {id: 3, name: 'C', val: []},
          {id: 4, name: 'D', val: []},
          {id: 5, name: 'E', val: []},
          {id: 6, name: 'F', val: []},
          {id: 7, name: 'G', val: []},
          {id: 8, name: 'H', val: []},
          {id: 9, name: 'I', val: []},
          {id: 10, name: 'J', val: []}
        ]
      }
    },
    methods: {
      addition() {
        this.cards.forEach(element => {
          if(!element.stop) {
            const last = element.value
            let sign = this.signs[Math.round(Math.random())]
            element.value = Number(sign + (Math.random() + 1).toFixed(2))
            element.arrow = last < element.value
            // this.logs.forEach(log => {
            //   if (log.id == element.id) {
            //     log.val.push(element.value)
            //   }
            // })
            let log = this.logs.filter(log => log.id === element.id)
            log[0].val.push(element.value)
          }
        })
        localStorage.setItem('logs', JSON.stringify(this.logs))
      },
      stopInterval(index) {
        this.cards[index].stop = !this.cards[index].stop
      },
    },
    destroyed() {
      clearInterval(this.interval)
    },
  };
</script>
