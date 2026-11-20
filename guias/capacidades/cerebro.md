# Capacidade: cérebro pessoal

Ligada quando `"cerebro": true`. Siga só depois do ok.

## O que é
Se a pessoa também usa o repositório "cérebro pessoal" (diário com análise, neurônios e coach), eu posso LER o cérebro para conhecer melhor o momento dela: o que pesa agora, metas, padrões. Eu não escrevo lá. Quem cuida do cérebro é a sessão do próprio cérebro.

## Antes de começar, diga à pessoa
- **Custo no plano:** médio, só quando eu consultar o cérebro (ler o índice e 1 a 3 neurônios). Eu não leio o cérebro em toda conversa, só quando o assunto pedir.
- **O que instalar e tempo:** nada; 2 minutos.
- **Privacidade:** o cérebro é íntimo. O que eu ler de lá não vai para arquivo meu, página nem rotina sem ela pedir.
- Peça o ok.

## Passos
1. Pergunte o caminho da pasta do cérebro e grave em `"caminho_cerebro"` no config.
2. Teste lendo só `<caminho>/cerebro/INDEX.md` e diga quantos neurônios achou.
3. Acrescente no AGENTS.md, "Capacidades ligadas": "Cérebro: só leitura em <caminho>. Comece pelo `cerebro/INDEX.md` e abra só o neurônio do assunto. Nunca escreva lá."
4. No Claude Code, a pasta de fora pede permissão (`/add-dir <caminho>`). No Codex, rode com acesso de leitura àquela pasta. No Antigravity, adicione a pasta ao workspace.

## Para desligar
Tire a linha do AGENTS.md e ponha `false` no config.

> **Registro:** tudo o que este passo a passo criar fora da pasta (agendamento, programa, modelo, pasta) vai antes para `estado/criados.md`, com o comando para desfazer. É o que o "apagar tudo" usa.
