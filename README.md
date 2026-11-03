# Senac ResourceHub
 
Sistema de Reservas de Laboratórios e Equipamentos do Centro Universitário Senac. Projeto acadêmico da disciplina Engenharia de Software II.
 
Produção: https://senac-resource-hub.vercel.app
 
Este repositório contém a versão funcional do sistema e, a partir do Laboratório 07, o Product Backlog da próxima evolução do produto (issues e quadro no GitHub Projects).
 
## Elevator pitch
 
Para alunos, professores e técnicos do Senac que precisam usar laboratórios e equipamentos do Departamento de Inovação (DI), o Senac ResourceHub é uma plataforma web de reservas que mostra a disponibilidade em tempo real e garante uma unidade física livre para cada reserva. Diferente da consulta presencial ou de combinados informais, o nosso sistema evita conflitos de horário e, nesta evolução, passa a liberar automaticamente os recursos reservados que não foram usados.
 
## Problema
 
Hoje o aluno pode chegar ao DI e descobrir que a impressora 3D ou o laboratório já está ocupado. A primeira versão do ResourceHub resolveu a consulta e a reserva, mas ainda existem três problemas:
 
- Reservas feitas e não utilizadas deixam o recurso bloqueado enquanto outras pessoas precisam dele.
- Quando uma unidade entra em manutenção, quem já tinha reserva nela não fica sabendo.
- Quem encontra um horário cheio não tem como saber se uma vaga abriu.
## Público
 
- **Aluno**: consulta e reserva laboratórios, kits, equipamentos e impressoras 3D.
- **Professor**: reserva laboratórios para aulas e atividades práticas.
- **Administrador / técnico do DI**: cadastra recursos e unidades, acompanha as reservas e cuida da manutenção.
## Proposta de valor
 
Fazer cada horário reservado ser realmente usado: quem reservou confirma que chegou, quem não apareceu libera o recurso e quem estava esperando é avisado.
 
## Funcionalidades essenciais (Must)
 
1. Consultar disponibilidade e reservar sem conflito de horário (já existe na versão atual).
2. Check-in na reserva, com liberação automática quando o usuário não comparece.
3. Tratamento das reservas de unidades que entram em manutenção.
O backlog completo está nas [issues](../../issues) e no quadro do Projects.
 
## Fora de escopo neste semestre (Won't)
 
- Login com conta institucional do Senac (SSO).
- Integração com o calendário oficial do Senac.
- Upload de arquivos para impressão 3D.
- Modelos 3D mais realistas dos equipamentos.
- Aplicativo mobile nativo.
- Troca de stack ou mudanças grandes de arquitetura.
## Indicadores de sucesso
 
- Taxa de comparecimento: percentual de reservas com check-in.
- Nenhuma reserva futura ativa em unidade marcada como Manutenção.
## Equipe
 
| Nome | Papel |
|---|---|
| João Pedro Ferreira Pellegrini | Product Owner |
| Victor Eduardo Almeida Bispo | Scrum Master |
| Vitor Orati Sena | Developer |
| Bruno Orati Sena | Developer |
 
A primeira versão do sistema foi desenvolvida por Bruno Orati Sena, Guilherme Inácio Silva e Vitor Orati Sena.
 
## Matriz RACI
 
R = Responsável, A = Aprovador, C = Consultado, I = Informado
 
| Atividade | João Pedro (PO) | Victor (SM) | Vitor (Dev) | Bruno (Dev) |
|---|---|---|---|---|
| Priorizar o Product Backlog | A/R | C | C | C |
| Escrever histórias de usuário | A/R | R | C | C |
| Definir critérios de aceite | A/R | C | C | C |
| Estimar histórias (Planning Poker) | C | C | A/R | R |
| Facilitar cerimônias e manter o quadro | I | A/R | C | C |
| Remover impedimentos da equipe | I | A/R | C | C |
| Implementar as histórias | I | I | A/R | R |
| Revisar código e testar | C | I | R | A/R |
| Aceitar a história como concluída | A | I | C | C |
| Entregar o link do repositório no Teams | I | A/R | I | I |
 
---
 
# Informações técnicas
 
## Funcionalidades da versão atual
 
- Cadastro e login
- Confirmação de e-mail
- Recuperação de senha
- Catálogo de recursos (laboratórios, equipamentos, impressoras 3D, kits e espaço compartilhado)
- Visualizações 3D interativas por recurso
- Consulta de disponibilidade em calendário
- Reservas com atribuição automática de unidade física
- Oficina de Fabricação e Prototipagem (espaço compartilhado, uso orientado)
- Minhas Reservas
- Perfil (dados pessoais, senha, exclusão de conta)
- Notificações (reservas próprias e, para administradores, atividade administrativa)
- Área administrativa completa (dashboard, recursos, unidades, reservas, usuários)
## Tecnologias
 
- Next.js
- React
- TypeScript
- Supabase
- PostgreSQL
- Tailwind CSS
- Three.js / React Three Fiber
- Vercel
## Perfis
 
- **User** — reserva recursos, gerencia as próprias reservas e o próprio perfil.
- **Admin** — tudo o que um User faz, além de gerenciar recursos, unidades, reservas de qualquer usuário e outros usuários.
Todo cadastro público cria automaticamente um usuário `User` — não existe seleção de perfil no cadastro. Um Admin promove um `User` existente a `Admin` em `/admin/usuarios`; o primeiro Admin do sistema é configurado manualmente no banco (ver `documentacao/decisoes/admin.md`).
 
## Requisitos para executar
 
- Node.js 20 ou superior
- npm
- Um projeto Supabase (URL + publishable key)
## Como instalar
 
```bash
npm install
```
 
Copie `.env.example` para `.env.local` e preencha os valores do seu projeto Supabase.
 
## Como iniciar o desenvolvimento
 
```bash
npm run dev
```
 
Acesse [http://localhost:3000](http://localhost:3000).
 
## Como gerar build de produção
 
```bash
npm run build
npm run start
```
 
## Estrutura resumida do projeto
 
```
app/                  rotas e páginas (App Router)
components/           componentes de UI compartilhados
lib/                  utilitários, camada de dados e lógica compartilhada
public/
  imagens/            imagens estáticas
supabase/
  migrations/         schema versionado do banco
documentacao/
  requisitos/         documento original de requisitos
  referencias/         mockups de referência visual
  decisoes/            decisões arquiteturais consolidadas
```
 
## Deploy
 
Produção: https://senac-resource-hub.vercel.app
 
Banco de dados e autenticação: Supabase Cloud.
 
Claude terminou a resposta
