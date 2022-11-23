<template>
    <v-container>
        <v-row>
            <v-col cols="12" md="6">
            <v-text-field
                label="Camp 1"
                placeholder="Escriu primer text" 
                v-model="camp1"
            ></v-text-field>
            <v-text-field
                label="Camp 2"
                placeholder="Escriu segon text" 
                v-model="camp2"
            ></v-text-field>
            <v-btn @click="mostraElsTexts()"  color="green">mostrar a la consola</v-btn>
            <br><br>
            <v-btn @click="borrarElsTexts()"  color="yellow">borrar a la consola</v-btn>
        </v-col>
            <v-col cols="12" md="6">
                
                <div style="font-size:40px">
                    {{camp1}}
                </div>
                <div style="font-size:40px">
                    {{camp2}}
                </div>
                <mostrarCamps 
                :parametre1="camp1"
                :parametre2="camp2"
                ></mostrarCamps>
                <!-- altres maneres
                <div style="font-size:40px" v-text="camp2"></div>
                <div style="font-size:40px" v-html="camp1+camp2"></div> (reconeix el text com html 
                i tots els v- executen js)-->
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default{
    data(){
        return{
            camp1:"",
            camp2:""
        }
    },
    methods:{
        //ES6
        mostraElsTexts(){
            console.log("El camp 1 és ", this.camp1)
            console.log("El camp 2 és ", this.camp2)
        },
        //ES5
        borrarElsTexts:function(){
            this.camp1=""
            this.camp2=""
        }


    }


}
</script>