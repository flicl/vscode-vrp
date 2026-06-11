<!-- markdownlint-disable MD033 -->
<div align="center">
  <img src="logo-square.png" alt="FL Solutions VRP Logo" width="128" height="128" />

# FL Solutions — Huawei VRP
  
  **Chega de errar sintaxe de madrugada! Syntax highlighting e snippets de respeito para Huawei VRP no VS Code.**

  ![Version](https://img.shields.io/badge/version-0.0.5-blue.svg)
  ![License](https://img.shields.io/badge/license-MIT-green.svg)
  ![VS Code](https://img.shields.io/badge/VS%20Code-1.51+-blueviolet.svg)
</div>
<!-- markdownlint-enable MD033 -->

---

## 📖 O que tem aqui?

- [Qual é a pegada?](#-qual-é-a-pegada)
- [✨ O que salva a vida?](#-o-que-salva-a-vida)
- [🚀 Como instalar](#-como-instalar)
- [💻 Como fica a tela?](#-como-fica-a-tela)

---

## 🧐 Qual é a pegada?

Essa extensão nasceu da minha própria necessidade operacional 😂. Quem opera rede sabe como é: você vai fechar aquele BGP ou subir um BNG no **Huawei NetEngine (NE8000, etc)**, o bloco de config é gigante, e qualquer letrinha esquecida te dá uma baita dor de cabeça (e as vezes um rollback na manutenção).

O objetivo aqui é simples: **ajudar a bater o olho e achar o erro rápido**, além de **ganhar tempo na digitação** com snippets que já entregam a configuração mastigada pro roteador.

---

## ✨ O que salva a vida?

### Cores que fazem sentido (Syntax Highlighting)

O VS Code vai colorir os comandos de VRP pra você não se perder. Destaque pra quem precisa:

| O que a gente pinta | Como fica |
| :--- | :--- |
| **BGP** | `bgp 65000`, `group`, `peer`, `ipv4-family unicast` |
| **OSPF / OSPFv3** | `ospf 1 router-id`, `ospfv3 1`, `area`, `network` |
| **Route-Policy** | `route-policy`, `if-match`, `apply local-preference` |
| **Interfaces** | `interface Eth-Trunk10`, `vlan-type dot1q` |
| **BNG / BRAS** | `ip-pool bas`, `radius-server`, `pppoe-server` |
| **IPs (v4 e v6)** | Highlight automático pra você não errar o bloco visualmente |
| **Ações Padrão** | 🟢 `permit` e `import` (Verdes), `export` (Colorido), 🔴 `deny` (Vermelho) |
| **Perigo! ⚠️** | Comandos como 🔴 **`reboot`**, **`reset`**, **`shutdown`** gritam na tela em vermelho |

---

### Snippets (É só dar Tab!)

Chega de copiar e colar do bloco de notas ou ficar caçando template antigo. Digita o atalho, aperta `Tab` e a config cai pronta:

#### 🌐 Roteamento

- `bgp-peer-group-v4` ou `v6` — Monta o BGP completo com peer group.
- `ospf-full` / `ospfv3-full` — OSPF base redondinho.

#### 🛡️ Filtros e Políticas

- `rp-inbound` / `rp-outbound-v4` — Route-policies prontas de IN e OUT.
- `ip-prefix-bogons` — Prefix-list de Bogons RFC (pra não ter que lembrar os blocos de cabeça).

#### 🛜 BNG / BRAS

- `bng-domain`, `bng-ip-pool`, `bng-virtual-template` — Padrão pra subir um PPPoE Server rapidão.
- `bng-l2tp-lac` / `bng-l2tp-lns` — Configuração de túneis L2TP LAC/LNS.
- `bng-radius-group-prod` — Radius Server Group completo para produção com atributos.

#### 🔧 Geral

- `iface-sub-dot1q` — Cria subinterface com VLAN.
- `ssh-harden` / `snmp-v3` — Segurança nos padrões fortes.
- `virtual-system-create` — Criação e alocação de recursos em Virtual Systems (VS).
- `netconf-harden` / `grpc-server` — Hardening de NETCONF/NACM e servidor gRPC para telemetria.
- `local-aaa-harden` — Regras avançadas de segurança e bloqueio de usuários AAA.
- `static-route-defaults` — Configurações padrão de rotas estáticas globais (BFD, Preference).

*(Dá um `Ctrl+Space` no arquivo `.vrp` pra ver a lista toda!)*

---

## 🚀 Como instalar

A instalação é super simples e feita diretamente pelo arquivo `.vsix`:

1. **Baixe a última versão**:
   - Acesse a página de [Releases do GitHub](https://github.com/flicl/vscode-vrp/releases).
   - Baixe o arquivo `vrp-X.X.X.vsix` mais recente.

2. **Instalação**:
   - Abra o VS Code / Antigravity.
   - Vá na aba de Extensões (`Ctrl+Shift+X` ou `Cmd+Shift+X`).
   - Clique nos três pontinhos (`...`) no canto superior direito da barra de extensões.
   - Selecione **"Install from VSIX..."** (Instalar a partir de VSIX...).
   - Escolha o arquivo `.vsix` que você acabou de baixar.

*(Alternativa Ninja via Terminal no seu editor)*:

```bash
code --install-extension vrp-0.0.5.vsix
```

1. Já era! Abriu arquivo `.vrp` ou `.cfg`, as cores já entram em ação.

---

## 💻 Como fica a tela?

Dá uma olhada no visual:

![Exemplo de Configuração BGP e IPv6](screenshot.png)

> *(Lembrando que as cores exatas mudam de acordo com o tema que você usa no seu VS Code, mas a lógica de destacar o que importa é a mesma!)*

---

## 📄 Licença

Tá liberado na licença **MIT** - o arquivo [LICENSE.txt](LICENSE.txt) tá aí pra quem quiser ler o juridiquês.

*Criado a base de muito café #CodaFofis.*
