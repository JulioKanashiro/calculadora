# calculrepo1
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora Financeira - Kaldi Solutions</title>
</head>
<body>
<!-- Introdução -->
    <h1>Calculadora de estufa cafeeira 🤓</h1>
    <p>Nós da Kaldi Solutions simulamos o prejuizo que você está tendo agora gratuitamente!! ☕</p>
    <div>
        <!-- caixa de entrada de dados pessoais ou empresariais-->
        <h2>Dados pessoais</h2>
        Nome Completo: <br><input type="text" id="iptNome" placeholder="Digite seu nome"><br><br>
        Email para contato: <br><input type="text" id="iptEmail" placeholder="Digite seu email"><br><br>
        Insira o nome de sua empresa em que trabalha ou se é autonomo: <br><input type="text" id="iptEmpresa" placeholder="Digite o nome da empresa"><br><br>
        Dê uma avaliação para sua colheita de 0 à 10: <br><input type="text" id="iptSatisfacao" placeholder="Digite uma avaliação">
    </div>
    <div>
        <!-- caixa de dados numericos e estatisticos sobre o plantíl -->
        <h2 style="color: brown;">Dados da colheita </h2>
        Digite a quantidade de sacas (60kg) produzidas na safra anual: 
        <br><input type="text" id="iptSacas" placeholder="Digite a quantidade de sacas produzidas"><br><br>
        Digite o valor de venda por saca:
        <br><input type="text" id="iptVendaSaca" placeholder="Digite o valor de venda por saca">
    <br><br>
        <button onclick="simulacao()">Simule seu negócio</button><br><br>
    </div>
    <div id="res">⬇️Veja abaixo a simulação de seu negócio⬇️</div>
</body>
</html>
<script>
    function simulacao() {
        
        // Variaveis "genericas"
        var nome = iptNome.value
        var email = iptEmail.value
        var empresa = iptEmpresa.value
        var satisfacao = iptSatisfacao.value
        var qtdSacaS = Number(iptSacas.value)
        var razao = 1.153
        var sacaKgS = qtdSacaS * 60
        var valorSacaS = Number(iptVendaSaca.value)
    
        // Variaveis Safrais
        var capEstufa = qtdSacaS * razao
        var ganhosS = capEstufa * valorSacaS  
        var lucroAtualS = qtdSacaS * valorSacaS
        var prejuizoS =  ganhosS - lucroAtualS
        var margemPerdaS = (prejuizoS * 100) / lucroAtualS

        // variaveis projeções futuras
        var pAno3 = prejuizoS * 3
        var pAno5 = prejuizoS * 5
        var pAno10 = prejuizoS * 10

        // ifelse1 - Avaliação
        if(satisfacao <= 4) {
            res.innerHTML = `<h2 style="color: red;"> Você considerou a safra como ruim 😢</h2>
                             <h2 style="color: red;"> Contudo, não desanime, temos a solução...</h2>`
        } else if(satisfacao <= 6){
            res.innerHTML = `<h2 style="color: darkblue;"> Você considerou a safra como mediana 😐</h2>
                             <h2 style="color: red;">Todavia....</h2>`
        } else {
            res.innerHTML = `<h2 style="color: green;"> Você considerou a safra como boa 😊</h2>
                             <h2 style="color: red;">Todavia....</h2>`
        }
        
        // ifelse2 - Solução
        if(empresa == 'autonomo') {
            res.innerHTML += `
                <h1>Sem a Kaldi Solutions</h1>
                <h2> Projeção de safra </h2>
                    Olá ${nome}, ao vender ${qtdSacaS} sacas equivalentes a ${sacaKgS}kg por R$ ${valorSacaS.toFixed(2)} cada,  
                    nessa safra você teve uma receita de <b>R$ ${lucroAtualS.toFixed(2)}</b>.
                    <br> Você sabia que hoje você deixa de ganhar cerca de <b>R$ ${prejuizoS.toFixed(2)}</b> em sua produção.
            `
            res.innerHTML += `
                <h2> Projeção de sua safra para anos futuros</h2>
                <ul>
                    <li>Em um ano você terá uma perda de aproximadamente <b>R$ ${prejuizoS.toFixed(2)}</b></li>
                    <li>Em três anos você terá uma perda de aproximadamente <b>R$ ${pAno3.toFixed(2)}</b></li>
                    <li>Em cinco anos você terá uma perda de aproximadamente <b>R$ ${pAno5.toFixed(2)}</b></li>
                    <li>Em dez anos você terá uma perda de aproximadamente <b>R$ ${pAno10.toFixed(2)}</b></li>
                </ul>
                <h2 style="color: red;"> ...Você está deixando de lucrar!</h2>
            `

            res.innerHTML += `
                <h1>Com a Kaldi Solutions</h1>
                <h2> Projeção de safra do negócio </h2>
                    Com o nosso apoio, você senhor(a) ${nome} conseguirá reduzir a perda de produtividade significativamente, potencializando um aumento de <b>${margemPerdaS.toFixed(1)}%</b> que atualmente equivale cerca de <b>R$ ${prejuizoS.toFixed(2)}</b>
            `
        } else {
            res.innerHTML += `         
                <h1>Sem a Kaldi Solutions</h1>       
                <h2> Projeção de safra </h2>
                        Olá ${nome}, sua empresa ${empresa} ao vender ${qtdSacaS} sacas 
                        equivalentes a ${sacaKgS}kg por R$ ${valorSacaS.toFixed(2)} cada,  
                        nessa safra você teve uma receita de <b>R$ ${lucroAtualS.toFixed(2)}</b>.
                        <br> Você sabia que hoje você deixa de ganhar cerca de <b>R$ ${prejuizoS.toFixed(2)}</b> em sua produção.
            `
            res.innerHTML += `
                <h2> Projeção de sua safra para anos futuros</h2>
                <ul>
                    <li>Em um ano você terá uma perda de aproximadamente <b>R$ ${prejuizoS.toFixed(2)}</b></li>
                    <li>Em três anos você terá uma perda de aproximadamente <b>R$ ${pAno3.toFixed(2)}</b></li>
                    <li>Em cinco anos você terá uma perda de aproximadamente <b>R$ ${pAno5.toFixed(2)}</b></li>
                    <li>Em dez anos você terá uma perda de aproximadamente <b>R$ ${pAno10.toFixed(2)}</b></li>
                </ul>
                <h2 style="color: red;"> ...Você está deixando de lucrar!</h2>
            `
            res.innerHTML += `
                <h1>Com a Kaldi Solutions</h1>
                <h2> Projeção de safra do negócio</h2>
                    Com o nosso apoio, você senhor(a) ${nome} conseguirá reduzir a perda de produtividade de sua empresa ${empresa} significativamente, <br>potencializando um aumento de <b>${margemPerdaS.toFixed(1)}%</b> que atualmente equivale cerca de <b>R$ ${prejuizoS.toFixed(2)}</b>
            `
        }

        res.innerHTML += `<br><br>
                        <span style="display: flex; justify-content: center; width: 65%; margin: auto">
                            Enviamos um email para ${email} contendo mais informações a respeito de seu caso juntamente de canais de comunicação caso queira entrar em contato conosco para utilizar nossos produtos.
                        </span>
        `
    }
</script>
