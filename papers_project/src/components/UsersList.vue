<template>
     <div id="users-table">
        <div id="users-table-heading">
            <div class="users-id">#:</div>
            <div>Usuário:</div>            
            <div>Papéis:</div>          
        </div>
        <div id="users-table-rows">
            <div class="users-table-row">
                <div class="users-number"></div>
                    <div>Márcio Passos</div>
                
                    <div>
                        <ul>
                            <li>Gestor</li>
                            <li>Administrador</li>                        
                        </ul>
                    </div>                              
            </div>
        </div>
    </div>  
</template>

<style scoped>
    #users-table {
        max-width: 800px;
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
        width: 19%;
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