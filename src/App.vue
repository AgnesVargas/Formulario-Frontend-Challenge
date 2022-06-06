<template>
  <div id="app">
    <div class="cabecalho">
      <h4>FORMULÁRIO</h4>
    </div>
    <a
      href="https://cdpn.io/pen/debug/BaJWKeL?authentication_hash=dGMXWNKydbok"
    >
      <img class="setaEsquerda" src="../img/seta.png" />
    </a>
    <div id="main-container">
      <img class="etapaUm" src="../img/EtapaUm.png" />
      <h1>Seja bem-vindo</h1>
      <form id="registro" @submit.prevent="checkForm">
        <h3>Dados de contato</h3>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Orci,
          volutpat in iaculis nec nibh nisl tellus.
        </p>
        <div class="full-box">
          <label for="nomeCompleto">Nome Completo</label>
          <input
            name="Nome Completo"
            type="text"
            v-model="nome"
            minlength="3"
            @blur="validarNome"
            class="caixaTextoN"
          />
          <p v-if="nomeErrorEmpty" class="textError">Nome não pode ser vazio</p>
          <p v-if="nomeErrorLength" class="textError">
            Nome deve ter pelo menos 3 caracteres
          </p>
        </div>
        <div class="half-box spacing">
          <label for="Email">Email</label>
          <input
            name="Email"
            type="email"
            v-model="email"
            minlength="10"
            @blur="validarEmail"
            class="caixaTextoE"
          />
          <p v-if="emailErrorEmpty" class="textError">
            E-mail não pode ser vazio
          </p>
        </div>

        <div class="half-box">
          <label for="confirmeSeuEmail">Confirme seu Email</label>
          <input
            name="Confirme seu Email"
            type="email"
            v-model="cemail"
            minlength="10"
            @blur="validarCemail"
            class="caixaTextoCe"
          />
          <p v-if="cemailError" class="textError">E-mail inválido</p>
        </div>
        <div class="half-box spacing">
          <label for="CPF">CPF</label>
          <input
            required
            name="cpf"
            type="text"
            v-mask="'###.###.###-##'"
            v-model="cpf"
            minlength="11"
            maxlength="14"
            @blur="validarCPF"
            class="caixaTextoCpf"
          />
          <p v-if="cpfError" class="textError">CPF inválido</p>
          <p v-if="cpfErrorLength" class="textError">
            CPF deve ter 11 caracteres
          </p>
        </div>
        <div class="half-box">
          <label for="Celular">Celular</label>
          <input
            name="Celular"
            type="tel"
            v-mask="'(##) #####-####'"
            v-model="celular"
            minlength="15"
            maxlength="15"
            @blur="validarCelular"
            class="caixaTextoCelular"
          />
          <p v-if="celularError" class="textError">
            Celular não pode ser vazio
          </p>
          <p v-if="celularErrorLength" class="textError">
            Celular deve ter pelo menos 11 caracteres
          </p>
        </div>
        <div class="half-box data-nasc">
          <label for="dataNascimento" class="caixaTextoData"
            >Data de nascimento</label
          >
          <input
            name="Data de nascimento"
            type="date"
            v-model="dataNasc"
            maxlength="6"
            @blur="validarDataNasc"
          />
          <p v-if="dataNascError" class="textError">
            Data de Nascimento não pode ser vazia
          </p>
        </div>

        <label class="text1">
          <p>Lore ipsum dolor sit amet, consectetur adipiscing elit.</p>
        </label>
        <div>
          <label class="text2">
            <p>Matis semper odio pretium vestibulum nulla.</p>
          </label>
        </div>
        <div class="full-box emaileSMS">
          <input type="checkbox" name="Email e SMS" />
          <label for="EmaileSMS">Email e SMS</label>
        </div>

        <div class="full-box whatsApp">
          <input type="checkbox" name="WhatsApp" />
          <label for="WhatsApp">WhatsApp</label>
        </div>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Orci,
          volutpat in iaculis nec nibh nisl tellus.
          <br />
          Amet tellus nunc dolor magna aliquet risus.
          <br />
          Habitant neque, id risus diam.
        </p>
        <div class="half-box button">
          <a href="">
            <button
              type="submit"
              id="btn-submit"
              name="Continuar"
              click="checkForm"
            >
              Continuar
            </button></a
          >
        </div>
        <footer></footer>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      nome: "",
      email: "",
      cemail: "",
      cpf: "",
      celular: "",
      dataNasc: "",
      nomeErrorEmpty: false,
      nomeErrorLength: false,
      emailErrorEmpty: false,
      emailErrorLength: false,
      cemailError: false,
      cpfError: false,
      cpfErrorLength: false,
      celularError: false,
      celularErrorLength: false,
      dataNascError: false,
      imageUrl: null,
    };
  },
  methods: {
    validarNome() {
      this.nomeErrorEmpty = this.nome === "";
      this.nomeErrorLength = this.nome.length < 3;
      return false;
    },
    validarEmail() {
      this.emailErrorEmpty = this.email === "";
      this.emailErrorLength = this.email.length < 13;
    },
    validarCemail() {
      this.cemailError = this.cemail !== this.email;
    },
    validarCPF() {
      this.cpfError = this.cpf === "";
      this.cpfErrorLength = this.cpf.length < 11;
    },
    validarCelular() {
      this.celularError = this.celular === "";
      this.celularErrorLength = this.celular.length < 15;
    },
    validarDataNasc() {
      this.dataNascError = this.datanasc === "";
    },
    checkForm(){
      const isNomeCorreto = this.validarNome();
      const isEmailCorreto = this.validarEmail();
      const isCemailCorreto = this.validarCemail();
      const isCpfCorreto = this.validarCpf();
      const isCelularCorreto = this.validarCelular();
      const isDataNascCorreto = this.validarDataNasc();
       if (
        isNomeCorreto &&
        isEmailCorreto &&
        isCemailCorreto &&
        isCpfCorreto &&
        isCelularCorreto &&
        isDataNascCorreto
       ) {
        this.logUsuario()
      }
    },
    logUsuario (){
    axios.get('https://api.thecatapi.com/v1/images/search')
        .then(response => {
          this.imageUrl = response.data[0].url;
          console.log(response.data);
        })
        .catch(error => {
          console.log('Usuário não foi cadastrado', error);
        })
    }
        },
};

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: black;
}
.cabecalho {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 13px;
  color: white;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  font-size: 15px;
  margin-bottom: 0.5%;
}
.full-box {
  display: flex;
  gap: 15px;
  flex-direction: column;
}
.caixaTextoN {
  background-color: white;
  color: black;
  font-size: 0.8rem;
  border-radius: 3px;
  padding: 6px 9px;
  width: 100%;
  outline: unset;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
}
.caixaTextoN :focus {
  border: 2px solid #e82c54;
}
.caixaTextoE {
  background-color: white;
  color: black;
  font-size: 0.8rem;
  border-radius: 3px;
  padding: 6px 9px;
  width: 100%;
  outline: unset;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
}
.caixaTextoE :focus {
  border: 2px solid #e82c54;
}
.caixaTextoCe {
  background-color: white;
  color: black;
  font-size: 0.8rem;
  border-radius: 3px;
  padding: 6px 9px;
  width: 100%;
  outline: unset;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
}
.caixaTextoCe :focus {
  border: 2px solid #e82c54;
}
.caixaTextoCpf {
  background-color: white;
  color: black;
  font-size: 0.8rem;
  border-radius: 3px;
  padding: 6px 9px;
  width: 100%;
  outline: unset;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
}
.caixaTextoCpf :focus {
  border: 2px solid #e82c54;
}
.caixaTextoCelular {
  background-color: white;
  color: black;
  font-size: 0.8rem;
  border-radius: 3px;
  padding: 6px 9px;
  width: 100%;
  outline: unset;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
}
.caixaTextoCelular :focus {
  border: 2px solid #e82c54;
}
.full-box label,
.full-box input {
  display: inline-block;
}
.half-box {
  display: flex;
  gap: 15px;
  flex-direction: column;
}
.half-box label,
.half-box input {
  display: inline-block;
}
/*geral*/
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Helvetica, sans-serif;
  color: black;
  border: none;
}
input,
label {
  display: block;
  width: 100%;
}
a {
  color: #e82c54;
}
body {
  background-color: #e82c54;
  background-image: url("../img/carteira.png");
  background-position-x: 55%;
  background-position-y: 0%;
}
h1 {
  font-size: 50px;
}
h3 {
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  color: black;
  height: 50px;
}
h4 {
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  color: white;
  margin-top: 2%;
}
.emaileSMS,
.whatsApp {
  display: flex;
  flex-direction: row;
  height: 30px;
}
.emaileSMS input,
.whatsApp input {
  width: min-content;
  height: min-content;
}
/*form*/
#main-container {
  width: 60%;
  background-color: white;
  padding: 7%;
}
#main-container h1 {
  text-align: left;
  margin-bottom: 25px;
}
form {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.full-box {
  flex: 1 1 100%;
  position: relative;
}
.half-box {
  flex: 1 1 45%;
  position: relative;
}
.spacing {
  margin-right: 2.5%;
}
.textError {
  color: red;
  font-size: 12px;
  margin: 0;
}
.full-box {
  margin-top: 10px;
}
.half-box {
  margin-top: 30px;
}
label {
  font-weight: bold;
  font-size: 0.8rem;
}
input {
  border: 1px solid black;
  border-radius: 5px;
  padding: 5px;
  font-size: 0.9rem;
  margin-bottom: 5px;
  height: 50px;
}
.half-box.data-nasc input {
  width: min-content;
  height: 30px;
  border-color: gray;
}
input:focus {
  border-color: #e82c54;
}
input[type="submit"] {
  background-color: #e82c54;
  color: white;
  border: none;
  border-radius: 20px;
  height: 40px;
  cursor: pointer;
}
.half-box.button button {
  background-color: #e82c54;
  color: white;
  border-radius: 10px;
  height: 40px;
  width: 15%;
  font-family: Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  cursor: pointer;
  margin-bottom: 20px;
}
#agreement {
  margin-right: 5px;
}
.setaEsquerda {
  width: 30px;
  margin-top: -5%;
  margin-left: 1%;
  justify-content: center;
  margin-bottom: 0.2%;
}
.text1 {
  height: 40px;
  margin-top: 15px;
}
.text2 {
  height: 35px;
}
.etapaUm {
  width: 680px;
  margin-left: -5%;
  margin-top: -15%;
}
#agreement,
#agreement-label {
  display: inline-block;
  width: auto;
}
footer {
  margin-bottom: 5%;
}
</style>

