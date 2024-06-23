# Gerador de Senhas

Este é um gerador de senhas simples, desenvolvido com HTML, CSS e JavaScript, que permite ao usuário criar senhas seguras de forma fácil e rápida. A interface intuitiva permite definir o tamanho da senha e copiar a senha gerada com um único clique.

## Visão Geral

### Funcionalidades
- Definir o comprimento da senha (entre 5 e 25 caracteres).
- Gerar senhas aleatórias com caracteres alfanuméricos e símbolos.
- Copiar a senha gerada para a área de transferência com um clique.

## Tecnologias Utilizadas
- **HTML**: Estrutura da aplicação.
- **CSS**: Estilização e layout responsivo.
- **JavaScript**: Lógica para geração e cópia de senhas.

## Estrutura do Projeto

### HTML
```html
<!DOCTYPE html>
<html lang="ptbr">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="keywords" content="Gerador de Senhas, password generator" />
    <link rel="stylesheet" href="style.css" />
    <title>Gerador de Senhas</title>
</head>
<body>
    <h1>Gerador de Senhas</h1>
    <main class="container-input">
        <span>Tamanho <span id="valor"></span> caracteres</span>
        <input
            type="range"
            id="slider"
            class="slider"
            min="5"
            max="25"
            value="15"
        />
        <button id="button" class="button-cta" onclick="generatePassword()">
            Gerar senha
        </button>
    </main>
    <div
        id="container-password"
        onclick="copyPassword()"
        class="container-password hide"
    >
        <span class="title">Sua senha foi gerada:</span>
        <span id="password" class="password">1234</span>
        <span class="tooltip">Clique na senha para copiar. 👆</span>
    </div>
    <footer>
        <p>Desenvolvido por Dimello! :)</p>
    </footer>
    <script src="script.js"></script>
</body>
</html>
```

### CSS
```css
* {
    font-family: sans-serif;
    width: 100%;
    margin: 0 auto;
    box-sizing: border-box;
}

body {
    background-color: #181818;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

h1 {
    display: flex;
    justify-content: center;
    margin-bottom: 24px;
    color: white;
    font-family: monospace;
    font-size: 60px;
}

.container-input {
    max-width: 480px;
    margin: 14px 0px;
}

.container-input span {
    color: white;
    font-size: 22px;
}

.slider {
    appearance: none;
    width: 100%;
    border-radius: 5px;
    background: #dfdfdf;
    height: 18px;
    outline: none;
    margin-top: 8px;
}

.button-cta {
    height: 40px;
    background-color: #3eb72b;
    border: 0;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 40px;
    color: white;
    font-weight: bold;
    font-size: 18px;
}

.container-password {
    max-width: 480px;
    margin: 14px 0;
    display: flex;
    align-items: center;
    flex-direction: column;
    cursor: pointer;
}

.title {
    text-align: center;
    color: white;
    font-size: 28px;
    margin-top: 24px;
    margin-bottom: 8px;
}

.password {
    height: 60px;
    background-color: rgba(0, 0, 0, 0.40);
    border-radius: 4px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    border: 1px solid #313131;
    transition: transform 0.5s;
}

.password:hover {
    transform: scale(1.05);
}

.tooltip {
    color: white;
    position: relative;
    top: 20px;
    padding: 6px 8px;
    background: rgb(15, 15, 15);
    text-align: center;
    font-size: 16px;
    border-radius: 6px;
    visibility: hidden;
    opacity: 0;
    transition: all 0.5s ease-in-out;
}

.container-password:hover .tooltip {
    visibility: visible;
    bottom: 50px;
    opacity: 1;
}

p {
    display: flex;
    justify-content: center;
    align-items: center;
    padding-top: 100px;
    color: white;
}

.hide {
    display: none;
}
```

### JavaScript
```javascript
let sliderElemnet = document.querySelector("#slider");
let buttonElement = document.querySelector("#button");
let sizePassword = document.querySelector("#valor");
let password = document.querySelector("#password");
let containerPassword = document.querySelector("#container-password");
let charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%&";
let novaSenha = "";

sizePassword.innerHTML = sliderElemnet.value;
slider.oninput = function(){
    sizePassword.innerHTML = this.value;
}

function generatePassword(){
    let pass = "";
    for(let i = 0, n = charset.length; i < sliderElemnet.value; ++i){
        pass += charset.charAt(Math.floor(Math.random() * n));
    }
    containerPassword.classList.remove("hide");
    password.innerHTML = pass;
    novaSenha = pass;
}

function copyPassword(){
    navigator.clipboard.writeText(novaSenha).then(() => alert("Senha copiada com sucesso!"));
}
```

## Como Usar

1. **Ajustar o comprimento da senha**: Utilize o controle deslizante para selecionar o tamanho desejado para a senha.
2. **Gerar a senha**: Clique no botão "Gerar senha".
3. **Copiar a senha**: Clique na senha gerada para copiá-la automaticamente para a área de transferência. Você receberá uma notificação confirmando a cópia.

## Contribuição
Para contribuir com este projeto, faça um fork do repositório, crie um branch com suas alterações e envie um pull request para revisão.

## Autor
Desenvolvido por D1MELLO! :)

## Licença
Este projeto está licenciado sob a [MIT License](LICENSE).
