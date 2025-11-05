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