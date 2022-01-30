<template>
 <h1 class="head">Добавление товара</h1>
  <div class="addForm">
   
    <p class="text">Наименование товара*</p>
    <input v-model="name"  type="text" class="name input" placeholder="Введите наименование товара">
    <p class="text">Описание товара</p>
    <input v-model="about" type="text" class="about input" placeholder="Введите описание товара" id="about">
    <p class="text">Ссылка на изображение товара*</p>
    <input type="text" class="link input" placeholder="Введите ссылку">
    <p class="text">Цена товара*</p>
    <input v-model="price" type="text" class="price input" placeholder="Введите цену"><br>


    <button v-on:click="add">Добавить товар</button>

   
  </div>
   <div >
   <ul>
   <div v-for="(c, index) in addCard" :key="c.name" class="card" @remove="card.splice(index, 1)">
    <img class="image" src="https://shop.instantphotoclub.ru/wp-content/uploads/sites/2/2020/01/best-istant-cameras-polaroid-onestep2.jpg" />
    <h1 class="card-title"> {{c.name}}</h1>
    <p class="card-title">{{c.about}}</p>
    <h1 class="card-title"><b>{{c.price}}</b></h1>
    </div>
   </ul>
   </div>
  
  
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      name: '',
      about: '',
      price: '',
      addCard: [{name:'Наименование товара',about:'Описание товара в несколько строчек',price:'33124 рублей'}] 
    };
  },
  methods: {
    add() {
      const newCard = {
        name: this.name,
        about: this.about,
        price: this.price
      };
      this.card.push(newCard);
     
      
    }
  }

};

</script>
<style scoped>
.head {
  color: #3f3f3f;
  font-family: 'Source Sans Pro', sans-serif;
font-style: normal;
font-weight: 600;
font-size: 28px;
line-height: 35px;
position: absolute;
width: 247px;
height: 35px;
left: 32px;
top: 32px;
}
.addForm {
  position: absolute;
width: 332px;
height: 440px;
left: 32px;
top: 83px;

background: #FFFEFB;
box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
border-radius: 4px;
margin:5px;
}
.text {
  
background: #FFFEFB;
font-family: Source Sans Pro;
font-style: normal;
font-weight: normal;
font-size: 10px;
line-height: 13px;
/* identical to box height */

letter-spacing: -0.02em;

/* Temp / Darks / Lesser */

color: #49485E;
padding: 5px;
margin: 5px;
border-radius: 4px;
}
#about {
  width: 284px;
height: 108px;
}
.input {
   width: 284px;
   background: #FFFEFB;
font-family: Source Sans Pro;
font-style: normal;
font-weight: normal;
font-size: 10px;
line-height: 13px;
/* identical to box height */

letter-spacing: -0.02em;

/* Temp / Darks / Lesser */

color: #49485E;
padding: 5px;
margin: 5px;
border-radius: 4px;
}
button {
  position: absolute;
width: 284px;
height: 36px;
margin-left: 15px;
margin-top: 10px;

background: #EEEEEE;
border-radius: 10px;
}
.card {
  position: absolute;
width: 332px;
height: 423px;
left: 380px;
top: 83px;

background: #FFFEFB;
box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
border-radius: 4px;
}
.card-title , b {
  font-family: Source Sans Pro;
font-style: normal;

font-size: 16px;
line-height: 20px;
background: #FFFEFB;

color: #3F3F3F;
}
.image {
  width: 332px;
height: 200px;
}
</style>