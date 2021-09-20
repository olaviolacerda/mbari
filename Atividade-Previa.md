# Atividade Pratica Previa - ARI

- [Atividade Pratica Previa - ARI](#atividade-pratica-previa---ari)
  - [5. Fazer uma análise crítica sobre a aplicação monolítica](#5-fazer-uma-análise-crítica-sobre-a-aplicação-monolítica)
    - [Analise Critica](#analise-critica)
      - [PS.: Meu teclado possui alguns problemas de acentuacao, espero que entenda.](#ps-meu-teclado-possui-alguns-problemas-de-acentuacao-espero-que-entenda)

> Disciplina: `ARI – Arquitetura de Integração`
>
> Aluno: `OLAVIO LACERDA BUENO JUNIOR`
>

## 5. Fazer uma análise crítica sobre a aplicação monolítica

destacando o entendimento sobre o seu funcionamento,
quais seriam os benefícios e/ou problemas dessa aplicação
em uma arquitetura de integração com clientes.

### Analise Critica

Nesse exemplo, temos de cara um problema que pode levar a grande dificuldade no futuro: acoplamento. Temos um banco de dados contendo todos os dados da aplicacao, coisa que poderiamos ter de forma bem mais controlada caso estivessemos aqui falando de Microsservicos. Temos aqui um servico que lida com 4 dominios de negocio: cliente, endereco, fatura e instalacao. O banco de dados possuira uma entrada longa de dados para cada um desses, tendo relacionamentos que poderiam ser facilmente adaptados para requisicao-resposta, caso fosse utilizado um sistema de microsservicos. Pensamos desse modo, caso o endereco pare de funcionar, nao podera mais ser criado cliente nem mesmo solicitar instalacao, ao meu ver, ta ai um dos maiores Red Flags para o uso de aplicacao monolitica para esse tipo de sistema. Precisamos de resiliencia, e dessa forma aqui, ou funciona tudo ou funciona nada. Em um sistema de microsservicos poderiamos ter um dominio de Cliente, onde teriamos informacoes dos mesmos e algum subdominio de endereco; Um dominio de instalacoes, onde teriamos controle de fluxos, request assincronas e um suporte muito maior para notificacoes de usuario, reservas e agendamentos; Outro dominio seria de fatura, onde lidariamos com dados "financeiros", precisariamos ter bastante uso de eventos, para processamento de pagamentos e etc, o que nesse modelo, poderia se prejudicar ao ter que dividir maquinas e recursos com as demais camadas da aplicacao. No modelo de MS temos como fazer o balanceamento das aplicacoes, ajudando tanto no desenvolvimento como escalabilidade, resiliencia e uso de recursos. 

#### PS.: Meu teclado possui alguns problemas de acentuacao, espero que entenda.

Link do codigo: [https://github.com/olaviolacerda/mbari](https://github.com/olaviolacerda/mbari)