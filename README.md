# KDTF

KDTF significa **Kumulus Data Transformation Framework**. O framework cobre arquitetura, engenharia de dados e analytics com implementação, validação e Evidence Gate. O `manifest.json` versionado **neste repositório Git** é a fonte oficial da versão e das capacidades. Cada instalação usa uma revisão concreta do Git e mostra a versão dessa revisão.

## Publicar este pacote

Extraia o ZIP e envie **o conteúdo desta pasta** para a raiz de um repositório Git próprio. Não envie apenas o ZIP. Escolha o nome e a visibilidade do repositório; este pacote não cria um repositório remoto nem define uma licença para o seu conteúdo.

```bash
git init
git add .
git commit -m "Publish KDTF"
git branch -M main
git remote add origin https://github.com/fbrcmachado/kdtf.git
git push -u origin main
```

Se o repositório remoto já existir, use o fluxo Git correspondente e preserve seu histórico. Substitua `SEU_USUARIO` e o nome do repositório pelos seus.

## Instalar em outro projeto com um agente

Depois de publicar, abra o projeto consumidor no agente e peça:

```text
Leia https://raw.githubusercontent.com/SEU_USUARIO/kdtf/main/SETUP.md
Instale o KDTF neste projeto a partir de https://github.com/SEU_USUARIO/kdtf.git.
Preserve meus arquivos existentes e mostre o diff antes de concluir.
```

O `SETUP.md` descreve os caminhos para Codex, Claude Code, GitHub Copilot, Cursor, Gemini CLI, Windsurf e Antigravity. Os adaptadores prontos ficam em `adapters/`; todos leem a mesma skill e o mesmo manifesto no projeto consumidor.

## Uso direto com Codex

Em um projeto Git, a instalação reproduzível pode usar um submódulo:

```bash
git submodule add https://github.com/fbrcmachado/kdtf.git .agents/skills/kdtf
git submodule update --init .agents/skills/kdtf
```

Em uma nova conversa: `Use $kdtf. Ativar KDTF.`

## Evolução

Altere o comportamento em `SKILL.md` e nas referências; atualize `version`, `edition` e `capabilities` em `manifest.json` na mesma mudança. Revise os adaptadores e registre uma tag Git para a versão. Projetos com submódulo atualizam o ponteiro com `git submodule update --remote .agents/skills/kdtf` e revisam a mudança. A ativação lê **a revisão instalada localmente**, sem consultar automaticamente a ponta remota. Se o repositório evoluir, a cópia instalada só muda quando for atualizada.

A skill pessoal instalada no ChatGPT Work é uma cópia separada: publicar este repositório não a atualiza automaticamente.
