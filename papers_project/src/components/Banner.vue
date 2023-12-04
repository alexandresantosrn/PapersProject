<template>
    <div id="banner">
        <div class="sessions">            
            

            <router-link to="/">
                <div id="create-users" @click="createUsers(), mudarCorUser()" :style="{ backgroundColor: colorUser}">
                    <img :src="add_user_src" :alt="add_user_alt" class="img-users-list"> 
                    SIMULADOR
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
            add_user_src: '/img/money-bag.png',
            add_user_alt: 'Adicionar Usuário',
            add_paper_src: '/img/add-paper.png',
            add_paper_alt: 'Adicionar Papel',
            show_users: false,
            show_add_user: false,
            show_add_paper: false,
            colorUsers: 'white',
            colorUser: 'white',
            colorPaper: 'white'           
        }
    },
    methods: {
        listUsers() {
            this.show_users = true;
            this.show_add_user = false;
            this.show_add_paper = false;
            
            this.$emit('list_users', this.show_users);
        },
        createUsers(){
            this.show_users = false;
            this.show_add_user = true;
            this.show_add_paper = false;          

            this.$emit('create_users', this.show_add_user);
        },
        createPapers(){
            this.show_users = false;
            this.show_add_user = false;
            this.show_add_paper = true; 
            
            this.$emit('create_papers', this.show_add_paper);
        },
        mudarCorUsers() {
            this.colorUsers = '#FFFFE0', 
            this.colorUser = 'White',
            this.colorPaper = 'White'          
        },
        mudarCorUser() {
            this.colorUsers = 'White',
            this.colorUser = '#FFFFE0', 
            this.colorPaper = 'White'          
        },
        mudarCorPapers() {
            this.colorUsers = 'White', 
            this.colorUser = 'White',
            this.colorPaper = '#FFFFE0'          
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