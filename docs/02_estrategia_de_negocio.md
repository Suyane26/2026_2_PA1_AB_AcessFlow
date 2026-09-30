# 📊 Estratégia de Negócio

## 👥 Segmentos de Clientes
O AccessFlow atende 2 segmentos primários, cada um representado por uma persona:

| Segmento | Personas Representativas | Quem são |
| :--- | :--- | :--- |
| **Usuários Finais do Transporte Público** | **Ana** (Estudante)<br>**Carlos** (Trabalhador CLT)<br>**Beatriz** (Usuária Avulsa) | Estudantes, trabalhadores assalariados e passageiros avulsos que utilizam o transporte público e hoje dependem de carteirinha estudantil, vale-transporte ou bilhete único. |
| **Administradores e Gestores** | **Marcos** (Coordenador de Ensino)<br>**Patrícia** (Analista de RH)<br>**Roberto** (Gestor de Operadora)<br>**Fernanda** (Órgão Público) | Profissionais de RH de empresas, secretarias de instituições de ensino, operadoras de transporte e órgãos públicos de mobilidade responsáveis pela gestão, emissão e auditoria dos benefícios de transporte[cite: 1]. |

> **Parceiros (Não clientes):** Operadoras de transporte, órgãos públicos e autoridades de mobilidade (como ETUFOR) atuam como parceiros de integração e validação (sem persona no MVP).
> **Fora do foco inicial:** Usuários ocasionais (créditos avulsos) e vítimas de furto, que entram como público futuro atendido pelas mesmas funções.

---

## 🛠️ Jobs to be Done (JTBD)

### 🎓 Estudantes (Cynthia)
* **Funcional:**
- Acessar áreas privadas da instituição
- Conseguir desconto na hora do pagamento em cinema, eventos ou sites parceiros
- Usar o transporte público no dia a dia
- Comentar/avaliar sua experiência com o transporte público
- Validar o embarque de forma rápida e confiável, mesmo sem internet
- Manter controle do próprio saldo e histórico de uso
  
### 💼 Trabalhadores (Lucas)
* **Funcional:**
- Passar na catraca no pico sem travar fila
- Receber vale no celular no dia do crédito
- Ser avisado do saldo liberado
- Usar QR Code como plano B
- Consultar extrato
- Bloquear saldo contra furto.

### 👩‍💼 Gestores de Benefícios (Ana Maria)
* **Funcional:**
- Emitir e gerenciar credenciais de benefício de transporte em escala, sem processo manual
- Definir e aplicar regras de elegibilidade e valores de benefício por perfil
- Auditar o uso e o custo dos benefícios concedidos, com dados confiáveis
- Reduzir o volume de chamados sobre cartão perdido, saldo ou falha de validação
- Bloquear e reemitir credenciais remotamente, sem deslocamento físico
- Integrar a gestão de benefícios aos sistemas já usados (RH, sistemas acadêmicos)

---

## 🧩 Problem-Solution Fit Canvas

### Causas Raízes e Soluções
| Segmento | Job | Dor (Problema) | Causa Raiz |
| :--- | :--- | :--- | :--- |
| **Estudantes** | Embarcar só com celular | Cartão esquecido/perdido deixa aluno retido. | Acesso depende de objeto físico vulnerável. |
| **Estudantes** | Recarga remota | Filas e deslocamento tiram tempo. | Sistema legado exige gravação física no chip. |
| **Trabalhadores** | Passar sem travar fila | Tarja/chip gasto falha na leitura. | Leitor depende de contato físico, sem QR Code. |
| **Trabalhadores** | Saber crédito | Falta de transparência sobre o depósito. | Crédito da empresa não comunica com app final. |
| **Gestores** | Bloqueio imediato | Usuários desligados mantêm benefícios ativos. | Cadastro preso à operadora, sem controle direto do RH. |
| **Gestores** | Auditar/Conciliar | Conciliação depende de planilhas manuais. | Dados separados da folha e do sistema acadêmico. |

**Solução:** Uma plataforma mobile-first que transforma o celular no cartão de transporte, com validação por NFC e QR Code dinâmico offline, recarga digital (Pix/Cartão) e bloqueio remoto, integrada a um painel web B2B para gestão institucional e auditoria em tempo real.

**Gatilhos para agir:**
* *Estudantes:* Ficar retido na catraca, fila para 2ª via.
* *Trabalhadores:* Atraso por falha de leitura, cartão furtado.
* *Gestores:* Aumento de chamados de reemissão, pressão por redução de custos.

---

## 🏢 Business Model Canvas

* **Segmentos de Clientes:** Estudantes, Trabalhadores, Gestores de Benefícios (Pagantes).
* **Propostas de Valor:** 
  * *Estudantes:* Celular vira carteirinha (NFC/QR offline), recarga Pix, bloqueio instantâneo.
  * *Trabalhadores:* Crédito avisado na hora, embarque expresso, extrato e proteção de saldo.
  * *Gestores:* Painel único de cadastro, regras automatizadas, bloqueio real-time, auditoria e integração nativa. Reduz custo e fraude.
* **Canais:** App Mobile (Android/iOS), Painel Web, Parcerias Institucionais, Notificações Push, Materiais no campus/empresa, B2B Direto.
* **Relacionamento:** Autoatendimento mobile, onboarding guiado B2B, notificações proativas, suporte/chat, transparência de status.
* **Fontes de Renda:** Licenciamento B2B (assinatura por usuário ativo), Comissão de Recarga (Take-rate futuro), Taxa de Integração API, Módulos de Auditoria Avançada.
* **Recursos-chave:** App/Web, Validador NFC(HCE)/QR Dinâmico, Gateway de Pagamento, Integração em Nuvem, Criptografia LGPD.
* **Atividades-chave:** Dev do software, Segurança de tokens, Integrações (RH/Operadoras), Suporte/Onboarding, Monitoramento Antifraude.
* **Parcerias-chave:** Operadoras de Transporte (ex: ETUFOR), Gateways Pix/Cartão, ERPs de Folha/Sistemas Acadêmicos.
* **Estrutura de Custo:** Nuvem/Hospedagem, Dev Team, Taxas Antifraude/Pagamentos, Suporte B2B/B2C, Compliance Legal.

---

## 🎁 Canvas de Proposta de Valor (Resumo de Ganhos)
* **Aliviadores de Dores:** Celular elimina o esquecimento do plástico; recarga sem fila; QR Code como plano B nativo; integração em 1 clique para demissões; bloqueios sem burocracia ou taxa.
* **Criadores de Ganhos:** Confirmação em tempo real (visual/tátil); Alertas preventivos de saldo baixo; Trilha de auditoria antifraude; Relatórios financeiros automáticos; Funcionalidade 100% offline garantida.

---

## 🛤️ Roadmap Estratégico

**Pilares Estratégicos:**
1. Confiabilidade total na validação (NFC, QR, Offline).
2. Um app substitui todos os cartões plásticos.
3. Fim da fila: onboarding, recarga e validação rápidos.
4. Gestão simples e centralizada para as instituições.
5. Validação constante com usuários reais.

### Fase 1: MVP da Credencial Digital (Cartão Virtual e Validação)
* **Duração:** 6 a 8 semanas
* **Foco:** Provar que o celular substitui o cartão físico com segurança (base).
* **Entregas:** Cadastro (foto, ID, benefício), Vínculo assistido, Validação NFC (HCE)/QR dinâmico, Modo offline local, Tela de status em tempo real.
* **Métricas:** Validação em <3s, 90% sucesso na 1ª tentativa, 70% ativação, NPS >= 35.

### Fase 2: Recarga e Segurança (Fidelização)
* **Duração:** 8 a 10 semanas
* **Foco:** Controle de saldo, recargas e segurança do ativo.
* **Entregas:** Recarga Pix/Cartões, Extrato/Histórico, Alerta de saldo baixo, Bloqueio/Reemissão remota, Push Notifications.
* **Métricas:** 50% WAU (ativos semanais), Recarga em <30s, Aprovação pagto >=95%, Retenção D30 >=40%.

### Fase 3: Painel Institucional e Monetização (Escala)
* **Duração:** 10 a 12 semanas
* **Foco:** Escala B2B, Integração e Receita.
* **Entregas:** Painel Web B2B (CRUD de usuários), Regras de recarga automática, Live Dashboard/Auditoria, Integrações API (RH/Sistemas acadêmicos), Faturamento institucional.
* **Métricas:** >=2 instituições ativas, 60% elegíveis cadastrados, 70% mais rápido que processo físico.
