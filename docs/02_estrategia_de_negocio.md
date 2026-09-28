# 📊 Estratégia de Negócio

## 👥 Segmentos de Clientes
O AccessFlow atende 3 segmentos primários, cada um representado por uma persona:

| Segmento | Persona | Quem são |
| :--- | :--- | :--- |
| **Estudantes (Carteirinha)** | Cynthia | Estudantes do ensino médio, técnico e superior que usam transporte com desconto. |
| **Trabalhadores (Vale-transporte)** | Lucas | Empregados CLT que recebem o benefício da empresa para o trajeto casa-trabalho. |
| **Gestores de Benefícios** | Ana Maria | RH de empresas, secretarias/coordenações de escolas e faculdades que emitem e gerenciam benefícios. |

> **Parceiros (Não clientes):** Operadoras de transporte, órgãos públicos e autoridades de mobilidade (como ETUFOR) atuam como parceiros de integração e validação (sem persona no MVP).
> **Fora do foco inicial:** Usuários ocasionais (créditos avulsos) e vítimas de furto, que entram como público futuro atendido pelas mesmas funções.

---

## 🛠️ Jobs to be Done (JTBD)

### 🎓 Estudantes (Cynthia)
* **Funcional:** Embarcar usando só o celular; ver saldo antes de sair; recarregar por Pix; bloquear benefício na hora em caso de perda; consultar histórico; validar embarque sem sinal de internet.
* **Emocional:** Sentir segurança de não ficar retida na catraca; alívio por não depender de fila/2ª via; tranquilidade por saber o saldo; confiança na autonomia; praticidade; menos ansiedade.
* **Social:** Ser vista como organizada e digital; não atrasar a fila; ser reconhecida como usuária legítima (foto oficial); parecer atualizada em tecnologia.

### 💼 Trabalhadores (Lucas)
* **Funcional:** Passar na catraca no pico sem travar fila; receber vale no celular no dia do crédito; ser avisado do saldo liberado; usar QR Code como plano B; consultar extrato; bloquear saldo contra furto.
* **Emocional:** Segurança de chegar no horário; alívio contra falhas de plástico; confiança com tela de confirmação; tranquilidade com aviso de crédito; menos irritação; proteção contra perdas.
* **Social:** Ser visto como pontual/responsável; prático; evitar constrangimento na catraca; parceiro em dia com RH; indicar inovação aos colegas.

### 👩‍💼 Gestores de Benefícios (Ana Maria)
* **Funcional:** Cadastrar/vincular usuários; definir regras/valores de recarga; bloquear/desbloquear com efeito imediato; monitorar dashboards; emitir relatórios de auditoria; integrar com folha/sistema acadêmico.
* **Emocional:** Controle sobre benefícios; alívio com menos chamados; segurança ao prestar contas; confiança contra fraudes; menos estresse com planilhas; tranquilidade com base unificada.
* **Social:** Gestora organizada/transparente; reconhecida por reduzir custos; vista como inovadora; confiável perante operadoras; referência interna ágil.

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

**Gatilhos para agir:**
* *Estudantes:* Ficar retido na catraca, fila para 2ª via, perda do celular.
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