<template>
    <q-page padding>
           <q-form v-on:keyup.enter="logar()" 
           :model="formularioLogin" 
           ref="formularioLogin" 
           class="q-gutter-md">
           <div>
                 <q-icon name="login" size="30px"></q-icon>
           </div>
                <q-input filled lazy-rules type="email" label="Email">
                    
                    

                </q-input>
                 <q-input filled lazy-rules type="password" label="Senha">
                </q-input>
                <div class="row justify-cente content-center">
                    <q-btn label="Logar" @click="logar()" color="primary">
                        <q-tooltip 
                        transition-show="rotate"
                        transition-hide="rotate">Logar</q-tooltip>
                    </q-btn>
                    <q-btn label="Limpar" @click="limpar()" color="primary" 
                    flat class="q-ml-sm">
                    <q-tooltip
                    transition-show="rotate"     
                    transition-hide="rotate">Limpar Formulário</q-tooltip>
                    </q-btn>
                </div>
                <div class="form-group"></div>
           </q-form>
    </q-page>
</template>

<script>
export default {
    data(){
        return {
            formularioLogin: {}
        }

    },
    methods:{
        logar(){
            alert("Teste");
        },
        limpar(){
            this.formularioLogin = {}
        }
    },
    create(){ alert("Alert");
        console.log("Iniciou!!!");
    }
}
</script>

<style lang="scss">
.q-icon {
    position: absolute;
}
</style>>

