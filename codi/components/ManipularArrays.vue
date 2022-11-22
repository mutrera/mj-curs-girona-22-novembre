<template>
    <v-container>
        <v-row>
            <v-col cols="12" md="6" style="background-color:aquamarine">
            <v-text-field
            label="Temperatura"
            placeholder="Escriu la temperatura"
            type="number"
            v-model="temperatura"
            >
            </v-text-field>
            <v-btn @click="afegir()">afegir</v-btn>
            <v-btn @dblclick="netejar()">netejar</v-btn>
            <v-btn @mouseenter="netultim()">borrar darrer</v-btn>
            <v-btn @click="temperaturesAleatories()">aleatori</v-btn>
            </v-col>
            <v-col cols="12" md="6" style="background-color:orange">
            Resultat:
            <br>
            Mostres:{{tamanyArray}}
            <br>
            Mostres superiors a 50 graus:{{mesDe50}}
            <br>
            <v-sparkline
                :value="temperatures"
                :gradient="['red', 'blue', 'yellow']">
            </v-sparkline>
            <pre>
                {{temperatures}}
            </pre>
           
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
export default{
    //mounted s'executa desprès de estar tot montat
    mounted(){
        //inicialitzem  l'array de temperatures
        this.temperaturesAleatories()
 
    },
    // data és un
    data(){
        return{
            temperatura:0,
            temperatures:[]
        }
    }, 
    //methods és un
    methods:{
        afegir(){
            console.log("Afegint..." )
            console.log("temperatura: ", this.temperatura)
            const tmp =parseFloat(this.temperatura)
            this.temperatures.push(tmp)

        },
        netejar(){
            console.log("netejant...")
            this.temperatures = []
        },
       netultim(){
        console.log("netejant ultim")
        this.temperatures.pop()
       }, 
       temperaturesAleatories(){
        console.log("fem temperatures aleatories...")
       //crem un array buid
        var nouArray=[]
        //repetim 100 vegades
        for(var i =0; i<100; i++){
            //afegim valors()
            var valorAleatoriDecimal= Math.random()*100
            var valorAleatoriEnter =this.processarEnter(valorAleatoriDecimal)
            //amb parseInt es retornara numeros sensers
            // nouArray.push(parseInt(valorAleatori))
            nouArray.push(valorAleatoriEnter)
        }
        //assignem al array del component
        this.temperatures = nouArray
       
       },
       //aquesta funcio no té assignat un botó
       processarEnter(val){
        return parseInt(val)
       }

    },
    computed:{
        tamanyArray(){
            return this.temperatures.length
        }, 
        mesDe50(){
            var motresDeMesDe50Graus = 0
            this.temperatures.forEach((temperatura)=>{
                if(temperatura>50){
                    motresDeMesDe50Graus++

                }
            })
            return motresDeMesDe50Graus
        }

    },
    //serveix per veure si hi ha coses que canvien
    watch:{
        temperatura(newValue, oldValue){
            console.log(newValue, oldValue)
        },
        mesDe50(newValue,oldValue){
            if(newValue>55){
                alert("ALERTA")
            }
        }



    }
}

</script>