<div align="center">
  <img src="logo.png" alt="FL Solutions VRP Logo" width="128" height="128" />

  # FL Solutions — Huawei VRP
  
  **Syntax highlighting e snippets para arquivos de configuração Huawei VRP (Versatile Routing Platform) no VS Code.**

  [![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](#)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](#)
  [![VS Code](https://img.shields.io/badge/VS%20Code-1.51+-blueviolet.svg)](#)
</div>

---

## 📖 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [✨ Funcionalidades](#-funcionalidades)
  - [Syntax Highlighting](#syntax-highlighting)
  - [Snippets Avançados](#snippets-avançados)
- [🚀 Instalação](#-instalação)
- [💻 Exemplos de Configuração](#-exemplos-de-configuração)
- [📄 Licença](#-licença)

---

## 🧐 Sobre o Projeto

Desenvolvida pela **FL Solutions** com foco nas operações em roteadores **Huawei NetEngine** (como a série NE8000, ambientes BNG/BRAS e similares), esta extensão oferece um ambiente robusto e produtivo para a leitura e criação de arquivos de configuração (`.vrp` e `.cfg`).

O objetivo central é **prevenir erros de sintaxe** e **acelerar a escrita** de configurações extensas por meio de snippets padronizados e um syntax highlighting meticulosamente desenhado para o Huawei VRP.

---

## ✨ Funcionalidades

### Syntax Highlighting

A extensão reconhece e colore automaticamente dezenas de construtos do Huawei VRP, oferecendo clareza visual para revisar configurações com segurança:

| Contexto | Exemplos de Construtos Destacados |
| :--- | :--- |
| **BGP** | `bgp 65000`, `group`, `peer`, `ipv4-family unicast`, `ipv6-family unicast`, `fake-as` |
| **OSPF / OSPFv3** | `ospf 1 router-id`, `ospfv3 1`, `area 0.0.0.0`, `network`, `opaque-capability` |
| **Route-Policy** | `route-policy NAME permit node 10`, `if-match`, `apply local-preference` |
| **Prefix-Lists** | `ip ip-prefix BOGONS index 10 permit`, `ip ipv6-prefix MEUS-PREFIXOS-V6` |
| **Interfaces** | `interface Eth-Trunk10`, `vlan-type dot1q`, `ipv6 enable`, `ipv6 address` |
| **Segurança (SSH/SNMP)** | `ssh server cipher`, `snmp-agent local-engineid`, `snmp-agent sys-info version v3` |
| **BNG / BRAS** | `ip-pool bas`, `ipv6-pool bas`, `radius-server group`, `domain`, `bas`, `pppoe-server` |
| **AAA** | `aaa`, `authentication-scheme`, `local-user`, `domain` |
| **Endereços IP** | `198.51.100.22`, `2001:DB8:1234::1` *(Highlight automático IPv4 e IPv6)* |
| **Ações** | <span style="color:green">`permit`</span> (verde), <span style="color:red">`deny`</span> (vermelho), `undo` (negação) |
| **Ações Críticas** | <span style="color:red">**`return`**, **`reboot`**, **`reset`**, **`shutdown`**</span> (vermelho forte) |

---

### Snippets Avançados

Gere blocos complexos de configuração em segundos. Digite o prefixo desejado e pressione `Tab`:

#### 🌐 BGP e Roteamento Dinâmico
- `bgp-peer-group-v4` — BGP completo com peer group externo IPv4.
- `bgp-peer-group-v6` — BGP completo com peer group externo IPv6 + fake-as.
- `ospf-full` / `ospfv3-full` — Configuração base de OSPF e OSPFv3.

#### 🛡️ Políticas e Filtros
- `rp-inbound` / `rp-inbound-v6` — Route-policy de entrada (deny bogons, permit default).
- `rp-outbound-v4` / `rp-outbound-v6` — Route-policy de saída (anúncio de bloco com AS-path prepend).
- `ip-prefix-bogons` — Prefix-list BOGONS completa (RFC1918 + RFC5735).

#### 🛜 BNG / BRAS
- `bng-domain` — BNG AAA Domain base config (IP pool, IPv6, Radius, DNS).
- `bng-radius` — Radius Server Template (auth, acct, shared-key).
- `bng-ip-pool` / `bng-ipv6-pool-wan` / `bng-ipv6-pool-pd` — Pools de IP e IPv6 para CGNAT, WAN e Prefix Delegation.
- `bng-virtual-template` / `bng-access-interface` — Configuração de PPPoE Server.

#### 🔧 Interfaces e Segurança
- `iface-sub-dot1q` / `iface-sub-dot1q-v6` — Subinterfaces dot1q e dual-stack.
- `ssh-harden` — SSH server + client com algoritmos fortes (AES-GCM, SHA2).
- `snmp-v3` — SNMP v3 com restrição de source-interface.

*(Acesse a lista completa digitando `Ctrl+Space` em um arquivo `.vrp`)*

---

## 🚀 Instalação

Para utilizar a extensão no seu VS Code, siga os passos abaixo para instalação local:

1. **Faça o clone ou baixe este repositório**:
   ```bash
   git clone https://github.com/flicl/vscode-vrp.git flsolutions.vrp-0.1.0
   ```

2. **Mova a pasta para o diretório de extensões do seu usuário**:
   - **Windows:** Aperte `Win + R`, digite `%USERPROFILE%\.vscode\extensions` e dê Enter. Mova a pasta `flsolutions.vrp-0.1.0` para lá.
   - **Linux / Mac:** Mova a pasta para `~/.vscode/extensions/`.
     ```bash
     mv flsolutions.vrp-0.1.0 ~/.vscode/extensions/
     ```

3. **Reinicie o VS Code.**

4. Pronto! Qualquer arquivo com a extensão `.vrp` ou `.cfg` utilizará o suporte automaticamente.

> 💡 **Dica de Desenvolvimento:** Se você for modificar a extensão, pode criar um symlink da pasta do projeto diretamente para o seu diretório `.vscode/extensions/`. Use `Developer: Reload Window` no Command Palette para aplicar as mudanças instantaneamente.

---

## 💻 Exemplos de Configuração

Veja como o código fica formatado com o suporte do **FL Solutions VRP**:

```vrp
# BGP Configuration Example
bgp 65000
 router-id 192.0.2.1
 graceful-restart
 undo check-first-as
 group UPSTREAM-1 external
 peer UPSTREAM-1 as-number 65001
 peer 10.0.0.2 group UPSTREAM-1
 peer 10.0.0.2 description PEER-UPSTREAM-1
 #
 ipv4-family unicast
  undo synchronization
  preference 100 100 100
  peer UPSTREAM-1 enable
  peer UPSTREAM-1 route-policy IN-UPSTREAM-1 import
  peer UPSTREAM-1 route-policy OUT-UPSTREAM-1 export
```

```vrp
# IPv6 Static Route Example
ip ip-prefix BOGONS index 10 permit 10.0.0.0 8 greater-equal 8 less-equal 32

ip ipv6-prefix MEUS-PREFIXOS-V6 index 10 permit 2001:DB8:: 32

ipv6 route-static 2001:DB8:: 32 NULL0 description BL-BLOCO-PUB-v6
```

---

## 📄 Licença

Este projeto é licenciado sob a licença **MIT** - veja o arquivo [LICENSE.txt](LICENSE.txt) para detalhes.

<div align="center">
  <sub>Criado com orgulho pela <b>FL Solutions</b> (2026).</sub>
</div>
