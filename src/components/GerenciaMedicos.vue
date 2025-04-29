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
                            <button @click="salvar">Salvar</button>
                            <button @click="cancelar">Cancelar</button>     
                        </div><!-- form-actions -->
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
  background-color: white;
  width: 60%;
  height: 80%;
  border-radius: 17px;
  justify-content: space-around;
  align-items: center;
  padding: 20px;
}

.form-header {
    display: flex;
  background-color: black;
  width: 100%;
  height: 13%;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
}


/* .form-actions {
    display: flex;
    background-color: black;
    width: 60%;
    height: 5%;
    align-items: center;
    justify-content: center;


} */
.form-actions {
  display: flex;
  gap: 20px;
  justify-content: center;
  width: 80%;
}
.form-actions {
  display: flex;
  gap: 20px;
  justify-content: center;
  width: 80%;
}

.form-actions button {
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
  color: white;
  background-color: #0077cc;
  transition: background-color 0.3s ease;
}
.form-fields input {
  padding: 10px;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 16px;
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
.form-fields {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 80%;
}


.form-actions button:hover {
  background-color: #005fa3;
}


h1 {
    color: antiquewhite;
    font-size: 28px;
}
</style>

<script setup>
import { ref, onMounted } from 'vue'

const titleMedico = ref("Cadastro Médico")


const nome = ref('')
const crm = ref('')
const especialidade = ref('')
const telefone = ref('')
const email = ref('')




</script>

