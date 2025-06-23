## H1 - Como consumidor, eu gostaria de avaliar estabelecimentos de alimentação para ajudar outros usuários a escolherem locais seguros e de qualidade.

| Condição de Entrada             | Classes Válidas                                             | Classes Inválidas                               | Classes Inválidas               |
| ------------------------------- | ----------------------------------------------------------- | ----------------------------------------------- | ------------------------------- |
| **Preenchimento dos Critérios** | Avaliação contém pelo menos um critério com nota (Higiene, Qualidade da comida, Atendimento, Tempo de espera, Preço justo) **(1)**    | Avaliação enviada sem nenhuma nota **(2)**      |                                 |
| **Nota da Avaliação**           | A nota está entre 1 e 5 **(3)**                             | A nota é menor que 1 **(4)**                    | A nota é maior que 5 **(5)**    |
| **Comprimento do Comentário**   | Comentário tem 10 ou mais caracteres **(6)**                | Comentário tem menos de 10 caracteres **(7)**   |                                 |
| **Conteúdo do Comentário**      | Não contém palavras da blacklist **(8)**                    | Contém palavras da blacklist **(9)**            |                                 |
| **Frequência de Avaliação**     | 1ª avaliação na semana para o estabelecimento **(10)**      | Já existe avaliação na mesma semana **(11)**    |                                 |

---

##  H2 - Como consumidor, eu gostaria de acessar de forma ágil informações de higiene e avaliações de estabelecimentos alimentícios para tomar decisões seguras e informadas sobre onde comer ou comprar alimentos.

| Condição de Entrada           | Classes Válidas                                        | Classes Inválidas                                      |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------------------------ |
| **Atualização dos Dados**     | Dados da inspeção com menos de 12 meses **(12)**       | Dados da inspeção com mais de 12 meses **(13)**        |
| **Disponibilidade dos Dados** | Estabelecimento possui dados de higiene **(14)**       | Estabelecimento não possui dados de higiene **(15)**   |
| **Nível de Acesso**           | Usuário está autenticado **(16)**                      | Usuário não está autenticado **(17)**                  |
| **Ordenação das Avaliações**  | Ordena por relevância, data ou nota **(18)**           |                                                        |

---

## H3 - Como consumidor, eu gostaria de registrar relatos e denúncias sobre problemas de qualidade alimentar, como má higiene ou alimentos vencidos, para alertar outros usuários e os próprios comerciantes.

| Condição de Entrada           | Classes Válidas                                                  | Classes Inválidas                                      |
| ----------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------ |
| **Vinculação com Estab.**     | Denúncia é associada a um estabelecimento existente **(19)**     | Denúncia não é associada a um estabelecimento **(20)** |
| **Tipo de Problema**          | Seleciona uma opção predefinida da lista (Higiene, Alimento vencido, Armazenamento inadequado, Atendimento insatisfatório) **(21)**                |                                                        |
| **Comprimento da Descrição**  | Descrição com 20 ou mais caracteres **(22)**                     | Descrição com menos de 20 caracteres **(23)**          |
| **Frequência de Denúncia**    | 1ª denúncia nas últimas 24h para o estabelecimento **(24)**      | Já existe denúncia nas últimas 24h **(25)**            |
| **Anexo de Arquivo**          | Anexa uma foto (opcional) **(26)**                               |                                                        |

---

## H5 - Como consumidor, eu gostaria de receber alertas sobre locais denunciados ou avaliados negativamente, para evitar riscos à saúde.

| Condição de Entrada           | Classes Válidas                                                          | Classes Inválidas                                                            |
| ----------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| **Configuração de Alertas**   | Alertas estão ativados no perfil **(27)**                                | Alertas estão desativados no perfil **(28)**                                 |
| **Gatilho de Alerta**         | 4 ou mais denúncias; OU nota média < 2.5 **(29)**                        | Menos de 4 denúncias E nota média ≥ 2.5 **(30)**                             |
| **Frequência de Alerta**      | Nenhum alerta para o mesmo local/usuário nos últimos 7 dias **(31)**     | Já foi enviado alerta para o mesmo local/usuário nos últimos 7 dias **(32)** |
| **Contagem de Denúncias**     | Denúncias rejeitadas pela moderação não são contadas **(33)**            |                                                                              |

---

## H6 - Como consumidor, eu gostaria de receber recomendações personalizadas de locais seguros com base nas minhas preferências alimentares e avaliações anteriores.

| Condição de Entrada            | Classes Válidas                                                        | Classes Inválidas                                     |
| ------------------------------ | ---------------------------------------------------------------------- | ----------------------------------------------------- |
| **Base para Recomendação**     | Usuário tem preferências cadastradas OU avaliações anteriores **(34)** | Usuário novo sem preferências ou avaliações **(35)**  |
| **Filtro de Recomendações**    | Filtra por distância, preço ou tipo de comida **(36)**                 |                                                       |
| **Feedback na Recomendação**   | Marca uma recomendação como "não relevante" **(37)**                   |                                                       |

---

## H9 - Como consumidor, eu gostaria de excluir minha conta se eu decidir parar de usar o serviço. 

| Condição de Entrada           | Classes Válidas                                                   | Classes Inválidas                                     |
| ----------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------- |
| **Status do Usuário**         | Usuário está autenticado **(38)**                                 | Usuário não está autenticado **(39)**                 |
| **Validação de Segurança**    | Senha atual informada corretamente **(40)**                       | Senha atual informada incorretamente **(41)**         |
| **Ação de Confirmação**       | Clica no botão final para confirmar a exclusão **(42)**           | Clica em "Cancelar" na tela de confirmação **(43)**   |
| **Tratamento do Conteúdo**    | Conteúdo do usuário (avaliações) é mantido e anonimizado **(44)** |                                                       |

---

## H10 - Como consumidor, eu gostaria de ver um mapa com a localização dos estabelecimentos cadastrados, para encontrar os melhores locais próximos a mim.

| Condição de Entrada             | Classes Válidas                                                 | Classes Inválidas                                        |
| ------------------------------- | --------------------------------------------------------------- | -------------------------------------------------------- |
| **Permissão de Localização**    | Usuário concede permissão **(45)**                              | Usuário nega permissão **(46)**                          |
| **Geolocalização do Estab.**    | Estabelecimento possui coordenadas válidas **(47)**             | Estabelecimento não possui coordenadas válidas **(48)**  |
| **Exibição no Marcador**        | Marcador do mapa exibe Nome, Nota e Categoria **(49)**          |                                                          |
| **Raio de Busca**               | Busca dentro do raio máximo de 10km **(50)**                    | Busca excede o raio de 10km **(51)**                     |

---

## H11 - Como consumidor, eu gostaria de filtrar os estabelecimentos por tipo de comida ou por nota de avaliação, para encontrar rapidamente opções que atendam ao que estou buscando.

| Condição de Entrada            | Classes Válidas                                                              |
| ------------------------------ | ---------------------------------------------------------------------------- |
| **Tipo de Filtro**             | Filtra por tipo de comida **(52)**                                           |
| **Filtro por Nota**            | Filtra por nota mínima **(53)**                                              |
| **Filtros Combinados**         | Aplica múltiplos filtros simultaneamente (lógica E) **(54)**                 |
| **Ordenação de Resultados**    | Ordena por "melhor avaliado" **(55)**                                        |
| **Limpeza de Filtros**         | Clica no botão para limpar todos os filtros aplicados **(56)**               |
| **Busca Sem Resultados**       | Filtro aplicado não encontra correspondências **(57)**                       |

---

## H12 - Como dono do estabelecimento, eu gostaria de atualizar meu perfil no app para informar os consumidores sobre mudanças e manter meu perfil atrativo.

| Condição de Entrada            | Classes Válidas                                               | Classes Inválidas                                      |
| ------------------------------ | ------------------------------------------------------------- | ------------------------------------------------------ |
| **Permissão de Edição**        | Usuário é autenticado como "dono" do estabelecimento **(58)** | Usuário não tem permissão para editar **(59)**         |
| **Upload de Imagem (Formato)** | Imagem é JPG ou PNG **(60)**                                  | Imagem tem formato não suportado (ex: GIF) **(61)**    |
| **Upload de Imagem (Tamanho)** | Imagem tem até 5MB **(62)**                                   | Imagem tem mais de 5MB **(63)**                        |
| **Limite de Imagens**          | Envia até 5 imagens (1 logo + 4 fotos) **(64)**               | Tenta enviar a 6ª imagem **(65)**                      |
| **Conteúdo dos Textos**        | Campos de texto não contêm palavras da blacklist **(66)**     | Campos de texto contêm palavras da blacklist **(67)**  |

---

## H14 – Como dono de um estabelecimento, eu gostaria de cadastrar meu próprio estabelecimento na plataforma para que os consumidores possam avaliar nos meus serviços.

| Condição de Entrada             | Classes Válidas                                               | Classes Inválidas                                               |
| ------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| **Perfil do Usuário**           | Usuário tem perfil de "Dono de Estabelecimento" **(68)**      | Usuário não tem perfil de "Dono" **(69)**                       |
| **Preenchimento do Formulário** | Todos os campos obrigatórios estão preenchidos **(70)**       | Pelo menos um campo obrigatório está vazio **(71)**             |
| **Unicidade do Nome**           | Nome do estabelecimento é único na mesma rua **(72)**         | Nome já existe para outro estabelecimento na mesma rua **(73)** |
| **Limite de Cadastros**         | Dono possui menos de 10 estabelecimentos cadastrados **(74)** | Dono já possui 10 estabelecimentos cadastrados **(75)**         |

---

## H15 - Como Moderadora da plataforma, eu gostaria de analisar relatos de usuários para manter a veracidade das informações publicadas antes de exibi-los publicamente.

| Condição de Entrada       | Classes Válidas                                                  | Classes Inválidas                                  |
| ------------------------- | ---------------------------------------------------------------- | -------------------------------------------------- |
| **Permissão de Acesso**   | Usuário tem perfil de "Moderador" ou "Administrador" **(76)**    | Usuário tem perfil comum ou de "Dono" **(77)**     |
| **Ação de Moderação**     | Modera um relato como "Aprovar" ou "Rejeitar" **(78)**           |                                                    |
| **Bloqueio Automático**   | Relato com termos da blacklist é enviado para moderação **(79)** |                                                    |

---

## H16 - Como Moderadora da plataforma, eu gostaria de uma funcionalidade de histórico dos usuários para analisar o comportamento dos usuários.

| Condição de Entrada            | Classes Válidas                                                      | Classes Inválidas                                          |
| ------------------------------ | -------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Permissão de Visualização**  | Usuário é "Moderador" ou "Administrador" **(80)**                    | Usuário é comum ou "Dono" **(81)**                         |
| **Acesso a Dados Sensíveis**   | Administrador tenta visualizar dados sensíveis **(82)**              | Moderador padrão tenta visualizar dados sensíveis **(83)** |
| **Filtro por Datas**           | Filtro de data com intervalo de até 12 meses **(84)**                | Moderador tenta filtrar por mais de 12 meses **(85)**      |
| **Filtro por Tipo de Ação**    | Filtra o histórico por tipo de ação (ex: login, comentário) **(86)** |                                                            |
