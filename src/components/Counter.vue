<template>
    <!-- /* Pasar las propiedas computadas */ -->
  <h2> {{customTitle}}</h2>
    <p>{{counter}} <sup>2</sup> = {{ counter * counter }}</p>


    <div id="botones">
        <button v-on:click="increase">
            +1
        </button>
        <button @click="decrease">
            -1
        </button>
    </div>


</template>

<script>
export default {
    props: {
        title: String,
        start: {
            Number,
            default: 0,
            validator(value){
                return value >= 0
            }
        }
    },

    data(){
        return{
            counter: this.start //este start es el que posamos previamente en nuestro componente en el archivo app,
                                //indicando que comieza con el 15, este es el paso 3
        }
    },
    methods:{
        getSquareValue(){
            return this.counter * this.counter
        },
        increase(){
            this.counter++;
        },
        decrease(){
            this.counter--;
        }
    },
    computed: {
        squareCounter(){
            console.log('computed squareCounter')
            return this.counter * this.counter
        },
        //Las propiedades computadas siempre tienen que devolver algo
        customTitle(){
            return this.title || 'Counter'
        }
    }
}
</script>

<style>

button{
    background-color: #64bb87;
    border-radius: 5px;
    border: 1px solid white;
    color: white;
    cursor: pointer;
    margin: 0 5px;
    padding: 5px 15px;
    transition: 0.3s ease-in-out;
    }

    button:hover{
        background-color: #5aa67b;
        transition: 0.3s ease-in-out;
    }

</style>