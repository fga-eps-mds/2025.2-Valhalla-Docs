# Backlog do Produto

## Releases Planejadas

O planejamento do projeto "Guardiões da Universidade" foi estruturado em três grandes entregas principais (Releases/Ondas), desenhadas para garantir a evolução incremental do produto, partindo de um Mínimo Produto Viável (MVP) funcional até a versão final rica em interatividade.

O cronograma de entregas foi definido da seguinte forma:

**Release 1 (MVP - Funcionalidades Essenciais e Moderação):**
O foco da primeira fase foi estabelecer o núcleo do sistema. O objetivo foi permitir que o fluxo principal de denúncia ocorresse e que a administração pudesse moderar o conteúdo.
* *Entregáveis:* Funcionalidades baseadas na Lean Inception, incluindo: Cadastro e Login de usuários; Gerenciamento de Perfil (adição e edição); CRUD básico de Denúncias (Publicar, Visualizar e Excluir a própria denúncia); e Funcionalidades Administrativas (Exclusão de denúncias e usuários para moderação).

**Release 2 (Refinamento, Mídia e Notícias):**
A segunda fase focou na expansão das capacidades do sistema e na melhoria da experiência do usuário, introduzindo recursos de edição e conteúdo informativo.
* *Entregáveis:* Implementação da Edição de Denúncias (antes restrita apenas à exclusão); Suporte a upload de Mídias (fotos e vídeos); Filtros de Busca e Categorização; e o Módulo de Notícias (Publicação e Gestão de notícias por administradores).

**Release 3 (Interação, Engajamento e Dados):**
A fase final visa promover o engajamento da comunidade e fornecer transparência através de dados.
* *Entregáveis:* Sistema de Comentários e Reações; Funcionalidade de Apoiar ou Reportar denúncias; Seção de "Top Denúncias" (mais apoiadas nos últimos 30 dias); Página de Gráficos e Página de Perguntas Frequentes (FAQ).

A tabela a seguir resume o planejamento das fases:

| Release | Foco da Entrega | Entregáveis Principais (Features) | Status |
| :--- | :--- | :--- | :--- |
| **Release 1** | **MVP e Moderação** | • Auth (Login/Cadastro)<br>• Perfil (Criar/Editar)<br>• Denúncia (Criar/Ver/Excluir)<br>• Moderação (Admin excluir user/denúncia) | Concluído |
| **Release 2** | **Refinamento e Conteúdo** | • Edição de Denúncias<br>• Upload de Mídia (Foto/Vídeo)<br>• Filtros de Busca e Categoria<br>• Módulo de Notícias (Admin) | Planejado |
| **Release 3** | **Engajamento e Dados** | • Comentários e Reações<br>• Apoiar/Reportar Denúncia<br>• Top Denúncias (30 dias)<br>• Gráficos e FAQ | Planejado |

### Entrega MVP

**Descrição:** A plataforma funciona de maneira estável e eficiente. O usuário ao acessar a homepage pode ser redirecionado a página de login e cadastro, onde pode se cadastrar sem erros, ao acessar é redirecionado a página de denuncias e consegue visualizar as denúncias publicadas. O sistema permite ainda a criação de novas denúncias, a edição de dados do perfil e, para administradores, a funcionalidade de moderação (exclusão de usuários e postagens).


## Tabela do Backlog do Produto

|   ID | Issue Title                                      |   Story Points |   Sprint | Milestone   |
|-----:|:-------------------------------------------------|---------------:|---------:|:------------|
|    1 | Página de Cadastro                               |              3 |        1 | Milestone 1 |
|    2 | Página de Login                                  |              1 |        1 | Milestone 1 |
|    3 | CRUD Categoria                                   |              1 |        1 | Milestone 1 |
|    4 | Crud de denuncia                                 |              2 |        1 | Milestone 1 |
|    5 | Administrador Mestre                             |              3 |        2 | Milestone 1 |
|    6 | Página de Denuncias                              |              2 |        2 | Milestone 1 |
|    7 | Homepage                                         |              2 |        2 | Milestone 2 |
|    8 | Links para Denúncias                             |              2 |        3 | Milestone 1 |
|    9 | Timeline de Denúncias                            |              3 |        3 | Milestone 1 |
|   10 | Guia de Denúncia                                 |              3 |        3 | Milestone 1 |
|   11 | Modal de publicação de Denuncias                 |              2 |        3 | Milestone 1 |
|   12 | Recuperarar de Senha                             |              3 |        4 | Milestone 1 |
|   13 | Encaminhamento Automático                        |              3 |        4 | Milestone 3 |
|   14 | Encerrar Sessão                                  |              2 |        4 | Milestone 2 |
|   15 | Manter Sessão Ativa                              |              2 |        4 | Milestone 2 |
|   16 | Página de mudança de senha                       |              3 |        4 | Milestone 2 |
|   17 | Gerir Usuários                                   |              3 |        5 | Milestone 1 |
|   18 | Gerir Denúncias                                  |              3 |        5 | Milestone 1 |
|   19 | Gerenciar Denúncias                              |              5 |        5 | Milestone 3 |
|   20 | Editar dados do Perfil                           |              3 |        5 | Milestone 2 |
|   21 | Visualizar de dados do Perfil                    |              3 |        5 | Milestone 2 |
|   22 | Visualizar do Histórico de Denúncias             |              3 |        5 | Milestone 3 |
|   23 | Gerenciar denuncias (User)                       |              8 |        6 | Milestone 3 |
|   24 | Encaminhamento Automático                        |              5 |        6 | Milestone 2 |
|   25 | Postagens e Gestão de Notícias                   |              5 |        6 | Milestone 2 |
|   26 | Filtro e Busca                                   |              5 |        6 | Milestone 3 |
|   27 | Reagir a Postagens                               |              5 |        6 | Milestone 3 |
|   28 | Comentar nas Denúncias                           |              3 |        6 | Milestone 3 |
|   29 | Perguntas Frequentes                             |              3 |        6 | Milestone 3 |
|   30 | Moderação de Denuncia e Abuso                    |              5 |        6 | Milestone 3 |
|   31 | Visualização de "Top Denuncias"                  |              3 |        7 | Milestone 3 |
|   32 | Visualizar Interações do Usuário                 |              5 |        7 | Milestone 3 |
|   33 | Visualização de "Top Denuncias"                  |              3 |        7 | Milestone 3 |
|   34 | Visualizar gráfico de linha do tempo de Denuncia |              5 |        7 | Milestone 3 |
|   35 | Visualizar gráfico por categoria de Denúncia     |              5 |        7 | Milestone 3 |