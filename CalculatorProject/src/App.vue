<template>
  <div class="app">

    <div class="main">
      <!-- CALCULATOR RESULT -->
      <div class="calculatorResult">
        {{current || 0}}
      </div>
      <!-- CALCULATOR BTN -->
      <div class="calculatorBtn">
        <div class="calculatorBtn_elem" v-for="elem in calculatorElem">
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
        calculatorElem: ['C','*','/','-','7','8','9','+','4','5','6','%','1','2','3','=','0','.']
      }
    },
    methods: {
      
    }
  }
</script>

