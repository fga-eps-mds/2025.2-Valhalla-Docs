# Requisitos do Sistema

Esta tabela lista todos os requisitos do projeto, sua prioridade e descrição detalhada.

### Requisitos Funcionais

| ID | Requisito | Importância | Descrição | Critérios de Sucesso |
|---|---|---|---|---|
| **Autenticação e Conta** | | | | |
| RF-001 | Login de Usuáriso | MUST | Eu como usuário cadastrado, quero fazer login usando meu e-mail e senha para ter acesso às funcionalidades exclusivas do meu perfil e interagir com a plataforma. | - O usuário consegue fazer login com credenciais válidas e é redirecionado para a página inicial logada.<br>- O sistema exibe uma mensagem de erro clara ("E-mail ou senha inválidos") ao tentar login com credenciais incorretas. |
| RF-002 | Cadastro | MUST | Eu como visitante, quero criar uma conta fornecendo meus dados básicos para poder utilizar as funcionalidades do site. | - Após preencher o formulário com dados válidos, a conta é criada com sucesso e o usuário é logado.<br>- O sistema exibe uma mensagem de erro se o e-mail informado já estiver em uso.<br>- O sistema valida a força da senha e informa o usuário se os critérios não forem atendidos. |
| RF-003 | Recuperação da Senha | MUST | Eu como usuário cadastrado que esqueceu a senha, quero solicitar um link de redefinição por e-mail para recuperar o acesso à minha conta de forma segura. | - Ao inserir um e-mail cadastrado, o usuário recebe um e-mail com um link para redefinir sua senha.<br>- Após redefinir a senha, o usuário consegue fazer login com as novas credenciais. |
| RF-004 | Manter Sessão Ativa | SHOULD | Eu como usuário cadastrado, quero ter a opção de 'Manter-se Conectado' ao fazer login para não precisar inserir minhas credenciais toda vez que eu visitar o site no mesmo dispositivo. | - Se a opção "Manter-se Conectado" for marcada, o usuário permanece logado após fechar e reabrir o navegador.<br>- Se a opção não for marcada, o usuário é desconectado ao fechar a sessão do navegador. |
| RF-005 | Encerramento de Sessão | MUST | Eu como usuário logado, quero clicar em um botão 'Sair' para encerrar minha sessão de forma segura e proteger minha conta. | - Ao clicar no botão "Sair", a sessão do usuário é encerrada imediatamente.<br>- Após o logout, o usuário é redirecionado para a página inicial.<br>- O usuário não consegue acessar páginas restritas após o logout. |
| **Página de Perfil** | | | | |
| RF-006 | Visualização de Dados do Perfil | MUST | Eu como usuário logado, quero visualizar as informações do meu perfil (nome, e-mail, foto, pontuação) para consultar meus dados cadastrados. | - Todas as informações salvas do usuário são exibidas corretamente na página de perfil. |
| **Página de Orientação** | | | | |
| **Página de Gráficos e Notícias** | | | | |
| **Página de Denúncias** | | | | |
| **Administração** | | | | |

### Requisitos Não-Funcionais

| ID | Requisito | Importância | Descrição | Critérios de Sucesso |
|---|---|---|---|---|
| **Confiabilidade e Disponibilidade** |
| RNF-001 | Disponibilidade do Sistema | MUST | Eu como usuário, quero que o sistema esteja disponível na maior parte do tempo, para que eu possa acessá-lo sempre que precisar. | - O sistema deve ter disponibilidade mínima de 99,5% mensal (~3h36min de downtime). |
| RNF-002 | Suporte a Múltiplos Usuários | MUST | Eu como administrador, quero que o sistema suporte muitos usuários conectados ao mesmo tempo, para garantir estabilidade mesmo em períodos de pico. | - O sistema deve suportar pelo menos 250 usuários simultâneos sem degradação perceptível. |
| **Usabilidade** |
| RNF-003 | Interface Intuitiva | MUST | Eu como usuário, quero uma interface simples e clara, para que eu consiga utilizar a plataforma sem precisar de ajuda externa. | - Ícones, textos e botões devem ser autoexplicativos.<br>- Fluxos críticos (ex.: denúncia, cadastro) devem ser realizados em até 4 passos. |
| RNF-004 | Responsividade | MUST | Eu como usuário que acessa pelo celular, quero que a plataforma seja responsiva, para que eu consiga navegar sem dificuldades em qualquer dispositivo. | - A interface deve funcionar corretamente em desktop, tablet e mobile.<br>- Todos os elementos devem se adaptar automaticamente ao tamanho da tela. |
| RNF-005 | Confirmação em Ações Críticas | MUST | Eu como usuário, quero receber uma confirmação antes de ações irreversíveis (ex.: excluir conta, cancelar denúncia), para evitar erros acidentais. | - Toda ação crítica deve exibir uma caixa de confirmação.<br>- Apenas após confirmação explícita a ação é executada. |
| **Manutenção e Evolução** |
| RNF-006 | Qualidade do Código | MUST | Eu como desenvolvedor, quero que o código siga boas práticas, para que seja legível, padronizado e fácil de manter. | - O código deve seguir padrões de clean code.<br>- Deve haver documentação interna (README, comentários claros). |
| RNF-007 | Testes | MUST | Eu como administrador de qualidade, quero que o sistema seja testado, para garantir que erros sejam detectados rapidamente. | - Deve haver cobertura mínima de 70% do código crítico (login, denúncias, permissões). |
| RNF-008 | Documentação Técnica | MUST | Eu como desenvolvedor, quero ter documentação atualizada da plataforma, para compreender arquitetura, APIs e permissões. | - Deve haver documentação clara de endpoints, fluxos e arquitetura.<br>- Documentação deve ser atualizada junto a cada nova release. |
| **Segurança e Privacidade** |
| RNF-009 | Criptografia de Senhas e Dados Pessoais | MUST | Eu como usuário cadastrado quero que minha senha e demais dados pessoais e dados sensíveis sejam protegidos e armazenados por criptografia, a fim de garantir a segurança, inviolabilidade e não vazamento dos meus dados. | - As senhas não serão armazenadas em texto plano, e sim com um hash seguro.<br>- O sistema deve autenticar um usuário com sucesso ao comparar o hash da senha digitada no login com o hash armazenado no banco de dados.<br>- Dados pessoais e sensíveis no banco de dados devem estar criptografados. |
| RNF-010 | Anonimização de Denúncias | MUST | Eu como usuário cadastrado denunciante quero a opção de anonimato e não exposição dos meus dados a denúncia feita, para que eu me sinta seguro e protegido sempre que sentir a necessidade de realizar outras denúncias. | - Login e fornecimento de informações pessoais opcionais na realização de uma denúncia.<br>- O sistema não deve armazenar metadados que possam identificar o denunciante, como endereço de IP, junto à denúncia. |
| RNF-011 | Notificações de Segurança | COULD | Eu como usuário cadastrado quero ser notificado por email sobre atividades que ameacem a segurança da minha conta, para que eu possa agir rapidamente, como em caso de alteração da minha senha ou um login em um novo dispositivo. | - O sistema envia um e-mail de notificação imediatamente após uma alteração de senha bem-sucedida.<br>- O sistema envia uma notificação quando um login é realizado a partir de um novo dispositivo pela primeira vez.<br>- O e-mail deve conter informações relevantes e um link para a página de suporte ou para redefinir a senha. |
| **Conformidade Legal** |
| RNF-012 | LGPD e Consentimento | MUST | Eu como usuário, quero ter controle sobre meus dados, para garantir que a plataforma está em conformidade com a Lei Geral de Proteção de Dados (LGPD). | - O sistema deve apresentar política de privacidade clara e acessível.<br>- No cadastro, o usuário deve consentir ativamente com termos de uso e política de privacidade.<br>- No perfil, o usuário deve poder gerenciar permissões e solicitar exclusão de dados. |

