<template>
  <div class="body">
    <div class="container">
      <div v-if="num<= this.data.length" >
        <article   class="cart-current" >Задание {{ num }} из {{data.length}}:
          <h3 class="">{{ title }}</h3>
          <div> {{ descr }}</div>
          <div class="choice">Выбери правильный ответ</div>
          <div class="item">
            <div v-for="it in arrAnswer" :key="it">
              <input @click="rightAnswer" ref="rightAnswer" class="radio-button" type="radio" :value="it.tit" :id="id" name="button" >
              <label>{{ it.tit}}</label>
            </div>
          </div>
        </article>
        <div class="button_box">
          <button class="button" ref="btn" @click="generateCart" disabled>Дальше</button>
        </div>
      </div>
      <div v-else> 
        <div>Количество набранных баллов {{ arrSum }} из {{ data.length }}</div>
      </div>
    </div>
  </div>
</template>

<script>
 

import arrT from '/index.json'

export default {
  name: 'TheBody',
     components: {
     },
  data() {
    return {
      num:0,
      tit:'',
      elem:'',
      title:'',
      descr:'',
      element:'',
      quation:'',
      answer:'',
      data: arrT,
      arrAnswer:[],
      sum:'',
      findRadioButton:'',
      findButtonActive:'',
      arrSum:0
    }
 },
 mounted() {
  this.generateCart()
 },
methods: {
  generateCart(event) {
    this.num = this.num+1;
      if(this.num <= this.data.length){
        const el = this.data.find(element => element.id == this.num);
        this.arrAnswer = el.options
        this.title = el.title
        this.descr = el.descr
        this.sum = eval(this.descr);
        this.p = el.id
        this.quation = el.title
        event.target.setAttribute('disabled', true)
      }
    },
  rightAnswer(event) {
    this.findRadioButton = this.arrAnswer.find(item => item.tit == this.sum)
      console.log(this.findRadioButton);//правильный ответ
      if(event.target.value == this.findRadioButton.tit){
        console.log('верно');
        this.arrSum++
      }
      else { console.log('неверно');
      }
        this.$refs.btn.disabled = false     
    },
  },
}
</script>

<style>
.body {
  border: 1px solid rgb(180, 173, 239);
  max-width: 700px;
  margin: 0px auto;
  height: 80vh;
}
.cart {
  border: 1px solid rgb(19, 18, 30);
  max-width: 700px;
  min-height: 100px;
}
.cart-current{
  border: 1px solid rgb(28, 11, 216);
  margin: 30px;
  min-height: 200px;
}
.item{
  height: 100px;
  margin-top:30px;
  border: 1px solid rgb(216, 45, 11);
  max-width: 700px;
  padding-right: 150px;
}
.button {
  background: rgb(64, 222, 236);
}
.button_box{
  display: flex;
  gap:100px;
  justify-content: center;
}
.choice {
  margin-top:30px;
}

</style>
