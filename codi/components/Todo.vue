<template>
    <v-container>
        <v-row>
            <v-col cols="12" sm="6">
                <v-textarea
                    label="Tasca"
                    placeholder="p.e: fer el llit" 
                    outlined
                    v-model="laNovaTasca"
                >
                </v-textarea>
                <v-btn 
                    @click="afegirTasca()"
                    color="blue"
                    :disabled="!tincText"
                    >afegir tasca</v-btn>
            </v-col>
            <v-col cols="12" sm="6">
                Tens {{tasquesFetes}} tasques fetes
                <br>
                i {{tasques.length - tasquesFetes}} per fer.
                <br>
                <br>
                <br>
                <v-row class="tasca" v-for="(el,index) in tasques">
                    <v-col cols="8">
                    
                       <h2>{{el.text}} - {{index}}</h2>
                    </v-col>
                    <v-col cols="4">
                        <v-checkbox
                            v-model="el.feta"
                        ></v-checkbox>
                    </v-col>
                </v-row>









                <pre>
                    {{tasques}}
                </pre>
                
            </v-col>   
        </v-row> 
    </v-container>
</template>

<script>
export default{
    methods:{
        afegirTasca(){
            console.log("afegint tasca...")

            if(this.laNovaTasca.length <= 0){
                alert("El camp tasca no pot estar buid")
                return
            }

            var tasca = {}
            tasca.text = this.laNovaTasca
            tasca.feta = false

            this.tasques.push(tasca)
            this.laNovaTasca = ""
        }
    },
    data(){
        return {  
            laNovaTasca:"",     
            tasques:[
                {
                    text:"Fer el llit",
                    feta:true
                },
                {
                    text:"Fer els deures",
                    feta:false
                },
                {
                    text:"Anar a comprar",
                    feta:true
                }]
        }
    },
    computed:{
        tincText(){
            if(this.laNovaTasca.length <=0){
                return false
            }
            else{
                return true
            }
        },
        tasquesFetes(){
            var tasquesFetesVar = []
            this.tasques.forEach((tasca)=>{
                if(tasca.feta == true){
                    tasquesFetesVar.push(tasca)
                }
            })
            return tasquesFetesVar.length
        }
    }
}
</script>


<style>
    .tasca{
        background-color: bisque;
        margin-bottom: 10px;
    }
</style>