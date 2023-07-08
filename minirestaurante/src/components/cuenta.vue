<template lang="">
    <div>

<div class="titulo_cuenta">

<h1>Su cuenta a pagar :</h1>


</div>


<div class="contenedor_cuenta">
    <div class="cont_valor"   v-for="(e, index) in arrayrecibido" :key="index">

<h2>{{e.nombre_producto}}: ${{parseFloat(e.precioG)}} </h2>
</div>

<div class="cont_total">
    <h1>Total a pagar: ${{  arrayrecibido.reduce((total, producto) => total + parseFloat(producto.precioG), 0)}}</h1>

</div>




</div>


        

    </div>
</template>












<script>
export default {
    props: {
        arrayrecibido: {
            type: Array,
            required: true 
        },
    },


 
   
    
}
</script>
<style scoped>


    div{
        color: white;
    }


.contenedor_cuenta{
    background-color: white;
    margin: auto;
    width: 45%;
    border: 3px dashed #183153;
    padding:10px;
    
}

.cont_valor{
    border-bottom: 2px solid #183153;
    margin: 10px 0;
    text-align: center;
    color: #183153;
    font-size: 18px;
}

.cont_total{
    text-align: center;
    color: #183153;
}


.titulo_cuenta{
  
    margin: 50px auto;
    width: 90%;
    text-align: center;
    font-size: 25px;
}




@media(max-width:1188px){

.titulo_cuenta{
    font-size: 20px;
}

.contenedor_cuenta{
    width: 80%;
}




}


@media (max-width:789px){

}



</style>