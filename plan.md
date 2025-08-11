```markdown
# Plano Detalhado de Implementação do App GymRats

Este plano detalha todas as alterações e arquivos dependentes para criar um aplicativo GymRats completo, com autenticação, criação e gerenciamento de desafios, registro de atividades com upload de fotos, rankings, interação social e integração simulada com plataformas de saúde.

---

## 1. Autenticação e Gestão de Usuários

### Arquivos a serem criados/modificados:
- **src/components/AuthForm.tsx**  
  - Crie um componente de formulário com campos de e-mail/usuário e senha.  
  - Adicione validação de entrada e mensagens de erro amigáveis.

- **src/app/login/page.tsx**  
  - Implemente a página de login utilizando o componente AuthForm.  
  - Garanta uma interface limpa com tipografia moderna, cores neutras e espaçamento adequado.

- **src/app/api/auth/route.ts**  
  - Crie uma API simples para processar login/mock signup.  
  - Retorne status e mensagens de erro apropriadas (ex.: status 401 para credenciais inválidas).

---

## 2. Criação e Gerenciamento de Desafios

### Arquivos a serem criados/modificados:
- **src/components/ChallengeCard.tsx**  
  - Desenvolva um componente de cartão para exibir informações de cada desafio (nome, objetivo, descrição, data).  
  - Estilize com borda sutil, sombra leve e espaçamento consistente.

- **src/app/challenges/page.tsx**  
  - Implemente a lista de desafios, utilizando dados mock ou a API.  
  - Inclua um botão “Criar Desafio” que abre um modal com formulário.

- **src/app/challenges/[id]/page.tsx**  
  - Crie uma página de detalhe/edição de desafio com informações completas e um formulário de atualização.  
  - Trate erros de API e validações com mensagens claras.

- **src/app/api/challenge/route.ts**  
  - Implemente endpoints REST (GET, POST, PUT, DELETE) para desafios.  
  - Inclua tratamento de erros e resposta em JSON.

---

## 3. Registro de Atividades e Upload de Fotos

### Arquivos a serem criados/modificados:
- **src/components/ActivityPost.tsx**  
  - Crie um formulário para registrar atividades com campos para texto e upload de foto.  
  - Utilize um <input type="file"> e adicione verificação de tipo/tamanho do arquivo; defina fallback via onerror no <img>.

- **src/app/activity/page.tsx**  
  - Implemente uma página para exibir e criar postagens de atividades.  
  - Organize a interface com seções para formulário de postagem e histórico de atividades.

- **src/app/api/activity/route.ts**  
  - Desenvolva uma API para receber dados de atividades e arquivos enviados.  
  - Garanta respostas consistentes em caso de sucesso ou erro.

---

## 4. Rankings, Leaderboard e Gamificação

### Arquivos a serem criados/modificados:
- **src/components/Leaderboard.tsx**  
  - Crie um componente que liste participantes com suas pontuações em ordem decrescente.  
  - Use um layout de tabela ou lista com espaçamentos consistentes e tipografia clara.

- **src/app/leaderboard/page.tsx**  
  - Implemente a página de leaderboard que consome dados do endpoint ou mock local.

- **(Opcional) src/app/api/leaderboard/route.ts**  
  - Caso opte por API, crie um endpoint para retornar dados de ranking.

---

## 5. Interação Social e Sistema de Comentários

### Arquivos a serem criados/modificados:
- **src/components/Comments.tsx**  
  - Crie um componente de comentários para ser incorporado em ActivityPost.  
  - Permita input de texto, exibição de lista de comentários e tratamento de erros.

- **src/app/api/comments/route.ts**  
  - Crie endpoints para criação e listagem de comentários.  
  - Implemente validação e mensagens de retorno.

---

## 6. Página de Perfil e Integração com Plataformas de Saúde

### Arquivos a serem criados/modificados:
- **src/app/profile/page.tsx**  
  - Desenvolva uma página de perfil com os dados do usuário, atividades recentes, desafios ativos e leaderboard local.  
  - Inclua um botão "Sincronizar Dados de Saúde" que chame a API de integração.

- **src/app/api/health-sync/route.ts**  
  - Implemente uma API mock para simular a sincronização com Apple Health/Google Fit, retornando dados fictícios.

---

## 7. Estilo Global e Melhorias de UI/UX

### Arquivos a serem modificados:
- **src/app/globals.css**  
  - Atualize para incluir estilos modernos: tipografia limpa, paleta de cores neutras e espaçamentos consistentes.  
  - Adicione classes utilitárias para botões, formulários e cartões.

- **Erros e Validações**  
  - Em todos os formulários, adicione mensagens de erro visíveis e feedback visual (ex.: bordas vermelhas em inputs com erro).  
  - Nos endpoints, retorne status HTTP claros e mensagens de erro em JSON.

---

## 8. Testes e Documentação

### Testes:
- Utilize comandos `curl` para testar cada API:
  - Para autenticação, enviar dados para `/api/auth/route.ts`.
  - Para criação/atualização de desafios, usar `/api/challenge/route.ts`.
  - Para upload de atividades, utilizar `/api/activity/route.ts`.
- Verifique status HTTP e mensagens de erro.

### Documentação:
- Atualize **README.md** com instruções de instalação, uso e detalhes dos endpoints.
- Liste dependências e explicite as práticas adotadas (validações, tratamento de erros, layout responsivo).

---

## Resumo
- Implementamos um sistema de autenticação, com página de login e API mock.  
- Desenvolvemos componentes para desafios, atividades, leaderboard e comentários, todos integrados via endpoints REST.  
- Criamos páginas Next.js dedicadas para cada funcionalidade (login, desafios, atividades, leaderboard, perfil).  
- Adicionamos upload de foto com tratamento de erros e fallback para imagens.  
- Incluímos uma API mock para sincronização de dados de saúde.  
- Estilos globais modernos foram aplicados para uma UI limpa e responsiva.  
- Todos os endpoints incluem validação e mensagens de erro claras.  
- Instruções de teste com curl e documentação foram previstas no README.
