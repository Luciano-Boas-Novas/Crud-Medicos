'
<template>
  <section>
    <div class="title-app">
      <h1>Apicação Cadastro CRUD</h1>
    </div>
    <div class="crud-container">
      <div class="crud-box">
        <div class="doctor-content">
          <div
            class="form-wrapper"
            v-if="
              modoAtual === 'cadastro' ||
              modoAtual === 'menu' ||
              modoAtual === 'listagem'
            "
          >
            <div v-if="modoAtual === 'cadastro'" class="form-content">
              <div class="form-header">
                <h1>{{ titleMedico }}</h1>
              </div>
              <div class="form-voltar">
                <button @click="voltarFormInicial" class="btn-voltar">
                  voltar
                </button>
              </div>

              <div class="form-fields">
                <input type="text" v-model="nome" placeholder="Nome Médico" />
                <input type="text" v-model="crm" placeholder="CRM" />
                <input
                  type="text"
                  v-model="especialidade"
                  placeholder="Especialidade"
                />
                <select v-model="status">
                  <option value="ativo">Ativo</option>
                  <option value="inativo">Inativo</option>
                </select>
                <input type="email" v-model="email" placeholder="Email" />
              </div>
              <!-- form-fields Campos do formulário médico -->
              <div class="form-actions">
                <button v-on:click="salvar">Salvar</button>
                <button v-on:click="cancelar">Cancelar</button>
              </div>
              <!-- form-actions -->
            </div>
            <!--form-content-->
            <div v-if="modoAtual === 'menu'" class="opcoes-usuario">
              <h2>Gerenciar Médicos</h2>
              <button @click="exibirCadastro">Cadastrar Médico</button>
              <button @click="listarMedicos">Listar Médicos</button>
              <button @click="editarMedico(index)">Editar Médico</button>
              <button @click="excluirMedico">Excluir Médico</button>
            </div>
            <!--opçoes de usuario-->
            <div v-else-if="modoAtual === 'listagem'" class="list-content">
              <!-- Cabeçalho da listagem de médicos -->
              <div class="form-header">
                <h1>Lista de Médicos</h1>
              </div>
              <!-- Fim da form-header -->
              <!-- Botão para voltar ao menu inicial -->
              <div class="form-voltar">
                <button @click="voltarFormInicial" class="btn-voltar">
                  Voltar
                </button>
              </div>
              <!-- Fim da form-voltar -->
              <!-- Lista dos médicos -->
              <div class="list-scroll">
                <div
                  v-for="(medico, index) in medicos"
                  :key="index"
                  class="medico-card"
                >
                  <p :class="{ done: medico.status === 'inativo' }">
                    Nome: {{ medico.nome }}
                  </p>
                  <p :class="{ done: medico.status === 'inativo' }">
                    CRM: {{ medico.crm }}
                  </p>
                  <p :class="{ done: medico.status === 'inativo' }">
                    Especialidade: {{ medico.especialidade }}
                  </p>
                  <p :class="{ done: medico.status === 'inativo' }">
                    Status: {{ medico.status }}
                  </p>
                  <p :class="{ done: medico.status === 'inativo' }">
                    Email: {{ medico.email }}
                  </p>

                  <!-- Condicional para ativar o médico, caso o status seja 'inativo' -->
                  <button
                    v-if="medico.status === 'inativo'"
                    class="btn-editar"
                    @click="ativarMedico(index)"
                  >
                    Ativar
                  </button>

                  <div class="buttons-actions">
                    <button class="btn-editar" @click="editarMedico(index)">
                      Editar
                    </button>
                    <button class="btn-editar" @click="excluirMedico(index)">
                      Excluir
                    </button>
                  </div>
                </div>
              </div>
              <!-- Fim da list-scroll -->
            </div>
            <!-- Fim da list-content -->
          </div>
          <!-- form-wrapper -->
        </div>
        <!-- doctor-content -->
      </div>
      <!-- crud-box -->
    </div>
    <!-- crud-container -->
  </section>
</template>

<style scoped>
.crud-container {
  display: flex;
  width: 198vh;
  height: 200vh;
  background-color: #b3b5b7;
  justify-content: center;
  align-items: flex-start;
}

.crud-box {
  margin-top: 200px;
  display: flex;
  height: 1400px;
  width: 1600px;
  margin-bottom: 900px;
  justify-content: center;
  align-items: center;
}

.doctor-content {
  display: flex;
  width: 1200px;
  height: 1600px;
  justify-content: center;
  align-items: flex-start;
}

.form-wrapper {
  display: flex;
  flex-direction: column;
  background-color: white;
  height: 47%;
  width: 60%;
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
  width: 340px;
  height: 80px;
}

.form-actions button {
  font-size: 16px;
  cursor: pointer;
  width: 80%;
  height: 80%;
  padding: 10px 20px;
  border: 5px solid;

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
  justify-content: space-evenly;
  width: 514px;
  height: 598px;
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
  display: flex;
  font-size: 16px;
  cursor: pointer;
  width: 63%;
  justify-content: center;
  align-items: center;
  padding: 5px 14px;
  border: 4px solid;
  border-radius: 6px;
  box-shadow: 1px 1px 4px rgb(10, 4, 4);
  /* background-color: #02cb46; */
  position: relative;
  color: rgb(6 6 6);
  transition: background-color 0.3s ease;
}
.opcoes-usuario button:hover {
  background-color: #00a33e;
}
.form-fields select {
  width: 217px;
  height: 40px;
  border: solid 1px #000000;
  border-radius: 7px;
}
.form-fields input {
  padding: 10px;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 16px;
}

.form-fields {
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

.form-content {
  display: flex;
  background-color: rgb(0, 0, 0);
  width: 60%;
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

.list-content {
  display: flex;
  background-color: black;
  width: 80%;
  height: 70%;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  border-radius: 17px;
}
.form-voltar {
  display: flex;

  width: 420px;
  height: 66.27px;
  justify-content: end;
  align-items: flex-end;
}
.btn-voltar {
  display: flex;
  align-self: center;
  justify-self: end;
  padding: 10px 10px;
  font-size: 18px;
  border-radius: 10px;
  border: solid #ffffff 5px;
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

.buttons-actions {
  display: flex;
  gap: 15px;
  padding: 10px 20px;
  justify-content: center;
  align-items: center;
}

.done {
  text-decoration: line-through;
}
.btn-editar {
  display: flex;
  justify-self: center;
  text-align: center;
  align-self: center;
  width: 60%;
  height: 60%;
  padding: 10px 20px;
  border: 5px solid;
  cursor: pointer;
  border-radius: 7px;
  box-shadow: 1px 1px 4px rgb(10, 4, 4);
  background-color: #1c8c42;
  position: relative;

  color: rgb(255, 255, 255);
}

.title-app {
  display: flex;
  width: 198vh;
  height: 284px;

  color: #ffe;
  justify-content: center;
  align-items: center;
  background-color: #b3b5b7;
}
.title-app h1 {
  font-size: 40px;
  color: #ffffff;
}
</style>

<script setup>
import { ref } from 'vue';

const modoAtual = ref('menu');
const titleMedico = ref('Cadastro Médico');
const indiceEdicao = ref(null);
const medicos = ref([
  {
    nome: 'Dr. João',
    crm: '123',
    especialidade: 'Cardiologia',
    status: 'inativo',
    email: 'joao@example.com',
  },
  {
    nome: 'Dra. Maria',
    crm: '124',
    especialidade: 'Neurologia',
    status: 'Ativo',
    email: 'maria@example.com',
  },
]);

const nome = ref('');
const crm = ref('');
const especialidade = ref('');
const status = ref('');
const email = ref('');

function limparCampos() {
  nome.value = '';
  crm.value = '';
  especialidade.value = '';
  status.value = '';
  email.value = '';
}

function exibirCadastro() {
  modoAtual.value = 'cadastro';
}

function voltarFormInicial() {
  modoAtual.value = 'menu';
  limparCampos();
}

function excluirMedico(index) {
  modoAtual.value = 'listagem';

  medicos.value.splice(index, 1);
}

function cancelar() {
  limparCampos();
}
function salvar() {
  if (indiceEdicao.value !== null) {
    medicos.value[indiceEdicao.value] = {
      nome: nome.value,
      crm: crm.value,
      especialidade: especialidade.value,
      status: status.value,
      email: email.value,
    };
  } else {
    medicos.value.push({
      nome: nome.value,
      crm: crm.value,
      especialidade: especialidade.value,
      status: status.value,
      email: email.value,
    });
  }
  limparCampos();
  modoAtual.value = 'menu';
}

function listarMedicos() {
  modoAtual.value = 'listagem';
}
function editarMedico(index) {
  if (modoAtual.value === 'menu') {
    modoAtual.value = 'listagem';
  } else {
    modoAtual.value = 'cadastro';
  }
  const medico = medicos.value[index];
  nome.value = medico.nome;
  crm.value = medico.crm;
  especialidade.value = medico.especialidade;
  status.value = medico.status;
  email.value = medico.email;
  indiceEdicao.value = index;
  titleMedico.value = 'Editar Médico';
}

function ativarMedico(index) {
  medicos.value[index].status = 'Ativo';
}
</script>

'
