<template>
    <div>
        <h1>{{ titulo }}</h1>
        <form>
            <label for="">Nombre :</label>
            <input type="text" v-model="personaje.nombre">
            <!-- <input type="submit" @click.prevent="fetchCharacter"> -->
            <button type="button" class="btn bg-dark text-white" @click.prevent="fetchPersonaje">
                    Buscar
            </button>
        </form>
        <section>
            <img :src="img.front_default" alt="">
            <h3>Movimientos:</h3>
            <div class="movimientos">
                <ul>
                <li v-for="(movimiento, index) in movimientos" :key="index">
                    {{ movimiento.move.name }}
                </li>
            </ul>
            </div>
            
            <h3>Habilidades:</h3>
            <ul>
                <li v-for="(habilidad, index) in habilidades" :key="index">
                    {{ habilidad.ability.name }}
                </li>
            </ul>
        </section>
    </div>
</template>

<script>
export default {
    name: 'poke-component',
    // props: {},
    data: function(){
        return {
            titulo: "Pokeguía",
            personaje:{
                nombre: "",
                movimiento: "",
                movimientos: [],
                habilidades: [],
                habilidad: "",
                sprites: {
                    front_default: "",
                }
            }
        }
    },
    computed: {
        img(){
            return this.personaje.sprites;
        },
        habilidades(){
            return this.personaje.abilities;
        },
        movimientos(){
            return this.personaje.moves;
        }
    },
    methods: {
     async fetchPersonaje(){
            
            await fetch(`https://pokeapi.co/api/v2/pokemon/${this.personaje.nombre}`)
                .then((response) => response.json())
                .then((json) => {
                    console.log(json);
                    this.personaje = json;
                })
                .catch((error) => {
                    alert("personaje no encontrado");
                    console.log(error);
                });
            
        }
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
    created: function () {
        this.fetchPersonaje;
    },
    mounted: function () {
        this.personaje.nombre = "pikachu";
        this.fetchPersonaje();
    }
}   
</script>

<style scoped>
    li{
        font-size: 1em;
        list-style: none;
    }
    section{
        text-align: center;
    }
    .movimientos{
        height: 6em;
        margin: 0 auto;
        overflow: auto;
        width: 15em;
        
    }
</style>