<template>
    <v-container>
        <v-row>
            <!-- posa espais abans de la columna-> offset-md -->
            <v-col style="margin-top:10vh" cols="12" md="4" offset-md="4">
             <v-text-field 
             label="Usuari"
             v-model="usuari">
             </v-text-field>
             <v-text-field 
             label="Password"
           
             v-model="contrasenya">
             </v-text-field>
             <div v-if="hiHaMajusculesMinuscules" style="color:green"> Molt bé, tens majuscules i minuscules</div>
             <div v-else style="color:red"> Ep, cal posar alguna majuscules i minuscules</div>
             <div v-if="siHiHaMesDe6Caracters" style="color:green"> Molt bé, tens més de 6 caracters</div>
             <div v-else style="color:red"> Ep, cal posar com a mínim 6 caracters</div>
             <div v-if="siHiHaCaractersEspecials" style="color:green"> Molt bé, tens algun caracter especial</div>
             <div v-else style="color:red"> Ep, cal posar algun caracter especial</div>
             <br>
             <v-btn>Login</v-btn>
            </v-col>
            <v-col>
             esquerra
            </v-col>
        </v-row>
    </v-container>
</template>
<script>
export default{
    data(){
        return{
            usuari:"",
            contrasenya:""
        }
    },
    methods:{
        conteLletres(str){
            return /[a-zA-Z]/.test(str)
        }

    },
    computed:{
        hiHaMajusculesMinuscules(){
            let textOriginal = this.contrasenya
            let hiHaMajuscules = false
            let hiHaMinuscules = false

            for(var i= 0; i< textOriginal.length; i++){
                let caracter = textOriginal[i]
           
                //mirar si es majuscula
                if(this.conteLletres(caracter)){
                    
                    if(caracter.toUpperCase() === caracter){
                     
                        hiHaMajuscules = true
                    }else{
                        hiHaMinuscules = true


                    }
            }
        }
            
            return hiHaMajuscules && hiHaMinuscules

        },
        siHiHaMesDe6Caracters(){
  //fem algo i tornen true si hi ha més de 6 caracters
  if(this.contrasenya 
  && typeof(this.contrasenya) =="string"
  && this.contrasenya.length>=6){
    return true
  }
  //tornon false
        },
        siHiHaCaractersEspecials(){
            return false

        }
    }

}

</script>
