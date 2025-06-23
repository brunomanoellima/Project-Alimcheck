## H1 - Como consumidor, eu gostaria de avaliar estabelecimentos de alimentação para ajudar outros usuários a escolherem locais seguros e de qualidade.

## Critérios de Aceitação:
* O usuário pode avaliar os seguintes critérios individualmente:
    * Higiene
    * Qualidade da comida
    * Atendimento
    * Tempo de espera
    * Preço justo
* Cada critério deve aceitar notas de 1 a 5.
* O campo de comentário é opcional, mas, se preenchido, deve:
    * Conter no mínimo 10 caracteres (evita comentários irrelevantes)
    * Ser validado contra uma blacklist de palavras ofensivas
    * Rejeitar comentários com linguagem ofensiva, discriminatória ou inapropriada
* O sistema deve bloquear:
    * Comentários vazios, se algum campo for obrigatório
    * Comentários com palavras ofensivas listadas na blacklist
    * Comentários com apenas emojis ou símbolos sem texto significativo
* O usuário deve receber feedback visual se uma avaliação for rejeitada, explicando o motivo.
* A interface de avaliação deve estar adaptada para dispositivos móveis e desktop.
    * Definir breakpoints claros de responsividade. Como a resolução de tela para cada dispositivo (Ex: Mobile: < 768px; Tablet: 768px - 1024px; Desktop: > 1024px)

## Regra de Negócio:
* O comentário deve conter no mínimo 10 caracteres alfanuméricos.
* Cada avaliação deve conter pelo menos um dos critérios definidos (higiene, qualidade da comida, atendimento, tempo de espera ou preço justo) com nota entre 1 e 5.
* Comentários vazios ou contendo termos ofensivos (com base em uma blacklist predefinida) são automaticamente bloqueados ou marcados para revisão.
* O sistema deve manter uma blacklist de palavras ofensivas atualizada, que deve ser verificada sempre que um novo comentário é enviado.
* Cada usuário pode avaliar o mesmo estabelecimento apenas uma vez por semana.
* Deve exibir na tentativa de nova avaliação com a mensagem: "Você já avaliou este estabelecimento nesta semana."

### Tabela de Classes de Equivalência - H1

| Condição de Entrada             | Classes Válidas                                             | Classes Inválidas                               | Classes Inválidas                              |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|-------------------------------|
| Preenchimento dos Critérios | Avaliação contém pelo menos um critério com nota (Higiene, Qualidade da comida, Atendimento, Tempo de espera, Preço justo) **(1)** | Avaliação enviada sem nenhuma nota **(2)** |
| Nota da Avaliação | A nota está entre 1 e 5 **(3)** | A nota é menor que 1 **(4)** | A nota é maior que 5 **(5)** |
| Comprimento do Comentário | Comentário tem 10 ou mais caracteres **(6)** | Comentário tem menos de 10 caracteres **(7)** | - |
| Conteúdo do Comentário | Não contém palavras da blacklist **(8)** | Contém palavras da blacklist **(9)** | - |
| Frequência de Avaliação | 1ª avaliação na semana para o estabelecimento **(10)** | Já existe avaliação na mesma semana **(11)** | - |

### Tabela de Casos de Teste - H1

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,6,8,10             | Higiene: 4, Qualidade: 5, Atendimento: 3, Tempo: 4, Preço: 5; Comentário: "Ótima experiência, recomendo!"; Primeira avaliação na semana | Avaliação registrada |
| Caso 2         | **2**,3,6,8,10         | Higiene: -, Qualidade: -, Atendimento: -, Tempo: -, Preço: -; Comentário: "Ótima experiência"; Primeira avaliação na semana | Rejeição: "Pelo menos um critério deve ser avaliado" |
| Caso 3         | 1,**4**,6,8,10         | Higiene: 0, Qualidade: 5, Atendimento: 3, Tempo: 4, Preço: 5; Comentário: "Ótima experiência"; Primeira avaliação na semana | Rejeição: "Notas devem estar entre 1 e 5" |
| Caso 4         | 1,**5**,6,8,10         | Higiene: 6, Qualidade: 5, Atendimento: 3, Tempo: 4, Preço: 5; Comentário: "Ótima experiência"; Primeira avaliação na semana | Rejeição: "Notas devem estar entre 1 e 5" |
| Caso 5         | 1,3,**7**,8,10         | Higiene: 4, Qualidade: 5, Atendimento: 3, Tempo: 4, Preço: 5; Comentário: "Bom"; Primeira avaliação na semana | Rejeição: "Comentário deve ter pelo menos 10 caracteres" |
| Caso 6         | 1,3,6,**9**,10         | Higiene: 4, Qualidade: 5, Atendimento: 3, Tempo: 4, Preço: 5; Comentário: "Serviço horrível, ofensivo"; Primeira avaliação na semana | Rejeição: "Comentário contém palavras inadequadas" |
| Caso 7         | 1,3,6,8,**11** | Higiene: 4, Qualidade: 5, Atendimento: 3, Tempo: 4, Preço: 5; Comentário: "Ótima experiência"; Já avaliado na semana | Rejeição: "Você já avaliou este estabelecimento nesta semana" |

---

## H2 - Como consumidor, eu gostaria de acessar de forma ágil informações de higiene e avaliações de estabelecimentos alimentícios para tomar decisões seguras e informadas sobre onde comer ou comprar alimentos.

## Critérios de aceitação:
* O sistema deve exibir a classificação sanitária (ex.: A, B, C) e a data da última inspeção em até 2 segundos após o acesso ao perfil do estabelecimento.
* A fonte dos dados deve estar visível e identificar claramente a origem (ex.: órgão de vigilância sanitária), com data de atualização.
* Um alerta visual deve indicar se os dados de inspeção estão desatualizados (última vistoria há mais de 12 meses).
* As avaliações devem exibir nota (1 a 5) e comentários, quando disponíveis, com opção de ordenação por relevância, data ou nota.
* O usuário pode buscar estabelecimentos por nome, localização ou categoria (ex.: restaurante, padaria).
* A busca deve retornar resultados em menos de 2 segundos e estar acessível em até dois cliques da tela inicial.
    * "Tela inicial > Menu > Busca"
* Toda ação do usuário (busca, acesso a dados, ordenação) deve gerar feedback visual imediato (sucesso, erro ou ausência de dados).
    * Exibir no rodapé da tela de resultados.
* Quando não houver dados de higiene disponíveis para um estabelecimento, o sistema deve exibir uma mensagem clara informando essa ausência.

## Regras de negócio:
* Somente usuários autenticados poderão comentar.
* As informações de higiene devem ser atualizadas automaticamente a partir de fontes oficiais, com verificação mensal.
* Apenas usuários autenticados podem visualizar avaliações detalhadas (comentários), mas a busca e visualização geral são públicas.
* Avaliações marcadas como suspeitas (com base na blacklist) devem ser revisadas por um moderador em até 48 horas.
    * Moderação feita por equipe interna via painel de administração.
* Estabelecimentos sem inspeções sanitárias registradas devem ser exibidos com uma notificação clara de ausência de dados.

### Tabela de Classes de Equivalência - H2

| Condição de Entrada           | Classes Válidas                                        | Classes Inválidas                                      |
|-------------------------------|------------------------------------------------|-----------------------------------------------|
| Atualização dos Dados | Dados da inspeção com menos de 12 meses **(1)** | Dados da inspeção com mais de 12 meses **(2)** |
| Disponibilidade dos Dados | Estabelecimento possui dados de higiene **(3)** | Estabelecimento não possui dados de higiene **(4)** |
| Nível de Acesso | Usuário está autenticado **(5)** | Usuário não está autenticado **(6)** |
| Ordenação das Avaliações | Ordena por relevância, data ou nota **(7)** | - |

### Tabela de Casos de Teste - H2

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,7                 | Data: "01/06/2024", Dados: "Possui dados", Usuário: Autenticado, Ordenação: "Relevância" | Exibe data "01/06/2024", dados "Possui dados", comentários detalhados, ordenação por relevância |
| Caso 2         | **2**,3,5,7             | Data: "01/06/2023", Dados: "Possui dados" Usuário: Autenticado, Ordenação: "Relevância" | Exibe data "2023-06-01", dados "Possui dados", alerta visual de desatualização, comentários detalhados, ordenação por relevância |
| Caso 3         | 1,**4**,5,7             | Data: "01/06/2024", Dados: "Sem dados", Usuário: Autenticado, Ordenação: "Relevância" | Exibe mensagem "Sem dados de higiene disponíveis", sem alerta, comentários detalhados, ordenação por relevância |
| Caso 4         | 1,3,**6**,7             | Data: "01/06/2024", Dados: "Possui dados", Usuário: Não autenticado, Ordenação: "Relevância" | Exibe data "01/06/2024", dados: "Possui dados", sem comentários detalhados, ordenação por relevância |

---

## H3 - Como consumidor, eu gostaria de registrar relatos e denúncias sobre problemas de qualidade alimentar, como má higiene ou alimentos vencidos, para alertar outros usuários e os próprios comerciantes.

## Critérios de Aceitação:
* O usuário poderá selecionar o tipo de problema entre opções predefinidas:
    * Higiene
    * Alimento vencido
    * Armazenamento inadequado
    * Atendimento insatisfatório
* O campo de descrição será obrigatório, com no mínimo 20 caracteres.
* O sistema deve permitir anexar fotos (opcional).
* Denúncias com linguagem ofensiva, discriminatória ou difamatória devem ser automaticamente bloqueadas.
* Após o envio, o usuário verá uma mensagem de confirmação.
* A denúncia será exibida no perfil do estabelecimento após moderação ou filtro automático.
    * As denúncias de usuários não serão publicadas automaticamente.
    * Toda denúncia passará por um processo de moderação híbrida, que pode envolver filtros automáticos e/ou moderação humana.
* A data e hora da denúncia devem ser registradas automaticamente.

## Regras de Negócio:
* Cada denúncia deve estar vinculada a um estabelecimento já existente na base de dados.
* Apenas usuários autenticados poderão registrar denúncias.
* Comentários com palavras da blacklist serão marcados para revisão ou excluídos automaticamente.
* Será permitido apenas uma denúncia por usuário por estabelecimento a cada 24 horas.
* Caso exista uma denúncia anterior dentro desse período, o sistema deve bloquear o envio e exibir uma mensagem de erro ao usuário.
* Denúncias aprovadas ficarão visíveis a todos os usuários da plataforma.
* Comerciantes poderão responder publicamente às denúncias no prazo de até 7 dias após sua publicação.

  
### Tabela de Classes de Equivalência - H3

| Condição de Entrada           | Classes Válidas                                                  | Classes Inválidas                                      |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Vinculação com Estab. | Denúncia é associada a um estabelecimento existente **(1)** | Denúncia não é associada a um estabelecimento **(2)** |
| Tipo de Problema | Seleciona uma opção predefinida da lista (Higiene, Alimento vencido, Armazenamento inadequado, Atendimento insatisfatório) **(3)** | - |
| Comprimento da Descrição | Descrição com 20 ou mais caracteres **(4)** | Descrição com menos de 20 caracteres **(5)** |
| Frequência de Denúncia | 1ª denúncia nas últimas 24h para o estabelecimento **(6)** | Já existe denúncia nas últimas 24h **(7)** |
| Anexo de Arquivo | Anexa uma foto (opcional) **(8)** | - |

### Tabela de Casos de Teste - H3

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,4,6,8               | Estabelecimento: "Restaurante A", Tipo: "Higiene", Descrição: "Má higiene observada na cozinha com restos de comida", Anexo: "foto.jpg", 1ª denúncia nas 24h | Denúncia registrada com sucesso |
| Caso 2         | **2**,3,4,6,8           | Estabelecimento: "Restaurante Inexistente", Tipo: "Higiene", Descrição: "Má higiene observada na cozinha com restos de comida", Anexo: "foto.jpg", 1ª denúncia nas 24h | Rejeição: "Estabelecimento não encontrado" |
| Caso 3         | 1,**5**,3,6,8           | Estabelecimento: "Restaurante A", Tipo: "Higiene", Descrição: "Má higiene", Anexo: "foto.jpg", 1ª denúncia nas 24h | Rejeição: "Descrição deve ter no mínimo 20 caracteres" |
| Caso 4         | 1,3,4,**7**,8           | Estabelecimento: "Restaurante A", Tipo: "Higiene", Descrição: "Má higiene observada na cozinha com restos de comida", Anexo: "foto.jpg", Já denunciado nas 24h | Rejeição: "Limite de uma denúncia por 24 horas atingido" |

---

## H5 - Como consumidor, eu gostaria de receber alertas sobre locais denunciados ou avaliados negativamente, para evitar riscos à saúde.

## Critérios de Aceitação
* O sistema deve oferecer a opção de ativar ou desativar alertas de segurança alimentar nas configurações do perfil do usuário.
* Quando um estabelecimento for:
    * Denunciado 4 vezes ou mais
    * Receber nota média inferior a 2.5.
        * A média será calculada considerando os últimos 30 dias.
* O alerta deve ser enviado via:
    * O app deve enviar notificações push e também exibir alertas in-app.
* O alerta deve conter:
    * Nome do estabelecimento
    * Motivo do alerta (denúncias ou baixa avaliação)
    * Link para visualizar detalhes
* O sistema deve exibir um ícone de alerta ao lado do nome do estabelecimento nas listagens e no mapa.

## Regras de Negócio
* O sistema só envia alertas para usuários que optaram por recebê-los nas configurações.
* Os alertas são gerados com base em regras automatizadas, sem necessidade de moderação.
    * Os alertas serão automáticos, mas denúncias podem ser revistas manualmente caso o usuário conteste.
* Um mesmo estabelecimento pode gerar no máximo um alerta a cada 7 dias para o mesmo usuário.
* Denúncias falsas ou maliciosas que forem rejeitadas pela moderação não entram na contagem de alerta.
* O sistema deve armazenar um log de alertas enviados, sem expor dados pessoais dos denunciantes.
    * O log será armazenado em banco de dados, com retenção de 12 meses, para fins de auditoria.

      
### Tabela de Classes de Equivalência - H5

| Condição de Entrada           | Classes Válidas                                                          | Classes Inválidas                                                            | Classes Inválidas                                                            |
|-------------------------------|--------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| Configuração de Alertas       | Alertas estão ativados no perfil **(1)** | Alertas estão desativados no perfil **(2)** | -                                                                            |
| Gatilho de Alerta             | 4 ou mais denúncias; OU nota média < 2.5 **(3)** | Menos de 4 denúncias **(4)** | Nota média ≥ 2.5 **(5)** |
| Frequência de Alerta          | Nenhum alerta para o mesmo local/usuário nos últimos 7 dias **(6)** | Já foi enviado alerta para o mesmo local/usuário nos últimos 7 dias **(7)** | -                                                                            |
| Contagem de Denúncias         | Denúncias rejeitadas pela moderação não são contadas **(8)** | -                                                                            | -                                                                            |

### Tabela de Casos de Teste - H5

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,6,8                 | Alertas: Ativados, Denúncias: 5, Nota Média: 2.0, Último Alerta: há 8 dias | Alerta enviado (push e in-app) com nome, motivo "5 denúncias", link para detalhes |
| Caso 2         | **2**,3,6,8             | Alertas: Desativados, Denúncias: 5, Nota Média: 2.0, Último Alerta: há 8 dias | Nenhum alerta enviado |
| Caso 3         | 1,**4**,6,8             | Alertas: Ativados, Denúncias: 2, Nota Média: 2.0, Último Alerta: há 8 dias | Nenhum alerta enviado |
| Caso 4         | 1,3,**5**,6,8           | Alertas: Ativados, Denúncias: 5, Nota Média: 3.0, Último Alerta: há 8 dias | Nenhum alerta enviado |
| Caso 5         | 1,3,6,**7**,8           | Alertas: Ativados, Denúncias: 5, Nota Média: 2.0, Último Alerta: há 2 dias | Nenhum alerta enviado |

---

## H6 - Como consumidor, eu gostaria de receber recomendações personalizadas de locais seguros com base nas minhas preferências alimentares e avaliações anteriores.

## Critérios de Aceitação
* Cadastro de Preferências Alimentares:
    * O usuário pode alterar essas preferências a qualquer momento.
* Recomendações serão baseadas nas últimas 10 avaliações do usuário, usando regras fixas de categoria.
* Uso de Avaliações Anteriores
    * O sistema utiliza as avaliações anteriores do usuário (notas e comentários) para identificar padrões de preferência.
    * Avaliações com notas altas influenciam positivamente as recomendações futuras.
        * Notas maiores ou iguais a 4.0 influenciarão positivamente nas recomendações.
* Filtro e Feedback
    * O usuário pode filtrar as recomendações por distância, preço e tipo de comida.
* Personalização com base nas avaliações, histórico de navegação e perguntas respondidas após o cadastro do usuário no aplicativo.
* O usuário pode marcar uma recomendação como "não relevante", ajudando a refinar futuras sugestões.
* A lista de tipos de comida disponíveis nos filtros será pré-definida pelo sistema, mas customizável por administradores via painel de administração.

### Tabela de Classes de Equivalência - H6

| Condição de Entrada            | Classes Válidas                                                        | Classes Inválidas                                     |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Base para Recomendação | Usuário tem preferências cadastradas OU avaliações anteriores **(1)** | Usuário novo sem preferências ou avaliações **(2)** |
| Filtro de Recomendações | Filtra por distância, preço ou tipo de comida **(3)** | - |
| Feedback na Recomendação | Marca uma recomendação como "não relevante" **(4)** | - |

### Tabela de Casos de Teste - H6

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,4                   | Preferências: Vegetariano, Avaliações: [4.5, 4.0], Filtro: Distância 5km | Recomendações personalizadas|
| Caso 2         | **2**,3,4               | Preferências: Nenhuma, Avaliações: Nenhuma, Filtro: Distância 5km | Recomendações genéricas exibidas |

---

## H9 - Como consumidor, eu gostaria de excluir minha conta se eu decidir parar de usar o serviço.

## Critérios de Aceitação
* O usuário deve estar autenticado para solicitar a exclusão da conta.
* A opção "Excluir Conta" deve estar visível nas configurações do perfil do usuário.
* Ao clicar na opção, o sistema deve:
    * Exibir uma mensagem de confirmação informando que a ação é irreversível.
    * O usuário receberá uma mensagem de confirmação por e-mail.
    * Solicitar a senha atual como validação final.
* Após a confirmação, o sistema deve:
    * Remover o acesso do usuário imediatamente.
    * Apagar ou anonimizar os dados pessoais, conforme a política de privacidade.
    * Manter as avaliações, denúncias e comentários, mas desvinculados do nome do usuário (apenas como “usuário removido”).
* O usuário deve receber uma notificação ou mensagem final confirmando a exclusão da conta.

## Regras de Negócio
* A exclusão de conta deve ser permitida apenas para usuários autenticados e ativos.
    * Armazenar ID do usuário, data, hora e tipo de ação. Retenção de 12 meses.
* A confirmação de identidade deve ser feita por meio de reentrada da senha para prevenir exclusões acidentais.
* Dados sensíveis (como nome, e-mail, telefone) devem ser removidos ou anonimizados em conformidade com a LGPD.
    * Link da política de privacidade: Lei nº 13.709/2018 - Lei Geral de Proteção de Dados Pessoais (LGPD).
* A exclusão da conta é irreversível: não será possível restaurar os dados após a conclusão da ação.
    * Apagar em caso de solicitação do usuário. Anonimizar em caso de inatividade superior a 12 meses.
* Conteúdos públicos gerados pelo usuário (avaliações, comentários, denúncias) devem permanecer visíveis para fins de integridade histórica, mas sem identificação pessoal.
* A operação de exclusão deve ser registrada no sistema para fins de auditoria (sem armazenar dados pessoais após anonimização).

### Tabela de Classes de Equivalência - H9

| Condição de Entrada           | Classes Válidas                                                   | Classes Inválidas                                     |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Status do Usuário | Usuário está autenticado **(1)** | Usuário não está autenticado **(2)** |
| Validação de Segurança | Senha atual informada corretamente **(3)** | Senha atual informada incorretamente **(4)** |
| Ação de Confirmação | Clica no botão final para confirmar a exclusão **(5)** | Clica em "Cancelar" na tela de confirmação **(6)** |
| Tratamento do Conteúdo | Conteúdo do usuário (avaliações) é mantido e anonimizado **(7)** | - |

## Tabela de Casos de Teste - H9

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,7                 | Usuário: Autenticado, Senha: "Abc123", Ação: "Sim, excluir" | Conta excluída, e-mail de confirmação enviado, avaliações anonimizadas |
| Caso 2         | **2**,3,5,7             | Usuário: Não autenticado, Senha: "Abc123", Ação: "Sim, excluir" | Rejeição: "Usuário não autenticado" |
| Caso 3         | 1,**4**,5,7             | Usuário: Autenticado, Senha: "Errada", Ação: "Sim, excluir" | Rejeição: "Senha incorreta" |
| Caso 4         | 1,3,**6**,7                 | Usuário: Autenticado, Senha: "Abc123", Ação: "Cancelar" | Exclusão cancelada, conta mantida |

---

## H10 - Como consumidor, eu gostaria de ver um mapa com a localização dos estabelecimentos cadastrados, para encontrar os melhores locais próximos a mim.

## Critérios de Aceitação
* O sistema deve exibir um mapa interativo acessível a partir da tela inicial ou menu principal.
    * Botão fixo no menu principal com ícone de mapa.
* Os estabelecimentos cadastrados devem ser representados por marcadores no mapa, com:
    * Nome do local
    * Nota média (visível ao tocar ou clicar no marcador)
    * Categoria do estabelecimento (ícone ou cor diferente)
* O sistema deve solicitar permissão de localização do usuário ao acessar o mapa.
* O mapa deve exibir estabelecimentos próximos à localização atual do usuário, com opção de:
    * Buscar por endereço ou bairro
    * Aplicar filtros (nota mínima, tipo de estabelecimento, distância)
        * "Padrão de 2 km, configurável via painel"
* Ao selecionar um marcador, o usuário deve poder abrir a página de detalhes do estabelecimento.

## Regras de Negócio
* A funcionalidade de mapa só estará disponível se o usuário conceder permissão de localização, ou realizar uma busca manual por endereço.
* A nota média exibida no mapa deve refletir apenas avaliações aprovadas e públicas.
* O sistema deve utilizar coordenadas geográficas válidas para posicionar os estabelecimentos (baseado em endereço informado no cadastro).
    * Exibir: "Não foi possível localizar o endereço. Tente novamente".
* Estabelecimentos sem localização válida não serão exibidos no mapa até correção manual.
* A busca e os filtros devem estar limitados a um raio de até 10km da posição atual ou endereço buscado, para garantir desempenho.
* Geolocalização só será usada durante a sessão ativa e não será armazenada.


### Tabela de Classes de Equivalência - H10

| Condição de Entrada             | Classes Válidas                                                 | Classes Inválidas                                        |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Permissão de Localização | Usuário concede permissão **(1)** | Usuário nega permissão **(2)** |
| Geolocalização do Estab. | Estabelecimento possui coordenadas válidas **(3)** | Estabelecimento não possui coordenadas válidas **(4)** |
| Exibição no Marcador | Marcador do mapa exibe Nome, Nota e Categoria **(5)** | - |
| Raio de Busca | Busca dentro do raio máximo de 10km **(6)** | Busca excede o raio de 10km **(7)** |

### Tabela de Casos de Teste - H10

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,6                 | Permissão: Concedida, Coordenadas: Válidas, Raio: 5km | Mapa exibe marcadores com Nome, Nota, Categoria |
| Caso 2         | **2**,3,5,6             | Permissão: Negada, Coordenadas: Válidas, Raio: 5km | Permite inserir endereço manualmente, exibe marcadores |
| Caso 3         | 1,**4**,5,6             | Permissão: Concedida, Coordenadas: Inválidas, Raio: 5km | Nenhum marcador exibido |
| Caso 4         | 1,3,5,**7**             | Permissão: Concedida, Coordenadas: Válidas, Raio: 15km | Raio limitado a 10km, marcadores ajustados |

---

## H11 - Como consumidor, eu gostaria de filtrar os estabelecimentos por tipo de comida ou por nota de avaliação, para encontrar rapidamente opções que atendam ao que estou buscando.

## Critérios de Aceitação
* O sistema deve disponibilizar um filtro por tipo de comida, incluindo opções como:
    * Comida caseira
    * Fast food
    * Vegetariana/Vegana
    * Doces e sobremesas
* O sistema deve permitir filtrar por nota de avaliação, com:
    * Nota mínima (ex: 4 estrelas ou mais)
    * Ordenação por melhor avaliado
* Ao aplicar a ordenação por "melhor avaliado", o sistema deverá listar os estabelecimentos na seguinte ordem de prioridade:
    * Maior nota média de avaliação (calculada com base nas avaliações públicas aprovadas).
    * Maior número de avaliações recebidas (caso haja empate na média da nota).
    * Proximidade geográfica em relação à localização atual ou ao local pesquisado (se ainda houver empate após os dois primeiros critérios).
* Os filtros devem estar acessíveis na listagem de estabelecimentos e no mapa interativo.
* O sistema deve atualizar os resultados automaticamente ao aplicar os filtros.
* Deve haver a opção de limpar todos os filtros e retornar à listagem completa.
* O filtro deve funcionar tanto por localização atual quanto por busca manual (ex: bairro ou endereço).
* O sistema deve atualizar os resultados automaticamente sempre que o usuário adicionar ou remover filtros.
* Caso nenhum resultado atenda a todos os filtros ativos, o sistema deverá exibir uma mensagem como:
    * "Nenhum estabelecimento encontrado com os filtros aplicados."
* Quando o usuário aplicar múltiplos filtros (exemplo: tipo de comida + nota mínima + localização), o sistema deve exibir apenas os estabelecimentos que atendam simultaneamente a todos os critérios selecionados (lógica AND entre filtros).

## Regras de Negócio
* Os tipos de comida disponíveis nos filtros devem ser predefinidos pelo sistema, mas podem ser expandidos por administradores.
* A nota exibida nos filtros deve ser calculada com base em avaliações públicas aprovadas.
* O sistema deve limitar a listagem a 50 resultados por busca, com paginação ou scroll infinito para desempenho.
* Se nenhum estabelecimento corresponder aos filtros aplicados, o sistema deve exibir uma mensagem amigável, como: "Nenhum resultado encontrado para os critérios selecionados."
* Filtros combinados (ex: “Vegetariana” + “nota maior que 4”) devem retornar apenas estabelecimentos que atendam a todos os critérios simultaneamente.
* O sistema deve manter os filtros ativos enquanto o usuário navega entre os resultados, até que ele os limpe manualmente.
* A lista de tipos de comida disponíveis nos filtros será pré-definida pelo sistema, mas customizável por administradores via painel de administração.
* Quando o usuário aplicar filtros (por tipo de comida ou nota de avaliação), os resultados exibidos no mapa devem ser automaticamente atualizados, refletindo apenas os estabelecimentos que atendam aos critérios selecionados.
* Detalhamento da Integração Visual:
    * Os filtros estarão localizados na mesma tela onde o mapa é exibido, preferencialmente acima ou ao lado do mapa (conforme decisão de UI/UX).
    * Cada vez que o usuário alterar algum filtro:
        * Os pinos (marcadores) no mapa devem ser atualizados em tempo real, removendo ou adicionando estabelecimentos de acordo com os filtros ativos.
    * Se nenhum estabelecimento atender aos filtros:
        * O mapa deve exibir um estado vazio (ex: sem pinos) acompanhado de uma mensagem amigável, como:
            * "Nenhum estabelecimento encontrado para os filtros selecionados nesta área do mapa."

### Tabela de Classes de Equivalência - H11

| Condição de Entrada            | Classes Válidas                                                              | Classes Inválidas                                     |
|-------------------------------|----------------------------------------------------------------------------|------------------------------------------------------|
| Tipo de Filtro                 | Filtra por tipo de comida (por ex., vegetariana) **(1)**                    | Filtro com tipo inválido (texto vazio ou não listado) **(2)** |
| Filtro por Nota                | Filtra por nota mínima (por ex., ≥ 4, dentro de 1 a 5) **(3)**             | Nota fora do intervalo (por ex., >5 ou <1) **(4)**   |
| Filtros Combinados             | Aplica múltiplos filtros simultaneamente (lógica AND) **(5)**               | Filtros combinados com lógica incorreta (OR) **(11)**|
| Ordenação de Resultados        | Ordena por "melhor avaliado" (baseado em nota, nº de avaliações, proximidade) **(6)** | -                                                  |
| Limpeza de Filtros             | Clica no botão para limpar todos os filtros aplicados **(7)**               | -                                                  |
| Busca Sem Resultados           | Filtro aplicado não encontra correspondências, exibe mensagem amigável (lista e mapa vazio) **(8)** | -                                                  |

### Tabela de Casos de Teste - H11

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,6,7,8             | Tipo: Vegetariana, Nota: ≥4, Ordenação: Melhor Avaliado, Limpeza: Não, Localização: Atual | Resultados filtrados (lógica AND), ordenados por nota/avaliações/proximidade, mensagem "Nenhum..." se vazio |
| Caso 2         | **2**,3,5,6,7,8         | Tipo: "", Nota: ≥4, Ordenação: Melhor Avaliado, Limpeza: Não, Localização: Atual | Rejeição: "Tipo de filtro inválido", mapa inalterado |
| Caso 3         | 1,**4**,5,6,7,8         | Tipo: Vegetariana, Nota: 6, Ordenação: Melhor Avaliado, Limpeza: Não, Localização: Atual | Rejeição: "Nota fora do intervalo válido", mapa inalterado |
| Caso 4         | 1,3,**11**,6,7,8        | Tipo: Vegetariana, Nota: ≥4, Ordenação: Melhor Avaliado, Filtro Adicional: Fast Food , Localização: Atual | Rejeição: "Filtros combinados inválidos (lógica OR)", mapa inalterado |
---

## H12 - Como dono do estabelecimento, eu gostaria de atualizar meu perfil no app para informar os consumidores sobre mudanças e manter meu perfil atrativo.

## Critérios de Aceitação
* Usuários autenticados como donos de estabelecimento possuem um perfil específico.
* Campos editáveis no perfil:
    * Nome do estabelecimento
    * Descrição (até 1000 caracteres)
    * Horário de funcionamento
    * Tipo de culinária
    * Endereço e formas de contato (telefone, redes sociais)
    * Imagens (logo e fotos do local/comida)
    * Informações sobre restrições alimentares atendidas (vegano, sem glúten, etc.)
* Histórico de alterações
    * O sistema mantém um log das últimas atualizações realizadas (visível apenas ao dono).
* O sistema impede o envio de:
    * Linguagem ofensiva
    * Informações falsas (como números de telefone inválidos)
    * Imagens em formato não suportado (apenas JPG/PNG, até 5MB cada)

## Regras de Negócio
* Controle de edição
    * Um estabelecimento pode ter no máximo um perfil ativo vinculado a um único usuário autenticado como dono.
    * Cada alteração de perfil deve ser salva com data/hora, mesmo que não haja campo visível para isso.
* Publicação imediata
    * Alterações são refletidas imediatamente no perfil público do estabelecimento, sem moderação prévia (a menos que violem termos de uso ou política de conteúdo).
    * Conteúdos que violem a política de uso, incluindo discurso de ódio, spam ou linguagem ofensiva.
* Limite de imagens
    * Verificar spam apenas nos campos de título e descrição de comentário.
    * O perfil pode conter até 5 imagens, sendo 1 logo + 4 fotos adicionais.
    * Substituições podem ser feitas a qualquer momento, respeitando o limite de tamanho e formato.
* Filtro automático de conteúdo
    * O sistema aplica um filtro automático para linguagem ofensiva em textos inseridos.
    * Número com 11 dígitos, validado por expressão regular.

### Tabela de Classes de Equivalência - H12

| Condição de Entrada            | Classes Válidas                                               | Classes Inválidas                                      |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Permissão de Edição | Usuário é autenticado como "dono" do estabelecimento **(1)** | Usuário não tem permissão para editar **(2)** |
| Upload de Imagem (Formato) | Imagem é JPG ou PNG **(3)** | Imagem tem formato não suportado (ex. GIF) **(4)** |
| Upload de Imagem (Tamanho) | Imagem tem até 5MB **(5)** | Imagem tem mais de 5MB **(6)** |
| Limite de Imagens | Envia até 5 imagens (1 logo + 4 fotos) **(7)** | Tenta enviar a 6ª imagem **(8)** |
| Conteúdo dos Textos | Campos de texto não contêm palavras da blacklist **(9)** | Campos de texto contêm palavras da blacklist **(10)** |

### Tabela de Casos de Teste - H12

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,7,9               | Usuário: Dono, Imagem: "logo.jpg" (2MB), Texto: "Descrição válida" | Perfil atualizado com 1 logo e 4 fotos |
| Caso 2         | **2**,3,5,7,9           | Usuário: Cliente, Imagem: "logo.jpg" (2MB), Texto: "Descrição válida" | Rejeição: "Permissão negada" |
| Caso 3         | 1,**4**,5,7,9           | Usuário: Dono, Imagem: "logo.gif" (2MB), Texto: "Descrição válida" | Rejeição: "Formato de imagem não suportado" |
| Caso 4         | 1,3,**6**,7,9           | Usuário: Dono, Imagem: "logo.jpg" (6MB), Texto: "Descrição válida" | Rejeição: "Imagem excede 5MB" |
| Caso 5         | 1,3,5,**8**,9           | Usuário: Dono, Imagem: "logo.jpg" (2MB) + 5 fotos, Texto: "Descrição válida" | Rejeição: "Limite de 5 imagens atingido" |
| Caso 6         | 1,3,5,7,**10**          | Usuário: Dono, Imagem: "logo.jpg" (2MB), Texto: "Descrição ofensiva" | Rejeição: "Texto contém palavras da blacklist" |

---

## H14 - Como dono de um estabelecimento, eu gostaria de cadastrar meu próprio estabelecimento na plataforma para que os consumidores possam avaliar meus serviços.

## Critérios de Aceitação
* O dono do estabelecimento deve obrigatoriamente estar cadastrado na plataforma para acessar a funcionalidade de cadastro.
* O sistema deve apresentar um formulário com os seguintes campos obrigatórios:
    * Nome do estabelecimento
    * Tipo de estabelecimento (ex: restaurante, feira, mercado, etc)
        * Validação comparando com a lista de categorias do banco de dados.
    * Endereço (com CEP e número)
    * Horário de funcionamento
    * Telefone ou meio de contato
* O campo de descrição deve ser opcional, com limite de até 500 caracteres.
* O sistema deve permitir anexar uma imagem de capa (opcional, até 5MB).
    * Aceitar formatos .jpg e .png, tamanho máximo 5MB.
    * Validação por API de análise de imagem (ex: Google Vision).
* Após o envio, o sistema deve exibir uma mensagem de confirmação.
* O dono deve poder visualizar e editar o cadastro posteriormente.

## Regras de Negócio
* Apenas usuários com perfil de "Dono de Estabelecimento" podem cadastrar um estabelecimento.
* Cada dono pode cadastrar no máximo 10 estabelecimentos por CPF/CNPJ.
* O nome do estabelecimento deve ser único dentro da mesma rua.
    * Validação ignorando acentos, maiúsculas/minúsculas e espaços extras.
* Imagens do estabelecimento devem ser analisadas automaticamente para prevenir conteúdo impróprio.
* O sistema deve armazenar a data e hora de cada cadastro, e manter um registro de edições realizadas no perfil do estabelecimento.
* Estabelecimentos com dados incompletos ou falsos podem ser removidos pela moderação, com notificação ao dono.
  
### Tabela de Classes de Equivalência - H14

| Condição de Entrada             | Classes Válidas                                               | Classes Inválidas                                               |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Perfil do Usuário | Usuário com perfil de "Dono de Estabelecimento" **(1)** | Usuário sem perfil de "Dono" **(2)** |
| Preenchimento do Formulário | Todos os campos obrigatórios estão preenchidos (nome, tipo, endereço, horário, contato) **(3)** | Pelo menos um campo obrigatório está vazio **(4)** |
| Unicidade de Nome | Nome do estabelecimento é único na mesma rua **(5)** | Nome já existe para outro estabelecimento na mesma rua **(6)** |
| Limite de Cadastros | Dono possui menos de 10 estabelecimentos cadastrados **(7)** | Dono já possui 10 estabelecimentos cadastrados **(8)** |
| Validação de Imagens | Imagem sem conteúdo impróprio (validada por API) **(9)** | Imagem com conteúdo impróprio (detectado por API) **(10)** |

### Tabela de Casos de Teste - H14

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,7,9               | Usuário: Dono, Nome: "Restaurante A", Tipo: Restaurante, Endereço: "Rua 1", Horário: "9:18", Contato: "12345678901", Imagem: "capa.jpg" (2MB) | Cadastro bem-sucedido com mensagem de confirmação |
| Caso 2         | **2**,3,5,7,9           | Usuário: Cliente, Nome: "Restaurante A", Tipo: Restaurante, Endereço: "Rua 1", Horário: "9:18", Contato: "12345678901", Imagem: "capa.jpg" (2MB) | Rejeição: "Permissão negada" |
| Caso 3         | 1,**4**,5,7,9           | Usuário: Dono, Nome: "", Tipo: Restaurante, Endereço: "Rua 1", Horário: "9:18", Contato: "12345678901", Imagem: "capa.jpg" (2MB) | Rejeição: "Campos obrigatórios ausentes" |
| Caso 4         | 1,3,**6**,7,9           | Usuário: Dono, Nome: "Restaurante A", Tipo: Restaurante, Endereço: "Rua 1", Horário: "9:18", Contato: "12345678901", Imagem: "capa.jpg" (2MB); Nome duplicado | Rejeição: "Nome já existe na mesma rua" |
| Caso 5         | 1,3,5,**8**,9           | Usuário: Dono, Nome: "Restaurante A", Tipo: Restaurante, Endereço: "Rua 1", Horário: "9:18", Contato: "12345678901", Imagem: "capa.jpg" (6MB) | Rejeição: "Imagem excede 5MB" |
| Caso 6         | 1,3,5,7,**10**          | Usuário: Dono, Nome: "Restaurante A", Tipo: Restaurante, Endereço: "Rua 1", Horário: "99:18", Contato: "12345678901", Imagem: "capa_imprópria.jpg" (2MB) | Rejeição: "Imagem contém conteúdo impróprio" |

---

## H15 - Como Moderadora da plataforma, eu gostaria de analisar relatos de usuários para manter a veracidade das informações publicadas antes de exibi-los publicamente.

## Critérios de Aceitação
* A moderadora deve ter acesso a uma área específica chamada “Painel de Moderação”.
* O painel deve listar relatos pendentes de validação, incluindo:
    * Comentários
    * Denúncias
    * Avaliações com texto
* Para cada item listado, o sistema deve exibir:
    * Nome do usuário (ou ID do usuário)
    * Data e hora do envio
    * Tipo de conteúdo (comentário, denúncia, avaliação)
    * Conteúdo completo do relato
* A moderadora deve ter as seguintes ações disponíveis para cada relato:
    * Aprovar
    * Rejeitar
    * Marcar como suspeito (para revisão posterior ou por outro nível de moderação)
* Após uma ação, o sistema deve atualizar o status do relato e removê-lo da lista pendente.
* Um relato só deve ser exibido publicamente após aprovação.

## Regras de Negócio
* Apenas usuários com perfil de moderação ou superior podem acessar o painel de análise de relatos.
* O sistema deve manter um log de decisão para cada relato moderado (incluindo quem moderou, ação tomada, e data/hora).
    * Manter por 12 meses para consulta administrativa.
* Relatos rejeitados não são excluídos do banco de dados, mas ficam com status “invisível ao público” e acessíveis apenas por moderadores e administradores.
    * Excluir permanentemente após 12 meses.
* Relatos aprovados são publicados imediatamente na interface pública, vinculados ao usuário e ao estabelecimento correspondente.
* Relatos classificados como "suspeitos" permanecem ocultos e devem ser analisados por outro moderador ou escalados a um administrador.

### Tabela de Classes de Equivalência - H15

| Condição de Entrada       | Classes Válidas                                                  | Classes Inválidas                                  |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Permissão de Acesso | Usuário tem perfil de "Moderador" ou "Administrador" **(1)** | Usuário tem perfil comum ou de "Dono" **(2)** |
| Ação de Moderação | Modera um relato como "Aprovar" ou "Rejeitar" **(3)** | - |
| Bloqueio Automático | Relato com termos da blacklist é enviado para moderação **(4)** | - |

### Tabela de Casos de Teste - H15

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,4                   | Usuário: Moderador, Relato: "Denúncia válida", Ação: Aprovar | Relato aprovado, removido da lista pendente, publicado |
| Caso 2         | **2**,3,4               | Usuário: Cliente, Relato: "Denúncia válida", Ação: Aprovar | Rejeição: "Acesso negado" |

---

## H16 - Como Moderadora da plataforma, eu gostaria de uma funcionalidade de histórico dos usuários para analisar o comportamento dos usuários.

## Critérios de Aceitação
* A moderadora deve conseguir acessar o histórico de um usuário a partir do seu perfil.
* A moderadora deve poder visualizar um log com ações recentes de cada usuário.
    * Login, logout, envio de comentário, exclusão de denúncia.
* O histórico deve incluir data, hora e tipo de atividade realizada.
* A funcionalidade deve estar disponível apenas para contas com perfil de moderação ou administração.
* O sistema deve permitir filtrar por tipo de ação ou Intervalo de datas.
    * Filtro máximo de 12 meses retroativos por consulta.

## Regras de negócios
* Somente usuários com perfil de moderador ou administrador podem acessar o histórico de atividades de outros usuários.
* Todas as ações dos usuários devem ser registradas automaticamente, armazenado com carimbo de data e hora.
* O sistema não permite exclusão ou edição do histórico por parte de usuários comuns.
* A visualização do histórico deve estar limitada a 12 meses anteriores por padrão, com possibilidade de extensão apenas por administradores.
    * Admins poderão solicitar extensão via painel administrativo.
* A visualização de informações sensíveis deve ser restringida apenas a administradores, e não aos moderadores padrão.
    * Informações sensíveis incluem: nome, telefone, e-mail, CPF.
* Logs de atividades devem ser criptografados em repouso para garantir integridade e confidencialidade.

### Tabela de Classes de Equivalência - H16

| Condição de Entrada          | Classes Válidas                                            | Classes Inválidas                                          |
|-------------------------------|-------------------------------------------------------------|-----------------------------------------------|
| Permissão de Visualização | Usuário é "Moderador" ou "Administrador" **(1)** | Usuário é comum ou "Dono" **(2)** |
| Permissão a Dados Sensíveis | Administrador **(3)** | Moderador padrão tenta visualizar dados sensíveis **(4)** |
| Filtro por Período de Data | Filtro de data com intervalo de até 12 meses **(5)** | Moderador tenta filtrar por mais de 12 meses **(6)** |
| Filtro por Tipo de Ação | Filtra por tipo de ação (ex: login, comentário) **(7)** | - |

### Tabela de Casos de Teste - H16

| Casos de Teste | Classes de Equivalência | Entradas | Resultado Esperado |
|----------------|-------------------------|----------|---------------------|
| Caso 1         | 1,3,5,7                 | Usuário: Administrador, Filtro: Últimos 6 meses, Ação: Login | Histórico exibido com ações de login |
| Caso 2         | **2**,3,5,7             | Usuário: Cliente, Filtro: Últimos 6 meses, Ação: Login | Rejeição: "Acesso negado" |
| Caso 3         | 1,**4**,5,7             | Usuário: Moderador, Filtro: Dados Sensíveis | Rejeição: "Acesso a dados sensíveis negado" |
| Caso 4         | 1,3,**6**,7             | Usuário: Moderador, Filtro: Últimos 24 meses, Ação: Login | Rejeição: "Filtro excedeu 12 meses" |
