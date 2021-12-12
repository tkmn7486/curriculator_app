<template>
  <div class="app">
    <div class="resultArea">
      <h2>{{result}}</h2>
      <p class="inputSide">入力中…<input v-model="inputNumber"></p>
    </div>
    <div class="menu">
      <button class="subTax">税抜</button>
      <button class="addTax" @click="addTax">税込</button>
      <button class="AC" @click="deleteAll">AC</button>
      <button class="C" @click="clear">C</button>
    </div>
    <div class="otherButton">
      <div class="first_step">
        <button @click="input_1">1</button>
        <button @click="input_2">2</button>
        <button @click="input_3">3</button>
      </div>
      <div class="second_step">
        <button @click="input_4">4</button>
        <button @click="input_5">5</button>
        <button @click="input_6">6</button>
      </div>
      <div class="third_step">
        <button @click="input_7">7</button>
        <button @click="input_8">8</button>
        <button @click="input_9">9</button>
      </div>
      <div class="zeroButton">
        <button @click="input_0">0</button>
      </div>

      <div class="clcButton">
        <button @click="plus">+</button>
        <button @click="minus">-</button>
        <button @click="multiplied">×</button>
        <button @click="divided">÷</button>
        <button @click="save">📝</button>
      </div>
    </div>
    <div class="saveSpace">
      <h2>★記録済み</h2>
      <ul v-for="cul in saveCuls" :key="cul.id">
        <li class="saveCul">{{cul}}</li><input class="memoBox">
      </ul>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue' 
export default {
  name: 'App',
  setup(){
    let result = ref(0)
    let inputNumber = ref("")
    let saveCuls = []

    const input_1=()=>{
      inputNumber.value = inputNumber.value +"1"
    }

    const input_2=()=>{
      inputNumber.value = inputNumber.value +"2"
    }

    const input_3=()=>{
      inputNumber.value = inputNumber.value +"3"
    }

    const input_4=()=>{
      inputNumber.value = inputNumber.value +"4"
    }

    const input_5=()=>{
      inputNumber.value = inputNumber.value +"5"
    }

    const input_6=()=>{
      inputNumber.value = inputNumber.value +"6"
    }

    const input_7=()=>{
      inputNumber.value = inputNumber.value +"7"
    }

    const input_8=()=>{
      inputNumber.value = inputNumber.value +"8"
    }

    const input_9=()=>{
      inputNumber.value = inputNumber.value +"9"
    }

    const input_0=()=>{
      inputNumber.value = inputNumber.value +"0"
    }

    const plus=()=>{
      inputNumber.value = Number(inputNumber.value)
      result.value=result.value + inputNumber.value
      inputNumber.value=""
    }

    const minus=()=>{
      inputNumber.value = Number(inputNumber.value)
      result.value=result.value - inputNumber.value 
      inputNumber.value=""
    }

    const multiplied=()=>{
      inputNumber.value = Number(inputNumber.value)
      result.value=result.value * inputNumber.value 
      inputNumber.value=""
    }

    const divided=()=>{
      inputNumber.value = Number(inputNumber.value)
      result.value=result.value / inputNumber.value 
      inputNumber.value=""
    }

    const deleteAll=()=>{
      inputNumber.value="";
      result.value=0;
    }

    const clear =()=>{
      inputNumber.value="";
    }

    const addTax=()=>{
      result.value = Math.floor(result.value*1.1);
    }

    const save=()=>{
      saveCuls.push(result.value);
      result.value="";
    }


    return{
      result,
      inputNumber,
      saveCuls,
      input_1,
      input_2,
      input_3,
      input_4,
      input_5,
      input_6,
      input_7,
      input_8,
      input_9,
      input_0,
      plus,
      minus,
      multiplied,
      divided,
      deleteAll,
      clear,
      addTax,
      save,
    }
  }
}
</script>

<style>
.app{
  background-color:rgb(211, 211, 211);
  width:280px
}

.inputSide{
  font-size:5px;
  padding-left:5px;
}

.addTax{
  color:black;
  background-color:white;
}

.subTax{
  color:black;
  background-color:white;
}

.memoBox{
  display:inline;
  margin-left:10px;
}

.saveCul{
  display:inline;
}

.resultArea{
  margin-left:10px;
  border:solid;
  width:250px;
}

.saveSpace{
  padding-top:20px;
}

.first_step{
  margin-left:50px;
}

.second_step{
  margin-left:50px;
}

.third_step{
  margin-left:50px;
}

.zeroButton{
  margin-left:98px;
}

button{
  padding-top:10px;
  padding-bottom:10px;
  padding-right:15px;
  padding-left:15px;
  margin:3px;
}
</style>