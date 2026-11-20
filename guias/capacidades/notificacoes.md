# Capacidade: notificações no computador

Ligada quando `"notificacoes": true`. Siga só depois do ok.

## O que é
Uma notificação do sistema quando algo demorado termina ou quando eu preciso de uma resposta.

## Antes de começar, diga à pessoa
- **Custo no plano:** quase zero (um comando curto).
- **O que instalar e tempo:** Mac e Linux não instalam nada; no Windows, o módulo BurntToast do PowerShell (opcional). 5–10 min.
- Peça o ok.

## Passos
1. Crie `ferramentas/avisar.sh` (ou `.ps1`) que recebe um texto:
   - Mac: `osascript -e 'display notification "texto" with title "Assistente"'`
   - Linux: `notify-send "Assistente" "texto"`
   - Windows: `New-BurntToastNotification -Text "Assistente","texto"` (depois de `Install-Module BurntToast`, que pede ok), ou um `msg *` simples.
2. Teste uma vez.
3. Algumas ferramentas já avisam sozinhas: o Codex tem a opção `notify` no `config.toml` e o Claude Code tem hooks de notificação. Se a pessoa preferir, configure por lá (é configuração: pede ok).
4. Acrescente no AGENTS.md, "Capacidades ligadas": "Notificações: ao terminar tarefa longa, rode `ferramentas/avisar.sh \"<o que terminou>\"`."

## Para desligar
Tire a linha do AGENTS.md e ponha `false` no config.

> **Registro:** tudo o que este passo a passo criar fora da pasta (agendamento, programa, modelo, pasta) vai antes para `estado/criados.md`, com o comando para desfazer. É o que o "apagar tudo" usa.
