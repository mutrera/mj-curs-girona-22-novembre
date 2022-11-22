<template>
    <v-container>
        <v-row>
            <v-col cols="12" sm="6">
                <v-textarea 
                label="Tasca"
                placeholder="nova tasca"
                outlined
                v-moldel="laNovaTasca"
                ></v-textarea>
                <v-btn @click="afegirTasca()">afegir tasca</v-btn>
            </v-col>   
            <v-col cols="12" sm="6">
                <v-row class="tasca" v-for="tasca in tasques">
                    <v-col cols="8" ><h2>{{tasca.text}}</h2>
                    </v-col>
                    <v-col cols="4">
                        <v-checkbox v-model="tasca.feta">
                        </v-checkbox>
                    </v-col>
                </v-row>
                <pre>
                    {{tasques}}
                </pre>
            
            </v-col>
        
        </v-row>
    </v-container>
</template>
<style>
.tasca{
    background-color: papayawhip;
    margin: 10px
}


</style>

<script>
export default{
    methods:{
        afegirTasca(){
            console.log("afegir tasca...")
            var text=this.laNovaTasca
            var tasca={}
            tasca.text = this.laNovaTasca
            tasca.feta = false
            if(this.laNovaTasca.length<=0){
                alert("El camp tasva no pot estar buid")
                return
            }

            this.tasques.push(tasca)
            this.laNovaTasca =""
        }
    },
    data(){
        return{
            laNovaTasca:"",
            tasques:[
            {
                text:"Fer el llit",
                feta:true
            },
            {
                text:"Fer els deures",
                feta:true
            },
            {
                text:"Anar a comprar",
                feta:true
            },
            
        ]
        }
      

},
   computed:{
    tincText(){
        if(this.laNovaTasca)
    }
   }

}
</script>