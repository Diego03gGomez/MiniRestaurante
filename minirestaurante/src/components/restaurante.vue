<template lang="">
    <div>


       




<header>

<div class="cont_menu">
    <i v-on:click="ocultar_menu()"   class="fa-solid fa-receipt cuenta2"></i>


   
<h1 v-on:click="ocultar_cuenta()"   >Burguer<img class="logo" src="/imagenes/logo.jpg" alt=""></h1>

<nav>
    <div ref="carrito" class="carrito mostrar">
<div class="titulo_carrito"  >
    <h1>Carrito</h1>

</div>
    



<div v-for="(e, index) in carrito" :key="index" class="div_guardado" >

<div class="imagen2"><img :src=e.imagen_p alt=""></div>
<div class="datos"><h2>{{e.nombre_producto}} <span>(${{e.precioG}})</span> </h2>  </div>

<a v-on:click="eliminar_tarea(index)" class="eliminar_g" href="#">Eliminar</a>
</div>


</div>





<ul class="nav"  >
    <a v-on:click="ocultar_menu()"    class="cuenta1" href="#">Ver la cuenta</a>
    <a class="menu"   href="#titulo_menu">Menues</a>
<a  class=" carrito1  mostrar_carrito" v-on:click="ocultar()"  href="#"><i class="fa-solid fa-cart-shopping"></i>Carrito</a>
<a class="mostrar_carrito"  v-on:click="ocultar()"    ><i class="fa-solid fa-cart-shopping carrito2"></i></a>
</ul>


</nav>



</div>








</header>
<div class="contenido_principal"  >

<div id="fondo_baner">

    <div class="cont_baner">
        <h1>Welcome to <br> the BurgerRestaurant</h1>
        <h3>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Ducimus reprehenderit <br> accusamus
         quidem iste nihil hic, repellat harum temporibus enim odit necessitatibus vel <br> dolorum nobis rerum eaque fugit nisi deleniti quos.
        </h3>
<a href="#">View more info</a>


    </div>



</div>
   










<div class="titulo_menu_container">
    <h1 id="titulo_menu" >Menues</h1>
</div>


<div  class="cont_hamburguesas">

<div v-for="(e, index) in hamburguesas" :key="index" class="card">
<div class="imagen">
    <img :src="e.imagen" alt="">
</div>

<div class="descripcion">

<h2>{{e.nombre}}</h2>
<h3>{{e.precio}}</h3>
<h4>{{e.descripcion}}</h4>
<img class="estrellas" src="/imagenes/estrellas.jpeg" alt="">
</div>
<button v-on:click="agregar($event)" class="btn_agregar" href="">Agregar al carrito<i class="fa-solid fa-cart-shopping"></i></button>




</div>







</div>

<footer>
<div class="cont_footer">
<h3>Copyright ©BurgerRestaurant.com</h3>

<h3> <a href="https://github.com/Diego03gGomez/MiniRestaurante" target="blank" >Diego Gomez: <i class="fa-brands fa-github"></i></a>  </h3>
  

</div>

 </footer>
        </div>


<cuenta class="cuenta ocultar  "   :arrayrecibido="carrito"  ></cuenta>

   
    </div>
</template>





































































<script>
import cuenta from './cuenta.vue';

export default {
    data() {
        return {
             hamburguesas : [
  {
    nombre: "Hamburguesa clásica",
    imagen: "https://images.pexels.com/photos/3616956/pexels-photo-3616956.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    precio: 9.99,
    descripcion: "Delicious classic burger with juicy meat and fresh ingredients."
  },
  {
    nombre: "Hamburguesa con queso",
    imagen: "https://images.pexels.com/photos/3219483/pexels-photo-3219483.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    precio: 10.99,
    descripcion: "Irresistible burger with melted cheese and special sauce."
  },
  {
    nombre: "Hamburguesa vegetariana",
    imagen: "https://images.pexels.com/photos/2983098/pexels-photo-2983098.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    precio: 8.99,
    descripcion: "Veggie burger with a tasty mix of vegetables and seasonings."
  },
  {
    nombre: "Hamburguesa doble",
    imagen: "https://images.pexels.com/photos/1362044/pexels-photo-1362044.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    precio: 12.99,
    descripcion: "Generous hamburger with double meat, cheese and all the toppings."
  },
  {
    nombre: "Hamburguesa BBQ",
    imagen: "https://images.pexels.com/photos/2966196/pexels-photo-2966196.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    precio: 11.99,
    descripcion: "Burger with delicious barbecue sauce, caramelized onion and bacon."
  },
  {
    nombre: "Hamburguesa picante",
    imagen: "https://images.pexels.com/photos/10115297/pexels-photo-10115297.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
    precio: 10.49,
    descripcion: "Burger with a touch of spice, jalapeños and spicy cheese."
  }
],

carrito : [
   /* {nombre_producto: "nombre", imagen_p: "https://th.bing.com/th/id/OIP.tubLY-wiuj2ZWl8-NhcXTAAAAA?pid=ImgDet&w=379&h=283&rs=1"}*/
]


        }
    },

    components: {
        cuenta,
    },
















methods: {
    acceder(event) {
     console.log(event.currentTarget.querySelector("img").src);
    },



    agregar(event){
let nombre = event.currentTarget.parentNode.querySelector("h2").textContent;
let imagenp = event.currentTarget.parentNode.querySelector("img").src;
let precio_g = event.currentTarget.parentNode.querySelector(".descripcion").querySelector("h3").textContent;
this.carrito.push({nombre_producto : nombre, imagen_p: imagenp, precioG: precio_g})
console.log(imagen);

    },

eliminar_tarea(index){
this.carrito.splice(index,1 );
},

ocultar(){
this.$refs.carrito.classList.toggle('mostrar');

},



ocultar_cuenta(){
    let $cuenta = document.querySelector(".cuenta");
$cuenta.classList.add("ocultar")

let $contenido = document.querySelector(".contenido_principal");
$contenido.classList.remove("ocultar")

},

ocultar_menu(){
    let $cuenta = document.querySelector(".cuenta");
$cuenta.classList.remove("ocultar")

let $contenido = document.querySelector(".contenido_principal");
$contenido.classList.add("ocultar")

}


},






}
</script>



















































































<style scoped>
.fa-github {
color: white;
font-size: 30px;

}

footer{
  background-color: black;
  padding: 20px 0;
 
  
}

.cont_footer {

margin: auto;
width: 80%;
display: flex;
justify-content: space-around;
align-items: center;
color: white;
font-family: 'PT Sans', sans-serif;
}

.cont_footer a{
  text-decoration: none;
  color: white;
}



header{
    background-color:#17181b
}

.cont_menu{
   padding: 10px 0;
    margin:auto;
    width: 85%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
}

.cont_menu nav ul{
    margin: 0;
    padding: 0;
    list-style: none;

}

.cont_menu nav ul  a{
    text-decoration: none;
    color: white;
    margin: 0 30px;
    font-weight: bold;
 font-size: 24px;
    
}
.cont_menu h1{
    font-size: 53px;
    color: white;
    display:flex;
    gap: 20px;
    align-items: center;
    font-family: 'Corinthia', cursive;
/*font-family: 'Yellowtail', cursive;*/

}

.titulo_carrito h1{
    font-family: 'Roboto', sans-serif;
    font-size: 35px;
}


.carrito{
    transition: all 0.9s;
    opacity: 1;
    background-color: red;
    position: absolute;
right: 0px;
top: 35px;
width: 30%;
display: flex;
flex-direction: column;
gap: 5px;
border-radius: 8px;

}

.btn_agregar{
    transition: all 0.90s;
    cursor: pointer;
    background-color:#fbc500;
    margin: auto;
width: 100%;
font-size: 20px;
padding: 5px 0;
    color: black;
    text-align: center;
    font-weight: bold;
    border-color: #fbc500;
    border-style: solid;
    border-radius: 8px;
        font-family: 'PT Sans', sans-serif;
}

.btn_agregar:hover{
    transition: all 0.90s;
    background-color: #17181b;
    color: white;
 
}




.div_guardado{
display: grid;
grid-template-columns: 2fr 1fr 1fr;
align-items: center;
color: white;
gap: 20px;
background-color: rgb(41, 41, 41);
border-radius: 8px;
}



.imagen2 img{
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 8px;
    
}







.cont_hamburguesas{
   /* background-color: brown;*/
    margin:52px auto;
    width: 70%;
 display: grid;
 gap: 30px;
 grid-template-columns: 1fr 1fr 1fr;
}

.estrellas{
   font-size: 10px;
   width: 100px;
}

.card{
    background-color: rgb(48, 47, 47);
    color: white;
padding: 5px 10px;
    line-height: 30px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
}


.ocultar{
  display: none;
}




.imagen img{
    width: 100%;
    height: 280px;
    object-fit: cover;
    border-radius: 8px;
}


.imagen2 img{
    width: 100%;
}

.eliminar_g{
    background-color: gold;
    text-align: center;
    border-radius: 2em;
    text-decoration: none;
    font-weight: bold;
    color:#17181b;
  padding: 10px;
  font-size: 15px;
}

span{
    color: gold;
}


.titulo_carrito{
    text-align: center;
    font-size: 20px;
}

.titulo_carrito h1{
    color:#17181b;
}


.mostrar{
    transition: all 0.9s;
    opacity: 0;
}


.datos{
    font-size: 14px;
}


.descripcion{
flex-grow: 3;

}


#fondo_baner{
    background: linear-gradient(to right, #020202cf, #00000057, #00000014), url(https://images.pexels.com/photos/3219483/pexels-photo-3219483.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1);
    background-size: cover;
    background-position: right;
    background-repeat: no-repeat;
  
    /*height: 71vh;*/
    height: 100%;
    padding-top: 200px;
    
    padding-bottom: 200px;
    object-fit: cover;
}



.cont_baner{
  /*  background-color: brown;*/
margin: auto;

    width: 70%;
    font-family: 'PT Sans', sans-serif;
}

.cont_baner h1{
    font-size: 60px;
    color: white;
   
font-family: 'Oswald', sans-serif;



}

.cont_baner h3{
    color: rgb(255 255 255 / 70%);
margin: 15px auto;
}

.cont_baner a{
  
    background-color:#fbc500;
text-decoration: none;
font-weight: bold;
color: black;
font-size: 25px;
padding: 10px;
border-radius: 10px;

}

.titulo_carrito{
    background-color: gold;
    border-radius: 5px;
 
    display: flex;
justify-content: center;
}

.carrito{
    background-color: black;
    top: 80px;
  
}


.logo{
width: 100px;
height: 90px;
border-radius: 2em;

}
.cont_menu h1{
    cursor: pointer;
}


.titulo_menu_container{


color: white;

margin: 40px auto;
width: 70%;
font-size: 30px;


}

.scroll{
  scroll-behavior: smooth;
}


.nav a{
    font-size: 10px;
    /* font-family: 'Oswald', sans-serif;
  font-family: 'Corinthia', cursive;
font-family: 'Fira Sans', sans-serif;
font-family: 'Inter', sans-serif;
font-family: 'Lora', serif;
font-family: 'Mada', sans-serif;
font-family: 'Montserrat', sans-serif;
font-family: 'Mulish', sans-serif;
font-family: 'Nunito', sans-serif;
font-family: 'Open Sans', sans-serif;
font-family: 'Oswald', sans-serif;*/
font-family: 'Poppins', sans-serif;


}

.deshabilitado {
  pointer-events: none;
  opacity: 0.6;
}

.cuenta2{
    color: white;
    font-size: 30px;
    display: none;
}

.carrito2{
    display: none;
}

.descripcion h3{
    color: #fbc500;
}

.descripcion h4{
    color: white;
}




@media (max-width:1188px){
    .cont_hamburguesas{
        grid-template-columns:  1fr 1fr 1fr;
        width: 90%;
    }

.carrito{
    width: 65%;
}
.cont_menu{
    width: 90%;
}

.cont_menu nav ul  a{
    margin: 0 10px;
}


}











@media (max-width: 789px){
    .cont_hamburguesas{
        grid-template-columns:  1fr;
    }

.carrito{
    width: 100%;
    top: 110px;

}

.imagen2 img{
    object-fit: cover;
}


.cont_baner{
    text-align: center;
    width: 100%;
}

.cont_baner h1{
    font-size: 50px;
}

.cont_menu{
    justify-content: space-around;
    align-items: center;
}

.cont_menu .menu{  
display: none;
}

.cuenta1{
    display:none;
}

.carrito1{
    display:none;
}

.carrito2{
    display: initial;
}

.cuenta2{
    display: initial;
}








}



  
</style>