<template>
    <div class="componente">
        <h2>Alterar os Dados de Usuário</h2>
        <p>Edite as informações</p>
        <p>{{ nome }}, tem {{ idade }} anos.</p>
        <button @click="alterarIdade" >Alterar Idade</button>
    </div>
</template>

<script>
export default {
    //props:['nome','idade']
    props:{
        nome: String,
        idade: Number
    },
    methods:{
        alterarIdade(){
            this.$emit('idadeMudou', 33)
        } 
    }
    
}
</script>

<style scoped>
    .componente {
        flex: 1;
        background-color: #98b99a;
        color: #fff;
    }
</style>
