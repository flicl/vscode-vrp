# Change Log

All notable changes to the **FL Solutions - Huawei VRP** extension.

## [0.0.4] - 2026-06-04

### Added

- Adicionados 8 novos snippets genéricos: BNG L2TP (LAC/LNS), criação de Virtual System (VS) e associação de recursos/interfaces, hardening de NETCONF/NACM, gRPC e telemetria, hardening de local AAA server, Radius Server Group de produção e configurações padrão para rotas estáticas.
- Melhoria no realce de sintaxe (syntax highlighting) com suporte a novos comandos e seções (grpc, telemetry, pki, whitelist, micro-isolation, bfd, stp, cfm, loop-detect, etc.).

## [0.0.3] - 2026-06-04

### Fixed

- Corrigido o bug visual no qual a logo principal e o ícone na listagem do VS Code não carregavam (redimensionado para as especificações exigidas).
- Links de imagens no README.md ajustados para serem renderizados corretamente no ambiente do VS Code Marketplace e detalhes da extensão.

## [0.0.2] - 2026-06-03

### Added

- Grammar completo: BGP (IPv4/IPv6 family, peer groups, fake-as, graceful-restart)
- OSPF e OSPFv3 com area, network e interface keywords
- route-policy: if-match / apply com todos os atributos BGP
- ip ip-prefix e ip ipv6-prefix com greater-equal / less-equal
- Rotas estáticas IPv4 e IPv6
- SSH server/client hardening (cipher, hmac, key-exchange, publickey)
- SNMP agent v3
- AAA, interface (dot1q, dual-stack), LoopBack
- BNG / BRAS: radius-server, ip-pool bas, ipv6-pool bas, bas, pppoe-server, domain params, ipv6 prefix, nas
- NE8000 Avançado: ssl policy, mpls, dcn, ccc, virtual-system, license, l2tp-group, cpu-defend, traffic policy
- 37 snippets: BGP, BOGONS RFC5735, route-policy, OSPF, SSH, SNMP, VPN, VRRP, BNG Domain, Radius, Pools, Virtual-Template
- Highlight de IPv4 e IPv6 addresses, undo, permit/deny, return

## [0.0.1] - 2020-11-19

- Release original (base para fork)
