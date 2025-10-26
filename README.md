<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Teste QR Code Sandbox</title>
</head>
<body>
  <h1>Teste de Pagamento QR Code (simulado)</h1>

  <button id="gerarQR">Gerar QR Code</button>
  <div id="qrArea" style="margin-top:20px;"></div>
  <p id="status"></p>

  <script>
    const btn = document.getElementById('gerarQR');
    const qrArea = document.getElementById('qrArea');
    const status = document.getElementById('status');

    btn.onclick = () => {
      // Simula payload do QR
      const payload = 'PIX:00020126360014BR.GOV.BCB.PIX0114+55119999999952040000530398654041.005802BR5913Teste User6009Sao Paulo61080540900062070503***63041D3D';

      // Gera QR Code com API do Google Chart (mais fácil)
      const qrImg = document.createElement('img');
      qrImg.src = `https://chart.googleapis.com/chart?cht=qr&chs=250x250&chl=${encodeURIComponent(payload)}`;
      qrImg.alt = 'QR Code';
      qrArea.innerHTML = '';
      qrArea.appendChild(qrImg);

      status.textContent = 'Aguardando pagamento...';

      // Simula pagamento automático após 5 segundos
      setTimeout(() => {
        status.textContent = 'Pagamento confirmado! ✅ (simulado)';
      }, 5000);
    };
  </script>
</body>
</html>
