# Issues do Product Backlog — Senac ResourceHub

Crie as issues nesta ordem. Em cada uma, copie o TÍTULO para o campo de título e o CORPO para a descrição. As labels vão no menu lateral "Labels".

Os pontos das 4 primeiras são uma sugestão. A equipe deve votar no Planning Poker (só os Developers votam) e, se o resultado for outro, usar a label do valor votado.

---

## 1

**Título:**
Como administrador, quero tratar as reservas futuras de uma unidade colocada em manutenção, para que nenhum usuário chegue ao DI e encontre o equipamento parado

**Labels:** tipo:história · prioridade:must · pontos:5

**Corpo:**

```
Contexto: hoje o administrador já consegue marcar uma unidade como Manutenção em /admin/unidades, e isso impede novas reservas. Mas as reservas que já existiam para essa unidade continuam ativas e o usuário não é avisado.

## Critérios de aceite
- [ ] Ao confirmar a troca para Manutenção ou Inativa, a janela de confirmação mostra quantas reservas futuras ativas a unidade possui
- [ ] Cada reserva futura é movida para outra unidade disponível do mesmo recurso, no mesmo período
- [ ] Se não houver outra unidade livre, a reserva é cancelada com o motivo "Unidade em manutenção"
- [ ] O usuário afetado recebe uma notificação na central informando a nova unidade ou o cancelamento
- [ ] Reservas que já estão em andamento não são alteradas

## Cenário
Dado que a unidade OSC-04 tem uma reserva futura para 10/11 às 14h e a OSC-05 está livre nesse horário
Quando o administrador marca a OSC-04 como Manutenção
Então a reserva passa para a OSC-05 e o usuário recebe a notificação da troca
```

---

## 2

**Título:**
Como usuário, quero entrar em uma lista de espera quando não houver unidade disponível no horário que preciso, para ser avisado se uma vaga abrir

**Labels:** tipo:história · prioridade:must · pontos:5

**Corpo:**

```
## Critérios de aceite
- [ ] O botão "Entrar na lista de espera" só aparece quando não existe unidade disponível no período escolhido
- [ ] O usuário não pode entrar duas vezes na lista do mesmo recurso e período
- [ ] O usuário consegue sair da lista pela página Minhas Reservas
- [ ] Quando uma reserva desse recurso e período é cancelada, o primeiro da fila recebe uma notificação na central
- [ ] Entrar na lista não cria reserva; depois do aviso o usuário reserva normalmente
- [ ] A entrada na lista é removida automaticamente quando o horário já passou

## Cenário
Dado que as 3 impressoras Bambu Lab A1 estão reservadas no dia 12/11 das 9h às 12h
Quando a Ana entra na lista de espera e uma dessas reservas é cancelada
Então a Ana recebe a notificação "Vaga disponível" e consegue reservar a unidade liberada
```

---

## 3

**Título:**
Como usuário, quero fazer check-in quando chegar para usar o recurso, para confirmar que a minha reserva está sendo utilizada

**Labels:** tipo:história · prioridade:must · pontos:3

**Corpo:**

```
## Critérios de aceite
- [ ] O botão "Fazer check-in" aparece em Minhas Reservas de 10 minutos antes até 15 minutos depois do início da reserva
- [ ] Fora dessa janela o botão não aparece
- [ ] O sistema grava a data e a hora do check-in
- [ ] Uma reserva aceita apenas um check-in
- [ ] Reservas canceladas não aceitam check-in
- [ ] Na área administrativa de reservas, o administrador vê se cada reserva teve check-in

## Cenário
Dado que o Bruno tem uma reserva do Laboratório de Redes às 19h
Quando ele clica em "Fazer check-in" às 19h05
Então o sistema registra o horário e a reserva aparece como "Em uso" com check-in confirmado
```

---

## 4

**Título:**
Como administrador, quero que reservas sem check-in sejam liberadas automaticamente 15 minutos após o início, para que o recurso volte a ficar disponível para outras pessoas

**Labels:** tipo:história · prioridade:must · pontos:5

**Corpo:**

```
Dependência: esta história só pode ser feita depois da história de check-in.

## Critérios de aceite
- [ ] Uma reserva ativa sem check-in 15 minutos após o início passa para o status "Ausência"
- [ ] Reservas com check-in nunca são liberadas
- [ ] Depois da liberação, a unidade aparece como disponível no calendário pelo restante do período
- [ ] O usuário recebe uma notificação informando que a reserva foi liberada por ausência
- [ ] O status "Ausência" aparece como opção no filtro da área administrativa de reservas

## Cenário
Dado que a Carla reservou o Kit Arduino KIT-03 das 14h às 16h e não fez check-in
Quando passa das 14h15
Então a reserva é marcada como Ausência e o KIT-03 aparece disponível das 14h15 às 16h
```

---

## 5

**Título:**
Como usuário, quero adicionar minha reserva ao meu calendário pessoal (Google ou Outlook), para não esquecer a data e o horário

**Labels:** tipo:história · prioridade:should

---

## 6

**Título:**
Como professor, quero reservar o mesmo laboratório toda semana no mesmo horário, para não precisar repetir a reserva a cada aula

**Labels:** tipo:história · prioridade:should

---

## 7

**Título:**
Como administrador, quero definir quais recursos precisam de aprovação de um técnico antes da confirmação, para controlar o uso de equipamentos sensíveis

**Labels:** tipo:história · prioridade:should

---

## 8

**Título:**
Como administrador, quero ver relatórios de uso por recurso, unidade e período, para identificar quais recursos são mais e menos utilizados

**Labels:** tipo:história · prioridade:should

---

## 9

**Título:**
Como usuário, quero receber um e-mail de lembrete 1 hora antes da minha reserva, para não perder o horário

**Labels:** tipo:história · prioridade:could

---

## 10

**Título:**
Como usuário, quero relatar um problema em um equipamento depois de usá-lo, para que a equipe do DI verifique a unidade

**Labels:** tipo:história · prioridade:could

---

## 11

**Título:**
Como administrador, quero consultar o histórico de quem criou, alterou ou cancelou cada reserva, para ter rastreabilidade das ações no sistema

**Labels:** tipo:história · prioridade:could
