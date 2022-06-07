<script>
import Card from './components/Card.vue'
import Instructions from './components/Instructions.vue'
export default {
  components: {
    Card,
    Instructions
  },
  data() {
    return {
      existingNumbers: [],
    }
  },

  methods: {
    greetingMessage() {
      event.preventDefault()
      let randomNumber = Math.round(Math.random()*1000);

      if (!this.existingNumbers.includes(randomNumber)) {
        this.existingNumbers.push(randomNumber);
      } else {
        greetingMessage();
      }
    },

    removeCard(item) {
      let itemToDelete = this.existingNumbers.indexOf(item);
      this.existingNumbers.splice(itemToDelete, 1);
    },

    sort() {
      this.existingNumbers.sort(function(a, b) {
        return a - b;
      });
    }
  },
}

</script>

<template>
  <div class="container">
    <div class="application">
      <header>
        <a href="" class="buttons" v-on:click.prevent="greetingMessage">add card</a>
        
        <a href="" class="buttons" v-on:click.prevent="sort">sort card</a>
      </header>

      <div class="cards">
        <Card 
          v-for="item in existingNumbers"
          :integers=item
          @remove="removeCard(item)"
        />
      </div>

      <footer>
        footer
      </footer>
    </div>  

    <div class="instructions">    
      <Instructions />
    </div>
  </div>
</template>

<style>
.container {
  display:flex;
}

.application {
  border: 1px solid;
  border-right: none;
}

header {
  border-bottom: 1px solid;
}

.buttons {
  padding: 10px 0 10px 30px;
  display: inline-block;
}

.cards {
  height: 600px;
  width: 701px;
  display: flex;
  flex-wrap: wrap;
  overflow-y: auto;
}

.instructions {
  border: 1px solid;
  width: 200px;
  padding: 20px 20px;
  display: flex;
  justify-content:center;
  align-items: center;
}

footer {
  border-top: 1px solid;
  padding: 10px 0 10px 30px;
}

</style>
