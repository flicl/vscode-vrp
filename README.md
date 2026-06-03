# FL Solutions — Huawei VRP

Syntax highlighting e snippets para arquivos de configuração **Huawei VRP** (Versatile Routing Platform) no VS Code / Antigravity IDE.

Desenvolvido pela **FL Solutions** para uso interno em roteadores Huawei NetEngine (NE8000 e similares).

---

## Funcionalidades

### Syntax Highlighting

A extensão reconhece e colore os seguintes construtos:

| Construto | Exemplos |
|---|---|
| **BGP** | `bgp 65000`, `group`, `peer`, `ipv4-family unicast`, `ipv6-family unicast`, `fake-as`, `graceful-restart` |
| **OSPF / OSPFv3** | `ospf 1 router-id`, `ospfv3 1`, `area 0.0.0.0`, `network`, `opaque-capability` |
| **route-policy** | `route-policy NAME permit node 10`, `if-match`, `apply local-preference` |
| **ip-prefix / ipv6-prefix** | `ip ip-prefix BOGONS index 10 permit`, `ip ipv6-prefix MEUS-PREFIXOS-V6` |
| **Rotas estáticas** | `ip route-static`, `ipv6 route-static` |
| **Interfaces** | `interface Eth-Trunk10`, `vlan-type dot1q`, `ipv6 enable`, `ipv6 address` |
| **SSH hardening** | `ssh server cipher`, `ssh server hmac`, `ssh server key-exchange`, `ssh client publickey` |
| **SNMP** | `snmp-agent local-engineid`, `snmp-agent sys-info version v3` |
| **NE8000 Avançado** | `ssl policy`, `diffserv domain`, `mpls lsr-id`, `license`, `virtual-system`, `ccc`, `dcn`, `cpu-defend policy`, `traffic policy` |
| **BNG / BRAS** | `ip-pool bas`, `ipv6-pool bas`, `radius-server group`, `domain`, `bas`, `pppoe-server bind Virtual-Template`, `ipv6 prefix` |
| **AAA** | `aaa`, `authentication-scheme`, `local-user`, `domain` |
| **Endereços IPv4** | `198.51.100.22`, `192.0.2.1` — highlight automático |
| **Endereços IPv6** | `2001:DB8:1234::1`, `2001:DB8:5678::C2` — highlight automático |
| **Ações** | `permit` → verde · `deny` → vermelho · `undo` → destaque de negação |
| **Perigosos** | `return`, `reboot`, `reset`, `shutdown` → vermelho forte |
| **Separadores** | Linhas `#` → comentário |
| **Header** | `<NE8000-BRAS>dis cu`, `!Software Version` → itálico |

---

### Snippets

Digite o prefixo e pressione `Tab` para expandir:

| Prefixo | O que gera |
|---|---|
| `bgp-peer-group-v4` | BGP completo com peer group externo IPv4 + ipv4-family |
| `bgp-peer-group-v6` | BGP completo com peer group externo IPv6 + ipv6-family + fake-as |
| `rp-inbound` | route-policy de entrada: deny bogons, deny meus prefixos, permit default com local-preference |
| `rp-inbound-v6` | route-policy de entrada IPv6 |
| `rp-outbound-v4` | route-policy de saída: anuncia bloco público com AS-path prepend |
| `rp-outbound-v6` | route-policy de saída IPv6 |
| `bng-domain` | BNG AAA Domain base config (IP pool, IPv6 pool, Radius, DNS) |
| `bng-radius` | Radius Server Template (auth, acct, shared-key, source-ip) |
| `bng-ip-pool` | IP Pool bas para CGNAT / assinantes Locais |
| `bng-ipv6-pool-wan` | IPv6 Pool bas para prefixos WAN (Framed) |
| `bng-ipv6-pool-pd` | IPv6 Pool bas para Prefix Delegation (PD) |
| `bng-virtual-template` | Virtual-Template interface para PPPoE server |
| `bng-access-interface` | Interface de Acesso (VLAN) com PPPoE Server e BAS ativado |
| `ip-prefix-bogons` | Prefix-list BOGONS completo (RFC1918 + RFC5735, 8 entradas) |
| `ip-prefix` | Entrada única de ip ip-prefix |
| `ipv6-prefix` | Entrada única de ip ipv6-prefix |
| `iface-sub-dot1q` | Subinterface com encapsulamento dot1q (IPv4) |
| `iface-sub-dot1q-v6` | Subinterface dot1q dual-stack IPv4 + IPv6 |
| `iface-loopback` | Interface LoopBack com /32 |
| `ospf-full` | OSPF com área e network statement |
| `ospfv3-full` | OSPFv3 configuração base |
| `ospfv3-iface` | Habilitar OSPF + OSPFv3 em interface (p2p, mtu-ignore) |
| `ip route-static` | Rota estática IPv4 com description |
| `ipv6 route-static` | Rota estática IPv6 com description |
| `ip route-null` | Rota blackhole para NULL0 (IPv4) |
| `ipv6 route-null` | Rota blackhole para NULL0 (IPv6) |
| `ssh-harden` | SSH server + client com todos os algoritmos fortes (AES-GCM, SHA2, DH ≥3072) |
| `snmp-v3` | SNMP v3 base com source-interface restrito |
| `aaa` | AAA com local-user, autenticação local, bloqueio por falha |
| `acl number` | ACL numerada |
| `ip vpn-instance` | VPN instance com RD e RT |
| `vrrp vrid` | VRRP com virtual-ip e priority |
| `vlan` | VLAN individual com description |
| `vlan batch` | VLAN em lote |
| `vty` | VTY 0–4 com SSH + AAA |
| `console` | Console 0 com AAA |
| `transceiver` | Desabilita alarme de transceiver não certificado |

---

## Arquivos suportados

Extensões reconhecidas automaticamente: `.vrp`, `.cfg`

---

## Instalação (Guia para Usuários)

Para instalar a extensão no seu VS Code, siga os passos manuais abaixo (caso não possua o arquivo `.vsix`):

1. **Copie a pasta** `flsolutions.vrp-0.1.0` inteira.
2. **Cole a pasta** no diretório de extensões do seu usuário:
   - **Windows:** Aperte `Win + R`, digite `%USERPROFILE%\.vscode\extensions` e dê Enter. Cole a pasta lá dentro.
   - **Linux / Mac:** Copie para o diretório `~/.vscode/extensions/`.
3. **Reinicie** o VS Code.
4. Pronto! Ao abrir um arquivo com final `.vrp` ou `.cfg`, o VS Code já vai usar a extensão automaticamente.

> **Nota para Desenvolvedores:** No ambiente de desenvolvimento, a extensão pode ser instalada via *symlink*. Qualquer edição nos arquivos reflete imediatamente após o comando `Developer: Reload Window`.

---

## Exemplos de configuração coberta

```vrp
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
route-policy IN-UPSTREAM-1 deny node 10
 if-match ip-prefix BOGONS
#
route-policy IN-UPSTREAM-1 permit node 30
 if-match ip-prefix ROTA-DEFAULT
 apply local-preference 800
```

```vrp
ip ip-prefix BOGONS index 10 permit 10.0.0.0 8 greater-equal 8 less-equal 32
ip ip-prefix BOGONS index 20 permit 100.64.0.0 10 greater-equal 10 less-equal 32

ip ipv6-prefix MEUS-PREFIXOS-V6 index 10 permit 2001:DB8:: 32

ipv6 route-static 2001:DB8:: 32 NULL0 description BL-BLOCO-PUB-v6
```

---

## Versão

`0.1.0` — FL Solutions · 2026
