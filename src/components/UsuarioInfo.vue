<template>
    <div class="componente">
        <h2>As Informações de Usuário</h2>
        <p>Vários detalhes...</p>
        <p>Usuário: <strong>{{ nome }}</strong> esta com {{ idade }}</p>
        <p v-if="false">Nome do Pai: <strong>{{ pessoa.nome }}</strong> esta com {{ pessoa.idade }}</p>
        <button @click="reiniciarNome">Reiniciar Nome</button>
        <button @click="reiniciarFn()">Reiniciar Nome(CallBack)</button>
    </div>
</template>

<script>
export default {
    //props:['nome', 'idade', 'pessoa'],
    props: {
        nome: {
            Type: String,
            required: true,
            // default: 'Anonimo',
            default: function () {
                return Array(10).fill(0).join('.')
            }
        },
        reiniciarFn: Function,
        idade: Number,
        pessoa: Object,
       
    },
    methods: {
        inverterNome() {
            return this.nome.split('').reverse().join('');
        },
        reiniciarNome() {
            let novo = this.nome
            novo = 'Pedro Afonso'
            this.$emit('nomeMudouFilho', novo)     
            
        },
        reiniciarNome1() {
            const antigo = this.nome
            this.nome = 'Pedro Afonso'            
            this.$emit('nomeMudouFilho', {
                novo: this.nome,
                antigo
            })
        },
    },

}
</script>

<style scoped>
.componente {
    flex: 1;
    background-color: #ec485f;
    color: #fff;
}
</style>
