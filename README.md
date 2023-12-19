<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anúncios com Contagem Regressiva</title>
</head>
<body>

    <!-- Conteúdo da Página -->
    <div id="content" style="display: none;">
        <h1>Seu Conteúdo Aqui</h1>
        <p>Texto interessante ou informações relevantes.</p>
    </div>

    <!-- Anúncios com Contagem Regressiva -->
    <div id="ads">
        <p>Anúncio Aqui</p>
        <p>Contagem Regressiva: <span id="countdown">15</span> segundos</p>
        <p id="reloadCount">Esta página foi recarregada <span id="reloadTimes">0</span> vezes.</p>
    </div>

    <script>
        // Contagem regressiva de 15 segundos
        let seconds = 15;

        // Recuperar o contador de recarregamentos do armazenamento local
        let reloadCount = parseInt(localStorage.getItem('reloadCount')) || 0;

        function updateReloadCount() {
            // Atualizar a exibição do contador
            document.getElementById('reloadTimes').innerText = reloadCount;
            // Salvar o contador no armazenamento local
            localStorage.setItem('reloadCount', reloadCount);
        }

        function countdown() {
            if (seconds > 0) {
                seconds--;
                document.getElementById('countdown').innerText = seconds;
                setTimeout(countdown, 1000);
            } else {
                // Incrementar o contador de recarregamentos antes de ocultar a área de anúncios
                reloadCount++;
                updateReloadCount();

                // Ocultar a área de anúncios após a contagem regressiva
                document.getElementById('ads').style.display = 'none';
                // Exibir o conteúdo principal
                document.getElementById('content').style.display = 'block';

                // Redirecionar a página após 15 segundos
                setTimeout(function() {
                    window.location.reload();
                }, 5000); // Aguarda 5 segundos antes de recarregar a página (você pode ajustar esse valor)
            }
        }

        // Iniciar a contagem regressiva quando a página carregar
        window.onload = function() {
            countdown();
            // Atualizar o contador exibido na carga inicial
            updateReloadCount();
        };
    </script>

</body>
</html>
