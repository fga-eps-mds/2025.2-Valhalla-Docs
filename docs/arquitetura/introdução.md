# Documento de Arquitetura - Guardiões da Universidade - Grupo Valhalla

**Versão** 1.0

### Histórico de Revisão
| Data | Versão | Descrição | Autor(es) |
|------|--------|-----------|-----------|
| 31/10| 1.0 | Introdução do Documento de Arquitetura |Gabriel Diniz; Pedro H. Américo;  Pedro Lucas|
| 31/10| 1.1 | Referências Documento de Arquitetura |Gabriel Diniz; Pedro H. Américo;  Pedro Lucas|
| 31/10| 1.2 | Representação Arquitetural Documento de Arquitetura |Gabriel Diniz; Pedro H. Américo;  Pedro Lucas|
| 31/10| 1.3 | Conclusão da Representação Arquitetural Doc. de Arquitetura |Gabriel Diniz; Pedro H. Américo; Pedro Ian; Pedro Lucas|


**Autores:**

| Nome | Matricula |
| ------ | ------ |
|Gabriel Diniz | 24102630 |
|Pedro H. Américo | 241025980 |
|Pedro Ian Guedes | 241025837 |
|Pedro Lucas B. | 241025710 |

## 1. Introdução

### 1.1 Propósito

Este documento descreve a arquitetura do sistema sendo desenvolvido pelo grupo, na disciplina de MDS – Métodos de Desenvolvimento de Software – edição do segundo semestre de 2025, para o sistema Guardiões da Universidade, a fim de fornecer uma visão abrangente do sistema para desenvolvedores, testadores e demais interessados em aspectos relacionados às tecnologias a serem usadas no desenvolvimento.

O propósito do sistema é desenvolver um canal de denúncias para os alunos da Universidade de Brasília (UnB), servindo como um meio para os discentes e servidores exporem suas denúncias, conhecerem os procedimentos oficiais de denúncia e visualizarem as demandas da universidade.

O problema que o projeto busca resolver é a falta de informação e o "sentimento de não ter voz", oferecendo um local apropriado para fortalecer o senso de comunidade, a segurança e demonstrar os problemas que mais afetam o dia a dia dos integrantes da UnB.

> “Informamos que o órgão central do Sistema de Ouvidoria do Poder Executivo Federal é a Ouvidora-Geral da União (OGU), pertencente à estrutura da Controladoria-Geral da União. Cabe à OGU (art.11, IV, do Decreto 9492/2018) o desenvolvimento e manutenção da Plataforma Integrada de Ouvidoria e Acesso à Informação (Fala.BR) para recebimento e tratamento das manifestações de ouvidoria e pedidos de acesso à informação. O uso do Fala.BR é obrigatório para todos os órgãos e entidades do poder executivo federal, assim, a Ouvidoria da UnB não tem autorização para utilizar outro sistema.”

### 1.2 Escopo

O detalhamento completo do escopo se encontra na seção Escopo e Requisitos. Em linhas gerais, o escopo do produto compreende a implementação de um conjunto completo de funcionalidades, incluindo:

- **Autenticação e Conta:** Permite que os usuários realizem cadastro, login de maneira segura e recuperação de senha.
- **Página de Perfil:** O usuário pode visualizar e editar suas informações, além de gerenciar seu histórico de denúncias.
- **Página de Orientação:** Disponibiliza informações, tutoriais e links para que as denúncias sejam realizadas de maneira oficial.
- **Página de Denúncia:** Permite a interação entre usuários através da publicação de denúncias, uma timeline, comentários e reações.
- **Administração:** Concede privilégios a administradores para gerenciar denúncias e usuários.
- **Segurança e Privacidade:** Garante a criptografia de dados sensíveis e a opção de denúncias anônimas.
- **Página de Gráficos e Notícias**: Permite aos usuários visualizar dados gerais sobre as denúncias e ver as notícias cadastradas por administradores.