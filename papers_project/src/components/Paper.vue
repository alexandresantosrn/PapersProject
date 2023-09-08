<template>
    <form id="paper-form" @submit="createPaper">
        <div class="input-container">
            <label for="nome">Nome do Papel:</label>
            <input type="text" id="nome" v-model="nome" placeholder="Informe a denominação do papel">
        </div>

        <div class="input container">
            <input type="submit" class="submit-btn" value="Cadastrar Papel">                    
        </div>
    </form>           
</template>

<script>
export default {
    name: 'Paper',
    data() {
        return {
            nome: null
        }
    },
    methods: {
        async createPaper(e){
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