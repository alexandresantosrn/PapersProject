<template>
    <form id="user-form" @submit="createPaper">
        <div class="input-container">
            <label for="nome">Nome do Usuário:</label>
            <input type="text" id="nome" v-model="nome" placeholder="Informe o nome do usuário">
        </div>

        <div id="opcionais-container" class="input-container">
            <label for="opcionais" id="opcionais-title">Selecione os papéis do usuário:</label>
            <div class="checkbox-container" v-for="papel in papeis" :key="papel.id">
                <input type="checkbox" name="papeis" v-model="papeis" :value="papel.descricao">
                <span>{{ papel.descricao }}</span>
            </div>                   
        </div>
              
        <div class="input container">
            <input type="submit" class="submit-btn" value="Cadastrar Usuário">                    
        </div>
    </form>           
</template>

<script>
export default {
    name: 'User',
    data() {
        return {
            nome: null,
            papeis: null,
            papeis: []
        }
    },
    methods: {
        async createUser(e){
            e.preventDefault();

            const data = {
                nome: this.nome
            }

            const dataJson = JSON.stringify(data);

            const req = await fetch('http://localhost:8081/papeis', {
                method: 'POST',
                headers: {'Content-type': 'application/json'},
                body: dataJson
            });
        },
        async getPapeis(){

            const req = await fetch('http://localhost:8081/papeis');
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