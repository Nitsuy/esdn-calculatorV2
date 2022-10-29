<script lang="ts">
import { stringifyStyle } from '@vue/shared';
import { ref } from 'vue'
import { defineComponent } from 'vue'

const count = ref(0)

export default defineComponent({
  data(){
    return{
      varD: 0,
      varE: 0,
      varS: 0,
      current: 0,
      classif: '',
    }
  },
  methods: {
    clear(){
      this.current = 0;
    },
    varDevelop(numD: number){
      this.varD = numD;
    },
    varEmissions(numE: number){
      this.varE = numE;
    },
    varSustain(numS: number){
      this.varS = numS;
    },
    result(){
      this.current = (this.varD * this.varE) - this.varS;
      this.classification();
    },
    classification(){
      if ((this.current > 3) && (this.current < 6)){
        this.classif = 'Medium Contaminating';
      }
      else
        if (this.current > 3){
          this.classif = 'Highly Contaminating';          
        }
        else{
          this.classif = 'Low Contaminating';
        }
    },
  }


});
</script>

<template>
  <div>

  </div>
  
  <h1 style="font-size: 20px">Emissions for Sustainable Development of Nations Scale (ESDN Scale)</h1>

  <div class="calculator"> 
    <div class="variables">GDP</div>
    <button @click="varDevelop(1)" class="btn">1</button>
    <button @click="varDevelop(2)" class="btn">2</button>
    <button @click="varDevelop(3)" class="btn">3</button>
    <div class="variables">CO2 Emissions</div>
    <button @click="varEmissions(1)" class="btn">1</button>
    <button @click="varEmissions(2)" class="btn">2</button>
    <button @click="varEmissions(3)" class="btn">3</button>
    <div class="variables">Sustainable Energy Sources</div>
    <button @click="varSustain(1)" class="btn">1</button>
    <button @click="varSustain(2)" class="btn">2</button>
    <button @click="varSustain(3)" class="btn">3</button>
    <div class="variables">Climate Impact</div>
    <div class="display">{{current || '0'}}</div>
    <button @click="result" class="btn">=</button>
    
  </div>
  <p>
      <code>Select the values for each variable and then click on the "=" button to show the country's climate impact!</code>
    </p>

  <div class="card">
    <button type="button" @click="">The country gets a ranking of: {{ current }}</button>
    
  </div>

  <div>
    <button type="button" @click="">The country is {{ classif }}</button>
  </div>

  <p>
      <code>Database employed constructed by the delegation of Germany, consult it <a href="https://docs.google.com/spreadsheets/d/1GhTFYoS1-a4TS1edTwrQdQLnZ57bl2DnIjwIm3v0L6M/edit?usp=sharing">here</a></code>
    </p>

  <div>Low Contaminating: 0-3</div>
  <div>Medium Contaminating: 3-6</div>
  <div>Highly Contaminating: 6-8</div>

</template>


<style scoped>
.read-the-docs {
  color: #888;
}
.calculator{
  margin: 0 auto;
  width: 600px;
  font-size: 20px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  border: 1px solid #333;
}

.display{
  grid-column-end: 1/3;
  background-color: black;
  color: white;
}

.btn{
  border: 1px solid #333;
  background-color: white;
  color: #333;
}

.btn:focus{
  background-color: green;
}

.variables{
  border: 1px solid #333;
  background-color: darkorange;
  color: white;
}


</style>
