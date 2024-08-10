<h1 align="center">
  Consulta e Armazenamento de Cotação do Dólar
</h1>

<p align="center">
  <a href="#about">Sobre</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#features">Features</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#technologies">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#installation">Instalação</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#Learned">O que eu aprendi?</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#author">Author</a>
</p>

---

<h2 id="about" align="center">📌 Sobre </h2>

Desenvolvimento de um sistema em Go para consultar e armazenar a cotação do dólar em tempo real, utilizando APIs, banco de dados, manipulação de arquivos, e gestão de contextos em Go, aplicando as melhores práticas de desenvolvimento para garantir robustez e segurança.

## Descrição do Projeto
Este repositório contém dois programas em Go (client.go e server.go) que trabalham juntos para pegar a cotação do dólar e salvar essa informação. Praticando habilidades avançadas 
 com Go.


<h2 id="features" align="center">⚙️ Features</h2>

- **Consumo de API:** O `server.go` consulta a cotação do dólar na [AwesomeAPI](https://economia.awesomeapi.com.br/json/last/USD-BRL) e retorna apenas o valor que interessa (`bid`). O tempo de resposta da requisição HTTP é gerenciada com um timeout a 200ms para garantir que tudo aconteça rapidamente.

- **Gerenciamento de Tempo (Timeouts):** Foi utilizado o pacote `context` para definir limites de tempo em diferentes partes do sistema. com 200ms para a requisição à API de câmbio, 10ms para operações de banco de dados e 300ms para o cliente obter a resposta do servidor.
  Em caso de timeout, logs de erros detalhados são gerados, facilitando o rastreamento de problemas.

- **Salvando Dados:** Cada cotação que o `server.go` recebe é armazenada em um banco de dados SQLite. Utilizando SQL preparado (PrepareContext) para prevenir SQL injection e garantir maior segurança.

- **Comunicação HTTP:** O `client.go` faz uma requisição ao `server.go`, pega a cotação e salva no arquivo `cotacao.txt`. Por padrão, ele sobrescreve o arquivo, mas o código pode ser ajustado para adicionar novas cotações em linhas separadas, se necessário.

- **Tratamento de Erros:** Implementamos funções específicas para lidar com erros de tempo limite e problemas HTTP. Isso garante que o sistema seja robusto e que mensagens de erro claras sejam enviadas ao usuário.

- **Logs e Monitoramento:** Todos os erros críticos, como falhas de tempo limite, são registrados em logs. Isso facilita bastante na hora de identificar e corrigir problemas.

<h2 id="technologies" align="center">💻 Tecnologias</h2>

Neste projeto foram utilizadas as seguintes tecnologias:

- **Go** - A espinha dorsal do sistema, lidando com tudo, desde solicitações HTTP até interações de banco de dados e criação de arquivos.
- **SQLite** - Um banco de dados leve embutido para armazenar dados.


<h2 id="installation" align="center">📦 Instalação</h2>

Para inicializar, faça fork deste repositorio e rode os comandos:

1. Instale o GO e CGO
2. Ligue o servidor
`go run server.go`
3. Execute o Client
`go run client.go`
4. Se tiver algum problema para inicializar, tente executar `go mod tidy`
<br>

<h2 id="Learned" align="center">☕ O que eu aprendi?</h2>

> Este projeto me permitiu aprofundar meus conhecimentos técnicos em Go, especialmente na gestão de Contextos e Timeouts para garantir operações seguras e eficientes. Aprendi a importância de limitar tempos de execução em diferentes camadas da aplicação, evitando gargalos e melhorando a performance geral.<br>
> Tive a oportunidade de trabalhar com SQLite, reforçando minhas habilidades em manipulação de bancos de dados e segurança com o uso de SQL preparado para evitar injeção de SQL.<br>
> Além disso, este projeto me ajudou a melhorar minha compreensão sobre comunicação entre sistemas via HTTP, desde a consulta de APIs até o tratamento de erros e logging detalhado utilizando o Go.<br>
> O desenvolvimento também reforçou a importância de manter o código organizado e limpo, seguindo as melhores práticas de programação, o que facilita a manutenção e escalabilidade do sistema.<br>


<h2 id="author">Autor</h2>

Feito com 💜 e dedicação por mim **Guilherme G Cadilhe** Aka: **Bobnini**. <br>

<h2>Agradecimentos</h2>

- Pós-graduação Lato Sensu, Desenvolvimento Avançado em Golang - Goexpert


