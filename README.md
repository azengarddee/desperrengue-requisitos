# Desperrengue - Requisitos de Software

> **Disciplina:** Requisitos de Software - **Professor:** Luiz Gomes  
> **Grupo 14** - Etapa 1 - Product Backlog Inicial

---

## Integrantes

| Nome | GitHub |
|:--|:--|
| Gabriel de Araujo Bernardes | — |
| Wagner Oliveira Claudiano | — |
| Washington Assis Freitas | [@Washington-Freitas](https://github.com/Washington-Freitas) |

---

## Sobre o Projeto

O **Desperrengue** e um marketplace mobile de servicos residenciais que conecta **clientes** a **prestadores verificados** (eletricistas, encanadores, pedreiros, etc.) com seguranca, transparencia e um modelo de comissionamento justo.

**Problema resolvido:** a assimetria de confianca entre quem precisa de um reparo e quem o executa — identidade nao verificada, precos opacos e pagamentos sem garantia.

**Solucao:** verificacao de identidade (KYC), orcamentos gratuitos (ate 3 propostas), custodia do pagamento liberada por PIN de presenca + evidencias fotograficas, mediacao de disputas e reputacao bidirecional.

**Modelo de negocio:** comissao de 12-15% apenas sobre servico concluido.

---

## Documentacao

| Documento | Descricao |
|:--|:--|
| [Product Backlog](./PRODUCT_BACKLOG.md) | Epicos, historias de usuario, criterios de aceitacao e prioridades |
| [Personas](./PERSONAS.md) | Perfis dos usuarios-alvo do sistema |

---

## Stack Tecnologica

| Camada | Tecnologia |
|:--|:--|
| Frontend Mobile | Flutter (Dart) — Android e iOS |
| Backend (BaaS) | Supabase (PostgreSQL, Auth, Realtime, Storage) |
| Autenticacao | E-mail + OTP, Google OAuth |
| Armazenamento | Supabase Storage (documentos KYC, fotos de pedido) |
| Notificacoes | Supabase Realtime |
| E-mail | Resend (aprovacao de KYC) |
| CEP | ViaCEP / BrasilAPI |

---

## Escopo do MVP

O MVP academico cobre o **ciclo completo do servico**:

```
Cadastro -> KYC -> Pedido -> Orcamento -> Aceite -> Pagamento (simulado) -> Execucao -> PIN -> Avaliacao
```

> O fluxo financeiro e **simulado** (sem gateway de pagamento real). A aprovacao do KYC pode estar em modo automatico (mock) para fins academicos.
