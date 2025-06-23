## H1 - Como consumidor, eu gostaria de avaliar estabelecimentos de alimentação para ajudar outros usuários a escolherem locais seguros e de qualidade.

| ID      | Condição de Entrada                                                  | Classe de Equivalência                                           | Resultado Esperado              |
| ------- | -------------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------- |
| H1-CE1  | Atribuir nota para um critério                                       | Nota entre 1 e 5                                                 | Válida                          |
| H1-CE2  | Atribuir nota para um critério                                       | Nota fora do intervalo 1 a 5 (ex: 0 ou 6)                        | Inválida (Rejeitado)            |
| H1-CE3  | Enviar avaliação com pelo menos um critério                          | Avaliação com apenas um critério de nota preenchido              | Válida                          |
| H1-CE4  | Enviar avaliação sem nenhum critério                                 | Avaliação sem nenhum critério de nota preenchido                 | Inválida (Rejeitado)            |
| H1-CE5  | Preencher o campo de comentário                                      | Comentário com 10 ou mais caracteres                             | Válida                          |
| H1-CE6  | Preencher o campo de comentário                                      | Comentário com menos de 10 caracteres                            | Inválida (Rejeitado)            |
| H1-CE7  | Verificar o filtro de palavras ofensivas                             | Comentário sem palavras da blacklist                             | Válida                          |
| H1-CE8  | Verificar o filtro de palavras ofensivas                             | Comentário com palavras da blacklist                             | Inválida (Rejeitado)            |
| H1-CE9  | Verificar a frequência de avaliações                                 | 1 avaliação por estabelecimento na semana                        | Válida                          |
| H1-CE10 | Verificar a frequência de avaliações                                 | Mais de 1 avaliação na mesma semana para o mesmo estabelecimento | Inválida (Bloqueado com alerta) |

##  H2 - Como consumidor, eu gostaria de acessar de forma ágil informações de higiene e avaliações de estabelecimentos alimentícios para tomar decisões seguras e informadas sobre onde comer ou comprar alimentos.

| ID     | Condição de Entrada                              | Classe de Equivalência                                                   | Resultado Esperado      |
| ------ | ------------------------------------------------ | ------------------------------------------------------------------------ | ----------------------- |
| H2-CE1 | Verificar a data da última inspeção              | Dados com menos de 12 meses desde a última atualização                   | Válida                  |
| H2-CE2 | Verificar a data da última inspeção              | Dados com mais de 12 meses (aciona um alerta visual)                     | Válida (Gera Alerta)    |
| H2-CE3 | Verificar a disponibilidade dos dados de higiene | Estabelecimento possui dados de higiene para exibir                      | Válida                  |
| H2-CE4 | Verificar a disponibilidade dos dados de higiene | Estabelecimento não possui dados de higiene (exibe mensagem de ausência) | Válida (Exibe Mensagem) |
| H2-CE5 | Verificar o nível de acesso às avaliações        | Usuário autenticado visualiza comentários detalhados                     | Válida                  |
| H2-CE6 | Verificar o nível de acesso às avaliações        | Usuário não autenticado visualiza apenas dados gerais (sem comentários)  | Válida                  |
| H2-CE7 | Verificar o fluxo de acesso à busca              | Acesso à busca pelo caminho: 'Tela inicial > Menu > Busca'               | Válida                  |

## H3 - Como consumidor, eu gostaria de registrar relatos e denúncias sobre problemas de qualidade alimentar, como má higiene ou alimentos vencidos, para alertar outros usuários e os próprios comerciantes.

| ID     | Condição de Entrada                           | Classe de Equivalência                                              | Resultado Esperado   |
| ------ | --------------------------------------------- | ------------------------------------------------------------------- | -------------------- |
| H3-CE1 | Selecionar o tipo de problema                 | Seleciona uma das opções da lista (Higiene, Alimento vencido, etc.) | Válida               |
| H3-CE2 | Preencher a descrição da denúncia             | Descrição com 20 ou mais caracteres                                 | Válida               |
| H3-CE3 | Preencher a descrição da denúncia             | Descrição com menos de 20 caracteres                                | Inválida (Rejeitado) |
| H3-CE4 | Anexar evidências (opcional)                  | Anexo de foto no formato permitido                                  | Válida               |
| H3-CE5 | Verificar o limite de frequência de denúncias | Até 1 denúncia por estabelecimento a cada 24 horas                  | Válida               |
| H3-CE6 | Verificar o limite de frequência de denúncias | Mais de 1 denúncia no mesmo estabelecimento em 24 horas             | Inválida (Bloqueado) |
| H3-CE7 | Vincular denúncia a um estabelecimento        | Denúncia associada a um estabelecimento existente na base           | Válida               |

## H5 - Como consumidor, eu gostaria de receber alertas sobre locais denunciados ou avaliados negativamente, para evitar riscos à saúde.

| ID     | Condição de Entrada                                | Classe de Equivalência                                                            | Resultado Esperado          |
| ------ | -------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------- |
| H5-CE1 | Verificar a configuração de alertas                | Alertas estão ativados nas configurações do perfil                                | Válida                      |
| H5-CE2 | Verificar a configuração de alertas                | Alertas estão desativados nas configurações do perfil                             | Válida (Não Recebe)         |
| H5-CE3 | Verificar gatilho de alerta por denúncias          | Estabelecimento com 4 ou mais denúncias válidas                                   | Válida (Dispara Alerta)     |
| H5-CE4 | Verificar gatilho de alerta por nota baixa         | Estabelecimento com nota média inferior a 2.5 (considerando os últimos 30 dias)   | Válida (Dispara Alerta)     |
| H5-CE5 | Verificar o não disparo do alerta                  | Estabelecimento com 3 denúncias e nota 2.6                                        | Válida (Não Dispara)        |
| H5-CE6 | Verificar o intervalo de tempo entre alertas       | Nenhum alerta enviado para o mesmo usuário/estabelecimento nos últimos 7 dias     | Válida                      |
| H5-CE7 | Verificar o intervalo de tempo entre alertas       | Já foi enviado um alerta para o mesmo usuário/estabelecimento nos últimos 7 dias  | Inválida (Não Envia)        |
| H5-CE8 | Verificar a contagem de denúncias para o alerta    | Denúncias rejeitadas pela moderação não são contadas                              | Válida                      |
| H5-CE9 | Verificar o canal do alerta                        | Alerta enviado via notificação push e também exibido in-app                       | Válida                      |

## H6 - Como consumidor, eu gostaria de receber recomendações personalizadas de locais seguros com base nas minhas preferências alimentares e avaliações anteriores.

| ID     | Condição de Entrada                                 | Classe de Equivalência                                                                 | Resultado Esperado |
| ------ | --------------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------ |
| H6-CE1 | Recomendar com base nas preferências                | Recomendações correspondem às preferências selecionadas no perfil (ex: vegetariano)    | Válida             |
| H6-CE2 | Recomendar com base em avaliações anteriores        | Recomendações são influenciadas por locais que o usuário avaliou com nota alta (≥ 4.0) | Válida             |
| H6-CE3 | Verificar o uso de filtros na recomendação          | Resultados são filtrados corretamente por distância, preço ou tipo de comida           | Válida             |
| H6-CE4 | Verificar o feedback do usuário em uma recomendação | Usuário marca uma recomendação como 'não relevante' para refinar sugestões futuras     | Válida             |
| H6-CE5 | Verificar recomendação para novo usuário            | Sistema exibe recomendações genéricas para usuário sem histórico                       | Válida             |

## H9 - Como consumidor, eu gostaria de excluir minha conta se eu decidir parar de usar o serviço. 

| ID     | Condição de Entrada                             | Classe de Equivalência                                           | Resultado Esperado       |
| ------ | ----------------------------------------------- | ---------------------------------------------------------------- | ------------------------ |
| H9-CE1 | Verificar se o usuário está autenticado         | Usuário logado tenta excluir a própria conta                     | Válida                   |
| H9-CE2 | Verificar a validação de segurança com senha    | Usuário informa a senha atual correta para confirmar             | Válida                   |
| H9-CE3 | Verificar a validação de segurança com senha    | Usuário informa a senha incorreta                                | Inválida (Rejeitado)     |
| H9-CE4 | Verificar se a ação foi confirmada pelo usuário | Usuário clica no botão final de confirmação (ex: 'Sim, excluir') | Válida                   |
| H9-CE5 | Verificar se a ação foi confirmada pelo usuário | Usuário cancela a ação na tela de confirmação                    | Válida (Não Prossegue)   |
| H9-CE6 | Verificar o tratamento dos dados após exclusão  | Dados pessoais são apagados ou anonimizados conforme a LGPD      | Válida                   |
| H9-CE7 | Verificar o recebimento da confirmação          | Usuário recebe um e-mail confirmando a exclusão da conta         | Válida                   |

## H10 - Como consumidor, eu gostaria de ver um mapa com a localização dos estabelecimentos cadastrados, para encontrar os melhores locais próximos a mim.

| ID      | Condição de Entrada                                    | Classe de Equivalência                                         | Resultado Esperado              |
| ------- | ------------------------------------------------------ | -------------------------------------------------------------- | ------------------------------- |
| H10-CE1 | Verificar comportamento com permissão de localização   | Usuário concede permissão de localização                       | Válida                          |
| H10-CE2 | Verificar comportamento sem permissão de localização   | Usuário nega permissão e insere um endereço manualmente        | Válida                          |
| H10-CE3 | Verificar se o estabelecimento tem geolocalização      | Estabelecimento possui coordenadas válidas para ser exibido    | Válida                          |
| H10-CE4 | Verificar se o estabelecimento tem geolocalização      | Estabelecimento não possui coordenadas e não é exibido no mapa | Válida (Comportamento Esperado) |
| H10-CE5 | Verificar o limite do raio de busca (até 10km)         | Busca dentro de um raio de até 10km                            | Válida                          |
| H10-CE6 | Verificar o limite do raio de busca (até 10km)         | Busca excede o raio de 10km                                    | Inválida (Limitado a 10km)      |
| H10-CE7 | Verificar raio de busca padrão                         | Mapa exibe resultados em um raio padrão de 2km ao abrir        | Válida                          |

## H11 - Como consumidor, eu gostaria de filtrar os estabelecimentos por tipo de comida ou por nota de avaliação, para encontrar rapidamente opções que atendam ao que estou buscando.

| ID      | Condição de Entrada                                | Classe de Equivalência                                                                         | Resultado Esperado |
| ------- | -------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------ |
| H11-CE1 | Verificar o filtro por tipo de comida              | Filtro 'Vegetariana' retorna apenas estabelecimentos vegetarianos.                             | Válida             |
| H11-CE2 | Verificar o filtro por nota mínima de avaliação    | Filtro 'nota mínima 4' retorna apenas estabelecimentos com nota ≥ 4.                           | Válida             |
| H11-CE3 | Verificar a aplicação de filtros combinados        | Filtro 'Vegetariana' + 'nota mínima 4' retorna apenas locais que atendem a ambos os critérios. | Válida             |
| H11-CE4 | Verificar a mensagem para busca sem resultados     | Filtro aplicado não encontra resultados e exibe uma mensagem amigável.                         | Válida             |
| H11-CE5 | Verificar a funcionalidade de limpar filtros       | Clicar em 'Limpar filtros' remove todos os critérios e exibe a lista completa.                 | Válida             |
| H11-CE6 | Verificar critérios de desempate                   | Ordenação por 'melhor avaliado' usa nº de avaliações e proximidade como desempate              | Válida             |

## H12 - Como dono do estabelecimento, eu gostaria de atualizar meu perfil no app para informar os consumidores sobre mudanças e manter meu perfil atrativo.

| ID      | Condição de Entrada                                | Classe de Equivalência                                          | Resultado Esperado   |
| ------- | -------------------------------------------------- | --------------------------------------------------------------- | -------------------- |
| H12-CE1 | Verificar se o usuário tem permissão para editar   | Usuário autenticado com perfil de 'dono' do estabelecimento     | Válida               |
| H12-CE2 | Verificar se o usuário tem permissão para editar   | Usuário comum tenta editar o perfil do estabelecimento          | Inválida (Bloqueado) |
| H12-CE3 | Verificar o formato e tamanho da imagem            | Imagem no formato JPG/PNG e com até 5MB                         | Válida               |
| H12-CE4 | Verificar o formato e tamanho da imagem            | Imagem em formato não suportado (ex: .gif)                      | Inválida (Rejeitado) |
| H12-CE5 | Verificar o formato e tamanho da imagem            | Imagem com tamanho maior que 5MB                                | Inválida (Rejeitado) |
| H12-CE6 | Verificar o filtro de linguagem ofensiva           | Texto nos campos 'nome' e 'descrição' sem palavras da blacklist | Válida               |
| H12-CE7 | Verificar o filtro de linguagem ofensiva           | Texto nos campos 'nome' e 'descrição' com palavras da blacklist | Inválida (Rejeitado) |
| H12-CE8 | Verificar limite de imagens                        | Envio de até 1 logo e 4 fotos adicionais                        | Válida               |
| H12-CE9 | Verificar limite de imagens                        | Tentativa de enviar uma 6ª imagem (além do logo e 4 fotos)      | Inválida (Bloqueado) |

## H14 – Como dono de um estabelecimento, eu gostaria de cadastrar meu próprio estabelecimento na plataforma para que os consumidores possam avaliar nos meus serviços.

| ID      | Condição de Entrada                                   | Classe de Equivalência                                                                 | Resultado Esperado   |
| ------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------- |
| H14-CE1 | Verificar se o usuário tem perfil para cadastrar      | Usuário com perfil de 'Dono de Estabelecimento'                                        | Válida               |
| H14-CE2 | Verificar se os campos obrigatórios foram preenchidos | Nome, tipo, endereço, horário e contato estão preenchidos                              | Válida               |
| H14-CE3 | Verificar se os campos obrigatórios foram preenchidos | Pelo menos um dos campos obrigatórios está vazio                                       | Inválida (Rejeitado) |
| H14-CE4 | Verificar se o nome do estabelecimento é único        | Nome do estabelecimento não está duplicado na mesma rua (ignorando maiúsculas/acentos) | Válida               |
| H14-CE5 | Verificar se o nome do estabelecimento é único        | Nome já existe para outro cadastro na mesma rua                                        | Inválida (Rejeitado) |
| H14-CE6 | Verificar o limite de estabelecimentos por dono       | Dono tenta cadastrar seu 11º estabelecimento                                           | Inválida (Bloqueado) |
| H14-CE7 | Verificar a validação de imagens                      | Imagem de capa não contém conteúdo impróprio (análise via API)                         | Válida               |
| H14-CE8 | Verificar a validação de imagens                      | Imagem de capa contém conteúdo impróprio                                               | Inválida (Rejeitado) |

## H15 - Como Moderadora da plataforma, eu gostaria de analisar relatos de usuários para manter a veracidade das informações publicadas antes de exibi-los publicamente.
   
| ID      | Condição de Entrada                            | Classe de Equivalência                                                  | Resultado Esperado       |
| ------- | ---------------------------------------------- | ----------------------------------------------------------------------- | ------------------------ |
| H15-CE1 | Verificar se o usuário tem permissão de acesso | Usuário com perfil de 'Moderador' ou 'Administrador' acessa o painel    | Válida                   |
| H15-CE2 | Verificar se o usuário tem permissão de acesso | Usuário comum ou dono tenta acessar o painel                            | Inválida (Acesso Negado) |
| H15-CE3 | Verificar a ação de 'Aprovar'                  | Moderadora 'Aprova' um relato, e ele se torna público                   | Válida                   |
| H15-CE4 | Verificar a ação de 'Rejeitar'                 | Moderadora 'Rejeita' um relato, e ele permanece invisível               | Válida                   |
| H15-CE5 | Verificar o bloqueio automático de conteúdo    | Conteúdo com termos da blacklist é marcado para análise e não publicado | Válida                   |
| H15-CE6 | Verificar a retenção de relatos rejeitados     | Relato rejeitado é excluído permanentemente após 12 meses               | Válida (Verificar no BD) |

## H16 - Como Moderadora da plataforma, eu gostaria de uma funcionalidade de histórico dos usuários para analisar o comportamento dos usuários.

| ID      | Condição de Entrada                                   | Classe de Equivalência                                                    | Resultado Esperado             |
| ------- | ----------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------ |
| H16-CE1 | Verificar a permissão para visualizar históricos      | Usuário é 'Moderador' ou 'Administrador'                                  | Válida                         |
| H16-CE2 | Verificar a permissão para visualizar históricos      | Usuário comum tenta acessar o histórico de outro                          | Inválida (Acesso Negado)       |
| H16-CE3 | Verificar o acesso a dados sensíveis (Admin)          | Administrador visualiza dados sensíveis (nome, e-mail, etc.)              | Válida                         |
| H16-CE4 | Verificar o acesso a dados sensíveis (Moderador)      | Moderador padrão é impedido de ver dados sensíveis                        | Válida                         |
| H16-CE5 | Verificar o filtro por intervalo de datas             | Filtro com intervalo dentro dos últimos 12 meses                          | Válida                         |
| H16-CE6 | Verificar o filtro por intervalo de datas (Moderador) | Moderador tenta filtrar com intervalo maior que 12 meses                  | Inválida (Limitado a 12 meses) |
| H16-CE7 | Verificar o filtro por intervalo de datas (Admin)     | Administrador filtra com intervalo maior que 12 meses, mediante permissão | Válida                         |
| H16-CE8 | Verificar os tipos de ações registradas               | Histórico exibe ações como 'Login', 'logout' e 'envio de comentário'      | Válida                         |
