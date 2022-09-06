<template>
  <div class="app">

    <div class="main">
      <!-- CALCULATOR RESULT -->
      <div class="calculatorResult">
        {{current || 0}}
      </div>
      <!-- CALCULATOR BTN -->
      <div class="calculatorBtn">

        <div class="calculatorBtn_elem" v-for="elem in calculatorElem" :key="elem"
        :class="{'green' : ['C','*','/','-','+','%','='].includes(elem)}"
        @click="calculatorMethod(elem)"
        >
          {{elem}}
        </div>

      </div>

    </div>

  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        current: "",
        previousCurrent: '',
        calculatorElem: ['C','*','/','-','7','8','9','+','4','5','6','%','1','2','3','=','0','.'],
        operator : null,
      }
    },
    methods: {
      // Ajout de la value si elem est un nombre ou un dot(.)
      calculatorMethod(elem) {
        if(!isNaN(elem) || elem === '.') { 
          this.current += elem + '';
        }

        // Clear value
        if(elem === 'C') {
          this.current = '';
        }

        // // Modulo value
        if(elem === '%') {
          this.current = this.current / 100 + "";
        }

        // Operator value
        if(['/','*','+','%','-'].includes(elem)) {
          this.operator = elem;
          this.previousCurrent = this.current;
          this.current = (this.previousCurrent + this.operator)
        }

        // Result 
        if(elem === '=') {
          this.current = eval(this.current)
        }

        this.previousCurrent = "";
        this.operator = null;
      }
    }
  }
</script>

