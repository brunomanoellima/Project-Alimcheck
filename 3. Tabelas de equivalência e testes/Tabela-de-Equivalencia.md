## H1 - Como consumidor, eu gostaria de avaliar estabelecimentos de alimentação para ajudar outros usuários a escolherem locais seguros e de qualidade.

**Critérios de Aceitação**  
- O usuário pode atribuir notas de 1 a 5 para critérios como higiene, qualidade da comida, atendimento, tempo de espera e preço justo.  
- A avaliação deve incluir pelo menos um critério com nota preenchida.  
- O campo de comentário é opcional, mas, se preenchido, deve:  
  - Conter no mínimo 10 caracteres alfanuméricos.  
  - Ser validado contra uma blacklist de palavras ofensivas.  
- O sistema deve rejeitar:  
  - Avaliações sem nenhum critério preenchido.  
  - Comentários com menos de 10 caracteres ou com palavras ofensivas.  
- Cada usuário pode avaliar o mesmo estabelecimento apenas uma vez por semana, exibindo a mensagem: "Você já avaliou este estabelecimento nesta semana" em tentativas adicionais.  
- Feedback visual deve ser exibido para avaliações rejeitadas, explicando o motivo.

**Regras de Negócio**  
- Notas devem estar no intervalo de 1 a 5; valores fora desse intervalo são rejeitados.  
- Pelo menos um critério deve ser avaliado para submissão da avaliação.  
- Comentários, se fornecidos, devem ter 10 ou mais caracteres alfanuméricos e não conter palavras da blacklist.  
- A frequência de avaliações é limitada a uma por semana por estabelecimento por usuário.  
- O sistema mantém uma blacklist atualizada de palavras ofensivas para validação de comentários.

| Condição de Entrada             | Classes Válidas                                             | Classes Inválidas                               | Classes Inválidas               |
| ------------------------------- | ----------------------------------------------------------- | ----------------------------------------------- | ------------------------------- |
| **Preenchimento dos Critérios** | Avaliação contém pelo menos um critério com nota (Higiene, Qualidade da comida, Atendimento, Tempo de espera, Preço justo) **(1)**    | Avaliação enviada sem nenhuma nota **(2)**      |                                 |
| **Nota da Avaliação**           | A nota está entre 1 e 5 **(3)**                             | A nota é menor que 1 **(4)**                    | A nota é maior que 5 **(5)**    |
| **Comprimento do Comentário**   | Comentário tem 10 ou mais caracteres **(6)**                | Comentário tem menos de 10 caracteres **(7)**   |                                 |
| **Conteúdo do Comentário**      | Não contém palavras da blacklist **(8)**                    | Contém palavras da blacklist **(9)**            |                                 |
| **Frequência de Avaliação**     | 1ª avaliação na semana para o estabelecimento **(10)**      | Já existe avaliação na mesma semana **(11)**    |                                 |

---

##  H2 - Como consumidor, eu gostaria de acessar de forma ágil informações de higiene e avaliações de estabelecimentos alimentícios para tomar decisões seguras e informadas sobre onde comer ou comprar alimentos.

**Critérios de Aceitação**  
- O sistema deve exibir a data da última inspeção de higiene do estabelecimento.  
- Dados com mais de 12 meses devem exibir um alerta visual indicando desatualização.  
- Se o estabelecimento possuir dados de higiene, eles devem ser exibidos; caso contrário, uma mensagem de ausência deve ser mostrada.  
- Usuários autenticados podem visualizar comentários detalhados de avaliações.  
- Usuários não autenticados visualizam apenas dados gerais, sem comentários detalhados.  
- O acesso à busca de informações deve ser possível pelo caminho: Tela inicial > Menu > Busca.

**Regras de Negócio**  
- Dados de higiene com menos de 12 meses são considerados válidos sem alerta.  
- Dados com mais de 12 meses acionam um alerta visual.  
- A ausência de dados de higiene resulta em uma mensagem específica ao usuário.  
- Comentários detalhados são restritos a usuários autenticados.  
- O fluxo de busca deve seguir o caminho especificado na interface.

| Condição de Entrada           | Classes Válidas                                        | Classes Inválidas                                      |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------------------------ |
| **Atualização dos Dados**     | Dados da inspeção com menos de 12 meses **(12)**       | Dados da inspeção com mais de 12 meses **(13)**        |
| **Disponibilidade dos Dados** | Estabelecimento possui dados de higiene **(14)**       | Estabelecimento não possui dados de higiene **(15)**   |
| **Nível de Acesso**           | Usuário está autenticado **(16)**                      | Usuário não está autenticado **(17)**                  |
| **Ordenação das Avaliações**  | Ordena por relevância, data ou nota **(18)**           |                                                        |

---

## H3 - Como consumidor, eu gostaria de registrar relatos e denúncias sobre problemas de qualidade alimentar, como má higiene ou alimentos vencidos, para alertar outros usuários e os próprios comerciantes.

**Critérios de Aceitação**  
- O usuário deve selecionar um tipo de problema (e.g., higiene, alimento vencido) de uma lista predefinida.  
- A descrição da denúncia deve conter no mínimo 20 caracteres.  
- O usuário pode anexar uma foto como evidência, em formato permitido (e.g., JPG, PNG).  
- Cada usuário pode registrar até uma denúncia por estabelecimento a cada 24 horas.  
- A denúncia deve ser vinculada a um estabelecimento existente na base de dados.  
- O sistema deve rejeitar descrições com menos de 20 caracteres ou denúncias repetidas dentro de 24 horas, exibindo feedback visual.

**Regras de Negócio**  
- A seleção de um tipo de problema é obrigatória.  
- Descrições com menos de 20 caracteres são rejeitadas.  
- Anexos de fotos são opcionais e devem estar em formatos suportados.  
- A frequência de denúncias é limitada a uma por estabelecimento por usuário a cada 24 horas.  
- Denúncias devem ser associadas a estabelecimentos registrados.


| Condição de Entrada           | Classes Válidas                                                  | Classes Inválidas                                      |
| ----------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------ |
| **Vinculação com Estab.**     | Denúncia é associada a um estabelecimento existente **(19)**     | Denúncia não é associada a um estabelecimento **(20)** |
| **Tipo de Problema**          | Seleciona uma opção predefinida da lista (Higiene, Alimento vencido, Armazenamento inadequado, Atendimento insatisfatório) **(21)**                |                                                        |
| **Comprimento da Descrição**  | Descrição com 20 ou mais caracteres **(22)**                     | Descrição com menos de 20 caracteres **(23)**          |
| **Frequência de Denúncia**    | 1ª denúncia nas últimas 24h para o estabelecimento **(24)**      | Já existe denúncia nas últimas 24h **(25)**            |
| **Anexo de Arquivo**          | Anexa uma foto (opcional) **(26)**                               |                                                        |

---

## H5 - Como consumidor, eu gostaria de receber alertas sobre locais denunciados ou avaliados negativamente, para evitar riscos à saúde.

**Critérios de Aceitação**  
- O usuário deve ter a opção de ativar ou desativar alertas nas configurações do perfil.  
- Alertas são disparados para estabelecimentos com:  
  - 4 ou mais denúncias válidas.  
  - Nota média inferior a 2.5 (baseada nos últimos 30 dias).  
- Nenhum alerta é enviado se o estabelecimento tiver menos de 4 denúncias ou nota média ≥ 2.5.  
- Alertas não são enviados para o mesmo usuário/estabelecimento dentro de 7 dias.  
- Denúncias rejeitadas pela moderação não contam para o gatilho de alertas.  
- Alertas devem ser enviados via notificação push e exibidos in-app.

**Regras de Negócio**  
- Alertas dependem da configuração ativada no perfil do usuário.  
- Gatilhos de alerta são baseados em 4+ denúncias válidas ou nota média < 2.5 nos últimos 30 dias.  
- Um intervalo mínimo de 7 dias é exigido entre alertas para o mesmo usuário/estabelecimento.  
- Denúncias rejeitadas não são contabilizadas.  
- O canal de entrega inclui notificações push e exibição in-app.

| Condição de Entrada           | Classes Válidas                                                          | Classes Inválidas                                                            |
| ----------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| **Configuração de Alertas**   | Alertas estão ativados no perfil **(27)**                                | Alertas estão desativados no perfil **(28)**                                 |
| **Gatilho de Alerta**         | 4 ou mais denúncias; OU nota média < 2.5 **(29)**                        | Menos de 4 denúncias E nota média ≥ 2.5 **(30)**                             |
| **Frequência de Alerta**      | Nenhum alerta para o mesmo local/usuário nos últimos 7 dias **(31)**     | Já foi enviado alerta para o mesmo local/usuário nos últimos 7 dias **(32)** |
| **Contagem de Denúncias**     | Denúncias rejeitadas pela moderação não são contadas **(33)**            |                                                                              |

---

## H6 - Como consumidor, eu gostaria de receber recomendações personalizadas de locais seguros com base nas minhas preferências alimentares e avaliações anteriores.

**Critérios de Aceitação**  
- Recomendações devem corresponder às preferências selecionadas no perfil (e.g., vegetariano).  
- Recomendações são influenciadas por estabelecimentos que o usuário avaliou com nota ≥ 4.0.  
- O usuário pode aplicar filtros de distância, preço ou tipo de comida às recomendações.  
- O usuário pode marcar uma recomendação como "não relevante" para refinar sugestões futuras.  
- Novos usuários sem histórico recebem recomendações genéricas.

**Regras de Negócio**  
- Preferências do perfil (e.g., tipo de comida) são a base primária para recomendações.  
- Avaliações com nota ≥ 4.0 influenciam o algoritmo de recomendação.  
- Filtros de distância, preço ou tipo de comida devem ser aplicados corretamente.  
- Feedback de "não relevante" é usado para ajustar futuras recomendações.  
- Recomendações genéricas são fornecidas para usuários sem histórico.


| Condição de Entrada            | Classes Válidas                                                        | Classes Inválidas                                     |
| ------------------------------ | ---------------------------------------------------------------------- | ----------------------------------------------------- |
| **Base para Recomendação**     | Usuário tem preferências cadastradas OU avaliações anteriores **(34)** | Usuário novo sem preferências ou avaliações **(35)**  |
| **Filtro de Recomendações**    | Filtra por distância, preço ou tipo de comida **(36)**                 |                                                       |
| **Feedback na Recomendação**   | Marca uma recomendação como "não relevante" **(37)**                   |                                                       |

---

## H9 - Como consumidor, eu gostaria de excluir minha conta se eu decidir parar de usar o serviço. 

**Critérios de Aceitação**  
- O usuário deve estar autenticado para iniciar o processo de exclusão.  
- A exclusão exige a validação da senha atual do usuário.  
- O usuário deve confirmar a exclusão clicando em um botão (e.g., "Sim, excluir").  
- O usuário pode cancelar a exclusão na tela de confirmação.  
- Após a exclusão, os dados pessoais devem ser apagados ou anonimizados conforme a LGPD.  
- O usuário deve receber um e-mail confirmando a exclusão da conta.  
- Senhas incorretas resultam em rejeição com feedback visual.

**Regras de Negócio**  
- Apenas usuários autenticados podem excluir suas contas.  
- A senha atual deve ser validada para prosseguir com a exclusão.  
- A confirmação final é obrigatória, com opção de cancelamento.  
- Dados pessoais são tratados conforme a LGPD após exclusão.  
- Um e-mail de confirmação é enviado ao usuário.

| Condição de Entrada           | Classes Válidas                                                   | Classes Inválidas                                     |
| ----------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------- |
| **Status do Usuário**         | Usuário está autenticado **(38)**                                 | Usuário não está autenticado **(39)**                 |
| **Validação de Segurança**    | Senha atual informada corretamente **(40)**                       | Senha atual informada incorretamente **(41)**         |
| **Ação de Confirmação**       | Clica no botão final para confirmar a exclusão **(42)**           | Clica em "Cancelar" na tela de confirmação **(43)**   |
| **Tratamento do Conteúdo**    | Conteúdo do usuário (avaliações) é mantido e anonimizado **(44)** |                                                       |

---

## H10 - Como consumidor, eu gostaria de ver um mapa com a localização dos estabelecimentos cadastrados, para encontrar os melhores locais próximos a mim.

**Critérios de Aceitação**  
- O sistema deve solicitar permissão de localização do usuário; se negada, permite inserir um endereço manualmente.  
- Estabelecimentos com coordenadas válidas são exibidos no mapa.  
- Estabelecimentos sem coordenadas não são exibidos.  
- O raio de busca é limitado a 10 km; buscas fora desse raio são rejeitadas.  
- Ao abrir o mapa, o raio padrão de busca é 2 km.

**Regras de Negócio**  
- A permissão de localização é opcional; um endereço manual pode ser usado.  
- Apenas estabelecimentos com geolocalização válida aparecem no mapa.  
- O raio de busca máximo é 10 km; o padrão é 2 km.  
- Buscas excedendo 10 km são limitadas automaticamente.

| Condição de Entrada             | Classes Válidas                                                 | Classes Inválidas                                        |
| ------------------------------- | --------------------------------------------------------------- | -------------------------------------------------------- |
| **Permissão de Localização**    | Usuário concede permissão **(45)**                              | Usuário nega permissão **(46)**                          |
| **Geolocalização do Estab.**    | Estabelecimento possui coordenadas válidas **(47)**             | Estabelecimento não possui coordenadas válidas **(48)**  |
| **Exibição no Marcador**        | Marcador do mapa exibe Nome, Nota e Categoria **(49)**          |                                                          |
| **Raio de Busca**               | Busca dentro do raio máximo de 10km **(50)**                    | Busca excede o raio de 10km **(51)**                     |

---

## H11 - Como consumidor, eu gostaria de filtrar os estabelecimentos por tipo de comida ou por nota de avaliação, para encontrar rapidamente opções que atendam ao que estou buscando.

**Critérios de Aceitação**  
- O usuário pode filtrar por tipo de comida (e.g., vegetariana).  
- O usuário pode filtrar por nota mínima (e.g., ≥ 4).  
- Filtros podem ser combinados (e.g., vegetariana + nota ≥ 4).  
- Se a busca não retornar resultados, uma mensagem amigável é exibida.  
- O usuário pode limpar todos os filtros, retornando à lista completa.  
- A ordenação por "melhor avaliado" usa número de avaliações e proximidade como desempate.

**Regras de Negócio**  
- Filtros por tipo de comida e nota mínima devem retornar resultados precisos.  
- Combinações de filtros são aplicadas corretamente.  
- A ausência de resultados gera uma mensagem amigável.  
- A funcionalidade de limpar filtros restaura a lista completa.  
- Critérios de desempate incluem número de avaliações e proximidade.

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

**Critérios de Aceitação**  
- Apenas usuários com perfil "dono" podem editar o perfil do estabelecimento.  
- Imagens enviadas devem estar em formato JPG/PNG e ter até 5 MB.  
- Textos nos campos "nome" e "descrição" devem ser validados contra uma blacklist de palavras ofensivas.  
- O sistema permite enviar até 1 logo e 4 fotos adicionais.  
- Tentativas de enviar imagens em formatos não suportados, maiores que 5 MB, ou uma 6ª imagem são rejeitadas com feedback visual.  
- Tentativas de edição por usuários sem permissão são bloqueadas.

**Regras de Negócio**  
- Apenas usuários com perfil "dono" têm permissão para editar.  
- Imagens devem ser JPG/PNG e ≤ 5 MB; outros formatos ou tamanhos são rejeitados.  
- Textos são validados contra a blacklist de palavras ofensivas.  
- O limite de imagens é 1 logo + 4 fotos; tentativas de exceder são bloqueadas.

| Condição de Entrada            | Classes Válidas                                               | Classes Inválidas                                      |
| ------------------------------ | ------------------------------------------------------------- | ------------------------------------------------------ |
| **Permissão de Edição**        | Usuário é autenticado como "dono" do estabelecimento **(58)** | Usuário não tem permissão para editar **(59)**         |
| **Upload de Imagem (Formato)** | Imagem é JPG ou PNG **(60)**                                  | Imagem tem formato não suportado (ex: GIF) **(61)**    |
| **Upload de Imagem (Tamanho)** | Imagem tem até 5MB **(62)**                                   | Imagem tem mais de 5MB **(63)**                        |
| **Limite de Imagens**          | Envia até 5 imagens (1 logo + 4 fotos) **(64)**               | Tenta enviar a 6ª imagem **(65)**                      |
| **Conteúdo dos Textos**        | Campos de texto não contêm palavras da blacklist **(66)**     | Campos de texto contêm palavras da blacklist **(67)**  |

---

## H14 – Como dono de um estabelecimento, eu gostaria de cadastrar meu próprio estabelecimento na plataforma para que os consumidores possam avaliar nos meus serviços.

**Critérios de Aceitação**  
- Apenas usuários com perfil "Dono de Estabelecimento" podem cadastrar.  
- Campos obrigatórios (nome, tipo, endereço, horário, contato) devem ser preenchidos.  
- O nome do estabelecimento deve ser único na mesma rua, ignorando maiúsculas e acentos.  
- Um dono pode cadastrar até 10 estabelecimentos; o 11º é rejeitado.  
- Imagens de capa são validadas contra conteúdo impróprio via API.  
- O sistema rejeita cadastros com campos obrigatórios vazios, nomes duplicados, ou imagens impróprias, exibindo feedback visual.

**Regras de Negócio**  
- O perfil "Dono de Estabelecimento" é necessário para cadastro.  
- Todos os campos obrigatórios devem ser preenchidos.  
- Nomes de estabelecimentos devem ser únicos na mesma rua.  
- O limite de cadastros por dono é 10 estabelecimentos.  
- Imagens de capa são analisadas para detectar conteúdo impróprio.

| Condição de Entrada             | Classes Válidas                                               | Classes Inválidas                                               |
| ------------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------- |
| **Perfil do Usuário**           | Usuário tem perfil de "Dono de Estabelecimento" **(68)**      | Usuário não tem perfil de "Dono" **(69)**                       |
| **Preenchimento do Formulário** | Todos os campos obrigatórios estão preenchidos **(70)**       | Pelo menos um campo obrigatório está vazio **(71)**             |
| **Unicidade do Nome**           | Nome do estabelecimento é único na mesma rua **(72)**         | Nome já existe para outro estabelecimento na mesma rua **(73)** |
| **Limite de Cadastros**         | Dono possui menos de 10 estabelecimentos cadastrados **(74)** | Dono já possui 10 estabelecimentos cadastrados **(75)**         |

---

## H15 - Como Moderadora da plataforma, eu gostaria de analisar relatos de usuários para manter a veracidade das informações publicadas antes de exibi-los publicamente.

**Critérios de Aceitação**  
- Apenas usuários com perfil "Moderador" ou "Administrador" podem acessar o painel de moderação.  
- A moderadora pode aprovar um relato, tornando-o público, ou rejeitá-lo, mantendo-o invisível.  
- Conteúdo com termos da blacklist é automaticamente marcado para análise e não publicado.  
- Relatos rejeitados são excluídos permanentemente após 12 meses.  
- Tentativas de acesso ao painel por usuários sem permissão são bloqueadas com mensagem de erro.

**Regras de Negócio**  
- O acesso ao painel é restrito a perfis "Moderador" ou "Administrador".  
- Ações de aprovação ou rejeição alteram a visibilidade dos relatos.  
- A blacklist bloqueia automaticamente conteúdo ofensivo para análise.  
- Relatos rejeitados são retidos por 12 meses antes da exclusão.


| Condição de Entrada       | Classes Válidas                                                  | Classes Inválidas                                  |
| ------------------------- | ---------------------------------------------------------------- | -------------------------------------------------- |
| **Permissão de Acesso**   | Usuário tem perfil de "Moderador" ou "Administrador" **(76)**    | Usuário tem perfil comum ou de "Dono" **(77)**     |
| **Ação de Moderação**     | Modera um relato como "Aprovar" ou "Rejeitar" **(78)**           |                                                    |
| **Bloqueio Automático**   | Relato com termos da blacklist é enviado para moderação **(79)** |                                                    |

---

## H16 - Como Moderadora da plataforma, eu gostaria de uma funcionalidade de histórico dos usuários para analisar o comportamento dos usuários.

**Como moderadora da plataforma**, eu gostaria de uma funcionalidade de histórico dos usuários para analisar o comportamento dos usuários.

**Critérios de Aceitação**  
- Apenas usuários com perfil "Moderador" ou "Administrador" podem visualizar históricos.  
- Administradores visualizam dados sensíveis (e.g., nome, e-mail); moderadores padrão não.  
- O filtro por intervalo de datas permite:  
  - Moderadores filtrarem até 12 meses.  
  - Administradores filtrarem além de 12 meses com permissão.  
- O histórico exibe ações como login, logout e envio de comentário.  
- Tentativas de acesso por usuários comuns são bloqueadas com mensagem de erro.  
- Filtros de datas maiores que 12 meses por moderadores são rejeitados.

**Regras de Negócio**  
- O acesso ao histórico é restrito a perfis "Moderador" ou "Administrador".  
- Dados sensíveis são visíveis apenas para administradores.  
- Moderadores estão limitados a filtros de até 12 meses; administradores podem exceder com permissão.  
- O histórico registra ações específicas (login, logout, envio de comentário).

| Condição de Entrada            | Classes Válidas                                                      | Classes Inválidas                                          |
| ------------------------------ | -------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Permissão de Visualização**  | Usuário é "Moderador" ou "Administrador" **(80)**                    | Usuário é comum ou "Dono" **(81)**                         |
| **Acesso a Dados Sensíveis**   | Administrador tenta visualizar dados sensíveis **(82)**              | Moderador padrão tenta visualizar dados sensíveis **(83)** |
| **Filtro por Datas**           | Filtro de data com intervalo de até 12 meses **(84)**                | Moderador tenta filtrar por mais de 12 meses **(85)**      |
| **Filtro por Tipo de Ação**    | Filtra o histórico por tipo de ação (ex: login, comentário) **(86)** |                                                            |
