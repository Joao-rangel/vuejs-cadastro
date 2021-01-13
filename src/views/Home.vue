<template>
  <div id="container">
    <div id="form">
      <label for="name">Nome</label>
      <input type="text" id="name" v-model="name">
      
      <label for="email">Email</label>
      <input type="text" id="email" v-model="email">

      <label for="cpf">CPF</label>
      <input type="text" id="cpf" v-model="cpf" placeholder="111.111.111-01">

      <div class="row">
        <div class="col">
          <label for="adress">Endereço</label>
          <input type="text" id="adress" v-model="adress" placeholder="Rua, Número e Bairro">
        </div>
        <div class="col">
          <label for="state">Estado</label>
          <select id="state" v-model="state" placeholder="Selecione o Estado">
            <option value="MG">Minas Gerais</option>
            <option value="RJ">Rio de Janeiro</option>
          </select>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <label for="cep">CEP</label>
          <input type="text" id="cep" v-model="cep" placeholder="22.222-000">
        </div>
        <div class="col">
          <label for="city">Cidade</label>
          <input type="text" id="city" v-model="city" placeholder="Selecione a Cidade">
        </div>
      </div>
    </div>

    <div>
      <h2>Forma de Pagamento</h2>
      <hr>

      <div class="radio-container">
        <span>
          <input type="radio" class="radio" id="creditCard">
          <label for="creditCard">Cartão de Crédito</label>
        </span>
        <span>
          <input type="radio" class="radio" id="bankSlip">
          <label for="bankSlip">Boleto Bancário</label>
        </span>
      </div>

      <div>
        <div class="row" id="creditExpiration">
          <div class="col">
            <label for="creditOwner">Nome no Cartão</label>
            <input type="text" id="creditOwner" placeholder="Nome impresso no cartão" v-model="creditOwner">
          </div>
          <div class="col">
            <label for="creditExpiration">Data de Expiração</label>
            <span class="row">
              <input type="text" id="creditExpirationMonth" placeholder="Mês" v-model="creditExpirationMonth">
              <input type="text" id="creditExpirationYear" placeholder="Ano" v-model="creditExpirationYear">
            </span>
          </div>
        </div>
      </div>
      
      <div class="row">
        <div class="col">
          <label for="creditNumber">Número do Cartão</label>
        <input type="text" id="creditNumber" placeholder="5555 5555 5555 5555" v-model="creditNumber">
        </div>
        <div class="col">
          <label for="creditSecurityCode">Código de Segurança</label>
         <input type="text" id="creditSecurityCode" placeholder="XXX" v-model="creditSecurityCode">
        </div>
      </div>
      <hr>
    </div>

    <div class="payment">
      <h3>Seu cartão será debitado em R$ 49,00</h3>
      <button type="button">REALIZAR MATRÍCULA</button>
      <p>Informações seguras e criptografadas</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
}
</script>

<style scoped>
#container {
  width: 100%;
  max-width: 720px;
}

#form {
  margin-top: 65px;
}

label {
  font-size: 23px;
  font-weight: 700;

}

input, select {
  width: 100%;
  height: 62px;
  margin: 4px 0 20px 0;
  padding-left: 16px;
  border-radius: 5px;
  border: 0;
  background: #EFF4F9;
  box-shadow: 0px 2px 2px rgba(187, 204, 221, 0.4);
}

input:focus, select:focus {
  border: 2px solid #17222D;
}

input::placeholder {
  font-weight: 600;
  color: #17222D;
  opacity: .3;
}

.row {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 22px;
}

h2 {
  color: #1188EE;
  font-size: 24px;
  margin: 18px 0 0 0;
}

hr {
  border: 1.2px solid #EFF4F9;
  background: #EFF4F9;
  margin: 16px 0 32px 0;
}

.radio-container {
  display: flex;
  margin: 56px 0 32px 0;
}

.radio {
  height: 20px;
  width: 20px;
  margin: 0 16px 0 32px;
  color: #1188EE;
  box-shadow: 0 0;
}

.payment h3 {
  font-weight: 600;
  margin: 60px 0 16px 0;
}

button {
  background-color: #1188EE;
  color: #EFF4F9;
  border: none;
  border-radius: 5px;
  padding: 16px 32px;
  font-size: 24px;
  font-weight: 700;
}

button:hover {
  opacity: 0.9;
}

.payment p {
  margin: 16px 0 62px 0;
}
</style>
