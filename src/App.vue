<template>
<section class="block">
  <div class="block__hotel">
    <p class="block__hotel-text">Место или название отеля</p>
    <label class="block__hotel-content">
      <img class="block__hotel-img" src="./assets/images/ImgMap.png" alt="mapImg">
      <input class="block__hotel-input" type="text" value="Введите здесь место">
    </label>
  </div>
  <div class="block__arrivall">
    <p class="block__arrivall-text">Заезд</p>
    <label class="block__arrivall-content">
      <img class="block__arrivall-img" src="./assets/images/imgDate.png" alt="mapDate">
      <select class="block__arrivall-date" name="number" v-model="actDay1">
        <option v-for="day in mounths[activeMounth1-1].days" :key="day" :value="day">{{day}}</option>
      </select>
      <select class="block__arrivall-date" name="mounth" v-model="activeMounth1">
        <option v-for="mounth in mounths" :key="mounth.id" :value="mounth.id">{{mounth.name}}</option>
      </select>
    </label>
  </div>
  <div class="block__departure">
    <p class="block__departure-text">Выезд</p>
    <label class="block__departure-content">
      <select class="block__departure-date" name="number" v-model="actDay2">
        <option v-for="day in mounths[activeMounth2-1].days" :key="day" :value="day">{{day}}</option>
      </select>
      <select class="block__departure-date" name="mounth" v-model="activeMounth2">
        <option v-for="mounth in mounths" :key="mounth.id" :value="mounth.id">{{mounth.name}}</option>
      </select>
    </label>
  </div>
  <div class="block__room">
    <div class="block__room-item">
      <p class="block__room-text">Номера</p>
      <lebel class="block__room-content">
        <input class="block__room-count" v-model="countRoom" type="number" name="room" min="0" max="10" step="1">
        <div class="block__room-arroys">
          <img class="block__room-arroy" @click="addCount(0)" src="./assets/images/arroyUpCount.png" alt="arroyUp">
          <img class="block__room-arroy" @click="minusCount(0)" src="./assets/images/arroyDownCount.png" alt="arroyUp">
        </div>
      </lebel>    
    </div>
    <div class="block__room-item">
      <p class="block__room-text">Взрослые</p>
      <lebel class="block__room-content">
        <input class="block__room-count" v-model="countAdults" type="number" name="adults" min="0" max="10" step="1">
        <div class="block__room-arroys">
          <img class="block__room-arroy" @click="addCount(1)" src="./assets/images/arroyUpCount.png" alt="arroyUp">
          <img class="block__room-arroy" @click="minusCount(1)" src="./assets/images/arroyDownCount.png" alt="arroyUp">
        </div>
      </lebel>
    </div>
    <div class="block__room-item">
      <p class="block__room-text">Дети</p>
      <lebel class="block__room-content">
        <input class="block__room-count" v-model="countChild" type="number" name="child" min="0" max="10" step="1">
        <div class="block__room-arroys">
          <img class="block__room-arroy" @click="addCount(2)" src="./assets/images/arroyUpCount.png" alt="arroyUp">
          <img class="block__room-arroy" @click="minusCount(2)" src="./assets/images/arroyDownCount.png" alt="arroyUp">
        </div>
      </lebel>
    </div>
  </div>
  <div class="block__btns">
    <img class="block__plus-btn" src="./assets/images/plusBtn.png" alt="plusBtn">
    <button class="block__search">Найти</button>
  </div>
</section>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      activeMounth1: 2,
      activeMounth2: 2,
      actDay1: "07",
      actDay2: 22,
      mounths: [
        {
          id: 1,
          name: "Январь",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        },
        {
          id: 2,
          name: "Февраль",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29]
        },
        {
          id: 3,
          name: "Март",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        },
        {
          id: 4,
          name: "Апрель",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30]
        },
        {
          id: 5,
          name: "Май",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        },
        {
          id: 6,
          name: "Июнь",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30]
        },
          {
          id: 7,
          name: "Июль",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        },
        {
          id: 8,
          name: "Август",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        },
        {
          id: 9,
          name: "Сентябырь",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30]
        },
        {
          id: 10,
          name: "Октябырь",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        },
        {
          id: 11,
          name: "Ноябырь",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30]
        },
        {
          id: 12,
          name: "Декабырь",
          days: ["01","02","03","04","05","06","07","08","09",10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31]
        }
      ],
      countRoom: 0,
      countAdults: 0,
      countChild: 0
    }
  },
  methods: {
    addCount(id) {
      switch (id) {
        case 0:
          this.countRoom++;
          break;
        case 1:
          this.countAdults++;
          break;
        case 2:
          this.countChild++;
          break;
        default:
          break;
      }
    },
    minusCount(id) {
      switch (id) {
        case 0:
          if(this.countRoom-1 != -1) this.countRoom--;
          break;
        case 1:
          if(this.countAdults-1 != -1) this.countAdults--;
          break;
        case 2:
          if(this.countChild-1 != -1) this.countChild--;
          break;
        default:
          break;
      }
    }
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.block{
  width: 1170px;
  height: 100px;
  background-color: white;
  padding: 25px 50px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  @media (max-width: 768px){
    width: 100%;
    height: max-content;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    &>div{
      margin-bottom: 20px;
    }
  }
  &__hotel{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 0 15px 0 0;
    width: 240px;
    height: 100%;
    border-right: 1px solid rgba($color: #e9e9e9, $alpha: 1.0);
    &-text{
      font-size: 12px;
      font-family: "Myriad Pro";
      color: rgb(35, 35, 35);
      line-height: 1.2;
      margin-bottom: 5px;
    }
    &-content{
      display: flex;
      justify-content: flex-start;
      align-items: flex-end;
    }
    &-img{
      margin-right: 10px;
    }
    &-input{
      font-size: 18px;
      font-family: "FiraSans";
      color: rgb(107, 107, 107);
      font-weight: bold;
      font-style: italic;
      line-height: 1.2;
      text-decoration: none;
      border: none;
      width: 210px;
      overflow: auto;
    }
  }
  &__arrivall{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    margin-left: 15px;
    width: 185px;
    height: 100%;
    &-text{
      font-size: 12px;
      font-family: "ProximaNova";
      color: rgb(35, 35, 35);
      line-height: 1.2;
      margin-bottom: 5px;
    }
    &-img{
      margin-right: 10px;
    }
    &-date{
      cursor: pointer;
      font-size: 18px;
      font-family: "FiraSans";
      color: rgb(56, 56, 56);
      font-weight: bold;
      font-style: italic;
      line-height: 1.2;
      text-decoration: none;
      border: none;
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
    }
  }
  &__departure{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    margin-left: 15px;
    width: 185px;
    height: 100%;
    border-right: 1px solid rgba($color: #e9e9e9, $alpha: 1.0);
    &-text{
      font-size: 12px;
      font-family: "ProximaNova";
      color: rgb(35, 35, 35);
      line-height: 1.2;
      margin-bottom: 5px;
    }
    &-img{
      margin-right: 10px;
    }
    &-date{
      cursor: pointer;
      font-size: 18px;
      font-family: "FiraSans";
      color: rgb(56, 56, 56);
      font-weight: bold;
      font-style: italic;
      line-height: 1.2;
      text-decoration: none;
      border: none;
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
    }
  }
  &__room{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 240px;
    margin-left: 10px;
    &-item{
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: center;
      width: 60px;
      height: 100%;
      margin-right: 10px;
    }
    &-text{
      font-size: 12px;
      font-family: "Myriad Pro";
      color: rgb(35, 35, 35);
      line-height: 1.2;
      margin-bottom: 5px;
    }
    &-count{
      font-size: 16px;
      font-family: "AvenirNextCyr";
      color: rgb(139, 145, 152);
      line-height: 1.2;
      width: 30px;
      height: 30px;
      text-align: center;
      -webkit-appearance: none;
      -moz-appearance: none;
      appearance: none;
      -moz-appearance: textfield;
      &::-webkit-outer-spin-button,
      &::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
      }
    }
    &-content{
      display: flex;
      justify-content: flex-start;
      align-items: center;
    }
    &-arroys{
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      margin-left: 5px;
    }
    &-arroy{
      cursor: pointer;
      &:first-of-type{
        margin-bottom: 8px;
      }
    }
  }
  &__btns{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    width: 255px;
    height: 100%;
  }
  &__plus-btn{
    cursor: pointer;
    margin-right: 20px;
  }
  &__search{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 175px;
    height: 65px;
    font-size: 16px;
    font-family: "ProximaNova";
    color: rgb(255, 255, 255);
    font-weight: bold;
    text-transform: uppercase;
    line-height: 1.2;
    text-shadow: 0px 0px 6.96px rgba(0, 0, 0, 0.05);
    background-color: rgba($color: #ed9915, $alpha: 1.0);
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
}
</style>