<template>
    <div id="banner">
        <div class="sessions">       
            <div id="users-list">
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
    name: 'Banner'
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
        line-height: 230px;       
    }


   
</style>