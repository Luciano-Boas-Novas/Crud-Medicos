<template>
    <section>
        <div class="crud-container">
            <div class="crud-box">
                <div class="doctor-content">
                    <div  class="form-wrapper" v-if="modoAtual === 'cadastro' || modoAtual === 'menu' || modoAtual === 'listagem'">
                        <div v-if="modoAtual === 'cadastro'" class="form-content">
                            

                        <div class="form-header">
                            <h1>{{ titleMedico }}</h1>
                            
                           

                        </div>
                        <div class="form-voltar">
                            <button @click="voltarFormInicial"class="btn-voltar">voltar</button>
                         </div>

                        <div class="search-bar">
                         
        <!-- Campo para digitar o CRM ou índice -->
      

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
                        <div v-if="modoAtual === 'menu'" class="opcoes-usuario">
                            <h2>Gerenciar Médicos</h2>
                            <button @click="exibirCadastro">Cadastrar Médico</button>
                            <button :class="OcultoForm"@click="listarMedicos">Listar Médicos</button>
                            <button  @click="editarMedico(index)">Editar Médico</button>
                            <button @click="excluirMedico">Excluir Médico</button>
                        </div><!--opçoes de usuario-->
                        <div v-else-if="modoAtual === 'listagem'" class="list-content">
                          <!-- Cabeçalho da listagem de médicos -->
                          <div class="form-header">
                            <h1>Lista de Médicos</h1>
                          </div> <!-- Fim da form-header -->
                          <!-- Botão para voltar ao menu inicial -->
                          <div class="form-voltar">
                            <button @click="voltarFormInicial" class="btn-voltar">
                              Voltar
                            </button>
                          </div> <!-- Fim da form-voltar -->
                          <!-- Lista dos médicos -->
                          <div class="list-scroll">
                            <div v-for="(medico, index) in medicos" :key="index" class="medico-card">
                                <p>Nome: {{ medico.nome }}</p>
                                <p>CRM: {{ medico.crm }}</p>
                                <p>Especialidade: {{ medico.especialidade }}</p>
                                <p>Telefone: {{ medico.telefone }}</p>
                                <p>Email: {{ medico.email }}</p>
                                <div class="buttons-actions">
                                <button class="btn-editar" @click="editarMedico(index)">Editar</button> <!-- Correção aqui -->
                                </div>
                              </div>

                          </div> <!-- Fim da list-scroll -->
                        </div> <!-- Fim da list-content -->
            
                        
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
  background-color: #1c8c42;
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
 
font-size: 16px;
cursor: pointer;
width: 80%;
height: 80%;
padding: 10px 20px;
border: 5px solid ;

border-radius: 7px;
box-shadow: 1px 1px 4px rgb(10, 4, 4);
background-color: #1c8c42;
position: relative; 

color: rgb(255, 255, 255);
  transition: background-color 0.3s ease;
}
.opcoes-usuario {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  
  background-color: #1c8c42;
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
  background-color: #ffffff;
  color: rgb(0, 0, 0);
  transition: background-color 0.3s;
}

.opcoes-usuario button:hover {
  background-color: #00a33e;
}

.form-fields input {
  padding: 10px;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 16px;
}
.search-bar{
    display: flex;
    background-color: rgb(0, 0, 0);
    width: 80%;
    height: 7%;
    align-items: center;
    justify-content: center;
   
}

.form-fields{
    display: flex;
    background-color: rgb(255, 255, 255);
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
    background-color: rgb(0, 0, 0);
    width: 80%;
    height: 70%;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    gap: 10px;
    border-radius: 17px;


}

.form-actions button:hover {
  background-color: #00e990;
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
  background-color: #1c8c42;
  color: white;
  transition: background-color 0.3s;
}

.medico-card {
  background-color: white;
  color: black;
  padding: 20px;
  border-radius: 12px;
  width: 90%;
  margin-bottom: 10px;
  border: 1px solid #ccc;
}

.list-scroll {
  overflow-y: auto;
  max-height: 400px;
  width: 90%;
  padding: 10px;
  background-color: #000000;
  border-radius: 10px;
}

.buttons-actions{

  display: flex;

  padding: 10px 20px;
  justify-content: center;
  align-items: center;

}
.btn-editar{

  width: 80%;
height: 80%;
padding: 10px 20px;
border: 5px solid ;
cursor: pointer;
border-radius: 7px;
box-shadow: 1px 1px 4px rgb(10, 4, 4);
background-color: #1c8c42;
position: relative; 

color: rgb(255, 255, 255);

}

</style>

<script setup>
import { ref,  onMounted} from 'vue'

const modoAtual = ref('menu');
const titleMedico = ref("Cadastro Médico");
const indiceEdicao = ref(null);
const medicos = ref([
  { nome: "Dr. João", crm: "123", especialidade: "Cardiologia", telefone: "99999-9999", email: "joao@example.com" },
  { nome: "Dra. Maria", crm: "124", especialidade: "Neurologia", telefone: "88888-8888", email: "maria@example.com" },
  
]);


const nome = ref('')
const crm = ref('')
const especialidade = ref('')
const telefone = ref('')
const email = ref('')




function limparCampos() {
  nome.value = ''
  crm.value = ''
  especialidade.value = ''
  telefone.value = ''
  email.value = ''
}


function exibirCadastro(){
  modoAtual.value = 'cadastro'
}

function voltarFormInicial(){
    modoAtual.value = 'menu'
    limparCampos()

}



function cancelar(){
  limparCampos()
}
function salvar() {
  if (indiceEdicao.value !== null) {
   
    medicos.value[indiceEdicao.value] ={
      nome: nome.value,
      crm: crm.value,
      especialidade: especialidade.value,
      telefone: telefone.value,
      email: email.value
    };
  }
  else {
    medicos.value.push({
      nome: nome.value,
      crm: crm.value,
      especialidade: especialidade.value,
      telefone: telefone.value,
      email: email.value
    });
  }
  limparCampos();
  modoAtual.value = 'menu';  
}



function listarMedicos(){
  modoAtual.value = 'listagem'


}
function editarMedico(index) {
  modoAtual.value = 'listagem';  
  const medico = medicos.value[index];
  
  nome.value = medico.nome;
  crm.value = medico.crm;
  especialidade.value = medico.especialidade;
  telefone.value = medico.telefone;
  email.value = medico.email;
  indiceEdicao.value = index;  
  titleMedico.value = 'Editar Médico';  
  
}





</script>

