# 📊 Estratégia de Negócio

## 👥 Segmentos de Clientes
O AccessFlow atende 2 segmentos primários, cada um representado por uma persona:

| Segmento | Personas Representativas | Quem são |
| :--- | :--- | :--- |
| **Usuários Finais do Transporte Público** | **Cynthia** (Estudante)<br>**Lucas** (Trabalhador CLT)<br>**Beatriz** (Usuária Avulsa) | Estudantes, trabalhadores assalariados e passageiros avulsos que utilizam o transporte público e hoje dependem de carteirinha estudantil, vale-transporte ou bilhete único. |
| **Administradores e Gestores** | **Marcos** (Coordenador de Ensino)<br>**Ana** (Analista de RH)<br>**Roberto** (Gestor de Operadora)<br>**Fernanda** (Órgão Público) | Profissionais de RH de empresas, secretarias de instituições de ensino, operadoras de transporte e órgãos públicos de mobilidade responsáveis pela gestão, emissão e auditoria dos benefícios de transporte[cite: 1]. |

> **Parceiros (Não clientes):** Operadoras de transporte, órgãos públicos e autoridades de mobilidade (como ETUFOR) atuam como parceiros de integração e validação (sem persona no MVP).
> **Fora do foco inicial:** Usuários ocasionais (créditos avulsos) e vítimas de furto, que entram como público futuro atendido pelas mesmas funções.

---

## 🛠️ Jobs to be Done (JTBD)

### Usuários Finais do Transporte Público:

#### 1. Estudantes (Cynthia)
* **Funcional:**
- Acessar áreas privadas da instituição[cite: 1]
- Conseguir desconto na hora do pagamento em cinema, eventos ou sites parceiros[cite: 1]
- Usar o transporte público no dia a dia[cite: 1]
- Comentar/avaliar sua experiência com o transporte público[cite: 1]
- Validar o embarque de forma rápida e confiável, mesmo sem internet[cite: 1]
- Manter controle do próprio saldo e histórico de uso[cite: 1]

#### 2. Trabalhadores (Lucas)
* **Funcional:**
- Utilizar o benefício de vale-transporte para deslocamento casa-trabalho[cite: 1]
- Validar o embarque de forma garantida em horários de pico, mesmo offline[cite: 1]
- Acompanhar o crédito mensal disponibilizado pela empresa[cite: 1]
- Notificar e bloquear remotamente a credencial em caso de perda do aparelho[cite: 1]
- Comentar/avaliar a experiência com o transporte público[cite: 1]
- Manter controle do histórico de uso e saldo restante[cite: 1]

#### 3. Usuários Avulsos (Beatriz)
* **Funcional:**
- Usar o transporte público de forma esporádica sem depender de vínculo institucional[cite: 1]
- Validar o embarque por QR Code Dinâmico, sem depender de tecnologia NFC no celular[cite: 1]
- Realizar recargas avulsas e instantâneas via Pix, cartão de débito ou crédito[cite: 1]
- Manter controle em tempo real do próprio saldo de passagens e histórico de viagens[cite: 1]
- Comentar/avaliar a experiência com o transporte público no dia a dia[cite: 1]
- Garantir o bloqueio remoto do saldo e a recuperação da credencial em caso de perda do aparelho[cite: 1]

---

### Administradores e Gestores:

#### 1. Coordenadores e Secretarias Acadêmicas (Marcos)
* **Funcional:**
- Emitir e gerenciar credenciais de benefício estudantil em escala, sem processos manuais[cite: 1]
- Importar listas de alunos elegíveis em lote por meio de planilhas (CSV/XLSX)[cite: 1]
- Bloquear e encerrar credenciais de alunos evadidos ou com curso trancado em tempo real[cite: 1]
- Exportar relatórios detalhados de uso e emissões para auditoria da diretoria[cite: 1]

#### 2. Analistas e Gestores de RH (Ana)
* **Funcional:**
- Configurar e automatizar a liberação do crédito mensal de vale-transporte por cargo ou grupo[cite: 1]
- Integrar a gestão de benefícios de transporte diretamente ao sistema de RH da empresa[cite: 1]
- Reduzir o volume de chamados de suporte sobre perda, saldo ou reemissão de cartões físicos[cite: 1]
- Fechar e exportar demonstrativos mensais de custos de transporte para o setor financeiro[cite: 1]

#### 3. Gestores de Operadoras de Transporte (Roberto)
* **Funcional:**
- Monitorar o volume e a taxa de sucesso das validações de embarque em tempo real por linha de ônibus[cite: 1]
- Consultar e exportar o extrato financeiro de comissão gerado pelas recargas da frota[cite: 1]
- Configurar regras de tarifa e validação alinhadas aos contratos de concessão[cite: 1]
- Garantir fluidez no embarque e reduzir problemas na catraca enfrentados pelos motoristas[cite: 1]

#### 4. Representantes de Órgãos Públicos e Reguladores (Fernanda)
* **Funcional:**
- Auditar logs de segurança, padrão de uso e tentativas de fraude no sistema de bilhetagem[cite: 1]
- Acessar relatórios agregados de validação e recarga de todas as operadoras ativas na cidade[cite: 1]
- Fiscalizar a conformidade regulatória e a segurança da criptografia dos tokens de embarque[cite: 1]
- Emitir pareceres e relatórios técnicos embasados em dados consolidados de mobilidade[cite: 1]
  
---

## 🧩 Problem-Solution Fit Canvas

### Causas Raízes e Soluções
| Segmento | Job | Dor (Problema) | Causa Raiz |
| :--- | :--- | :--- | :--- |
| **Usuários Finais** *(Estudantes)* | Embarcar só com celular | Cartão esquecido/perdido deixa o aluno retido na catraca. | Acesso depende exclusivamente de objeto físico em PVC/papel vulnerável[cite: 1, 4]. |
| **Usuários Finais** *(Estudantes)* | Recarga remota | Filas e deslocamento até pontos presenciais tiram tempo. | Sistema legado exige gravação física do saldo no chip do cartão[cite: 1, 4]. |
| **Usuários Finais** *(Trabalhadores)* | Passar sem travar a fila | Tarja/chip gasto falha na leitura ou app trava sem sinal. | Leitores exigem contato físico e validação dependente de internet[cite: 1, 4]. |
| **Usuários Finais** *(Trabalhadores)* | Saber o crédito | Falta de transparência sobre o depósito do vale-transporte. | Sistema de crédito da empresa não se comunica com o app do usuário em tempo real[cite: 1, 4]. |
| **Usuários Finais** *(Avulsos)* | Embarque sem burocracia | Exclusão de usuários sem cartão de benefício ou celular sem NFC. | Ausência de leitura óptica por QR Code e de alternativa digital imediata[cite: 1]. |
| **Administradores e Gestores** | Bloqueio e emissão | Usuários desligados/evadidos mantêm benefícios ativos; alto volume de chamados de 2ª via[cite: 1, 4]. | Cadastro engessado nas operadoras, sem controle direto e instantâneo do RH/Secretaria[cite: 1, 4]. |
| **Administradores e Gestores** | Auditar/Conciliar | Conciliação e prestação de contas dependem de planilhas manuais[cite: 1, 4]. | Dados fragmentados e separados do sistema de RH, acadêmico e órgãos reguladores[cite: 1, 4]. |

**Solução:** Uma plataforma mobile-first que transforma o celular no cartão de transporte, com validação por NFC e QR Code dinâmico offline, recarga digital (Pix/Cartão) e bloqueio remoto, integrada a um painel web B2B para gestão institucional e auditoria em tempo real[cite: 1, 4].

**Gatilhos para agir:**
* *Usuários Finais (Estudantes):* Ficar retido na catraca, filas demoradas para emissão de 2ª via[cite: 1, 4].
* *Usuários Finais (Trabalhadores):* Atraso por falha de leitura do cartão físico no ônibus, cartão roubado/furtado[cite: 1, 4].
* *Usuários Finais (Avulsos):* Necessidade de embarque imediato sem possuir cartão físico ou aparelho com NFC[cite: 1].
* *Administradores e Gestores:* Aumento exponencial no volume de chamados por perda de cartão, suspeitas de fraude na concessão e pressão da diretoria por redução de custos operacionais[cite: 1, 4].
  
---

## 🏢 Business Model Canvas

* **Segmentos de Clientes:** Usuários Finais do Transporte Público (Estudantes, Trabalhadores CLT e Usuários Avulsos) e Administradores e Gestores (RHs de Empresas, Secretarias de Ensino, Operadoras de Transporte e Órgãos Públicos)[cite: 1, 5].
* **Propostas de Valor:**
  * *Usuários Finais:* O celular vira a credencial de transporte (NFC e QR Code dinâmico offline), recarga instantânea por Pix/Cartão, alertas de saldo/crédito na hora, extrato de viagens e proteção com bloqueio remoto de saldo[cite: 1, 5].
  * *Administradores e Gestores:* Painel único de cadastro e importação em lote, automação de regras de benefício, bloqueio em tempo real, relatórios de auditoria e integração nativa com sistemas de RH/acadêmicos. Reduz custos operacionais de reemissão e combate fraudes[cite: 1, 5].
* **Canais:** App Mobile (Android/iOS), Painel Web Institucional, Parcerias Institucionais (Secretarias/RHs), Notificações Push, Divulgação no campus/empresa, Vendas B2B Diretas[cite: 1, 5].
* **Relacionamento:** Autoatendimento mobile intuitivo, onboarding guiado B2B, notificações proativas de saldo, suporte/chat e transparência de status[cite: 1, 5].
* **Fontes de Renda:** Licenciamento B2B (assinatura por usuário ativo/módulo), Comissão sobre Recarga (Take-rate futuro), Taxa de Integração via API e Módulos Avançados de Auditoria/Relatórios[cite: 1, 5].
* **Recursos-chave:** Plataforma App/Web, Validador NFC (HCE) / QR Dinâmico, Gateway de Pagamento, Infraestrutura em Nuvem, Criptografia e Conformidade LGPD[cite: 1, 5].
* **Atividades-chave:** Dev do software, Segurança de tokens, Integrações (RH/Acadêmico/Operadoras), Suporte/Onboarding B2B e B2C, Monitoramento Antifraude[cite: 1, 5].
* **Parcerias-chave:** Operadoras de Transporte (ex: ETUFOR), Gateways Pix/Cartão, ERPs de Folha de Pagamento e Sistemas Acadêmicos[cite: 1, 5].
* **Estrutura de Custo:** Nuvem/Hospedagem, Dev Team, Taxas Antifraude/Pagamentos, Suporte B2B/B2C, Compliance Legal e Segurança da Informação[cite: 1, 5].

---

## 🎁 Canvas de Proposta de Valor (Resumo de Ganhos)

* **Produtos e Serviços:** App Mobile-First para passageiros (NFC + QR Code dinâmico offline) e Painel Web B2B/B2G para gestão, automação de benefícios e auditoria em tempo real[cite: 1].
* **Aliviadores de Dores:** O celular elimina a dependência do cartão físico em PVC; recarga instantânea sem filas; QR Code como acesso universal para celulares sem NFC ou como alternativa offline; bloqueio imediato e sem taxas em caso de perda ou roubo; integração automatizada para demissões de funcionários e desvinculação de alunos.
* **Criadores de Ganhos:** Confirmação de embarque em tempo real (feedback visual/tátil); alertas proativos de saldo baixo e depósitos; compra/recarga avulsa instantânea via Pix; trilha de auditoria antifraude e relatórios financeiros automáticos; validação 100% offline garantida na catraca.
---

## 🗺️ Roadmap Estratégico

**Pilares Estratégicos:**
1. Confiabilidade de validação em tempo real (NFC, QR Code e modo offline) para reduzir falhas e desencontros na catraca
2. Substituição do cartão físico por uma credencial digital inclusiva, que funcione com ou sem NFC no aparelho do usuário
3. Conversão fim-a-fim (cadastro -> recarga -> validação) com foco em reduzir filas e atrito no embarque
4. Regras e dados padronizados para instituições (empresas, escolas, operadoras) com gestão simples e rápida
5. Retenção e confiança via alertas automáticos de saldo, extrato completo e bloqueio remoto em caso de roubo
6. Go-to-market por parcerias institucionais e validação com usuários reais
7. Monetização progressiva (licenciamento institucional + comissão sobre recargas + contratos com operadoras) sem prejudicar a adoção
8. Ciclo contínuo de validação e aprendizado (pesquisa com usuários, testes de campo e loops de feedback com instituições)

### Fase 1: MVP da Credencial Digital (Cartão Virtual e Validação)
* **Duração:** 6 a 8 semanas[cite: 7]
* **Foco:** Provar que o celular substitui o cartão físico com segurança tanto para usuários vinculados quanto avulsos (base)[cite: 1, 7].
* **Entregas:** Cadastro (foto, ID, benefício ou perfil avulso), Vínculo assistido + Cadastro direto, Validação NFC (HCE) / QR Code dinâmico, Modo offline local, Tela de status em tempo real[cite: 1, 7].
* **Métricas:** Validação em <3s, 90% sucesso na 1ª tentativa, 70% ativação, NPS >= 35[cite: 7].

### Fase 2: Recarga e Segurança (Fidelização)
* **Duração:** 8 a 10 semanas[cite: 7]
* **Foco:** Controle de saldo, recargas instantâneas e segurança do ativo[cite: 7].
* **Entregas:** Recarga Pix/Cartões (benefício e avulso), Extrato/Histórico de viagens, Alerta de saldo baixo, Bloqueio/Reemissão remota instantânea, Push Notifications[cite: 1, 7].
* **Métricas:** 50% WAU (ativos semanais), Recarga em <30s, Aprovação pagto >=95%, Retenção D30 >=40%[cite: 7].

### Fase 3: Painel Gestor, Auditoria e Monetização (Escala B2B/B2G)
* **Duração:** 10 a 12 semanas[cite: 8]
* **Foco:** Escala B2B/B2G, Integrações de sistemas e Geração de receita[cite: 1, 8].
* **Entregas:** Painel Web B2B/B2G (CRUD de usuários e importação em lote CSV/XLSX), Regras de recarga/concessão automática, Live Dashboard e logs de auditoria (para operadoras e órgãos reguladores), Integrações API (RH/Sistemas acadêmicos), Faturamento institucional[cite: 1, 8].
* **Métricas:** >=2 instituições/empresas ativas, 60% elegíveis cadastrados, 70% mais rápido que processo físico[cite: 8].
