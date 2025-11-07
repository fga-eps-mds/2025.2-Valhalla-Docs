# CASOS DE USO

## 1. Autenticação e Conta
##   1.1 Login de usuário
Este caso de uso descreve o processo de login, que permi4e ao usuário acessar o sistema utilizando suas credenciais institucionais. O objetivo é garantir que somente membros autorizados possam entrar na plataforma, de forma segura, rápida e controlada.
### 1.1.1 Pré-condições
- O usuário deve possuir uma conta previamente cadastrada. 
- O sistema deve estar conectado ao servidor e ao banco de dados de autenticação. 
- Deve haver conectividade com a internet. 
### 1.1.2  Fluxo básico
 1. O usuário acessa a tela inicial do sistema.

2. O sistema exibe os campos “E-mail” e “Senha”, além dos botões Entrar, Cadastre-se e Esqueci minha senha. 

3. O usuário insere o e-mail e a senha. 

4. O sistema valida o formato do e-mail. 

5. O sistema verifica se o e-mail existe no banco de dados. 

6. Caso exista, o sistema compara o hash da senha informada com o hash armazenado. 

7. Se as credenciais estiverem corretas, o sistema autentica o usuário e cria uma sessão segura. 

8. O sistema redireciona o usuário para a página inicial de denúncias (ou para o painel administrativo, se for administrador). 

9. Caso o usuário selecione “Manter-me conectado”, o sistema gera um token persistente para logins automáticos. 
### 1.1.3 Fluxo alternativo
- Se o e-mail não for encontrado, o sistema exibe a mensagem: “E-mail não cadastrado.” 
- Se a senha estiver incorreta, o sistema exibe: “Senha incorreta” 
- Se houver falha de conexão, o sistema exibe: “Não foi possível conectar ao servidor.” 
- Se o servidor estiver em manutenção, o sistema exibe: “Serviço temporariamente indisponível.” 
### 1.1.4 Pós-condições
- O usuário é autenticado e redirecionado para o ambiente correto. 
- O sistema registra o log de acesso. 
- A sessão do usuário é criada e armazenada temporariamente. 
### 1.1.5 Requisitos não funcionais
- O tempo máximo de autenticação deve ser de 3 segundos. 
- O sistema deve usar HTTPS e hash seguro (bcrypt/Argon2). 
- Interface responsiva e acessível. 
- O login deve ser compatível com diferentes navegadores e dispositivos. 
### 1.1.6 Referência cruzada
Relacionado ao requisito funcional 3.1 – Tela de Login. 

## 1.2 Cadastro de novo usuário
Este caso de uso descreve o processo de criação de uma nova conta no sistema. Ele garante que apenas usuários com e-mails válidos possam se registrar.

**Ator principal:** Usuário, Sistema.
### 1.2.1 Pré-condições
- O usuário deve possuir um e-mail válido. 
- O sistema deve estar conectado ao banco de dados de usuários. 
### 1.2.2 Fluxo básico
1. O usuário acessa a tela de login e clica em Cadastre-se. 
2. O sistema exibe o formulário de cadastro com os campos: Nome Completo, E-mail, Cargo/Ocupação, Senha e Confirmação de Senha. 
3. O usuário preenche os campos obrigatórios. 
4. O sistema valida: 

    - Se o nome possui ao menos dois nomes; 
    - Se o e-mail é válido; 
    - Se a senha contém letras maiúsculas, minúsculas, números e caracteres especiais. 
5. O sistema verifica se o e-mail já está cadastrado. 
6. Caso não esteja, cria o registro e armazena os dados. 
7. O sistema exibe a mensagem: “Cadastro realizado com sucesso.” 
8. O usuário é redirecionado para a tela de login. 

### 1.2.3 Fluxo alternativo
- Se o e-mail já estiver cadastrado, o sistema exibe: “E-mail já cadastrado.” 
- Se o e-mail não for válido, exibe: “E-mail inválido para cadastro.” 
- Se a senha for fraca, exibe: “Senha não atende aos requisitos mínimos.” 

### 1.2.4 Pós-condições
- O novo usuário é registrado e habilitado para login. 
- O sistema grava data e hora do cadastro. 

### 1.2.5 Requisitos não funcionais
- O formulário deve ser intuitivo e validado em tempo real. 
- O tempo total do cadastro não deve exceder 5 segundos. 
- O sistema deve aplicar boas práticas de usabilidade e acessibilidade. 

### 1.2.6 Referência cruzada
Relacionado ao requisito funcional 3.2 – Tela de Cadastro de Usuário. 

## 1.3 Recuperação de senha
Este caso de uso permite que o usuário redefina sua senha caso a tenha esquecido, garantindo segurança e controle no processo.

**Ator principal:** Usuário, Sistema.
### 1.3.1 Pré-condições
- O usuário deve possuir uma conta existente. 
- O sistema deve estar conectado ao serviço de e-mail. 

### 1.3.2 Fluxo básico
1. O usuário acessa a tela de login e clica em Esqueci minha senha. 

2. O sistema exibe o campo para inserção do e-mail. 
3. O usuário informa o e-mail. 
4. O sistema verifica se o e-mail está cadastrado. 
5. Caso positivo, o sistema gera um token temporário de redefinição de senha. 
6. O sistema envia um e-mail com o link seguro para redefinição. 
7. O usuário acessa o link e insere uma nova senha. 
8. O sistema valida a nova senha conforme as regras de complexidade. 
9. Se válida, o sistema atualiza o hash no banco de dados. 
10. O sistema exibe a mensagem: “Senha redefinida com sucesso.” 

### 1.3.3 Fluxo alternativo
- Se o e-mail não for encontrado, o sistema exibe: “E-mail não cadastrado.” 
- Se o link estiver expirado, o sistema solicita novo pedido de redefinição. 
- Se o servidor de e-mail estiver fora do ar, o sistema exibe: “Erro ao enviar e-mail, tente novamente mais tarde.” 

### 1.3.4 Pós-condições
- A senha do usuário é redefinida. 
- O sistema registra a ação no log de segurança. 

### 1.3.5 Requisitos não funcionais
- O link de redefinição deve expirar após 15 minutos. 
- Todo o processo deve ocorrer sob conexão segura (HTTPS). 
- Mensagens devem ser claras e orientativas. 

### 1.3.6 Referência cruzada
Relacionado ao requisito funcional 3.3 – Recuperação de Senha. 

## 1.4 Logout (Encerramento de sessão)
Este caso de uso descreve o encerramento da sessão do usuário, garantindo que os dados não permaneçam ativos após o uso.

**Ator principal:** Usuário, Sistema

### 1.4.1 Pré-condições
- O usuário deve estar logado. 

### 1.4.2 Fluxo básico
1. O usuário clica em Sair no menu de perfil. 

2. O sistema encerra a sessão ativa. 
3. O sistema limpa cookies e tokens temporários. 
4. O usuário é redirecionado para a tela de login. 
5. O sistema registra o evento no log de auditoria. 

### 1.4.3 Pós-condições
- Sessão encerrada com segurança. 
- Dados de sessão eliminados da memória local. 

### 1.4.4 Requisitos não funcionais
- O encerramento deve ocorrer em até 2 segundos.
- Tokens de sessão devem ser invalidados imediatamente. 

### 1.4.5 Referência cruzada
Relacionado ao requisito funcional 3.1 – Autenticação e 4.1 – Segurança de Sessão.

## 2. Página de perfil
## 2.1 Visualização de perfil
Este caso de uso descreve o processo em que o usuário acessa e visualiza suas informações pessoais dentro do sistema. O objetivo é permitir que o usuário tenha acesso rápido e claro aos seus dados de identificação, configurações de conta e histórico de uso, garantindo transparência e controle.

**Ator principal:** Usuário, Sistema

### 2.1.1 Pré-condições
- O usuário deve estar autenticado no sistema. 
- O módulo de perfil deve estar ativo e devidamente integrado ao banco de dados. 
- O sistema deve ter conexão estável com o servidor. 

### 2.1.2 Fluxo básico
1. O usuário acessa o menu lateral e seleciona a opção Meu Perfil. 

2. O sistema carrega as informações do usuário: nome completo, e-mail, data de criação da conta e foto de perfil. 
3. O sistema exibe também as configurações de privacidade, preferências de notificação e opções de segurança. 
4. O usuário pode navegar entre abas como Informações Pessoais, Minhas Denúncias, Configurações e Histórico de Atividades. 
5. O sistema apresenta as informações de maneira organizada e responsiva, garantindo boa legibilidade. 
6. O sistema verifica periodicamente se há atualizações nas informações (como mudança de senha ou foto). 
7. Caso haja atualizações, os dados são recarregados automaticamente. 

### 2.1.3 Fluxo alternativo
- Se o servidor estiver temporariamente indisponível, o sistema exibe: “Não foi possível carregar o perfil neste momento.” 
- Caso os dados do usuário estejam corrompidos, o sistema exibe: “Erro ao recuperar informações, contate o suporte.” 
- Se a imagem de perfil não for carregada, o sistema exibirá um avatar padrão. 

### 2.1.4 Pós-condições
- As informações do perfil são apresentadas corretamente ao usuário. 
- Logs de visualização são registrados para fins de auditoria. 

### 2.1.5 Requisitos não funcionais
- A tela deve carregar em até 3 segundos. 
- A interface deve ser responsiva e acessível. 
- O sistema deve garantir a integridade e consistência dos dados apresentados. 

### 2.1.6 Referência cruzada
Relacionado ao requisito funcional 3.5 – Perfil de Usuário. 

## 2.2 Edição e atualização de perfil
Este caso de uso descreve as ações realizadas pelo usuário para atualizar ou modificar suas informações pessoais e preferências dentro do sistema. O objetivo é dar autonomia ao usuário para manter seus dados sempre corretos e suas preferências configuradas conforme desejar.

**Ator principal:** Usuário, Sistema

### 2.2.1 Pré-condições
- O usuário deve estar logado no sistema. 
- O módulo de edição deve estar disponível e com permissão ativa. 

### 2.2.2 Fluxo básico
1. O usuário acessa o menu Meu Perfil e clica em Editar Perfil. 

2. O sistema exibe os campos editáveis: nome completo, senha, foto de perfil e preferências de notificação. 
3. O usuário realiza as alterações desejadas. 
4. O sistema realiza validações: 

    - Nome completo deve conter pelo menos dois nomes; 
    - A senha deve atender aos critérios de segurança; 
    - A foto de perfil deve ter formato válido (.jpg, .png) e tamanho inferior a 5MB.

5. O usuário confirma as alterações clicando em Salvar. 
6. O sistema atualiza os dados no banco de dados e exibe a mensagem: “Perfil atualizado com sucesso.” 
7. O sistema cria um log de alteração de dados com data e hora. 

### 2.2.3 Fluxo alternativo
- Se o usuário inserir senha fraca, o sistema exibirá: “Senha inválida, utilize caracteres especiais e números.” 
- Se a imagem exceder o limite de tamanho, o sistema exibirá: “Imagem muito grande, selecione outro arquivo.” 
- Se houver falha de conexão durante o salvamento, o sistema exibirá: “Erro ao salvar alterações, tente novamente.” 

### 2.2.4 Pós-condições
- Os dados são atualizados e refletidos em todas as telas do sistema. 
- O sistema mantém o histórico de alterações de dados do usuário. 

### 2.2.5 Requisitos não funcionais
- As alterações devem ser confirmadas em até 3 segundos. 
- O sistema deve registrar logs detalhados de cada modificação. 
- O design deve seguir padrões de usabilidade e clareza. 

### 2.2.6 Referência cruzada
Relacionado ao requisito funcional 3.5 – Perfil de Usuário (Edição). 

## 2.3 Histórico de denúncias e atividades
Este caso de uso descreve como o usuário pode consultar o histórico de suas denúncias e atividades dentro do sistema. O objetivo é fornecer transparência e controle sobre as ações realizadas, permitindo que o usuário acompanhe o andamento de suas participações.

**Ator principal:** Usuário, Sistema, Administrador

### 2.3.1 Pré-condições
- O usuário deve estar logado. 
- O sistema deve ter registros associados à conta do usuário. 

### 2.3.2 Fluxo básico
1. O usuário acessa o menu Meu Perfil e seleciona Minhas Denúncias. 

2. O sistema exibe uma lista com todas as denúncias enviadas, incluindo título, categoria, data e status atual (Pendente, Em Análise, Resolvida). 
3. O usuário pode clicar em uma denúncia específica para visualizar detalhes, comentários e anexos. 
4. O sistema apresenta uma linha do tempo mostrando as atualizações do status. 
5. O usuário pode filtrar as denúncias por data, categoria ou status. 
6. O sistema oferece a opção de exportar o histórico em PDF. 
7. O sistema mantém todas as informações salvas em ordem cronológica. 

### 2.3.3 Fluxo alternativo
- Se o usuário ainda não tiver denúncias, o sistema exibirá: “Nenhuma denúncia registrada até o momento.” 
- Se houver falha na conexão com o banco de dados, o sistema exibirá: “Erro ao carregar histórico.” 
- Se o usuário tentar acessar denúncia removida, o sistema informará que ela foi arquivada ou excluída. 

### 2.3.4 Pós-condições
- O histórico é exibido corretamente e atualizado em tempo real. 
- Logs de consulta são registrados para auditoria. 
- Requisitos não funcionais: 
- O carregamento do histórico não deve exceder 4 segundos. 
- O sistema deve garantir consistência e integridade dos registros. 
- A exportação deve ser gerada em formato padronizado (PDF/A). 

### 2.3.5 Referência cruzada
Relacionado ao requisito funcional 3.6 – Gestão de Denúncias (Visualização do Usuário).

## 2.4 Exclusão de conta
Este caso de uso descreve o processo de exclusão de conta, no qual o usuário solicita a remoção de seus dados pessoais e encerramento do acesso ao sistema.

**Ator principal:** Usuário, Sistema, Administrador

### 2.4.1 Pré-condições
- O usuário deve estar logado. 
- Não deve haver denúncias pendentes associadas à conta. 

### 2.4.2 Fluxo básico
1. O usuário acessa o menu Configurações de Conta. 

2. Clica em Excluir Conta. 
3. O sistema solicita confirmação da ação e apresenta um aviso sobre a perda de acesso. 
4. O usuário confirma a exclusão. 
5. O sistema solicita autenticação de segurança (reinsira a senha). 
6. O sistema torna inativo os dados pessoais e anonimiza as denúncias enviadas. 
7. O sistema exibe: “Conta excluída com sucesso.” 

### 2.4.3 Fluxo alternativo
- Se o usuário tiver denúncias pendentes, o sistema exibirá: “Não é possível excluir a conta enquanto houver denúncias abertas.” 
- Se houver falha de rede, o sistema exibirá: “Erro ao excluir a conta, tente novamente.” 

### 2.4.4 Pós-condições
- Conta excluída e dados pessoais removidos. 
- Denúncias associadas são mantidas de forma anônima. 

### 2.4.5 Requisitos não funcionais
- O processo deve seguir os princípios da LGPD. 
- A exclusão deve ser processada em até 5 segundos. 
- Logs da ação devem ser mantidos para auditoria institucional. 

### 2.4.6 Referência cruzada
Relacionado ao requisito funcional 4.3 – Exclusão e Anonimização de Dados. 

## 3. Página de orientação

## 3.1 Consulta e busca de guias e informações
Este caso de uso descreve o processo em que o usuário busca e consulta guias e tutoriais passo a passo sobre como realizar denúncias nos canais oficiais, garantindo que o processo seja feito corretamente. Ele permite ao usuário encontrar informações específicas de maneira rápida e eficiente.

**Ator principal:** Usuário, Sistema

### 3.1.1 Pré-condições
- O usuário deve ter acesso à internet. 
- O módulo de orientação deve estar ativo e devidamente preenchido com guias e tutoriais. 

### 3.1.2 Fluxo básico
1. O usuário acessa a plataforma e navega até a seção "Orientação". 

2. O sistema exibe um índice ou uma lista de guias disponíveis, categorizados por tipo de denúncia (ex: "Assédio Moral", "Problemas de Infraestrutura"). 
3. O usuário utiliza a barra de busca para encontrar informações específicas, digitando palavras-chave como "restaurante universitário" ou "iluminação". 
4. O sistema exibe os resultados da busca que correspondem às palavras-chave. 
5. O usuário clica em um dos guias da lista. 
6. O sistema carrega e exibe o conteúdo completo do guia, que inclui instruções detalhadas, textos explicativos e, se aplicável, imagens ou diagramas. 
7. O usuário lê o guia para entender o processo de denúncia. 

### 3.1.3 Fluxo alternativo
- Busca sem Resultados: Se a busca não retornar nenhum guia relevante, o sistema exibirá a mensagem: "Nenhum resultado encontrado para a sua busca. Por favor, tente outras palavras-chave." 
- Conteúdo Indisponível: Se o guia estiver incompleto ou houver um erro de carregamento, o sistema exibirá: "Não foi possível carregar o conteúdo. Por favor, tente novamente mais tarde." 

### 3.1.4 Pós-condições
- O usuário consegue encontrar e ler o guia completo, compreendendo o processo de uma denúncia oficial. 

### 3.1.5 Requisitos não funcionais
- A busca deve ser rápida e a interface deve ser intuitiva. O sistema deve garantir que os guias e tutoriais sejam de fácil leitura e compreensão. 

### 3.1.6 Referência cruzada
Relacionado ao requisito funcional 3.3.1 Guia de Denúncia. 

## 3.2 Leitura de tutoriais e acesso a links externos
Este caso de uso descreve como o usuário, após encontrar um guia, pode ler o conteúdo em profundidade, incluindo tutoriais e instruções detalhadas, e acessar diretamente os links para canais de denúncia externos e oficiais, garantindo que sua reclamação seja formalizada.

**Ator principal:** Usuário, Sistema

### 3.2.1 Pré-condições
- O usuário deve ter selecionado um guia na página de Orientação. 
- O sistema deve ter os links de órgãos oficiais cadastrados e funcionais. 

### 3.2.2 Fluxo básico
1. O sistema carrega o guia de denúncia, que pode incluir tutoriais passo a passo e links para sites externos. 

2. O usuário lê o tutorial para entender o procedimento completo. 
3. O usuário localiza e clica em um dos links oficiais fornecidos, como "Acesse o site da Ouvidoria da UnB". 
4. O sistema redireciona o usuário para o site oficial do órgão competente em no máximo 2 segundos. 
5. O usuário consegue prosseguir com a denúncia no canal oficial, utilizando as informações obtidas no tutorial. 

### 3.2.3 Fluxo alternativo
- Link Quebrado: Se o link oficial estiver quebrado ou o site do órgão estiver fora do ar, o sistema exibirá uma mensagem de erro: "O link não está funcionando no momento. Por favor, tente novamente mais tarde ou acesse diretamente o site do órgão." 

### 3.2.4 Pós-condições
- O usuário é redirecionado para a página externa do canal oficial de denúncia e tem as informações necessárias para formalizar sua reclamação. 

### 3.2.5 Requisitos não funcionais
- A responsividade dos links deve ser eficiente. 
- O sistema deve ser compatível com os principais navegadores. 

### 3.2.6 Referência cruzada
Relacionado ao requisito funcional 3.3.2 Links para Denúncia. 

## 4. Página de gráfico

## 4.1 Gráfico por categoria de denúncia
O usuário irá acessar a aba de gráficos e notícias e deseja ver os gráficos de denúncias.

**Ator principal:** Usuário, Sistema

### 4.1.1 Pré-condições
- O usuário deverá estar logado ao site. 
- O usuário terá a vista da tela inicial do site, e depois acessar a página de gráficos e notícias, onde ficarão os gráficos. 
- Deve haver denúncias cadastradas no sistema com categorias definidas. 

### 4.1.2 Fluxo básico
1. O usuário acessa a seção "Gráficos" do sistema. 

2. O sistema carrega e exibe um gráfico (por exemplo, de barras ou pizza) intitulado "Denúncias por Categoria". 
3. Cada parte do gráfico representa uma categoria de denúncia e seu tamanho/valor corresponde à quantidade total de denúncias naquela categoria.  
4. O usuário pode passar o mouse sobre uma seção do gráfico para ver o nome da categoria e o número exato de denúncias. 
5. O sistema garante que os dados do gráfico sejam atualizados em tempo real, refletindo novas denúncias assim que são registradas. 
6. O gráfico apresenta legendas claras e um design intuitivo para fácil interpretação. 

### 4.1.3 Fluxo alternativo
- Se não houver denúncias cadastradas, o sistema exibirá uma mensagem informativa no local do gráfico, como "Ainda não há dados para exibir. Nenhuma denúncia foi registrada." 

### 4.1.4 Pós-condições
- O usuário obtém uma visão clara e comparativa sobre quais tipos de problemas são mais frequentemente reportados na universidade. 

### 4.1.5 Requisitos não funcionais
- O gráfico deve carregar rapidamente, mesmo com um grande volume de dados. 
- A visualização do gráfico deve ser responsiva, adaptando-se a diferentes tamanhos de tela (desktop, tablet, mobile). 
- As cores e o design do gráfico devem ser acessíveis e de fácil distinção para todos os usuários. 

### 4.1.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.4.1 (Gráfico por Categoria de Denúncia) 

## 4.2 Linha do tempo de denúncias
O usuário visualizará um gráfico de linha do tempo que mostra a evolução do número de denúncias realizadas a cada mês, permitindo-lhe analisar tendências de crescimento ou diminuição ao longo do tempo.

**Ator principal:** Usuário, Sistema

### 4.2.1 Pré-condições
- O usuário deverá estar logado. 
- O usuário deve ter acesso à página de gráficos e notícias. 
- Devem existir denúncias cadastradas em diferentes meses para que a linha do tempo seja significativa. 

### 4.2.2 Fluxo básico
1. O usuário navega para a página de gráficos e notícias do sistema. 

2. O sistema exibe um gráfico de linha intitulado "Linha do Tempo de Denúncias" ou "Volume de Denúncias por Mês". 
3. O eixo X do gráfico representa os meses do ano. 
4. O eixo Y do gráfico representa a quantidade total de denúncias. 
5. Sistema plota os pontos de dados, onde cada ponto corresponde ao número total de denúncias registradas em um mês específico, e os conecta com uma linha. 
6. O usuário pode passar o mouse sobre um ponto no gráfico para ver o mês e o número exato de denúncias. 
7. O gráfico é atualizado em tempo real para refletir novas denúncias. 

### 4.2.3 Fluxo alternativo
- Se houver um período sem denúncias, o gráfico mostrará o valor "0" para o(s) mês(es) correspondente(s). 
- Se não houver denúncias no sistema, uma mensagem como "Nenhuma denúncia encontrada para gerar a linha do tempo" será exibida. 

### 4.2.4 Pós-condições
- O usuário consegue identificar padrões e tendências sazonais no volume de denúncias. 

### 4.2.5 Requisitos não funcionais
- A busca e agregação dos dados por mês devem ser eficientes para garantir o carregamento rápido do gráfico. 
- O design do gráfico deve ser claro e intuitivo. 
- O gráfico deve ser compatível com diversos navegadores e dispositivos. 

### 4.2.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.4.2 (Linha do Tempo de Denúncias). 

## 4.3 Top denúncias
O usuário visualizará uma seção destacada que lista as três denúncias que receberam o maior número de apoios (curtidas, votos) nos últimos 30 dias. Isso permite que os usuários identifiquem rapidamente os tópicos de maior relevância e repercussão na comunidade universitária.

**Ator principal:** Usuário, Sistema

### 4.3.1 Pré-condições
- O usuário deve estar logado no sistema.  
- Devem existir denúncias criadas nos últimos 30 dias que tenham recebido apoios de outros usuários. 

### 4.3.2 Fluxo básico
1. O usuário acessa a página de gráficos e notícias ou uma seção específica de "Destaques". 
2. O sistema realiza uma consulta para identificar todas as denúncias criadas nos últimos 30 dias. 
3. O sistema classifica essas denúncias em ordem decrescente pelo número de apoios recebidos. 
4. O sistema exibe as três primeiras denúncias dessa lista. 
5. Para cada denúncia exibida, o sistema mostra de forma clara seu título ou um resumo, e o número total de apoios que ela obteve. 
6. O usuário pode clicar em uma das denúncias para ver seus detalhes completos. 

### 4.3.3 Fluxo alternativo
- Se não houver denúncias nos últimos 30 dias, ou se nenhuma delas tiver recebido apoio, o sistema exibirá uma mensagem como "Nenhuma denúncia em destaque nos últimos 30 dias." 
- Se houver menos de três denúncias com apoios nos últimos 30 dias, o sistema exibirá apenas as que existirem. 

### 4.3.4 Pós-condições
- O usuário está ciente das questões mais urgentes e apoiadas pela comunidade nos últimos 30 dias. 

### 4.3.5 Requisitos não funcionais
- A consulta para determinar as "Top Denúncias" deve ser otimizada para não impactar o desempenho do sistema. 
- A exibição das denúncias deve ser visualmente atraente e clara. 

### 4.3.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.4.3 (Top Denúncias). 

## 5. Página de denúncias

## 5.1 Moderação e denúncia de abuso
Um usuário que encontra uma postagem ou comentário inapropriado deseja denunciar o conteúdo para que a moderação da plataforma possa analisar e tomar as medidas cabíveis.

**Ator principal:** Usuário, Administrador, Sistema

### 5.1.1 Pré-condições
- O usuário está logado e navegando pelo conteúdo da plataforma (denúncias ou comentários). 

### 5.1.2 Fluxo básico
1. O usuário identifica um conteúdo que viola as regras e clica no botão "Denunciar", que deve estar visível em todas as postagens e comentários. 

2. O sistema apresenta uma lista pré-definida de motivos para a denúncia (ex: assédio, spam, discurso de ódio). 
3. O usuário seleciona o motivo que melhor se aplica. 
4. O usuário confirma a ação. 
5. O sistema registra a denúncia de abuso, armazenando a data, hora, ID do denunciante e ID do conteúdo denunciado. 
6. O sistema envia uma notificação imediata para a equipe de moderação. 

### 5.1.3 Fluxo alternativo
- O usuário pode optar por cancelar a denúncia antes de confirmá-la. 

### 5.1.4 Pós-condições
- O conteúdo é marcado para revisão pela equipe de administradores. 
- A denúncia de abuso é registrada para futuras análises. 

### 5.1.5 Requisitos não funcionais
- O processo deve ser discreto e garantir o sigilo do denunciante. 
- O sistema de notificação para moderadores deve ser confiável e imediato. 

### 5.1.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.6 MODERAÇÃO E DENÚNCIA DE ABUSO 

## 5.2 Filtros e busca
Um usuário deseja encontrar uma denúncia específica de forma fácil, utilizando filtros por categoria ou uma busca por palavras-chave.

**Ator principal:** Usuário, Sistema

### 5.2.1 Pré-condições
- O usuário está na página que lista as denúncias. 
- Existem denúncias cadastradas no sistema. 

### 5.2.2 Fluxo básico
1. O usuário utiliza a barra de busca para digitar palavras-chave relacionadas ao título ou conteúdo da denúncia desejada. 

2. Alternativamente, o usuário seleciona filtros disponíveis, como categoria, período de tempo, etc. 
3. O usuário aplica a busca ou o filtro. 
4. O sistema processa a solicitação e exibe uma lista de denúncias que correspondem aos critérios informados. 
5. Os resultados da busca são apresentados em no máximo 2 segundos. 

### 5.2.3 Fluxo alternativo
- Se nenhum resultado for encontrado para os critérios de busca ou filtro, o sistema exibirá uma mensagem informativa, como "Nenhuma denúncia encontrada". 

### 5.2.4 Pós-condições
- O usuário visualiza uma lista refinada de denúncias, facilitando a localização do conteúdo de seu interesse. 

### 5.2.5 Requisitos não funcionais
- A performance da busca deve ser otimizada para retornar resultados rapidamente, mesmo com um grande volume de dados. 
- A interface dos filtros deve ser clara e de fácil compreensão. 

### 5.2.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.6 FILTROS E BUSCA. 

## 5.3 Publicação de denúncia
Um usuário que presenciou uma irregularidade registra uma denúncia na plataforma de forma clara e intuitiva para que o problema seja reportado e detenha as orientações cabíveis.

**Ator principal:** Usuári, Sistema

### 5.3.1 Pré-condições
- O usuário deve estar logado no sistema. 
- O usuário deve estar na página de denúncias para a criação de uma nova denúncia. 

### 5.3.2 Fluxo básico
1. O usuário acessa o formulário de nova denúncia. 

2. O usuário preenche os campos obrigatórios, como categoria e descrição da irregularidade, e pode incluir anexos opcionalmente. 
3. O usuário clica no botão para enviar a denúncia. 
4. O sistema valida as informações e registra a denúncia no banco de dados, atribuindo um ID único e um carimbo de data/hora. 
5. O sistema exibe uma mensagem de confirmação para o usuário, informando que a denúncia foi enviada com sucesso. 
6. A denúncia é imediatamente exibida na timeline de denúncias para que outros usuários possam visualizá-la. 

### 5.3.3 Fluxo alternativo
- Caso o usuário tente submeter o formulário sem preencher os campos obrigatórios, o sistema exibirá uma mensagem de erro, indicando quais campos precisam ser preenchidos. 

### 5.3.4 Pós-condições
- A denúncia é registrada com sucesso e fica visível para a comunidade na plataforma. 

### 5.3.5 Requisitos não funcionais
- O sistema deve garantir a opção de anonimato ao usuário, conforme o requisito de "Anonimização de Denúncias". 
- A interface do formulário deve ser intuitiva e fácil de usar. 

### 5.3.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.6 PUBLICAÇÃO DE DENÚNCIA. 

## 5.4 Timeline de denúncias
O usuário visualiza em uma linha do tempo todas as denúncias publicadas, ordenadas por data de publicação, para acompanhar os acontecimentos em ordem cronológica.

**Ator principal:** Usuário, Sistema

### 5.4.1 Pré-condições
- O usuário deve ter acesso à página principal de denúncias da plataforma. 

### 5.4.2 Fluxo básico
1. O usuário acessa a página de denúncias. 

2. O sistema carrega e exibe a lista de denúncias publicadas. 
3. As denúncias são automaticamente ordenadas da mais recente para a mais antiga. 
4. Cada item na timeline exibe o título, a data de publicação e o número de apoios recebidos. 
5. A timeline é atualizada em tempo real sempre que novas denúncias são publicadas no sistema. 

### 5.4.3 Fluxo alternativo
- Se não houver nenhuma denúncia registrada no sistema, será exibida uma mensagem informativa, como "Nenhuma denúncia foi publicada ainda." 

### 5.4.4 Pós-condições
- O usuário obtém uma visão geral e cronológica das denúncias registradas na plataforma. 

### 5.4.5 Requisitos não funcionais
- A interface deve ser responsiva, adaptando-se a diferentes tamanhos de tela. 
- O carregamento da timeline deve ser eficiente para não comprometer a experiência do usuário. 

### 5.4.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.6 TIMELINE DE DENÚNCIAS.

## 5.5 Comentários nas denúncias
Um usuário interessado em uma denúncia específica deseja interagir, adicionando um comentário para compartilhar informações a discussão.

**Ator principal:** Usuário, Sistema

### 5.5.1 Pré-condições
- O usuário deve estar logado na plataforma. 
- O usuário deve estar visualizando os detalhes de uma denúncia. 

### 5.5.2 Fluxo básico
1. O usuário navega até a seção de comentários da denúncia. 

2. O usuário digita sua mensagem no campo de texto apropriado. 
3. O usuário clica no botão "Comentar" ou "Enviar". 
4. O sistema registra o comentário, associando o autor, a data e o conteúdo. 
5. O novo comentário é exibido na lista, que é ordenada cronologicamente, com os mais recentes no topo. 

### 5.5.3 Fluxo alternativo
- Se o usuário tentar enviar um comentário vazio, o sistema exibirá uma mensagem de erro. 
- Outros usuários podem denunciar um comentário que considerem inapropriado para moderação. 

### 5.5.4 Pós-condições
- O comentário do usuário é adicionado à denúncia e fica visível para outros membros da comunidade. 

### 5.5.5 Requisitos não funcionais
- O sistema deve processar e exibir novos comentários rapidamente. 
- A interface para comentar deve ser clara e de fácil utilização. 

### 5.5.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.6 comentários nas denúncias. 

## 5.6 Sistema de reações
Um usuário que leu uma denúncia deseja reagir com "Apoiar" para expressar sua opinião de forma rápida, sem a necessidade de escrever um comentário.

**Ator principal:** Usuário, Sistema

### 5.6.1 Pré-condições
- O usuário deve estar logado na plataforma. 
- O usuário está visualizando uma denúncia. 

### 5.6.2 Fluxo básico
1. O usuário localiza o botão de reação "Apoiar" (like) na postagem da denúncia. 

2. O usuário clica no botão para expressar seu apoio. 
3. O sistema registra que o usuário reagiu àquela denúncia, garantindo que ele só possa reagir uma única vez. 
4. O número total de reações da denúncia é atualizado em tempo real para todos os usuários. 
5. O botão de reação muda de estado para indicar que o usuário já reagiu. 

### 5.6.3 Fluxo alternativo
- Se o usuário clicar novamente no botão "Apoiar", sua reação é removida, e a contagem total de apoios é decrementada em tempo real. 

### 5.6.4 Pós-condições
- O apoio do usuário é contabilizado, refletindo a repercussão da denúncia na comunidade. 

### 5.6.5 Requisitos não funcionais
- A atualização da contagem de reações deve ser instantânea e não deve sobrecarregar o sistema. 
- A interface das reações deve ser visualmente clara e responsiva ao clique do usuário. 

### 5.6.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.6 sistema de reações. 

## 6. Administração

## 6.1 Gestão de denúncias
O administrador acessa e gerencia todas as denúncias registradas para garantir que sejam processadas adequadamente e para moderar o conteúdo, removendo postagens que violem as regras da plataforma.

**Ator principal:** Administrador, Sistema

### 6.1.1 Pré-condições
- O usuário deve ter permissões de administrador e estar logado no sistema. 
- O administrador deve estar no painel de administração. 

### 6.1.2 Fluxo básico
1. O administrador acessa a seção de gerenciamento de denúncias. 

2. O sistema exibe uma lista de todas as denúncias, que pode ser filtrada por categoria ou usuário. 
3. O sistema apresenta as denúncias que foram reportadas por usuários em uma lista separada para análise prioritária. 
4. O administrador seleciona uma denúncia para analisar seu conteúdo e autor. 
5. O administrador decide a ação a ser tomada, como "Excluir" a denúncia. 
6. O administrador executa a ação, e o sistema remove a denúncia do ar facilmente. 
7. Toda alteração realizada pelo administrador é registrada no histórico da denúncia. 

### 6.1.3 Fluxo alternativo
- O administrador pode requerer a alteração da denuncia se o sistema obtiver tal suporte. 

### 6.1.4 Pós-condições
- A denúncia é moderada (excluída ou atualizada), garantindo que a plataforma permaneça livre de abusos. 
- O histórico de moderação é atualizado para fins de auditoria. 

### 6.1.5 Requisitos não funcionais
- A interface de gestão deve ser eficiente, permitindo que o administrador encontre e modere denúncias rapidamente. 
- As ações de exclusão devem ser seguras e registradas de forma confiável. 

### 6.1.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.7 gestão de denúncias.

## 6.2 Gestão de usuários
O administrador gerencia as contas dos usuários da plataforma, podendo desativar ou banir contas para manter a segurança e a integridade do sistema.

**Ator principal:** Administrador, Sistema

### 6.2.1 Pré-condições
- O administrador está logado no painel administrativo. 

### 6.2.2 Fluxo básico
1. O administrador acessa a seção "Gerenciar Usuários". 

2. O sistema exibe uma lista de todos os usuários cadastrados. 
3. O administrador pode buscar por um usuário específico. 
4. Ao encontrar o usuário, o administrador seleciona uma ação, como "Desativar", "Banir" ou "Excluir conta". 
5. O sistema solicita uma confirmação para a ação crítica. 
6. Após a confirmação, o sistema aplica a restrição ou remove a conta do usuário. 
7. Todas as ações administrativas realizadas na conta do usuário são registradas em um histórico. 

### 6.2.3 Fluxo alternativo
- O administrador pode precisar reativar uma conta que foi desativada anteriormente. 

### 6.2.4 Pós-condições
- A conta do usuário é gerenciada (desativada, banida ou excluída), e o usuário perde o acesso conforme a ação aplicada. 
- A segurança e a ordem da comunidade são mantidas. 

### 6.2.5 Requisitos não funcionais
- A busca por usuários deve ser rápida e eficiente. 
- As ações de gerenciamento de usuários devem ser devidamente registradas para garantir a rastreabilidade.

### 6.2.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.7 GESTÃO DE USUÁRIOS. 

## 6.3 Postagens e gestão de denúncias
O administrador deseja postar, editar ou excluir notícias e comunicados para disseminar informações pertinentes aos usuários da plataforma de maneira simples e rápida.

**Ator principal:** Administrador, Sistema

### 6.3.1 Pré-condições
- O administrador está logado no sistema. 

### 6.3.2 Fluxo básico (Criar notícia)
1. O administrador navega para a seção de gestão de notícias. 

2. Ele clica em "Criar Nova Notícia". 
3. Um editor de texto é apresentado, onde o administrador insere o título e o conteúdo da notícia. 
4. O administrador publica a notícia. 
5. A notícia aparece em uma área designada, visível para todos os usuários comuns. 

### 6.3.3 Fluxo básico (Editar ou excluir notícia)
1. O administrador acessa a lista de notícias publicadas. 

2. Ele seleciona a notícia que deseja modificar ou remover. 
3. Ele escolhe a opção "Editar" ou "Excluir". 
4. Se "Editar", o sistema abre o editor com o conteúdo existente para alteração. As alterações são salvas e refletidas imediatamente para os outros usuários. 
5. Se "Excluir", o sistema pede confirmação e remove a notícia da plataforma. 

### 6.3.4 FLuxo alternativo
- O administrador pode salvar uma notícia como rascunho para publicá-la posteriormente. 

### 6.3.5 Pós-condições
- Informações e comunicados importantes são compartilhados com os usuários da plataforma. 
- O conteúdo informativo do site é mantido atualizado. 

### 6.3.6 Requisitos não funcionais
- A interface de edição de notícias deve ser intuitiva e de fácil utilização. 
- A publicação e atualização de notícias devem ocorrer em tempo real, com responsividade imediata. 

### 6.3.7 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.7 POSTAGENS e Gestão de NOTÍCIAS. 

## 6.4 Configurações do sistema
O administrador acessa um painel de configurações gerais para ajustar o funcionamento da plataforma, como gerenciar categorias de denúncia e permissões de usuários, conforme a necessidade.

**Ator principal:** Administrador, Sistema

### 6.4.1 Pré-condições
- O usuário logado possui perfil de administrador e tem permissão para acessar as configurações. 

### 6.4.2 Fluxo básico
1. O administrador acessa a área de "Configurações do Sistema" no painel administrativo. 

2. O sistema exibe uma interface clara com diferentes seções de configuração (ex: Categorias de Denúncia, Permissões, Parâmetros de Segurança). 
3. O administrador seleciona a seção que deseja alterar. 
4. Ele realiza as modificações necessárias (ex: adiciona uma nova categoria de denúncia). 
5. O administrador salva as alterações. 
6. O sistema aplica as novas configurações e registra a alteração em um log administrativo. 

### 6.4.3 FLuxo alternativo
- O administrador descarta as alterações antes de salvar, e o sistema mantém as configurações anteriores. 

### 6.4.4 Pós-condições
- O comportamento do sistema é ajustado de acordo com as novas configurações definidas pelo administrador. 

### 6.4.5 Requisitos não funcionais
- O acesso a esta área deve ser estritamente restrito a usuários autorizados para evitar alterações indevidas. 
- A interface deve ser clara e organizada para facilitar a gestão dos parâmetros. 

### 6.4.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.7 CONFIGURAÇÕES DO SISTEMA. 

## 6.5 Administrador mestre
Como última instância de controle, o administrador mestre possui privilégios para gerenciar outros administradores e suas publicações, garantindo a supervisão completa sobre a plataforma.

**Ator principal:** Administrador mestre, Sistema

### 6.5.1 Pré-condições
- O usuário logado possui o perfil exclusivo de "Administrador Mestre". 

### 6.5.2 Fluxo básico
1. O administrador mestre acessa uma área de gestão de administradores ou de notícias. 

2. Ele pode visualizar a lista de todos os outros administradores do sistema. 
3. Ele seleciona um administrador e pode alterar suas permissões ou excluí-lo. 
4. Ao visualizar as notícias, ele pode editar ou excluir postagens feitas por qualquer outro administrador. 
5. O sistema executa a ação, que é soberana sobre as ações de outros administradores. 
6. Todas as ações são registradas em um log de auditoria de alta prioridade. 

### 6.5.3 Fluxo alternativo
- O administrador mestre pode optar por apenas revisar as atividades de outros administradores sem realizar nenhuma ação. 

### 6.5.4 Pós-condições
- O controle sobre a equipe administrativa e o conteúdo crítico é mantido, assegurando a hierarquia de gestão. 

### 6.5.5 Requisitos não funcionais
- A segurança para o acesso do Administrador Mestre deve ser reforçada, possivelmente com autenticação de múltiplos fatores. 
- Os privilégios deste perfil devem ser claramente definidos e isolados dos perfis de administradores padrão. 

### 6.5.6 Referência cruzada
Este caso de uso está relacionado ao requisito funcional 3.7 ADMINISTRADOR MESTRE. 
