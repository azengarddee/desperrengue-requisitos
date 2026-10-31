# Product Backlog - Desperrengue

> **Projeto:** Desperrengue - Marketplace de Servicos Residenciais  
> **Disciplina:** Requisitos de Software - **Professor:** Luiz Gomes  
> **Grupo 14** - Versao 1.0 - Outubro/2026

---

## Sumario

1. [Visao Geral](#1-visao-geral)
2. [Personas](#2-personas)
3. [Epicos](#3-epicos)
4. [Product Backlog](#4-product-backlog)
5. [Definition of Ready (DoR)](#5-definition-of-ready-dor)
6. [Definition of Done (DoD)](#6-definition-of-done-dod)
7. [Resumo de Prioridades](#7-resumo-de-prioridades)

---

## 1. Visao Geral

### Declaracao do Problema

| | |
|:--|:--|
| **O problema de** | desconfianca e falta de transparencia na contratacao de servicos residenciais |
| **Afeta** | clientes que precisam de reparos e profissionais autonomos que buscam trabalho |
| **Cujo impacto e** | cobrancas indevidas por orcamento, calotes, profissionais nao qualificados e pagamentos sem garantia |
| **Uma boa solucao seria** | uma plataforma que verifique identidade e qualificacao dos profissionais, garanta o pagamento em custodia e permita avaliacao bidirecional |

### Declaracao do Produto

> Para **clientes** que precisam de servicos residenciais confiaveis e para **profissionais autonomos** que buscam clientes qualificados, o **Desperrengue** e um marketplace mobile que oferece verificacao de identidade (KYC), orcamentos gratuitos, custodia de pagamento liberada por PIN de presenca e reputacao bidirecional — diferente de grupos de WhatsApp e anuncios informais, o Desperrengue garante seguranca para ambos os lados da transacao.

---

## 2. Personas

| ID | Persona | Papel | Descricao resumida |
|:--|:--|:--|:--|
| P1 | Ana Lima | Cliente | 34 anos, analista de RH, contrata servicos residenciais e exige confianca e garantia de pagamento |
| P2 | Roberto Mendes | Profissional | 42 anos, eletricista com CREA, busca clientes e quer garantia de recebimento |
| P3 | Carlos Souza | Dual (cliente + profissional) | 28 anos, pintor que tambem precisa contratar outros servicos |

> Detalhamento completo em [PERSONAS.md](./PERSONAS.md).

---

## 3. Epicos

Os epicos organizam as historias de usuario em grandes blocos funcionais do sistema.

| ID | Epico | Descricao |
|:--|:--|:--|
| EP01 | Autenticacao e Cadastro | Registro, login, verificacao de identidade e recuperacao de acesso |
| EP02 | Verificacao de Identidade (KYC) | Upload de documentos, selfie, registro profissional e aprovacao |
| EP03 | Multi-modo | Uma conta que atua como cliente e/ou profissional |
| EP04 | Perfil e Configuracoes | Dados pessoais, preferencias, tema, privacidade e exclusao de conta |
| EP05 | Busca e Descoberta | Pesquisa, listagem e visualizacao de profissionais |
| EP06 | Ciclo do Servico | Pedido -> Convite -> Orcamento -> Aceite -> Execucao -> Conclusao |
| EP07 | Pagamento e Carteira | Carteira digital, recarga Pix, custodia, saque e extrato |
| EP08 | Avaliacao e Reputacao | Avaliacao bidirecional cega, ranking Bayesiano e selos |
| EP09 | Gamificacao e Conquistas | Sistema de conquistas escalonadas por desempenho do profissional |
| EP10 | Chat e Notificacoes | Mensagens em tempo real e central de notificacoes |
| EP11 | Suporte e Disputas | Abertura de tickets, mediacao e resolucao de conflitos |
| EP12 | Vitrine Profissional | Portfolio automatico LIFO e cases de sucesso fixados |

---

## 4. Product Backlog

### Legenda de Prioridade (MoSCoW)

| Simbolo | Prioridade | Significado |
|:--:|:--|:--|
| [MUST] | **Must Have** | Essencial para o MVP — sem isso o sistema nao funciona |
| [SHOULD] | **Should Have** | Importante, mas nao bloqueia o lancamento |
| [COULD] | **Could Have** | Desejavel se houver tempo e recursos |
| [WONT] | **Won't Have** | Fora do escopo atual; planejado para versoes futuras |

### Legenda de Story Points (Fibonacci)

| SP | Tamanho | Descricao |
|:--|:--|:--|
| 1-2 | Muito pequeno | Tarefa simples, poucas dependencias |
| 3-5 | Medio | Logica moderada, alguma integracao |
| 8-13 | Grande | Alta complexidade, multiplas camadas |
| 21 | Muito grande | Deve ser quebrado em historias menores |

---

### EP01 — Autenticacao e Cadastro

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US01 | Como **novo usuario**, quero me **cadastrar com e-mail e senha** para criar minha conta no Desperrengue. | - Formulario com nome completo, e-mail e senha (min. 8 caracteres) / - Validacao de e-mail em formato correto / - Senha com confirmacao / - Erro claro em caso de e-mail ja cadastrado | [MUST] | 3 |
| US02 | Como **novo usuario**, quero **verificar minha identidade por codigo OTP** enviado ao meu e-mail para confirmar o cadastro. | - OTP de 6 digitos enviado ao e-mail / - Validade de 10 minutos / - Botao "Reenviar codigo" disponivel apos 60s / - Erro claro em caso de codigo invalido ou expirado | [MUST] | 3 |
| US03 | Como **usuario**, quero **fazer login com Google** para acessar o app de forma mais rapida. | - Botao "Entrar com Google" na tela de login / - Autenticacao OAuth 2.0 funcional / - Conta criada automaticamente no primeiro acesso / - Redirecionamento correto apos autenticacao | [MUST] | 5 |
| US04 | Como **usuario**, quero **recuperar minha senha** para retomar o acesso caso a esqueca. | - Campo "Esqueci minha senha" na tela de login / - E-mail de redefinicao enviado em ate 1 min / - Link com validade de 60 minutos / - Nova senha aceita no proximo login | [SHOULD] | 3 |
| US05 | Como **usuario**, quero **permanecer logado** entre sessoes para nao precisar autenticar toda vez que abro o app. | - Sessao armazenada de forma segura (Keystore/Keychain) / - App abre offline com perfil em cache / - Sessao encerrada ao fazer logout explicito / - Fallback para login se sessao corrompida | [MUST] | 5 |

---

### EP02 — Verificacao de Identidade (KYC)

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US06 | Como **profissional**, quero **enviar a frente do meu documento de identidade** para iniciar a verificacao da minha conta. | - Captura por camera ou galeria / - Documento legivel (orientacao e iluminacao validadas na UI) / - Armazenado em bucket privado, acessivel apenas por URL assinada / - Progresso salvo em rascunho | [MUST] | 5 |
| US07 | Como **profissional**, quero **enviar o verso do meu documento de identidade** para complementar a verificacao. | - Mesmas condicoes do US06 / - Fluxo sequencial: frente -> verso -> selfie | [MUST] | 3 |
| US08 | Como **profissional**, quero **tirar uma selfie** para confirmar que sou a mesma pessoa do documento. | - Camera frontal ativada automaticamente / - Foto capturada e armazenada de forma privada / - Instrucoes claras na tela | [MUST] | 3 |
| US09 | Como **profissional**, quero **informar meu registro profissional** (CREA, CFT ou CNPJ) para comprovar minha qualificacao. | - Campo de texto com tipo de registro selecionavel / - Armazenado associado ao perfil / - Exibido no perfil publico apos aprovacao | [MUST] | 3 |
| US10 | Como **profissional**, quero **aceitar os termos de prestacao de servicos** antes de finalizar o envio do KYC. | - Tela com os termos completos / - Botao "Aceitar e enviar" somente apos leitura (scroll ate o fim) / - Aceite registrado com timestamp | [MUST] | 2 |
| US11 | Como **profissional**, quero **acompanhar o status da minha verificacao** para saber se fui aprovado. | - Status visivel no perfil: Nao enviado / Em analise / Aprovado / Reprovado / - Notificacao ao mudar de status / - Motivo de reprovacao exibido com opcao de reenvio | [MUST] | 3 |
| US12 | Como **profissional**, quero **receber um e-mail de aprovacao** com link para ativar minha conta profissional. | - E-mail enviado automaticamente apos aprovacao / - Link abre o app e ativa o perfil profissional / - E-mail com design profissional e remetente verificado | [MUST] | 5 |

---

### EP03 — Multi-modo

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US13 | Como **usuario**, quero **escolher como desejo usar o app** (como cliente ou como profissional) para acessar a area correta. | - Tela de selecao de modo com cartoes visuais / - Exibicao do status de cada perfil (criar, completar cadastro, em analise, ativo) / - Tema visual muda conforme o modo selecionado | [MUST] | 5 |
| US14 | Como **usuario**, quero **alternar entre os modos** sem precisar sair da conta para usar o app de diferentes formas. | - Botao "Trocar de modo" acessivel no perfil / - Troca sem necessidade de novo login / - Ultimo modo usado e lembrado na proxima sessao | [MUST] | 3 |
| US15 | Como **usuario dual**, quero **nao conseguir contratar a mim mesmo** como profissional para evitar conflito de interesses. | - Meu proprio perfil aparece na busca com etiqueta "Voce" e aviso "Visao do cliente" / - Sistema impede a criacao de pedido para si mesmo (UI e banco) | [MUST] | 3 |

---

### EP04 — Perfil e Configuracoes

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US16 | Como **cliente**, quero **configurar meu perfil** com nome, telefone e endereco para que o app saiba onde preciso do servico. | - Formulario com nome, telefone e endereco / - Preenchimento automatico por CEP (ViaCEP) / - Opcao "Usar minha localizacao atual" (GPS + Nominatim) / - Dados salvos com rascunho automatico | [MUST] | 5 |
| US17 | Como **profissional**, quero **editar meu perfil** (foto, titulo, bio, especialidades, taxa de visita, valor/hora e raio de atendimento) para atrair mais clientes. | - Upload de foto de perfil / - Campos de bio, especialidades (multi-selecao) e valores / - Raio de atendimento em km / - Alteracoes refletidas imediatamente no perfil publico | [SHOULD] | 5 |
| US18 | Como **usuario**, quero **escolher o tema visual do app** (claro, escuro ou automatico) para melhorar minha experiencia. | - Seletor de tema em Perfil -> Aparencia / - Tema automatico segue o sistema operacional / - Preferencia persiste entre sessoes | [SHOULD] | 3 |
| US19 | Como **usuario**, quero **ativar o modo privacidade** para ocultar valores financeiros na tela. | - Icone de olho no painel e na carteira / - Valores exibidos como "R$ *****" / - Preferencia lembrada entre sessoes | [COULD] | 2 |
| US20 | Como **usuario**, quero **excluir minha conta** com garantia de apagamento dos meus dados pessoais (LGPD). | - Confirmacao por digitacao da palavra "EXCLUIR" / - Bloqueio se houver saldo positivo ou servico em andamento / - Dossie PDF com historico enviado por e-mail antes da exclusao / - Dados e arquivos removidos apos envio do dossie | [SHOULD] | 13 |

---

### EP05 — Busca e Descoberta

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US21 | Como **cliente**, quero **buscar profissionais por categoria de servico** para encontrar quem faz o que preciso. | - Lista de categorias na home (eletricista, encanador, pedreiro, etc.) / - Busca textual por especialidade / - Resultados filtrados por profissionais com status ATIVO | [MUST] | 5 |
| US22 | Como **cliente**, quero **ordenar os profissionais** por nota, proximidade ou taxa de visita para escolher o mais adequado. | - Opcoes de ordenacao: Melhor avaliados (rank Bayesiano), Mais proximos, Menor taxa de visita / - Ordenacao aplicada em tempo real | [SHOULD] | 3 |
| US23 | Como **cliente**, quero **ver o perfil completo de um profissional** (bio, especialidades, avaliacoes, portfolio e conquistas) para tomar uma decisao informada. | - Foto, nome, titulo e bio visiveis / - Nota media e numero de avaliacoes / - Ultimas avaliacoes publicas com direito de resposta / - Portfolio de trabalhos e conquistas desbloqueadas | [MUST] | 5 |

---

### EP06 — Ciclo do Servico

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US24 | Como **cliente**, quero **criar um pedido de servico** com descricao e fotos para que os profissionais entendam o que preciso. | - Assistente em 3 passos: (1) descricao + fotos, (2) quando, (3) revisao / - Ate 4 fotos anexadas / - Rascunho salvo automaticamente / - Endereco completo associado ao pedido | [MUST] | 8 |
| US25 | Como **cliente**, quero **escolher entre servico agendado e emergencia** para atender urgencias ou planejar com antecedencia. | - Modalidade "Agendado": selecao de data e horario no calendario / - Modalidade "Emergencia": ativacao imediata com radar de 5 minutos / - Interface diferenciada para cada modalidade | [MUST] | 8 |
| US26 | Como **cliente**, quero **convidar profissionais especificos ou abrir para multiplos orcamentos** para ter flexibilidade na contratacao. | - Pedido direto: convite para 1 profissional com prazo de 2h / - Pedido aberto: ate 3 profissionais recebem convites / - Cliente pode adicionar outros profissionais (ate o limite de 3 orcamentos) | [MUST] | 8 |
| US27 | Como **profissional**, quero **receber notificacao de novos convites ou pedidos** na minha area de atuacao para nao perder oportunidades. | - Notificacao em tempo real (Realtime) / - Painel "Oportunidades" com convites diretos e pedidos abertos por especialidade / - Prazo do convite visivel com contagem regressiva | [MUST] | 5 |
| US28 | Como **profissional**, quero **enviar um orcamento** com o preco e visualizar a comissao de 12% para saber quanto vou receber. | - Campo de valor com mascara BRL / - Comissao calculada ao vivo: "Voce recebera R$ X" / - Limite de 1 orcamento por profissional por pedido / - Opcao de retirar a proposta antes do aceite | [MUST] | 5 |
| US29 | Como **cliente**, quero **comparar e aceitar um orcamento** para contratar o profissional escolhido. | - Lista de orcamentos com valor, nome e nota do profissional / - Aceite atomico (rejeita os demais automaticamente) / - Confirmacao antes de prosseguir para o pagamento | [MUST] | 5 |
| US30 | Como **profissional**, quero **aceitar ou recusar uma emergencia em ate 5 minutos** para que o cliente encontre alguem rapidamente. | - Notificacao com contagem regressiva de 5 minutos / - Aceite leva imediatamente ao estado "em andamento" / - Recusa ou expiracao cancela a reserva e estorna o pagamento | [MUST] | 8 |
| US31 | Como **cliente**, quero **acompanhar o status do meu pedido em tempo real** para saber em que etapa esta o servico. | - Linha do tempo: aguardando orcamento -> aceite -> pagamento -> em andamento -> concluido / - Atualizacoes em tempo real via Realtime / - Tela atualiza automaticamente conforme o estado muda | [MUST] | 8 |
| US32 | Como **profissional**, quero **registrar 4 evidencias fotograficas** ao finalizar o servico para comprovar a execucao. | - Camera ou galeria para captura / - Exatamente 4 fotos obrigatorias / - Armazenadas em bucket privado, acessivel ao cliente e profissional | [MUST] | 5 |
| US33 | Como **profissional**, quero **inserir o PIN de presenca** informado pelo cliente para liberar o pagamento apos o servico. | - Teclado numerico dedicado / - Limite de 5 tentativas (persistido mesmo apos erro de transacao) / - PIN valido: pagamento liberado, servico concluido / - PIN invalido: mensagem de erro com tentativas restantes | [MUST] | 8 |

---

### EP07 — Pagamento e Carteira

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US34 | Como **cliente**, quero **visualizar o saldo da minha carteira** para saber quanto tenho disponivel para pagar servicos. | - Saldo disponivel e valor em custodia exibidos / - Atualizacao em tempo real (Realtime) / - Chip de saldo no cabecalho da home do cliente | [MUST] | 3 |
| US35 | Como **cliente**, quero **recarregar minha carteira via Pix** para ter saldo disponivel para pagar servicos. | - Mascara BRL com atalhos (+50, +100, +200, +500) / - QR Code + codigo copia-e-cola gerados / - Confirmacao automatica via webhook / - Botao "Simular pagamento Pix" disponivel em sandbox | [MUST] | 13 |
| US36 | Como **cliente**, quero **pagar o servico com o saldo da minha carteira** para que o valor fique em custodia ate a conclusao. | - Pagamento debita o saldo disponivel imediatamente / - Valor fica em custodia (nao acessivel ao profissional) ate o PIN / - Erro "Saldo insuficiente" com valor faltante e CTA para recarga | [MUST] | 8 |
| US37 | Como **cliente**, quero **ver meu extrato de transacoes** para acompanhar entradas, saidas e valores em custodia. | - Lista de lancamentos com data, tipo (recarga, pagamento, estorno) e valor / - Icones semanticos por tipo de transacao / - Atualizacao em tempo real | [SHOULD] | 5 |
| US38 | Como **profissional**, quero **solicitar saque via Pix** para receber o valor liquido dos servicos concluidos. | - Formulario com chave Pix (CPF/CNPJ/e-mail/celular/aleatoria) / - Declaracao de titularidade obrigatoria / - Chave guardada mascarada apos cadastro / - Saldo calculado no servidor | [SHOULD] | 8 |

---

### EP08 — Avaliacao e Reputacao

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US39 | Como **cliente**, quero **avaliar o profissional apos o servico** para contribuir com a reputacao da plataforma. | - Nota de 1 a 5 estrelas / - Pilulas de contexto dinamicas (1-3 estrelas: "O que deu errado?"; 4-5 estrelas: "O que mais te impressionou?") / - Campo de comentario opcional / - Gorjeta simulada opcional | [MUST] | 5 |
| US40 | Como **profissional**, quero **avaliar o cliente apos o servico** para construir reputacao bidirecional na plataforma. | - Nota e comentario sobre o cliente / - 5 criterios de avaliacao / - Reputacao do cliente visivel aos profissionais envolvidos | [MUST] | 5 |
| US41 | Como **usuario**, quero que **as avaliacoes sejam cegas** ate que ambas as partes avaliem para evitar influencia mutua. | - Avaliacao revelada quando as 2 partes concluem OU apos 48 horas / - Nenhuma das partes ve a nota da outra antes da revelacao / - Notificacao ao ser revelada | [SHOULD] | 8 |
| US42 | Como **profissional**, quero **responder publicamente a uma avaliacao** para dar minha versao dos fatos. | - Direito de resposta (uma vez por avaliacao) / - Resposta exibida abaixo do comentario do cliente no perfil publico | [COULD] | 3 |
| US43 | Como **cliente**, quero **ver o ranking dos profissionais** por uma nota confiavel para evitar manipulacao de avaliacoes. | - Ordenacao por Media Bayesiana / - Peso de recencia nas notas / - Selos automaticos (Mestre da Organizacao, Sempre Pontual, Super Profissional) | [SHOULD] | 8 |

---

### EP09 — Gamificacao e Conquistas

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US44 | Como **profissional**, quero **acumular conquistas** baseadas no meu desempenho para me destacar na plataforma. | - 9 categorias x 10 niveis = 90 conquistas / - Categorias: servicos concluidos, avaliacoes 5 estrelas, pontualidade, organizacao, preco justo, qualidade, cortesia, emergencias e clientes recorrentes / - Limites: 1, 10, 25, 50, 100, 500, 1.000, 2.500, 5.000 e 10.000 / - Metais: Bronze, Prata, Ouro, Platina e Diamante | [SHOULD] | 13 |
| US45 | Como **profissional**, quero **ver meu progresso em cada categoria de conquistas** para saber quanto falta para o proximo nivel. | - Tela "Minhas conquistas" com barra de progresso por categoria / - Medalhas das conquistas ja desbloqueadas em destaque | [SHOULD] | 5 |
| US46 | Como **cliente**, quero **ver as conquistas do profissional no perfil publico** para ter mais confianca antes de contratar. | - Secao "Conquistas" no perfil publico / - Exibe conquistas mais relevantes com medalha e nome | [COULD] | 3 |
| US47 | Como **profissional**, quero **receber uma notificacao de conquista desbloqueada** ao finalizar um servico para me sentir reconhecido. | - Card "Conquista desbloqueada!" exibido na conclusao do servico / - Notificacao registrada na central / - Desbloqueio idempotente (nao duplica por reprocessamento) | [COULD] | 3 |

---

### EP10 — Chat e Notificacoes

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US48 | Como **usuario**, quero **conversar com a outra parte via chat dentro do pedido** para combinar detalhes do servico. | - Chat em tempo real (Realtime) por demanda / - Mensagens persistidas no banco / - Historico acessivel durante e apos o servico | [MUST] | 8 |
| US49 | Como **usuario**, quero **compartilhar minha localizacao pelo chat** para facilitar o encontro do profissional. | - Botao de compartilhamento de localizacao no chat / - Localizacao exibida como mapa estatico clicavel | [COULD] | 5 |
| US50 | Como **usuario**, quero **receber notificacoes em tempo real** sobre atualizacoes do meu pedido para nao perder nada importante. | - Central de notificacoes com contador de nao lidas / - Tipos: novo orcamento, aceite, pagamento, PIN validado, avaliacao revelada, conquista / - Atualizacao em tempo real via Realtime | [MUST] | 8 |

---

### EP11 — Suporte e Disputas

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US51 | Como **cliente**, quero **relatar um problema com o servico prestado** para acionar a mediacao da plataforma. | - Tela de triagem com selecao do motivo / - Upload de evidencias (fotos) / - Revisao dos anexos antes do envio / - Confirmacao com numero de protocolo e SLA de 24h | [MUST] | 8 |
| US52 | Como **usuario**, quero **acompanhar o status do meu chamado de suporte** para saber se o problema esta sendo resolvido. | - Status do ticket visivel no pedido / - Notificacao ao haver atualizacao / - Resolucao com liberacao ou estorno do pagamento | [SHOULD] | 5 |

---

### EP12 — Vitrine Profissional

| ID | Historia de Usuario | Criterios de Aceitacao | Prioridade | SP |
|:--|:--|:--|:--:|:--:|
| US53 | Como **profissional**, quero que **meus melhores trabalhos aparecam automaticamente na minha vitrine** para atrair clientes sem esforco. | - Os 4 ultimos servicos concluidos com avaliacao >= 4 estrelas sao exibidos automaticamente (LIFO) / - 5o servico vai para o historico / - Vitrine visivel no perfil publico | [COULD] | 5 |
| US54 | Como **profissional**, quero **fixar ate 3 cases de sucesso** no meu perfil para destacar meus melhores trabalhos. | - Apenas servicos com nota 5 estrelas podem ser fixados / - Tela "Gerenciar vitrine" com opcao de fixar/desfixar / - Cases fixados aparecem antes dos automaticos | [COULD] | 5 |
| US55 | Como **profissional**, quero **adicionar um video, relatorio tecnico e fotos** a um case de sucesso para apresentar meu trabalho com riqueza de detalhes. | - Video opcional (ate 25 MB, mp4/quicktime) / - Galeria de 4 fotos / - Campo de relatorio tecnico escrito / - Avaliacao do cliente e resposta vinculadas | [COULD] | 8 |

---

## 5. Definition of Ready (DoR)

Uma historia de usuario esta **pronta para ser desenvolvida** quando:

- [ ] Esta escrita no formato: "Como [persona], quero [acao] para [valor/beneficio]"
- [ ] Tem criterios de aceitacao claros e testaveis
- [ ] Tem prioridade definida (MoSCoW)
- [ ] Tem story points estimados pela equipe
- [ ] Nao tem dependencias bloqueantes nao resolvidas
- [ ] A equipe compreende o que precisa ser feito

---

## 6. Definition of Done (DoD)

Uma historia de usuario esta **concluida** quando:

- [ ] Codigo implementado e revisado
- [ ] Criterios de aceitacao verificados manualmente
- [ ] Testes unitarios escritos (para logica de negocio)
- [ ] Sem erros em flutter analyze
- [ ] Integracao com o banco de dados testada
- [ ] Funcionalidade validada no dispositivo (Android fisico ou emulador)
- [ ] Sem regressao nas funcionalidades existentes
- [ ] Documentacao atualizada (se aplicavel)

---

## 7. Resumo de Prioridades

| Prioridade | Qtd. de Historias | Story Points Totais |
|:--|:--:|:--:|
| [MUST] Must Have | 30 | 157 |
| [SHOULD] Should Have | 12 | 63 |
| [COULD] Could Have | 10 | 42 |
| [WONT] Won't Have | 0 | — |
| **Total** | **52** | **262** |

### Distribuicao por Epico

| Epico | Must | Should | Could | Total SP |
|:--|:--:|:--:|:--:|:--:|
| EP01 — Autenticacao e Cadastro | 4 | 1 | 0 | 19 |
| EP02 — Verificacao KYC | 7 | 0 | 0 | 24 |
| EP03 — Multi-modo | 3 | 0 | 0 | 11 |
| EP04 — Perfil e Configuracoes | 2 | 2 | 1 | 26 |
| EP05 — Busca e Descoberta | 2 | 1 | 0 | 13 |
| EP06 — Ciclo do Servico | 10 | 0 | 0 | 68 |
| EP07 — Pagamento e Carteira | 3 | 2 | 0 | 37 |
| EP08 — Avaliacao e Reputacao | 2 | 2 | 1 | 29 |
| EP09 — Gamificacao | 0 | 2 | 2 | 24 |
| EP10 — Chat e Notificacoes | 2 | 0 | 1 | 21 |
| EP11 — Suporte e Disputas | 1 | 1 | 0 | 13 |
| EP12 — Vitrine Profissional | 0 | 0 | 3 | 18 |
