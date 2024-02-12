<template>
    <div class="container">
        <h1>Componente Usuário</h1>
        <p>Esse é um componente muito legal!</p>
        <p>Nome é <strong> {{ nome }}</strong> idade <strong>{{ idade }}</strong></p>
        <button v-show="true" @click="alterarNome">Alterar nome</button>
        <hr>
        <div class="componentes">
            <app-usuario-info :nome='nome' :idade='idade' :pessoa="pessoa" 
                @nomeMudouFilho="nome = $event"
                :reiniciarFn="reiniciarNome" />
            <app-usuario-editar :nome="nome" :idade="idade" @idadeMudou="idade = $event" />
        </div>
    </div>
</template>

<script>
import AppUsuarioInfo from './UsuarioInfo'
import AppUsuarioEditar from './UsuarioEditar'

export default {
    components: { AppUsuarioInfo, AppUsuarioEditar },
    data() {
        return {
            pessoa: {
                nome: 'JC',
                idade: 21
            },
            nome: 'FRC',
            idade: 58
        }
    },
    methods: {
        alterarNome() {
            this.nome = 'Flavio Campos'
            this.idade = 60

            this.pessoa.nome = 'Jose Campos'
            this.pessoa.idade = 90
        },
        reiniciarNome() {
            this.nome = 'Therezinha J. Campos'
        }
    }
}
</script>

<style scoped>
.container {
    background-color: #27363b;
    color: #fff;
    padding: 10px;
}

.container hr {
    margin: 20px 10px;
}

.componentes {
    display: flex;
}

.componentes>* {
    margin: 10px;
}
</style>
