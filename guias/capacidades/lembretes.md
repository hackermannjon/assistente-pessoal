# Capacidade: lembretes e agenda

Ligada quando `"lembretes": true`. Siga só depois do ok.

## O que é
Eu transformar "me lembra de X na quinta às 10h" num lembrete de verdade.

## Antes de começar, diga à pessoa
- **Custo no plano:** baixo (um arquivo ou um comando por lembrete).
- **O que instalar e tempo:** o jeito 1 não instala nada (5 min). O jeito 2 pede permissão do sistema (10 min).
- Peça o ok e a escolha.

## Jeito 1: arquivo de calendário (.ics), funciona em qualquer agenda
1. Eu crio `trabalho/lembretes/AAAA-MM-DD-assunto.ics` com o evento (data absoluta, fuso da pessoa, alarme).
2. A pessoa abre o arquivo com dois cliques e ele entra no calendário dela (Google, Apple, Outlook).

## Jeito 2: direto no sistema
- Mac: app Lembretes via `osascript` (o macOS pede permissão na primeira vez).
- Windows: tarefa agendada que mostra uma notificação (veja `notificacoes.md`).
- Se a ferramenta dela tiver conector de calendário (Google Agenda etc.), dá para usar, com o ok dela para conectar.

## Regras
- Data sempre absoluta (2026-03-05 10:00), nunca "quinta".
- Lembrete que envolve outra pessoa (convite) é mensagem: pede ok antes.

## Para desligar
Ponha `"lembretes": false`.

> **Registro:** tudo o que este passo a passo criar fora da pasta (agendamento, programa, modelo, pasta) vai antes para `estado/criados.md`, com o comando para desfazer. É o que o "apagar tudo" usa.
