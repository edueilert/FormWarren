<template>

      <div id="app">
            
            <form @submit.prevent="checkForm">
                
                
                <a href="https://warren.atlassian.net/jira/software/c/projects/EV/boards/454?modal=detail&selectedIssue=EV-57">
                   
                  <img class="setaesquerda" 
                  src="../imagens/setaesquerda.png">
                  
                </a>
              
                
                <img class="faixa" 
                     src="../imagens/1.png">

                <h1>Seja Bem-Vindo</h1>
                                
                    <p><br>
                        Lore ipsum dolor sit amet, consectetur adipiscing elit. Orci, vulutpat in iaculis nec nibh nisl tellus.>
                    </p>   
                
                <div class="caixa-cheia">
                    <label for="name"><br>Nome</label>
                    <input
                    type="text" 
                    name="name" 
                    v-model="name" 
                    id="name"
                    placeholder= "Digite seu nome: "
                    >
                    <p v-if="errorNameEmpty" class="textError">Nome não pode estar vazio </p>
                    <p v-if="errorNameLength" class="textError">Nome deve possuir no minimo 3 caracteres </p>
                </div>
                <div class="meia-caixa espaco">
                    <label for="email">E-mail</label>
                    <input 
                    type="email" 
                    name="email" 
                    v-model="email" 
                    id="email" 
                    placeholder= "Digite seu e-mail: ">
                    <p v-if="errorEmailEmpty" class="textError">O E-mail não pode estar vazio </p>
                    <p v-if="errorEmail" class="textError">O Email deve possuir alguns caracteres cruciais </p>
                </div>
                <div class="meia-caixa espaco">
                    <label for="confirmEmail">Confirme seu e-mail</label>
                    <input 
                    type="email" 
                    name="confirmEmail"
                    v-model="confirmEmail" 
                    id="confirmEmail" 
                    placeholder= "Confirme seu e-mail: ">
                    <p v-if="errorConfirmEmail" class="textError">O Email deve ser igual ao anterior</p>
                </div>
                <div class="meia-caixa espaco">
                    <label for="cpf">CPF</label>
                    <input
                    v-mask="'###.###.###-##'"
                    v-model="cpf"
                    type="text" 
                    name="cpf" 
                    id="cpf" 
                    placeholder= "Digite seu CPF: ">
                    <p v-if="errorCpfEmpty" class="textError">O CPF não pode estar em branco </p>
                    <p v-if="errorCpfLength" class="textError">O CPF deve possuir 11 caracteres </p>
                    <p v-if="errorCpfInvalid" class="textError">Digite um CPF válido </p>
                    
                </div> 
                <div class="meia-caixa espaco">
                    <label for="celphone">Celular</label>
                    <input
                    v-mask="'(##)#####-####'"
                    v-model="celphone"
                    type="tel" 
                    name="celphone" 
                    id="celphone" 
                    placeholder= "Digite seu telefone: ">
                    <p v-if="errorCelphoneEmpty" class="textError">O telefone não pode estar vazio </p>
                    <p v-if="errorCelphoneLength" class="textError">O telefone deve possuir 11 caracteres </p>
                </div>
                <div class="meia-caixa espaco">
                    <label for="nascimento">Data de nascimento</label>
                    <input
                    v-model="nascimento"
                    type="date"
                    name="nascimento" 
                    id="nascimento" 
                    placeholder= "Digite sua data de nascimento: ">
                    <p v-if="errorNascimentoEmpty" class="textError">A data está vazia </p>
                    <p v-if="errorNascimentoLength" class="textError">Defina uma data correta </p>
                </div>
                <div class="meia-caixa espaco">
                    <label for="vazio"></label>
                    
                </div>
                <div class="caixa-cheia">
                    <label for="text1">
                        Lore ipsum dolor sit amet, consectetur adipiscing elit.

                    </label>
                </div>
                <div class="caixa-cheia">
                    <label for="text2">
                        <br>
                        Matis semper odio pretium vestibulum nulla.
                        
                    </label>
                    <br>
                </div>
                
                <div class="caixa-cheia">
                    <input type="checkbox" id="emailsms" name="emailsms"> 
                    <label for="emailsms" id="emailsms-label">
                    E-mail e SMS    
                    </label>
                                        
                </div>
                
                <div class="caixa-cheia">
                    <input type="checkbox" id="whatsapp" name="whatsapp">
                    <label for="whatsapp" id="whatsapp-label">
                    WhatsApp
                    </label>
                    <p v-if="errorCheckboxEmpty" class="textError">Selecione alguma das caixas </p>
                                        
                </div>

                <p>Lore ipsum dolor sit amet, consectetur adipiscing elit. Orci, vulutpat in iaculis nec nibh nisl tellus. Amet tellus nunc dolor magna aliquet risus. Habitant neque, id risus diam. </p>

                <div>
                    <br>
                    <input type="submit" id="btn-submit" value="Próximo" href="https://www.youtube.com/">
                    
                </div>
              </form>
            <p class="error-validation template">

            </p>
        </div>
</template>

<script>

  function ValidadorCPF(Cpf) {
      var Soma;
      var Resto;
      var i;
      Soma = 0;
      if (Cpf == "00000000000") return false;
      if (Cpf == "11111111111") return false;
      if (Cpf == "22222222222") return false;
      if (Cpf == "33333333333") return false;
      if (Cpf == "44444444444") return false;
      if (Cpf == "55555555555") return false;
      if (Cpf == "66666666666") return false;
      if (Cpf == "77777777777") return false;
      if (Cpf == "88888888888") return false;
      if (Cpf == "99999999999") return false;
      for (i = 1; i <= 9; i++) Soma = Soma + parseInt(Cpf.substring(i - 1, i)) * (11 - i);
      Resto = (Soma * 10) % 11;
      if ((Resto == 10) || (Resto == 11)) Resto = 0;
      if (Resto != parseInt(Cpf.substring(9, 10))) return false;
      Soma = 0;
      for (i = 1; i <= 10; i++) Soma = Soma + parseInt(Cpf.substring(i - 1, i)) * (12 - i);
      Resto = (Soma * 10) % 11;
      if ((Resto == 10) || (Resto == 11)) Resto = 0;
      if (Resto != parseInt(Cpf.substring(10, 11))) return false;
      return true;
  }
  var Cpf = "12345678909";
  alert(ValidadorCPF(Cpf));

export default {
  name: 'App',
  components: {
    },
    data() {
      return {
        errorNameLength: false,
        errorNameEmpty: false,
        errorCpfLength: false,
        errorCpfEmpty: false,
        errorCpfInvalid: false,
        errorEmail: false,
        errorEmailEmpty: false,
        errorConfirmEmail: false,
        errorCelphoneLength: false,
        errorCelphoneEmpty: false,
        errorNascimentoLength: false,
        errorNascimentoEmpty: false,
        errorCheckboxEmpty: false,
        errorCheckbox: false,
        name: null,
        cpf: null,
        email: null,
        confirmEmail: null,
        celphone: null,
        nascimento: null,
        emailsms: null,
        whatsapp: null,

      }
    },
    methods:{
      checkForm () {
        if (!this.name) {
          this.errorNameEmpty = true
          this.errorNameLength = false
        } else if(this.name.length < 3) {
          this.errorNameEmpty = false
          this.errorNameLength = true
        } else {
          this.errorNameEmpty = false
          this.errorNameLength = false
        }

        if (!this.cpf) {
          this.errorCpfEmpty = true
          this.errorCpfLength = false
          this.errorCpfInvalid = false
        } else if(this.cpf.length < 14) {
          this.errorCpfLength = true
          this.errorCpfEmpty = false
          this.errorCpfInvalid = false
        } else if(!ValidadorCPF(this.cpf.replace(/[^0-9]/g, ''))) {
          this.errorCpfInvalid = true
          this.errorCpfLength = false
          this.errorCpfEmpty = false
        } else {
          this.errorCpfInvalid = false
          this.errorCpfLength = false
          this.errorCpfEmpty = false
        }

        if (!this.celphone) {
          this.errorCelphoneEmpty = true
          this.errorCelphoneLength = false
        } else if(this.celphone.length < 14) {
          this.errorCelphoneLength = true
          this.errorCelphoneEmpty = false
        } else {
          this.errorCelphoneEmpty = false
          this.errorCelphoneLength = false
        }

        if (!this.nascimento) {
          this.errorNascimentoEmpty = true
          this.errorNascimentoLength = false
        } else if(this.nascimento.length < 8) {
          this.errorNascimentoLength = true
          this.errorNascimentoEmpty = false
        } else {
          this.errorNascimentoEmpty = false
          this.errorNascimentoLength = false
        }

        const emailRegex = /^[a-z0-9.]+@[a-z0-9]+\.[a-z]+(\.[a-z]+)?$/i
        if (!emailRegex.test(this.email)) {
          this.errorEmail = true
         } else {
          this.errorEmail = false
         }

         if (this.email !== this.confirmEmail) {
            this.errorConfirmEmail = true
        } else {
            this.errorConfirmEmail = false
        }

    }
}}

</script>

<style>
* {
margin: 0;
padding: 0;
box-sizing: border-box;
font-family: 'Times New Roman', Times, serif;
color: black;
border: none;

}

body {
background-image: url('../imagens/walps2.png');
padding-top: 10vh;
padding-bottom: 10vh;
background-size: cover;
background-color: rgb(241, 98, 165);

}

input, label {
display: block;
width: 100%;

}

input:focus, label:focus {
    outline: none;
}

a {
    color: yellow;
}

#app {
    width: 580px;
    margin-left: auto;
    margin-right: auto;
    background-color: #FFFFFF;
    border-radius: 10px;
    padding: 25px;
    
}

#conteiner-pricipal h1 {
    text-align: center;
    margin-bottom: 25px;
    font-size: 1.6rem;
}
    
form {
    display: flex;
    flex-wrap: wrap;
    padding: 5%;
    justify-content: space-between;
}

.caixa-cheia {
    flex: 1 1 100%;
    position: relative;
}

.meia-caixa {
    flex: 1 1 45%;
    position: relative;
}


.espaco {
    margin-right: 2.5%;
}

label {
    font-weight: bold;
    font-size: .8rem;
}

input {
    border: 1px solid black;
    border-radius: 10px;
    padding: 15px;
    font-size: .9rem;
    margin-bottom: 20px;
}

input:focus {
    border-color: rgb(241, 98, 165);
}

input[type="submit"] {
    background-color: rgb(241, 98, 165);
    color: aliceblue;
    border: none;
    border-radius: 20px;
    height: 50px;
    cursor: pointer;
}

#emailsms {
    margin-right: 5px;
}

#emailsms, #emailsms-label {
    display: inline-block;
    width: auto;
}

#whatsapp {
    margin-right: 5px;
}

#whatsapp, #whatsapp-label {
    display: inline-block;
    width: auto;
}

.textError {
  color: red;
  size: 10px;
  margin-top: -4%;
  padding: 5px;
}

.faixa {
  width: 100%;
}

.setaesquerda {
  width: 50px;
  height: 50px;
  margin-top: -10px;
  

}

</style>
