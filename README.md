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
    </div>

    <script>
        // Contagem regressiva de 15 segundos
        let seconds = 15;

        function countdown() {
            if (seconds > 0) {
                seconds--;
                document.getElementById('countdown').innerText = seconds;
                setTimeout(countdown, 1000);
            } else {
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
        window.onload = countdown;
    </script>

</body>
</html>
