<template>
    <section>
        <div class="crud-container">
            <div class="crud-box">
                <div class="doctor-content">
                    <div class="form-wrapper">
                        
                        <div class="form-header">
                            <h1>{{ titleMedico }}</h1>

                        </div>

                        <div class="search-bar">
                            
                        </div><!-- search-bar -->

                        <div class="form-fields">
                           <input type="text" v-model="nome" placeholder="Nome completo" />
                           <input type="text" v-model="crm" placeholder="CRM" />
                           <input type="text" v-model="especialidade" placeholder="Especialidade" />
                           <input type="tel" v-model="telefone" placeholder="Telefone" />
                           <input type="email" v-model="email" placeholder="Email" />
                            
                        </div><!-- form-fields Campos do formulário médico -->

                        <div class="form-actions">
                            
                        </div><!-- form-actions Botões de ação (Salvar, Cancelar, etc.) -->
                    </div><!-- form-wrapper -->
                </div><!-- doctor-content -->
            </div><!-- crud-box -->
        </div> <!-- crud-container -->
    </section>
</template>

<style scoped>
.crud-container {
    display: flex;
    background-color: black;
    width: 198vh;
    height: 200vh;
    justify-content: center;
    align-items: flex-start;
}

.crud-box {
    margin-top: 200px;
    display: flex;
    background-color: aliceblue;
    height: 1400px;
    width: 1600px;
    margin-bottom: 900px;
    justify-content: center;
    align-items: center;
}

.doctor-content {
    display: flex;
    background-color: cadetblue;
    width: 1200px;
    height: 1000px;
    justify-content: center;
    align-items: center;
}

.form-wrapper {
    display: flex;
    flex-direction: column;
    background-color: aliceblue;
    width: 80%;
    height: 90%;
    border-radius: 17px;
    justify-content: space-between;
    align-items: center;
}

.form-header {
    display: flex;
    background-color: black;
    width: 80%;
    height: 13%;
    justify-content: center;
    align-items: center;
}


.form-actions {
    display: flex;
    background-color: black;
    width: 60%;
    height: 5%;
    align-items: center;
    justify-content: center;
}
.search-bar{
    display: flex;
    background-color: black;
    width: 80%;
    height: 7%;
    align-items: center;
    justify-content: center;
   
}

.form-fields{
    display: flex;
    background-color: black;
    width: 80%;
    height: 70%;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    gap: 10px;
    border-radius: 17px;
}

h1 {
    color: antiquewhite;
    font-size: 28px;
}
</style>

<script setup>
import { ref } from 'vue'



const titleMedico = ref("Cadastro Médico")


</script>
