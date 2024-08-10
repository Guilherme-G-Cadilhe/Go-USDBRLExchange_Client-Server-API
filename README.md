# Projeto: Consulta e Armazenamento de Cotação do Dólar

### Tema do Projeto

Desenvolvimento de um sistema em Go para consultar e armazenar a cotação do dólar em tempo real, utilizando APIs, banco de dados, manipulação de arquivos, e gestão de contextos em Go, aplicando as melhores práticas de desenvolvimento para garantir robustez e segurança.

### Descrição do Projeto

Este repositório contém dois programas em Go (client.go e server.go) que trabalham juntos para pegar a cotação do dólar e salvar essa informação. O projeto demonstra habilidades avançadas em desenvolvimento com Go utilizando as seguintes boas práticas:

- **Consumo de API:** O `server.go` consulta a cotação do dólar na [AwesomeAPI](https://economia.awesomeapi.com.br/json/last/USD-BRL) e retorna apenas o valor que interessa (`bid`). O tempo de resposta da requisição HTTP é gerenciada com um timeout a 200ms para garantir que tudo aconteça rapidamente.

- **Gerenciamento de Tempo (Timeouts):** Usamos o pacote `context` para definir limites de tempo em diferentes partes do sistema. com 200ms para a requisição à API de câmbio, 10ms para operações de banco de dados e 300ms para o cliente obter a resposta do servidor.
  Em caso de timeout, logs de erros detalhados são gerados, facilitando o rastreamento de problemas.

- **Salvando Dados:** Cada cotação que o `server.go` recebe é armazenada em um banco de dados SQLite. Utilizando SQL preparado (PrepareContext) para prevenir SQL injection e garantir maior segurança.

- **Comunicação HTTP:** O `client.go` faz uma requisição ao `server.go`, pega a cotação e salva no arquivo `cotacao.txt`. Por padrão, ele sobrescreve o arquivo, mas o código pode ser ajustado para adicionar novas cotações em linhas separadas, se necessário.

- **Tratamento de Erros:** Implementamos funções específicas para lidar com erros de tempo limite e problemas HTTP. Isso garante que o sistema seja robusto e que mensagens de erro claras sejam enviadas ao usuário.

- **Logs e Monitoramento:** Todos os erros críticos, como falhas de tempo limite, são registrados em logs. Isso facilita bastante na hora de identificar e corrigir problemas.
