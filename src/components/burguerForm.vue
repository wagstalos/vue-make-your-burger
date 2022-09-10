<template>
    <div>
        <Message :msg="msg" v-show="msg" />
        <form id="burger-form" @submit="createBuruer">
            <div class="input-container">
                <label for="nome">Nome do cliente:</label>
                <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolha o pão:</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione seu pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                        {{ pao.tipo }}
                    </option>
                </select>
            </div>
            <div class="input-container">
                <label for="carne">Escolha a carne:</label>
                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione o tipo de carne</option>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                        {{ carne.tipo }}
                    </option>
                </select>
            </div>

            <div id="opcionais-container" class="input-container">
                <label id="opcionais-title" for="opcionais">Escolha a opcionais:</label>
                <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                    <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                    <span>{{ opcional.tipo }}</span>
                </div>

            </div>

            <div class="input-container">
                <input type="submit" class="submit-btn" value="Criar meu burguer!">
            </div>
        </form>
    </div>
</template>

<script>
import Message from './Message.vue';
export default {
    name: "BurgeForm",
    data() {
        return {
            paes: null,
            canes: null,
            opcionaisdata: null,
            nome: null,
            pao: null,
            carne: null,
            opcionais: [],
            msg: null
        };
    },
    methods: {
        async getIngredientes() {
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();
            console.log(data);
            this.paes = data.paes;
            this.carnes = data.carnes;
            this.opcionaisdata = data.opcionais;
        },
        async createBuruer(e) {
            e.preventDefault();
            const data = {
                nome: this.nome,
                carne: this.carne,
                pao: this.pao,
                opcionais: Array(this.opcionais),
                status: "Solicitado"
            };
            const dataJson = JSON.stringify(data);
            const req = await fetch("http://localhost:3000/burgers", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });
            const res = await req.json();
            // colocar uma msg de sitema
            this.msg = `Pedido Nº ${res.id} realizado com sucesso`
            //limpar msg

            setTimeout(() => this.msg = "", 3000)
            //limpar os campos
            this.nome = "";
            this.carne = "",
                this.pao = "",
                this.opcionais = "";
        }
    },
    mounted() {
        this.getIngredientes();
    },
    components: { Message }
}
</script>

<style scoped>
#burger-form {
    max-width: 400px;
    margin: 0 auto;
}

.input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
    width: 100%;
}

input,
select {
    padding: 5px 10px;
    width: 100%;
}

#opcionais-container {
    flex-direction: row;
    flex-wrap: wrap;
}

#opcionais-title {
    width: 100%;
}

.checkbox-container {
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
    align-items: center;
}

.checkbox-container span,
.checkbox-container input{
    width: auto;
}

.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}

.submit-btn{
    background-color: #FCBA03;
    color: #222;
    border: none;
    border-radius: 10px;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    font-weight: 700;
    transition: .5s;
}

.submit-btn:hover{
    background-color: #222;
    color: #FCBA03;
}

</style>