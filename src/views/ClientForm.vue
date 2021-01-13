<template>
  <div id="container">
    <div id="form">
      <label for="name">Nome</label>
      <input type="text" id="name" v-model="name" />

      <label for="email">Email</label>
      <input type="text" id="email" v-model="email" />

      <label for="cpf">CPF</label>
      <input type="text" id="cpf" v-model="cpf" placeholder="111.111.111-01" />

      <div class="row">
        <div class="col">
          <label for="address">Endereço</label>
          <input
            type="text"
            id="address"
            v-model="address"
            placeholder="Rua, Número e Bairro"
          />
        </div>
        <div class="col">
          <label for="state">Estado</label>
          <select id="state" placeholder="Selecione o Estado" v-model="state">
            <option value="MG">Minas Gerais</option>
            <option value="RJ">Rio de Janeiro</option>
          </select>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <label for="cep">CEP</label>
          <input type="text" id="cep" placeholder="22.222-000" v-model="cep" />
        </div>
        <div class="col">
          <label for="city">Cidade</label>
          <input
            type="text"
            id="city"
            placeholder="Selecione a Cidade"
            v-model="city"
          />
        </div>
      </div>
    </div>

    <div>
      <h2>Forma de Pagamento</h2>
      <hr />

      <div class="radio-container">
        <span>
          <input
            type="radio"
            class="radio"
            name="radio"
            id="creditCard"
            value="creditCard"
            v-model="payment"
          />
          <label for="creditCard">Cartão de Crédito</label>
        </span>
        <span>
          <input
            type="radio"
            class="radio"
            name="radio"
            id="bankSlip"
            value="bankSlip"
            v-model="payment"
          />
          <label for="bankSlip">Boleto Bancário</label>
        </span>
      </div>

      <div>
        <div class="row" id="creditExpiration">
          <div class="col">
            <label for="creditOwner">Nome no Cartão</label>
            <input
              type="text"
              id="creditOwner"
              v-model="creditOwner"
              placeholder="Nome impresso no cartão"
            />
          </div>
          <div class="col">
            <label for="creditExpiration">Data de Expiração</label>
            <span class="row">
              <input
                type="text"
                id="creditExpirationMonth"
                placeholder="Mês"
                v-model="creditExpirationMonth"
              />
              <input
                type="text"
                id="creditExpirationYear"
                placeholder="Ano"
                v-model="creditExpirationYear"
              />
            </span>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col">
          <label for="creditNumber">Número do Cartão</label>
          <input
            type="text"
            id="creditNumber"
            v-model="creditNumber"
            placeholder="5555 5555 5555 5555"
          />
        </div>
        <div class="col">
          <label for="creditSecurityCode">Código de Segurança</label>
          <input
            type="text"
            id="creditSecurityCode"
            v-model="creditSecurityCode"
            placeholder="XXX"
          />
        </div>
      </div>
      <hr />
    </div>

    <div class="payment-confirmation">
      <h3>Seu cartão será debitado em R$ 49,00</h3>
      <h3 class="error-message" v-show="valitationError">
        Preencha os todos os campos para continuar
      </h3>
      <button v-on:click.prevent="addClient" type="submit">
        REALIZAR MATRÍCULA
      </button>
      <p>Informações seguras e criptografadas</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ClientForm",
  data() {
    return {
      name: "",
      email: "",
      cpf: "",
      address: "",
      state: "",
      cep: "",
      city: "",
      payment: "",
      creditOwner: "",
      creditExpirationMonth: "",
      creditExpirationYear: "",
      creditNumber: "",
      creditSecurityCode: "",
      date: new Date(),
      valitationError: false,
    };
  },
  methods: {
    addClient() {
      if (this.name.trim() === "") {
        return (this.valitationError = true);
      }
      if (this.email.trim() === "") {
        return (this.valitationError = true);
      }
      if (this.cpf.trim() === "") {
        return (this.valitationError = true);
      }

      const newClient = JSON.stringify({
        name: this.name,
        email: this.email,
        cpf: this.cpf,
        address: this.address,
        state: this.state,
        cep: this.cep,
        city: this.city,
        payment: this.payment,
        createdAt: this.date,
        creditCard:
          this.payment === "bankSlip"
            ? undefined
            : {
                owner: this.creditOwner,
                expirationMonth: this.creditExpirationMonth,
                expirationYear: this.creditExpirationYear,
                creditNumber: this.creditNumber,
                creditSecurityCode: this.creditSecurityCode,
              },
      });

      fetch("http://localhost:3333/client", {
        method: "post",
        headers: {
          Accept: "application/json; charset=UTF-8",
          "Content-Type": "application/json; charset=UTF-8",
        },
        body: newClient,
      })
        .then((response) => response.json())
        .then((response) => {
          this.gridData = response;
        });

      const formKeys = [
        "name",
        "email",
        "cpf",
        "address",
        "state",
        "cep",
        "city",
        "payment",
        "creditOwner",
        "creditExpirationMonth",
        "creditExpirationYear",
        "creditNumber",
        "creditSecurityCode",
      ];

      formKeys.forEach((key) => {
        this[key] = "";
      });

      this.valitationError = false;
    },
  },
};
</script>

<style scoped>
#container {
  width: 100%;
  max-width: 720px;
}

label {
  font-size: 23px;
  font-weight: 700;
}

input,
select {
  width: 100%;
  height: 62px;
  margin: 4px 0 20px 0;
  padding-left: 16px;
  border-radius: 5px;
  border: 0;
  background: #eff4f9;
  box-shadow: 0px 2px 2px rgba(187, 204, 221, 0.4);
}

input:focus,
select:focus {
  border: 2px solid #17222d;
}

input::placeholder {
  font-weight: 600;
  color: #17222d;
  opacity: 0.3;
}

.row {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 22px;
}

h2 {
  color: #1188ee;
  font-size: 24px;
  margin: 18px 0 0 0;
}

hr {
  border: 1.2px solid #eff4f9;
  background: #eff4f9;
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
  color: #1188ee;
  box-shadow: 0 0;
}

.payment-confirmation h3 {
  font-weight: 600;
  margin: 60px 0 16px 0;
}

.payment-confirmation .error-message {
  font-weight: 600;
  margin: 16px 0 16px 0;
  color: red;
}

.payment-confirmation button {
  background-color: #1188ee;
  color: #eff4f9;
  border: none;
  border-radius: 5px;
  padding: 16px 32px;
  font-size: 24px;
  font-weight: 700;
}

.payment-confirmation button:hover {
  opacity: 0.9;
}

.payment-confirmation p {
  margin: 16px 0 62px 0;
}
</style>
