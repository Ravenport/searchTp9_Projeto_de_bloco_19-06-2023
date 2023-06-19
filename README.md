js ----------------------------------------------------------------------------------------------
const selectBox = document.querySelector('.selectBox');
const selectInput = selectBox.querySelector('.select');
const lista = selectBox.querySelector('.list');
let count = 0;
const opcoes = [
  'Carnes Exóticas',
  'Carnes Tradicionais',
  'Ambas',
]
let opcoesAlt = opcoes;

selectInput.onfocus = () => {
  //retorna os itens que devem aparecer como opções do select
  let opcoesLista = opcoesAlt.map((data) => {
    if (count === 0) {
      count++;
      return `<li class="first">${data}</li>`;
    } else {
      count++;
      return `<li>${data}</li>`;
    }
  });

  selectBox.classList.add('active');
  mostrarLista(opcoesLista);

  let listaTotal = lista.querySelectorAll('li');
  for (let i = 0; i < listaTotal.length; i++) {
    // faz com que todas as opções sejam selecionáveis.
    listaTotal[i].setAttribute('onMouseDown', 'select(this)');
  }
}

selectInput.onblur = () => {
  selectBox.classList.remove('active');
};

function select(el) {
  // Define o valor do input para o valor selecionado na lista
  selectInput.value = el.textContent;
  selectBox.classList.remove('active');
}

function mostrarLista(list) {
  //Coloca a lista como nodes dentro da minha lista de opções do select
  let listJoin = list.join('');
  lista.innerHTML = listJoin;
}
js ----------------------------------------------------------------------------------------------

html ----------------------------------------------------------------------------------------------
<div class="selectBox">
    <input type="text" class="select" placeholder="Selecione" />
    <div class="list"></div>
  </div>
html ----------------------------------------------------------------------------------------------

css ----------------------------------------------------------------------------------------------
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

.selectBox input {
  width: 300px;
  padding: 15px;
  font-size: 18px;
  border-radius: 10px;
  border: 2px solid black;
  margin-left: 20px;
  margin-top: 20px;
}

.selectBox .list {
  max-height: 295px;
  overflow-y: auto;
}

.selectBox .list li {
  width: 300px;
  background-color: #fc6b6b69;
  margin-left: 20px;
  padding-top: 10px;
  text-align: center;
  padding: 13px;
  display: none;
}

.first {
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.selectBox.active .list li {
  display: block;
}

.selectBox.active .list li:hover {
  background-color: #ff8585;
}
css ----------------------------------------------------------------------------------------------
