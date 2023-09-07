<template>
    <div id="banner">
        <div class="sessions">       
            <div id="users-list">
                <img :src="users_list_src" :alt="users_list_alt" id="img-users-list">                
                LISTAR USUÁRIOS               
            </div>
            <div id="create-users">
                CRIAR USUÁRIOS
            </div>
            <div id="create-papers">
                CRIAR PAPÉIS
            </div>
        </div>
    </div>    
</template>

<script>
export default {
    name: 'Banner',
    data() {
        return {
            users_list_src: '/img/users-list.png',
            users_list_alt: "Listar Usuários"
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
        line-height: 10px;       
    }

    #img-users-list {
        height: 80px;
        margin: 15px;
    }


   
</style>