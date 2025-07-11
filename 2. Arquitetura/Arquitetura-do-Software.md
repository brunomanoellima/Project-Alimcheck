# Escolha do Padrão Arquitetural

| **Padrão Arquitetural** | **Justificativa** |
|----------------------|-------------------------------|
| **Cliente/Servidor (REST)** | O sistema segue uma arquitetura baseada em comunicação via API REST, onde o cliente (aplicativo Android) consome recursos expostos pelo servidor backend. Isso garante uma separação clara entre frontend (App Android) e backend (API REST), com protocolos HTTP para comunicação.

# Tech Stack Map

![Tech-stack-map](Anexo-Arquitetura/Tech-stack-map.jpg)

| **Camada** | **Tecnologia** | **Justificativa** |
|------------|-----------------|-------------------|
| **Backend** | Node.js + Express | Tecnologias leves e com grande comunidade para construção rápida de APIs REST. Fácil integração com banco de dados e serviços externos como Firebase. |
| **Frontend** | Android (Java/Kotlin), Google Maps SDK, Retrofit/Volley | 	**Java/Kotlin**: Linguagens padrão para desenvolvimento Android nativo. **Google Maps SDK**: Necessário para exibir localização dos estabelecimentos. **Retrofit/Volley**: Bibliotecas populares para consumir APIs REST de forma eficiente. |
| **Banco de Dados** | PostgreSQL (Railway) | Banco de dados relacional robusto, de código aberto, com suporte a consultas complexas e alta escalabilidade. |
| **Autenticação** | Firebase Authentication | Solução pronta para autenticação com suporte a login por email, senha e redes sociais. Reduz complexidade no backend. |
| **Notificações Push** | Firebase Cloud Messaging | Plataforma gratuita e confiável para envio de notificações push para dispositivos Android. |
| **Infraestrutura / Deploy** | Railway / Render / Heroku | Plataformas simples e gratuitas (com planos de estudante) para deploy rápido de aplicações Node.js e bancos de dados PostgreSQL. |
| **Gerenciamento de Projeto** | GitHub Projects + Notion | Para organizar tarefas de desenvolvimento. Notion: Para documentação interna e acompanhamento de progresso. |

# Modelo C4 

## Diagrama de Contexto

![Diagrama-de-Contexto](Anexo-Arquitetura/Modelo_C4.drawio.png)

## Diagrama de Conteiners

![Diagrama-de-Conteiners](Anexo-Arquitetura/Conteiners.drawio.png)

## Diagrama de Componentes

![Diagrama-de-Componentes](Anexo-Arquitetura/Componentes.drawio.png)

## Diagrama UML

![Diagrama-UML](Anexo-Arquitetura/UML.drawio.png)

# Rastreabilidade com Histórias de Usuários

| **História de Usuário**                                    | **Componentes / Serviços Envolvidos (exatos dos seus diagramas)**                                       | **Diagramas de Referência**                                      |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **H1 - Avaliar estabelecimentos**                          | Controle de avaliações, Serviço de scanner de palavras proibidas, Banco de dados                        | Diagrama de Componentes Alimentar, Modelo de Classes, Containers |
| **H2 - Consultar avaliações e dados de higiene**           | Controle de avaliações, MapaEstabelecimentos, Banco de dados                                            | Modelo de Classes, Containers, Componentes                       |
| **H3 - Registrar denúncias**                               | Controlador de Relatórios/Denúncias, Serviço de scanner de palavras proibidas, Banco de dados           | Modelo de Classes, Diagrama de Componentes, Containers           |
| **H4 - Receber alertas de locais com problemas**           | AlertService, Firebase, Banco de dados                                                                  | Containers, Componentes                                          |
| **H5 - Receber recomendações personalizadas**              | Serviços de recomendação, Controle de avaliações, Banco de dados                                        | Containers, Componentes                                          |
| **H6 - Excluir minha conta**                               | Controlador de usuários, Firebase Auth, Banco de dados                                                  | Containers, Componentes                                          |
| **H7 - Ver mapa com estabelecimentos**                     | MapaEstabelecimentos, EstabelecimentoController, LocationService, Google Maps SDK, Banco de dados       | Modelo de Classes, Containers, Componentes                       |
| **H8 - Filtrar estabelecimentos**                          | EstabelecimentoController, FilterService, MapaEstabelecimentos, Banco de dados                          | Modelo de Classes, Componentes                                   |
| **H9 - Atualizar perfil do estabelecimento**               | Controlador de Estabelecimentos, Banco de dados                                                         | Modelo de Classes, Componentes                                   |
| **H10 - Cadastrar estabelecimento**                        | Controlador de Estabelecimentos, Banco de dados                                                         | Modelo de Classes, Componentes                                   |
| **H11 - Moderação de relatos e avaliações**                | Controle de moderação, Serviço de scanner de palavras proibidas, Banco de dados                         | Modelo de Classes, Componentes                                   |
| **H12 - Histórico de ações de usuários**                   | UserActivityService (ou equivalente), Controle de moderação, Banco de dados                             | Modelo de Classes, Componentes                                   |
| **H13 - Gerar alertas de comunidade**                      | AlertService, Banco de dados                                                                            | Modelo de Classes, Componentes                                   |
| **H14 - Validar textos ofensivos (comentários/denúncias)** | Serviço de scanner de palavras proibidas, Controle de avaliações, Controle de moderação, Banco de dados | Modelo de Classes, Componentes                                   |
| **H15 - Monitorar usuários e avaliações**                  | Controle de moderação, Controlador de usuários, Banco de dados                                          | Modelo de Classes, Componentes                                   |
| **H16 - Consultar e gerenciar estabelecimentos**           | Controlador de Estabelecimentos, Banco de dados                                                         | Modelo de Classes, Componentes                                   |

