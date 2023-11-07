<template>
     <div id="users-table">
        <div id="users-table-heading">
            <div class="users-id">#:</div>
            <div>Usuário:</div>            
            <div>Papéis:</div>          
        </div>
        <div id="users-table-rows">
            <div class="users-table-row" v-for="user in users" :key="user.id">
                <div class="users-number">{{ user.id }}</div>
                    <div>{{ user.nome }}</div>                
                    <div>
                        <ul>
                            <li v-for="(papel, index) in user.papeis" :key="index">{{ papel.descricao }}</li>                                                   
                        </ul>
                    </div>                              
            </div>
        </div>
    </div>  
</template>

<script>
export default {
    name: 'Users',
    data() {
        return {
            users: null            
        }
    },
    methods: {
        async getUsuarios() {
           //const req = await fetch('http://192.168.2.115:8080/usuarios');    
           const req = await fetch('http://localhost:8080/usuarios');              
           const data = await req.json();
           this.users = data;           
        }
    },
    mounted() {
        this.getUsuarios()
    },
    // updated() {
    //     this.getUsuarios();
    // }
}
</script>

<style scoped>
    #users-table {
        max-width: 500px;
        margin: 0 auto;
    }

    #users-table-heading,
    #users-table-rows,
    .users-table-row {
       display: flex;
       flex-wrap: wrap;
    }

    #users-table-heading {
        font-weight: bold;
        padding: 12px;
        border-bottom: 3px solid #333;
    }

    #users-table-heading div,
    .users-table-row div {
        width: 39%;
    }
    
    .users-table-row {
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #CCC;
    }

    #users-table-heading .users-id,
    .users-table-row .users-number {
        width: 5%;
    }   

</style>