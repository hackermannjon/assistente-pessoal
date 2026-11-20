# Capacidade: rotinas automáticas

Ligada quando `"rotinas": true`. Nada vem agendado: siga só depois do ok.

## O que é
Eu fazer algo sozinha em horário marcado, sem ninguém olhando. Exemplos:
- **Memória no git** (todo dia à noite): commit da pasta `memoria/`. Não usa IA, custo zero.
- **Resumo da manhã:** lista curta do que está pendente, a partir da memória.
- **Surpresa do dia:** uma coisa útil que a pessoa não pediu (um plano, uma pesquisa, um checklist), entregue em `trabalho/` com o motivo.

## Antes de começar, diga à pessoa
- **Custo no plano:** cada rotina com IA é uma conversa inteira que roda sozinha. Uma por dia com o modelo barato é pouco; várias por dia, ou com o modelo forte, comem a cota que ela usaria conversando. Regra fixa: rotina usa SEMPRE o modelo mais barato (veja `guias/MODELOS-E-CUSTOS.md`) e nunca roda em loop.
- **O que instalar e tempo:** nada além da ferramenta que ela já usa; agendar leva 10–20 min.
- Peça o ok para cada rotina separada, com o horário.

## Passos (depois do ok)
1. Crie `ferramentas/rotina.sh` (ou `.ps1`) que:
   - para na hora se existir o arquivo `PARAR` na raiz desta pasta (o freio de emergência);
   - roda a ferramenta sem interface, com o modelo barato e com permissões só de leitura e escrita nesta pasta:
     - Codex: `codex exec -m <modelo barato> -s workspace-write "<pedido>"`
     - Claude Code: `claude -p "<pedido>" --model haiku --allowedTools "Read,Write,Edit,Glob,Grep"`
     - Antigravity: `agy -p "<pedido>"` (escolha o Flash)
   - grava a saída em `trabalho/rotinas/AAAA-MM-DD-<nome>.md`.
2. O pedido de cada rotina diz: o que fazer, onde salvar, "não mande mensagem a ninguém, não instale nada, não gaste dinheiro", e acrescentar uma linha em `memoria/diario.md`.
3. Agende no sistema (pede ok, é configuração do sistema):
   - Mac: um `launchd` em `~/Library/LaunchAgents/` (ou `crontab -e`).
   - Linux: `crontab -e`.
   - Windows: Agendador de Tarefas (`schtasks /create ...`).
   - Se a pessoa usa o app do Codex e ele tiver tarefas agendadas, pode ser mais simples agendar por lá. Confira na versão dela.
4. Rode uma vez na mão, mostre o resultado e só então deixe agendado.
5. Liste as rotinas ativas no AGENTS.md, seção "Capacidades ligadas", com horário e como parar.

## Freios
- Arquivo `PARAR` na raiz: nada roda.
- Teto de tempo por rotina (ex.: `timeout 1800` no comando).
- Rotina nunca usa o modelo mais caro nem subagentes.

## Para desligar
Remova o agendamento do sistema, apague o script e ponha `"rotinas": false`.

> **Registro:** tudo o que este passo a passo criar fora da pasta (agendamento, programa, modelo, pasta) vai antes para `estado/criados.md`, com o comando para desfazer. É o que o "apagar tudo" usa.
