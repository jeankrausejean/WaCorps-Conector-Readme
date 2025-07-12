Changelog - Conector WaCorps

Versão: 1.1.0
Data: 11/07/2025
Assunto: Implementação do Contador de Atualização do QR Code

---
### Adicionado
---

- **[HTML] Bloco do Contador**: Um novo bloco de HTML com o ID `#countdownArea` foi adicionado logo acima da área do QR Code (`#qrArea`). Este bloco contém:
  - Um `<div>` para a barra de progresso (`#progressFill` dentro de `.progress-bar`).
  - Um `<div>` para exibir o texto do tempo restante (`#countdownText`).

- **[JavaScript] Variável de Controle do Contador**: Foi adicionada uma variável global `let countdownInterval = null;` para armazenar a referência do timer e permitir que ele seja interrompido.

- **[JavaScript] Função `startCountdown(duration)`**: Uma nova função foi criada para:
  - Iniciar um timer de 40 segundos.
  - Exibir a área do contador na interface.
  - A cada segundo, atualizar a barra de progresso e o texto do tempo.
  - Ao chegar a zero, chamar automaticamente a função `connectInstance()` para gerar um novo QR Code.

- **[JavaScript] Função `stopCountdown()`**: Uma nova função foi criada para:
  - Parar qualquer contador que esteja em execução (`clearInterval`).
  - Ocultar a área do contador da interface.

---
### Modificado
---

- **[JavaScript] Função `clearFeedback()`**: Modificada para chamar `stopCountdown()` no início. Isso garante que, sempre que a tela for limpa para uma nova ação, o contador de QR Code seja interrompido e ocultado.

- **[JavaScript] Função `connectInstance()`**: Modificada para, após receber e exibir um QR Code com sucesso, chamar a função `startCountdown()` para iniciar a contagem regressiva de atualização.

- **[JavaScript] Função `createInstance()`**: Modificada para, caso a criação da instância retorne um QR Code, chamar a função `startCountdown()` para iniciar a contagem.

- **[JavaScript] Função `restartInstance()`**: Modificada para também chamar `startCountdown()` caso a reinicialização da instância resulte em um novo QR Code para ser escaneado.

---
### Estilo (CSS)
---

- **[CSS] Novas Regras de Estilo**: Foram adicionadas ao CSS as regras para os novos elementos:
  - `#countdownArea`: Estiliza o contêiner do contador.
  - `.progress-bar`: Estiliza a base da barra de progresso.
  - `.progress-fill`: Estiliza o preenchimento da barra de progresso, com uma transição suave.
  - `.countdown-timer`: Estiliza o texto que exibe o tempo restante.
  - As cores utilizadas foram adaptadas para seguir a identidade visual existente do conector.
