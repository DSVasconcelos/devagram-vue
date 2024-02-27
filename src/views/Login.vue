<script lang="ts">
    import InputPublico from "../components/InputPublico.vue";
    import IconeSenha from "../assets/imagens/senha.svg";
    import IconeLogin from "../assets/imagens/login.svg";

import {defineComponent} from "vue";
    export default defineComponent({
        setup(){
            return{
                IconeLogin,
                IconeSenha
            }
        },
    data() {
        return {
            login: '',
            senha: '',
            loading: false,
            erro: '',
        };
    },
    methods: {
        efetuarLogin() {
            if (!this.login && !this.senha) {
                this.erro = "Favor preencher formulario";
                return;
            }
            alert('Login efetuado: ' + this.login + ', ' + this.senha);
        },
        setLogin(v: any){
            this.login = v;
        },
        setSenha(v : any){
            this.senha = v;
        }
    },
    components: { InputPublico }
});
</script>
<template>
    <div class="container-publico">
        <img src="../assets/imagens/logo.svg" alt="Logo Devagram" class="logo"/>
        <form>
            <p v-if="erro" class="error">{{erro}}</p>

            <InputPublico :icone="IconeLogin" alt="Insira o login" tipo="text" 
                placeholder="Email" :modelvalue="login" @setInput="setLogin"/>

            <InputPublico :icone="IconeSenha" alt="Insira o login" tipo="password"
                 placeholder="Senha" :odelvalue="senha" @setInput="setSenha"/>

            <button @click.enter.prevent="efetuarLogin">Login</button>
            <div class="link">
                <p>Não possui uma conta?</p>
                <a>Faça seu cadastro agora</a>
            </div>
        </form>
    </div>
</template>

<style lang="scss" src="@/assets/styles/paginaPublica.scss"/>
