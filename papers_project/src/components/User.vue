<template>
    <div id="user-container">
        <Message :msg="msg" v-show="msg" />
        <form id="user-form" @submit="createUser">
            <div class="input-container">
                <label for="nome">Nome do Usuário:</label>
                <input type="text" id="nome" v-model="nome" placeholder="Informe o nome do usuário">
            </div>

            <div id="papeis-container" class="input-container">
                <label for="papeis" id="papeis-title">Selecione os papéis do usuário:</label>
                <div class="checkbox-container" v-for="papel in papeis" :key="papel.id">
                    <input type="checkbox" name="papeis" v-model="papeislist" :value="papel.descricao">
                    <span>{{ papel.descricao }}</span>
                </div>                   
            </div>
                
            <div class="input container">
                <input type="submit" class="submit-btn" value="Cadastrar Usuário">                    
            </div>           
        </form> 
    </div>              
</template>

<script>
import Message from './Message.vue';

export default {
    name: 'User',
    data() {
        return {
            nome: null,
            papeis: null,
            papeislist: [],
            msg: null
        }
    },
    components: {
        Message
    },
    methods: {
        async createUser(e){
            e.preventDefault();

            const data = {
                nome: this.nome,
                papeis: Array.from(this.papeislist)
            }

            const dataJson = JSON.stringify(data);

            const req = await fetch('http://localhost:8080/usuarios', {
                method: 'POST',
                headers: {'Content-type': 'application/json'},
                body: dataJson
            });

            //mensagem de exibição após cadastro do papel
            this.msg = 'Usuário cadastrado com sucesso!!'

            //limpar msg após 3 segundos
            setTimeout(() => this.msg = "", 3000);

            //limpar os campos
            this.nome = "";
            this.papeislist = "";
        },
        async getPapeis(){

            const req = await fetch('http://localhost:8080/papeis');
            const data = await req.json();
            
            this.papeis = data;            
        }
    },
    mounted(){
        this.getPapeis()
    },
    updated(){
        this.getPapeis() 
    }   
}
</script>

<style scoped>
    #user-form {
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

    input{
        padding: 5px 10px;  
        width: 300px;    
    }

    #papeis-container {
        flex-direction: row;
        flex-wrap: wrap;          
    }

    #papeis-title {
       width: 100%;     
    }

    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span, .checkbox-container input {
        width: auto;
    }

    .checkbox-container span {
        margin-left: 6px;       
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