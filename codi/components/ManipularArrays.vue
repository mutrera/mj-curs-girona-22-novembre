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
    // data és un
    data(){
        return{
            temperatura:0,
            temperatures:[33,24,41,23,44,11,23]
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
            //afegim valors
            var valorAleatori = Math.random()*100
            nouArray.push(valorAleatori)
        }
        //assignem al array del component
        this.temperatures = nouArray
       
       }

    }
}

</script>