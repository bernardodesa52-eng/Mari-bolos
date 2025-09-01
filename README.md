<!DOCTYPE html><html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mari Bolos</title>
<style>
  body { font-family: Arial, sans-serif; background-color: #fff0f5; color: #333; margin:0; padding:0; text-align:center; }
  header { background-color: #ffb6c1; padding: 20px; }
  header h1 { margin: 0; color: #fff; }
  .cardapio { display: flex; flex-wrap: wrap; justify-content: center; padding: 20px; }
  .produto { background-color: #fff; border-radius: 15px; padding: 15px; margin: 10px; width: 200px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
  .produto img { width: 100%; border-radius: 10px; }
  .produto h3 { margin: 10px 0 5px; }
  .produto p { margin: 5px 0; color: #ff1493; font-weight: bold; }
  .btn { display:inline-block; padding: 10px 15px; background-color:#ff1493; color:white; border-radius:10px; text-decoration:none; margin-top:5px; }
  .pix { margin-top:20px; }
</style>
</head>
<body><header>
  <h1>Mari Bolos 🍰</h1>
  <p>Delícias de confeitaria direto pra você!</p>
</header><div class="cardapio" id="cardapio">
  <!-- Os produtos vão ser carregados aqui automaticamente -->
</div><div class="pix">
  <h3>Pagamento via Pix</h3>
  <p>Chave Pix: 21965247403</p>
  <div id="qrcode"></div>
</div><script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script><script>
// Lista de produtos - basta editar essa lista para alterar o cardápio
let produtos = [
  { nome: "Bolo de Aipim", preco: 8, imagem: "https://via.placeholder.com/200", disponivel: true },
  { nome: "Brigadeiro Gourmet", preco: 3, imagem: "https://via.placeholder.com/200", disponivel: true }
];

const cardapio = document.getElementById('cardapio');

function atualizarCardapio() {
  cardapio.innerHTML = '';
  produtos.forEach((produto, index) => {
    if(produto.disponivel) {
      let div = document.createElement('div');
      div.className = 'produto';
      div.innerHTML = `
        <img src="${produto.imagem}" alt="${produto.nome}">
        <h3>${produto.nome}</h3>
        <p>R$ ${produto.preco}</p>
        <a class="btn" href="https://wa.me/5521965247403?text=Olá%20quero%20pedir%20${encodeURIComponent(produto.nome)}">Pedir via WhatsApp</a>
      `;
      cardapio.appendChild(div);
    }
  });
}

atualizarCardapio();

// Gerar QR Code Pix
QRCode.toCanvas(document.getElementById('qrcode'), '21965247403', function (error) {
  if (error) console.error(error);
});
</script></body>
</html>
