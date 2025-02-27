# Nome Secreto

Este projeto permite que os usuários insiram nomes de amigos e realizem um sorteio aleatório para determinar quem será o "amigo secreto".

## Funcionalidades

- Adicionar nomes de amigos à lista através de um campo de texto e botão "Adicionar".
- Exibir a lista de nomes adicionados na página.
- Realizar um sorteio aleatório ao clicar no botão "Sortear Amigo".
- Exibir o resultado do sorteio na página.

## Como Usar

1. Insira o nome de um amigo no campo de texto.
2. Clique no botão "Adicionar" para incluir o nome na lista.
3. Clique no botão "Sortear Amigo" para realizar o sorteio e ver o nome do amigo secreto sorteado.

## Código

Aqui está uma visão geral do código em `app.js`:

```javascript
let amigos = [];

function adicionarAmigo() {
    const input = document.getElementById('amigo');
    const nome = input.value.trim();
    
    if (nome) {
        amigos.push(nome);
        atualizarLista();
        input.value = '';
        input.focus();
    }
}

function atualizarLista() {
    const listaAmigos = document.getElementById('listaAmigos');
    listaAmigos.innerHTML = '';
    
    amigos.forEach(amigo => {
        const li = document.createElement('li');
        li.textContent = amigo;
        listaAmigos.appendChild(li);
    });
}

function sortearAmigo() {
    if (amigos.length === 0) {
        alert('Adicione alguns nomes primeiro!');
        return;
    }
    
    const indiceSorteado = Math.floor(Math.random() * amigos.length);
    const resultado = document.getElementById('resultado');
    resultado.innerHTML = `<li>O amigo secreto sorteado é: ${amigos[indiceSorteado]}</li>`;
}

