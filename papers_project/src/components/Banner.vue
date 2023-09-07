<template>
    <div id="banner">
        <div class="sessions">            
            <router-link to="/">
                <div id="users-list" @click="listUsers()">                    
                    <img :src="users_list_src" :alt="users_list_alt" class="img-users-list">                
                    LISTAR USUÁRIOS                                
                </div>
            </router-link>

            <router-link to="/">
                <div id="create-users">
                    <img :src="add_user_src" :alt="add_user_alt" class="img-users-list"> 
                    CRIAR USUÁRIOS
                </div>
            </router-link>

            <router-link to="/">
                <div id="create-papers">
                    <img :src="add_paper_src" :alt="add_paper_alt" class="img-users-list"> 
                    CRIAR PAPÉIS
                </div>
            </router-link>
        </div>
    </div>    
</template>

<script>
export default {
    name: 'Banner',
    data() {
        return {
            users_list_src: '/img/users-list.png',
            users_list_alt: 'Listar Usuários',
            add_user_src: '/img/add-user.png',
            add_user_alt: 'Adicionar Usuário',
            add_paper_src: '/img/add-paper.png',
            add_paper_alt: 'Adicionar Papel',
            show_users: false,
            show_add_user: false,
            show_add_paper: false
        }
    },
    methods: {
        listUsers() {
            this.show_users = true;
            this.show_add_user = false;
            this.show_add_paper = false;
            
            this.$emit('list_users', this.show_users);
        }
    }
}
</script>

<style scoped>
    #banner {       
        height: 200px;
        width: 100%;
        display: flex;        
    }

    .sessions {
        margin: auto;
        display: flex;
    }

    .sessions a {
        color: black;
        text-decoration: none;
    }

    .img-box2 {
        height: 85px;   
        width: 115px;
        margin: 5px;       
        border: 2px solid black;
        display: flex;

    }

    #users-list, 
    #create-users,
    #create-papers {
        border: 2px solid black;
        border-radius: 10px;
        height: 130px;
        width: 130px;        
        margin-right: 10px;
        text-align: center; 
        font-size: 12px;
        font-weight: bold;  
        line-height: 8px;       
    }

    .img-users-list {
        height: 80px;
        margin: 15px;
    }
       
</style>