# Estiliza-o-e-Leiautes
Desenvolvimento Front-end para Web

Objetivos

•
Dominar a sintaxe CSS3 e suas propriedades fundamentais;

•
Compreender o funcionamento de seletores e a organização modular de estilos;

•
Aplicar técnicas avançadas de layout com Flexbox e Grid;

•
Desenvolver habilidades especializadas na estilização de menus, botões e formulários;

•
Explorar pseudo-classes e pseudo-elementos que adicionam interatividade e sofisticação às suas interfaces.




<meu-projeto>

<index.html>

<css>
        </style.css>
<js>
   <main.js>

<imagens>
      <logo.png>
        <foto.jpg>
            
<sons>
   <click.mp3>

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Bem-vindo(a)!</title>
  <style>
    :root {
      --cor-primaria: #c1bfea;
      --cor-secundaria: #f0f0f0;
      --cor-texto: #333;
      --espacamento: 10px;
      --radius: 10px;
      --cor-erro: #ff4c4c;
    }

    body {
      font-family: Arial, Helvetica, sans-serif;
      background: linear-gradient(135deg, #b2afea, #b19cd9);
      color: var(--cor-texto);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      animation: slideFadeIn 0.8s ease-out;
      margin: 0;
    }

    header {
      text-align: center;
      margin-bottom: 20px;
      animation: slideFadeIn 0.8s ease-out 0.1s both;
    }

    .logo {
      width: 80px;
      border-radius: 50%;
    }

    h1 {
      color: white;
    }

    .form-container {
      background: rgba(255, 255, 255, 0.2);
      padding: 20px;
      border-radius: var(--radius);
      box-shadow: 0 4px 15px rgba(0,0,0,0.1);
      text-align: center;
    }

    input {
      padding: var(--espacamento);
      margin-top: 10px;
      border: none;
      border-radius: var(--radius);
      width: 80%;
    }

    input.invalido {
      border: 2px solid var(--cor-erro);
    }

    button {
      margin-top: 15px;
      padding: 10px 20px;
      border: none;
      border-radius: var(--radius);
      background-color: var(--cor-primaria);
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: linear-gradient(135deg, #6c63ff, #9a8cff);
      transform: translateY(-2px);
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    button:active {
      animation: pulse 0.3s ease;
    }

    #mensagem {
      font-size: 1.4em;
      margin-top: 20px;
      color: white;
    }

    .mensagem-erro {
      color: var(--cor-erro);
    }

    .imagem-container img {
      border-radius: var(--radius);
      margin-top: 20px;
      max-width: 100%;
      height: auto;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    }

    footer {
      margin-top: 40px;
      font-size: 0.9em;
      color: #eee;
      animation: slideFadeIn 0.8s ease-out 0.5s both;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .mensagem-animada { animation: fadeIn 0.8s ease forwards; }

    @keyframes pulse {
      0% { transform: scale(1); box-shadow: 0 0 0 rgba(172, 168, 235, 0.7); }
      50% { transform: scale(1.05); box-shadow: 0 0 20px rgba(108, 99, 255, 0.6); }
      100% { transform: scale(1); box-shadow: 0 0 0 rgba(108, 99, 255, 0.7); }
    }

    @keyframes slideFadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>
  <header>
    <img src="imagens/logo.png" alt="Logo" class="logo">
    <h1>Projeto Modular JS</h1>
  </header>

  <main>
    <section class="form-container">
      <label for="nome">Digite seu nome:</label>
      <input type="text" id="nome" placeholder="Seu nome aqui..." />
      <button id="btn">Mostrar mensagem</button>
    </section>

    <section class="imagem-container">
      <img src="imagens/foto.jpg" alt="Descrição da imagem" width="300" height="200">
    </section>

    <section class="mensagem-container">
      <p id="mensagem"></p>
    </section>
  </main>

  <footer>
    <p>Feito por Valinéia Dias Ingre Florenzano 💻</p>
  </footer>

  <script>
    function formatarNome(nome) {
      return nome.trim().charAt(0).toUpperCase() + nome.slice(1).toLowerCase();
    }

    function mostrarMensagem(nome) {
      const mensagemElemento = document.querySelector('#mensagem');

      if (!nome || nome.trim().length < 2) {
        mensagemElemento.textContent = "Por favor, digite um nome válido!";
        mensagemElemento.classList.add('mensagem-erro');
        mensagemElemento.classList.remove('mensagem-animada');

        const input = document.querySelector('#nome');
        input.classList.add('invalido');
        input.focus();
        return;
      }

      const mensagem = `Bem-vindo(a), ${formatarNome(nome)}!`;

      mensagemElemento.classList.remove('mensagem-erro', 'mensagem-animada');
      mensagemElemento.textContent = mensagem;
      void mensagemElemento.offsetWidth; // reinicia animação
      mensagemElemento.classList.add('mensagem-animada');

      document.querySelector('#nome').classList.remove('invalido');
    }

    document.addEventListener('DOMContentLoaded', () => {
      const botao = document.querySelector('#btn');
      let somClique;

      botao.addEventListener('click', () => {
        const nome = document.querySelector('#nome').value;

        if (!somClique) {
          somClique = new Audio('sons/click.mp3');
        }

        somClique.currentTime = 0;
        somClique.play().catch(err => console.warn('Som bloqueado pelo navegador:', err));

        mostrarMensagem(nome);
      });
    });
  </script>
</body>
</html>
