<template>
    <div id="paper-container">
        <Message :msg="msg" v-show="msg" />
        
        <form id="paper-form" @submit="createPaper">
            <div class="input-container">
                <label for="nome">Nome do Papel:</label>
                <input type="text" id="nome" v-model="nome" placeholder="Informe a denominação do papel">
            </div>

            <div class="input container">
                <input type="submit" class="submit-btn" value="Cadastrar Papel">                    
            </div>
        </form>
    </div>           
</template>

<script>
import Message from './Message.vue';

export default {
    name: 'Paper',
    data() {
        return {
            nome: null,
            msg: null
        }
    },
    components: {
        Message
    },
    methods: {
        async createPaper(e){
            e.preventDefault();

            //capturando dados
            const data = {
                descricao: this.nome
            }

            //montando Json
            const dataJson = JSON.stringify(data);

            //enviado dados via post
            const req = await fetch('http://localhost:8081/papeis', {
                method: 'POST',
                headers: {'Content-type': 'application/json'},
                body: dataJson
            });   

            //mensagem de exibição após cadastro do papel
            this.msg = 'Papel cadastrado com sucesso!!'

            //limpar msg após 2 segundos
            setTimeout(() => this.msg = "", 2000);

            //limpar os campos
            this.nome = "";
        }
    }
}
</script>

<style scoped>
    #paper-form {
        max-width: 400px;
        margin: auto;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;        
    }

    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;
        width: 300px;
    }

    .submit-btn {
        background-color: #222;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 14px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
        display: flex;
   }
   .submit-btn:hover {
        background-color: transparent;
        color: #222;
   }   
</style>