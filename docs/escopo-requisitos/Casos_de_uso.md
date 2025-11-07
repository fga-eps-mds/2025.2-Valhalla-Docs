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
