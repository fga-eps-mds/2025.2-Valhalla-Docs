# Requisitos do Sistema

Esta tabela lista todos os requisitos do projeto, sua prioridade e descrição detalhada.

| ID | Requisito | Importância | Descrição | Casos de Sucesso |
| :---: | :--- | :---: | :--- | :--- |
| **R001** | O sistema deve permitir o cadastro de novos usuários. | Alta | Detalhamento da funcionalidade de cadastro, incluindo campos obrigatórios (nome, email, senha). | - Usuário preenche e envia formulário de cadastro. <br> - Sistema valida dados e envia email de confirmação. <br> - Usuário loga com sucesso. |
| **R002** | A página inicial deve carregar em menos de 3 segundos. | Média | Requisito não funcional de desempenho. Define o tempo máximo de carregamento da página principal sob carga normal. | - Teste de desempenho indica tempo de carregamento de 2.5s. |
| **R003** | O usuário deve conseguir redefinir a senha através do email. | Alta | Detalhamento do fluxo de "Esqueci minha senha". | - Usuário solicita redefinição. <br> - Recebe link no email. <br> - Define nova senha com sucesso. |
| **R004** | O sistema deve ser responsivo para dispositivos móveis. | Média | Requisito não funcional de usabilidade. A interface deve se adaptar a telas de smartphones e tablets. | - Interface testada e aprovada em telas de 360px de largura. |