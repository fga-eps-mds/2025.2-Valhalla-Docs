# VISÃO DO PRODUTO E PROJETO

O "Guardiões da Universidade" é uma plataforma destinada à comunidade da Universidade de Brasília (UnB), incluindo discentes e servidores. O objetivo é criar um espaço unificado onde os membros da comunidade possam expor suas queixas e, simultaneamente, visualizar as demandas coletivas da universidade.

É fundamental entender que, devido a restrições legais, a UnB não pode reconhecer esta plataforma como um canal de denúncias oficial. Portanto, as reclamações registradas no sistema servem como um meio de exposição pública e não são contabilizadas formalmente pela instituição.

O projeto busca resolver dois problemas centrais: a dificuldade de acesso à informação e o sentimento de frustração da comunidade por não ter um canal de voz claro. A principal solução que a plataforma oferece é desburocratizar o processo como um guia centralizado, fornecendo orientações, tutoriais e links diretos para que o usuário possa formalizar sua demanda junto aos órgãos oficiais competentes.

## 1. VISÃO GERAL DO PRODUTO

### 1.1 Problema

A presente proposta insere-se no contexto da comunidade acadêmica da Universidade de Brasília (UnB), conforme delineado na introdução. A interação desta comunidade com os canais de ouvidoria e reclamação institucionais é mediada por portais oficiais que, embora sejam os únicos a possuir validade processual, apresentam barreiras significativas de usabilidade. Observa-se que estes canais frequentemente carecem de divulgação efetiva e de uma orientação centralizada, tornando a identificação do procedimento correto uma tarefa complexa para o usuário.

Esta falta de centralização informacional resulta em dois problemas centrais:

1.  Uma severa dificuldade de acesso à informação, que cria uma barreira burocrática ao registro de queixas;
2.  Uma consequente sensação de frustração e desamparo institucional, o que inibe o engajamento da comunidade.

A oportunidade de desenvolvimento de software reside em solucionar esta lacuna de usabilidade e orientação.

A solução de software proposta, "Guardiões da Universidade", é uma plataforma web projetada para atuar como uma camada de facilitação. Reconhecendo a limitação legal que impede a UnB de contabilizar denúncias de fontes não-oficiais, a plataforma não busca substituir os canais existentes. A sua contribuição justifica-se por facilitar o acesso a esses canais oficiais. O software servirá como um facilitador, disponibilizando de forma organizada as orientações que atualmente estão ausentes ou dispersos nos portais da universidade. Adicionalmente, a plataforma oferecerá um espaço para a exposição pública de queixas, tratando o problema secundário de desamparo e "sentimento de não serem ouvidos", fortalecendo a transparência na comunidade.

### 1.2 Declaração de Posição do Produto

O "Guardiões da Universidade" é uma plataforma web (Cliente-Servidor) que se propõe a resolver a lacuna de comunicação e informação entre a comunidade acadêmica da UnB (discentes e servidores) e os canais de denúncia oficiais da instituição.

O que torna este produto fundamentalmente diferente dos concorrentes (ou, neste caso, da alternativa oficial única, o Fala.BR) é que ele não tenta ser um canal oficial. Sua principal inovação é atuar como uma camada de facilitação: ele oferece um espaço para exposição pública de queixas (dando voz à comunidade) e, simultaneamente, serve como um guia centralizado que orienta o usuário sobre como navegar a burocracia e formalizar sua queixa no canal correto.

Os usuários-alvo são os discentes e servidores da Universidade de Brasília. Este produto é importante para eles pois ataca diretamente a frustração gerada pela dificuldade em encontrar os canais corretos e pelo sentimento de que suas reclamações não são vistas ou ouvidas pela comunidade.

Os clientes (usuários) deveriam utilizar este produto porque ele é a única solução que oferece o benefício duplo de dar visibilidade imediata a um problema (através do feed público) e capacitar o usuário para a ação formal (através dos guias), transformando a frustração em um processo claro e acessível.

A tabela a seguir resume a posição e o valor único do "Guardiões da Universidade" no ecossistema da UnB:

| | |
| :--- | :--- |
| **Para:** | Discentes e servidores da Universidade de Brasília (UnB). |
| **Necessidade:** | De um canal que resolva a "falta de informação" e a "sensação de desamparo institucional" sobre os problemas da universidade. |
| **O (nome do produto):** | Guardiões da Universidade. |
| **Que:** | É uma plataforma web (Cliente-Servidor) que serve como um meio para expor denúncias e, o mais importante, como um guia que orienta sobre os procedimentos oficiais de denúncia. |
| **Ao contrário de:** | Utilizar unicamente a plataforma oficial do governo (Fala.BR), que é a única alternativa autorizada, mas que não oferece um espaço comunitário para visualização de demandas nem um guia simplificado e centralizado focado na UnB. |
| **Nosso produto:** | Não substitui o canal oficial, mas atua como um facilitador que **redireciona e orienta** o usuário para os canais corretos, ao mesmo tempo em que fortalece o senso de comunidade ao expor os problemas do dia a dia. |

### 1.3 Objetivos do Produto

O objetivo primordial do projeto "Guardiões da Universidade" é **sanar a lacuna de comunicação e orientação** que a comunidade acadêmica da UnB enfrenta.

Conforme detalhado na seção 1.1, o problema central não é a ausência de canais formais, mas a dificuldade em acessá-los e a consequente sensação de desamparo institucional. Portanto, o objetivo estratégico deste software não é substituir os canais oficiais, mas sim atuar como uma camada de facilitação que capacita o usuário.

Para alcançar este objetivo principal, o projeto se baseia nos seguintes objetivos secundários:

1.  **Consolidar as Informações Oficiais:**
    O software deve funcionar como um repositório centralizado, agregando e organizando todos os guias, tutoriais e links relevantes para os processos formais de denúncia. Isso ataca diretamente a "falta de informação".

2.  **Oferecer um Canal de Exposição Comunitária:**
    A plataforma deve permitir a postagem pública de queixas. Isso visa tratar o "sentimento de não serem ouvidos", dando voz à comunidade e permitindo que todos visualizem as demandas coletivas.

3.  **Simplificar a Experiência do Usuário:**
    Através de uma interface intuitiva, o projeto visa traduzir a burocracia complexa dos canais existentes em um fluxo claro e acessível, efetivamente facilitando o processo.

### 1.4 Tecnologias a Serem Utilizadas

O sistema "Guardiões da Universidade" utiliza um conjunto de tecnologias modernas focadas em escalabilidade, separação de responsabilidades e uma experiência de desenvolvimento robusta e manutenível. A pilha de tecnologia (tech stack) é dividida nas seguintes categorias:

#### Linguagem Principal

* **TypeScript:**
    É a linguagem de programação principal utilizada em *todo* o projeto, tanto no Back-end (com NestJS) quanto no Front-end (com Next.js/React). Seu uso garante um código fortemente tipado, mais seguro e fácil de manter.

#### Gerenciamento, Design e Qualidade

* **Git / GitHub:**
    O Git é usado para o versionamento de código, com o GitHub servindo como repositório central. O projeto adota uma estratégia de **Monorepo**, hospedando o Back-end e o Front-end no mesmo repositório.

* **Zenhub:**
    É a ferramenta de gerenciamento de projeto integrada ao GitHub. É usada para organizar o Backlog do Produto, planejar as Sprints e acompanhar o fluxo de trabalho.

* **Figma:**
    É a ferramenta de design colaborativo usada para a prototipação de alta fidelidade (UI) e criação de diagramas da arquitetura.

* **Jest:**
    É o framework de testes adotado para a criação de testes unitários e de integração, garantindo a qualidade do código.

#### Arquitetura do Cliente (Front-end)

* **Next.js (React):**

    É o framework React escolhido para construir toda a camada de apresentação (UI). É responsável pelo roteamento das páginas e pela renderização dos componentes visuais.
* **TailwindCSS:**

    É o framework de CSS "utility-first" utilizado para a estilização dos componentes, permitindo a implementação rápida e consistente dos protótipos do Figma.
* **Axios:**

    É a biblioteca (cliente HTTP) responsável por executar a comunicação com o back-end, consumindo a API REST (fazendo requisições `POST`, `GET`, etc.).

#### Arquitetura do Servidor (Back-end)

* **NestJS (Node.js):**
    É o framework de servidor (rodando sobre Node.js) que organiza toda a lógica de negócio em uma Arquitetura em Camadas (Controllers e Services) e expõe a API REST para o front-end.

* **PostgreSQL:**
    É o sistema de banco de dados relacional escolhido para a persistência e armazenamento de todos os dados da aplicação (usuários, denúncias, etc.).

* **Prisma:**
    É o ORM (Object-Relational Mapper) que faz a "ponte" entre o código NestJS (JavaScript/TypeScript) e o banco de dados PostgreSQL (SQL). Ele garante que todas as consultas ao banco sejam seguras e tipadas.

* **JWT (JSON Web Tokens) e Bcrypt:**
    São as tecnologias de segurança. O **Bcrypt** é usado para criar um *hash* seguro das senhas dos usuários antes de salvá-las. O **JWT** é usado para criar "crachás" (tokens) de autenticação que o front-end envia para acessar rotas protegidas da API.