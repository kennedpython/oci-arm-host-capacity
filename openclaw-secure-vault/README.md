# OpenClaw Secure Vault

Diretório/projeto para acesso operacional à VM `OpenClaw_Servidor` e para armazenamento futuro de segredos **somente de forma criptografada**.

## Regra absoluta

Nunca versionar segredo em texto puro.

Não subir sem criptografia:

- chave privada SSH;
- senha;
- token de API;
- `.env` real;
- cookie;
- credencial Oracle/GitHub/Cloudflare/Telegram/OpenRouter/Groq/Gemini/Ollama.

## O que este projeto aceita

- chaves SSH públicas;
- templates;
- scripts de bootstrap;
- `.env.example`;
- arquivos criptografados localmente, por exemplo `.age`, `.gpg` ou `.sops.yaml`.

## Estrutura

```txt
openclaw-secure-vault/
  README.md
  .gitignore
  public/
    openclaw_host.env
    authorized_keys.pub
  client/
    ssh_config_openclaw
    bootstrap-openclaw.ps1
    bootstrap-openclaw.sh
    connect-openclaw.ps1
    connect-openclaw.sh
  encrypted/
    README.md
    .gitkeep
  templates/
    secrets.env.example
```

## VM

```txt
Host: 163.176.183.193
User: ubuntu
```

## Comandos finais locais

Depois do bootstrap no computador/dispositivo:

```bash
ssh openclaw
ssh openclaw-admin
ssh openclaw-recovery
```

## One-liners online

PowerShell:

```powershell
irm https://raw.githubusercontent.com/kennedpython/oci-arm-host-capacity/main/openclaw-secure-vault/client/connect-openclaw.ps1 | iex
```

Bash/Linux/macOS/WSL/Termux:

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/kennedpython/oci-arm-host-capacity/main/openclaw-secure-vault/client/connect-openclaw.sh)
```

## Observação crítica

Esses comandos instalam o `~/.ssh/config` e tentam conectar. Para a conexão funcionar, o dispositivo precisa ter a chave privada local em:

```txt
~/.ssh/oracle-vm.key
```

ou a chave recovery em:

```txt
~/.ssh/openclaw-servidor-recovery
```

O GitHub guarda a referência operacional e os scripts. As chaves privadas devem ficar no dispositivo ou, se forem versionadas no futuro, precisam estar criptografadas antes do commit.
