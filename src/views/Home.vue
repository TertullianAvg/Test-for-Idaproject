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


    <button @click="add">Добавить товар</button>

   
  </div>
   <div >
   
    
   <div v-for="c  in card" :key="c.name" class="card">
    <img class="image" src="https://shop.instantphotoclub.ru/wp-content/uploads/sites/2/2020/01/best-istant-cameras-polaroid-onestep2.jpg" />
      
    <h1 class="card-title"> {{c.name}}</h1>
    <p class="card-title">{{c.about}}</p>
    <h1 class="card-title"><b>{{c.price}}</b></h1>
    <button v-on:click="handleDelete(c)" id="delete"></button>
    </div>
     
   
   </div>
  
  
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      card: [{ name: 'Наименование товара', about: 'Описание товара в несколько строчек',price: '10000 рублей'}],
      
    };
  },
  methods: {
    add()  {
      
      const newCard = {
        name: this.name,
        about: this.about,
        price: this.price
      
      }
      this.card.push(newCard);
      this.name = '',
      this.about = '',
      this.price = ''

    
      
     
      
    },
    handleDelete(cardToRemove) {
      this.card = this.card.filter(c => c !== cardToRemove);
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
  position: relative;
width: 332px;
height: 423px;
left: 380px;
top: 83px;
display:  inline-block; ;
background: #FFFEFB;
box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
border-radius: 4px;
margin-left: 15px;
margin-top: 5px;
border:2px solid;
}
.card-title , b {
  font-family: Source Sans Pro;
font-style: normal;

font-size: 16px;
line-height: 20px;
background: #FFFEFB;

color: #3F3F3F;
margin: 5px;
}
.image {
  width: 332px;
height: 200px;
}
#delete {
  position: absolute;
  width: 32px;

height: 32px;
top: 0px;
left: 300px;

box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
border-radius: 10px;
background-size: 20px,20px;
background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMIAAAEDCAMAAABQ/CumAAAAb1BMVEX///8AAAAfHx/7+/tOTk64uLjc3NyWlpZfX1+Dg4PLy8vq6urg4OB6enqysrJycnKlpaXS0tLl5eWqqqrx8fGenp4RERFqampXV1cICAiNjY2AgIAzMzNubm7Nzc0ZGRkqKio8PDxDQ0PBwcEvLy+ane9pAAADXElEQVR4nO3d4W6iQBRAYaYogoJWC0Vta23t+z/jtrvZbDsD4uiFO2TP+WsT75c6oEAyUUREREREROMo9k574u/FSVXU24ln27SYrUvt2X9Xzt7M1d1lG+35o7i6fv4/ZcqfqMXkVsHnfyLRFCSvtws+O+kJ8p2IwJi5lqA8CgmM0VrUKzGBedMRzOUExjyoEAQORv/aaQjWkgJjlgqEQpaQKhDeZAlm+JN0/ihMWA9OEF4KGsckcUIlO95pVqw6SqUJ711vWeyn68sWzGb2IT2dXMei+2tt+ST11a2v6o7vU/M77Qm7251d+A/a411W1i64157t0p7aBCftyS6v5Qi8kD7f9lnzuVzwF0z/PTcJEu2p/Jo2EIS/PPddw7+hHNNK+Cp3CKK/hIfIPcHttUfyrXYIL9oj+eYuhq32SL492oLYvqSSZoHlnLY6CYqXapvLvQlNpw7VnFOv/QcQBghCCEEIIQghBCGEIITQf0mo8iSo8mkXYXy/2tw71bX2SL4dHcKT9ki+bR3CUnsk39yL2wvtkXw7uAct8VuYPddw3HUOWmE3ayDE79pTedV4B/qgPZVPLXc9R3RluPXRn9Gs6Of2BxlGYjiee9Q7057uktLzD5McZJ7/7bPup/iWAT8IY8xrddHzPHm1eg7w5uHjR115Pf1mr2z7bGjfXryzXl/Yz9TYdyjtm8T2G9jfFibezx9CgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECBAgAABAgQIECB4EewNl5w9r2yCveX0fnDCprr/kb3XT/zw8/XK3sXlZL1ub3DRP6H3IEQQJIIQQZAIQgRBIggRBIkgRC7B3QW35+QJ9XQ5aFN7t2Z/wosJLHc/566C21q19ibYH0X1Mm/CWntku6k3IbIvomi38CcEthj8l0IUbbSH/tn8CoJzuU01/0PqV2VIm8ImVxHca456tewL3t299uR/s6+3js/gf1b71mmnPb654VP0p4V9DX3wtleu5G8lheaRqT7cDPiqnO9X6WTw0pfsdG5ree/iwZOcnoiIiIiIPPoF3ZOgvjyJ61cAAAAASUVORK5CYII=);
background-repeat: no-repeat;
background-position: center;
}

</style>