# Secure Vault — OpenClaw

Este diretório foi criado para guardar **somente material seguro para versionamento**.

## Regra principal

Nunca coloque aqui chaves privadas, senhas, tokens, arquivos `.env`, cookies, certificados privados ou qualquer segredo em texto puro.

## O que pode ficar aqui

- Chaves SSH **públicas**.
- Scripts de bootstrap.
- Modelos de configuração.
- Arquivos criptografados localmente antes do commit, por exemplo `.age`, `.gpg` ou `sops.yaml.enc`.
- Documentação operacional.

## O que não pode ficar aqui

- `oracle-vm.key`
- `openclaw-servidor-recovery`
- qualquer arquivo sem `.pub` dentro de `.ssh`
- tokens da Oracle, OpenRouter, Telegram, Cloudflare, GitHub ou Ollama
- senhas em texto puro

## VM OpenClaw

Host público:

```txt
163.176.183.193
```

Usuário SSH:

```txt
ubuntu
```

Comandos desejados no cliente, após instalar o `~/.ssh/config`:

```bash
ssh openclaw
ssh openclaw-admin
ssh openclaw-recovery
```

## Fluxo correto para novos computadores

1. Gerar uma chave SSH nova no dispositivo.
2. Adicionar **somente a chave pública** ao GitHub ou ao arquivo público correspondente.
3. Manter a chave privada apenas no dispositivo.
4. Instalar o arquivo `~/.ssh/config` local.
5. Testar `ssh openclaw` e `ssh openclaw-admin`.

## Futuras informações realmente sensíveis

Antes de colocar qualquer segredo neste repositório, criptografe localmente com uma ferramenta própria, como `age`, `gpg` ou `sops`. O GitHub não deve receber segredo em texto puro.
