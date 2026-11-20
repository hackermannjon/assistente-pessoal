# Capacidade: voz

Ligada quando `"voz": true` no config. Nada disto vem instalado: siga os passos só depois do ok.

## O que é
Duas metades, que podem ser ligadas separadas:
- **Eu falo:** depois de cada resposta, eu leio em voz alta um resumo de 1 ou 2 frases.
- **Eu ouço:** você fala em vez de digitar.

## Antes de começar, diga à pessoa
- **Custo no plano:** baixo. Cada resposta falada é um comando a mais (algumas centenas de tokens). A voz em si roda no computador, fora do plano.
- **O que instalar e tempo:** depende da opção escolhida (tabela abaixo).
- Peça o ok e a escolha da opção.

## Opções para eu falar

| Opção | Custo em dinheiro | Instalar | Tempo | Qualidade |
|---|---|---|---|---|
| Voz do sistema | grátis, offline | nada no Mac e no Windows; `espeak-ng` no Linux | 2 min | robótica a razoável |
| edge-tts | grátis, precisa de internet | `pip install edge-tts` (Python 3) | 5 min | boa (vozes neurais, várias em pt-BR) |
| Piper | grátis, offline | binário do Piper + um modelo de voz (~60 MB) | 10–15 min | boa, roda local |
| Modelo que a pessoa já tem | o dela | o que o modelo pede | varia | a dela |

Pergunte primeiro: "você já tem um modelo de voz (um serviço, um modelo local, uma voz clonada)?" Se tiver, adapte o script abaixo para chamar esse modelo.

## Passos (depois do ok)
1. Crie `ferramentas/falar.py` (ou `.ps1` no Windows sem Python) que recebe um texto e fala, usando a opção escolhida:
   - Mac, voz do sistema: `say -v Luciana "texto"` (liste as vozes com `say -v '?'`).
   - Windows, voz do sistema: PowerShell com `Add-Type -AssemblyName System.Speech` e `SpeechSynthesizer.Speak`.
   - Linux: `espeak-ng -v pt-br "texto"` ou `spd-say`.
   - edge-tts: `edge-tts --voice pt-BR-FranciscaNeural --text "texto" --write-media /tmp/fala.mp3` e tocar o mp3 (`afplay` no Mac, `ffplay -nodisp -autoexit` em qualquer sistema).
2. Teste com uma frase curta e pergunte se a voz e o volume estão bons. Se for de noite, pergunte antes de tocar som.
3. Acrescente no AGENTS.md, seção "Capacidades ligadas": "Voz: no fim de cada resposta, rode `python3 ferramentas/falar.py \"<resumo de 1 ou 2 frases>\"`. Não leia código, tabelas nem links em voz."
4. Grave `"voz": true` no config e uma linha no `memoria/diario.md`.

## Opções para eu ouvir
- **Ditado do sistema** (grátis, sem instalar): no Mac, ative em Ajustes > Teclado > Ditado; no Windows, `Win + H`. Funciona em qualquer terminal ou app.
- **Voz do próprio app:** se a pessoa usa o app do ChatGPT ou do Claude, o modo de voz deles conversa direto, mas não lê estes arquivos. Para trabalhar com a memória, use o ditado no Codex/Claude Code.
- **Whisper local** (grátis, offline, mais preciso): só se ela pedir; instalação de 15–30 min e modelo de 0,5 a 1,5 GB.

## Para desligar
Tire a linha de voz do AGENTS.md e ponha `"voz": false`.
