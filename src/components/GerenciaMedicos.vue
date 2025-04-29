<template>
    <section>
        <div class="crud-container">
            <div class="crud-box">
                <div class="doctor-content">
                    <div  class="form-wrapper">
                        <div v-if="valorFalso" class="form-content">
                            

                        <div class="form-header">
                            <h1>{{ titleMedico }}</h1>
                            
                           

                        </div>
                        <div class="form-voltar">
                            <button @click="voltarFormInicial"class="btn-voltar">voltar</button>
                         </div>

                        <div class="search-bar">
                            
                        </div><!-- search-bar -->

                        <div  class="form-fields">
                        <input type="text" v-model="nome" placeholder="Nome Médico"/>
                        <input type="text" v-model="crm" placeholder="CRM" />
                        <input type="text" v-model="especialidade" placeholder="Especialidade" />
                        <input type="tel" v-model="telefone" placeholder="Telefone" />
                        <input type="email" v-model="email" placeholder="Email" /> 
                         </div><!-- form-fields Campos do formulário médico -->
                         <div class="form-actions">
                            <button v-on:click="salvar">Salvar</button>
                            <button v-on:click="cancelar">Cancelar</button>     
                        </div><!-- form-actions -->
                        </div><!--form-content-->
                        <div v-else class="opcoes-usuario">
                            <h2>Gerenciar Médicos</h2>
                            <button @click="exibirCadastro">Cadastrar Médico</button>
                            <button @click="listarMedicos">Listar Médicos</button>
                            <button @click="editarMedico">Editar Médico</button>
                            <button @click="excluirMedico">Excluir Médico</button>
                        </div><!--opçoes de usuario-->
                        
                    </div><!-- form-wrapper -->
                </div><!-- doctor-content -->

                <div class="list-medicos" v-if="valorFalso">
                    <div class="list-content">


                    </div><!--form-content-->
                       
                </div><!--list-medicos-->
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

  
  justify-content: center;
  align-items: center;
  width: 462px;
  height: 80px;
}

.form-actions button {
  height: 60%;
  width: 60%;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
  color: white;
  background-color: #0077cc;
  transition: background-color 0.3s ease;
}
.opcoes-usuario {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #001f3f;
  color: white;
  padding: 40px;
  border-radius: 20px;
  gap: 20px;
  margin-top: 50px;
}

.opcoes-usuario h2 {
  font-size: 24px;
  color: #ffe;
}

.opcoes-usuario button {
  padding: 12px 30px;
  font-size: 18px;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  background-color: #0074d9;
  color: white;
  transition: background-color 0.3s;
}

.opcoes-usuario button:hover {
  background-color: #005fa3;
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

.form-content{

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

.form-actions button:hover {
  background-color: #005fa3;
}


h1 {
    color: antiquewhite;
    font-size: 28px;
}

.list-medicos {
  
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

.list-content{


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
.form-voltar{
    display: flex;
    background-color: #ffe;
    width: 160px;
    height: 40px;
    justify-content: center;
    align-items: center;
}
.btn-voltar {
    padding: 12px 60px;
  font-size: 18px;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  background-color: #0074d9;
  color: white;
  transition: background-color 0.3s;
}


</style>

<script setup>
import { ref,  onUnmounted} from 'vue'


const valorFalso = ref(false)
const titleMedico = ref("Cadastro Médico")

function exibirCadastro(){
   valorFalso.value = !valorFalso.value
}

const medicos = ref([])

const nome = ref('')
const crm = ref('')
const especialidade = ref('')
const telefone = ref('')
const email = ref('')

function voltarFormInicial(){
    valorFalso.value = !valorFalso.value
}
function salvar(){

    medicos.value.push({
        nome: nome,
        crm: crm.value,
        especialidade: especialidade.value,
        telefone: telefone.value,
        email: email.value
        
        
    })


}
onUnmounted(() => {
    nome.value = ''
    crm.value = ''
    especialidade.value =''
    telefone.value = ''
    email.value = ''
})



</script>

