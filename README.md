# atv_mercadinho_cidinha

# Dados:
```
[
    {
        "id": 1,
        "nome": "Chocolate",
        "unidade": "Unidade",
        "precoUnitario":7.99,
        "quantidade":1
    },
    {
        "id": 2, 
        "nome": "Leite",
        "unidade": "Unidade",
        "precoUnitario":4.99,
        "quantidade":4
    },
        {
            "id": 3,
            "nome": "Batata",
            "unidade": "Kg",
            "precoUnitario":4.50,
            "quantidade":3
        }
]
```

* Copiem estes dados para a realização da atividade (coloquem-os no "dados.json")

# Index
```
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mercadinho da Cidinha</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>
<center>
    <header class="cabecalho">
        <h1>Mercadinho da Cidinha</h1>
        <h2>Novo Pedido</h2>
    </header>

    <main class="container">

        <form action="http://127.0.0.1:3000" method="post">

            <div class="campo">
                <label for="id">Identificação</label>
                <input type="number" id="id" name="id" placeholder="Digite a identificação" required>
            </div>
            <br>
            <div class="campo">
                <label for="nome">Nome do Produto</label>
                <input type="text" id="nome" name="nome" placeholder="Digite o nome do produto" required>
            </div>
            <br>
            <div class="campo">
                <label for="unidade">Unidade</label>
                <select id="unidade" name="Unidade" required>
                    <option value="" disabled selected>Selecione uma opção</option>
                    <option value="Kg">Kg</option>
                    <option value="Unidade">Unidade</option>
                </select>
            </div>
            <br>
            <div class="campo">
                <label for="preco">Preço Unitário</label>
                <input type="number" id="preco" step="0.01" name="precoUnitario" placeholder="R$ 0,00" required>
            </div>
            <br>
            <div class="campo">
                <label for="quantidade">Quantidade</label>
                <input type="number" id="quantidade" name="Quantidade" placeholder="Digite a quantidade" required>
            </div>
            <br>
            <div class="botoes">
                <button type="reset" class="limpar">Limpar</button>
                <button type="submit" class="enviar">Enviar Pedido</button>
            </div>

        </form>

    </main>
    
</center>

</body>
</html>
```
* Copiem estes dados para a realização da atividade (coloquem-os no "index.html")
# server
```
const express = require("express")
const compras = require("../dados.json")

const mostrarCompras = (req, res) => {
    res.send(compras)
}

const novaCompra = (req, res) => {
    if(req.body){
        res.send("Compra recebida, e em separação")
        compras.push(req.body)
    }else{
        res.send("Ocorreu um erro ao receber o pedido de compra")
    }
}

const app = express()
app.use(express.urlencoded({extended:true}))
const porta = 3000

app.get("/", mostrarCompras)

app.listen(porta, () => { 
    console.log(`Cliente: http://127.0.0.1:5500/cliente/`)
    console.log(`Servidor: http://127.0.0.1:${porta}`)
})
```
* Copiem estes dados para a realização da atividade (coloquem-os no "server.js")

# Atividade
Com base nesta revisão e o que já foi visto em outra aula, faça:

* Mudem este código e criem para este humilde mercado um meio de calcular o valor total da compra feita pelo cliente
