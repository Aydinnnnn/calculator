<template>
  <div class="calculator">
    <div  class="display">{{ current }}</div>



    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiple()" class="btn operator"><v-icon small color="error">mdi-close</v-icon></div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="plus()" class="btn operator">+</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="minus()" class="btn operator">-</div>
    <div @click="clear()" class="btn ">C</div>
    <div @click="append('0')" class="btn">0</div>
    <div @click="equal()" class="btn operator">=</div>
    <div @click="divide()" class="btn operator">/</div>

  </div>
</template>

<script>
export default {
  data(){
    return {
      current: "",
      operator: null,
      previous: null,
      clickedBtn : false


    }
  },
  methods:{


    clear(){
      this.current ="";

    },
    append(number){
      if(this.clickedBtn) {
        this.current = ''
        this.clickedBtn = false
      }
      this.current = this.current + number;
    },
    setOperator(){
      this.previous = this.current
      this.clickedBtn = true
    },
    plus(){
      this.operator = (a,b) => a +b;
      this.setOperator()
    },
    minus(){
      this.operator = (a,b) => a -b;
      this.setOperator()
    },
    divide(){
      this.operator = (a,b) => a /b;
      this.setOperator()
    },
    multiple(){
      this.operator = (a,b) => a *b;
      this.setOperator()
    },
    equal(){
      this.current =`${this.operator(parseInt(this.current),parseInt(this.previous))}`
      this.previous = null
    }



  }
}




</script>
<style >
.calculator{
  margin: 0 auto;
  width: 400px;
  display: grid;
  grid-template-columns:  repeat(4,4fr);
  /*grid-auto-rows: minmax(50px,auto);*/
  align-content: center;
}
.display{
  padding-top: 10px;
  background-color: #333333;
  color: antiquewhite;
  grid-column: 1/5;
  font-size: 30px;
  height: 50px;
}

.btn{
  background-color: grey;
  font-size: 30px;
  border:1px solid #333 ;
  padding:10px
}
.operator{
  background-color: orange;
}
</style>