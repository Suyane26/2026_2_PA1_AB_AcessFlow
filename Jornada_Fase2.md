# Mapeamento de Jornadas do Usuário — AccessFlow

---

## Jornada 3: Estudante Universitária
* **Persona:** Ana, a estudante universitária que depende da carteirinha estudantil e não pode perder o embarque.
* **Objetivo:** Cadastrar e usar o cartão virtual do AccessFlow para validar embarque sem cartão físico, com recarga e segurança no MVP.

---

### Etapa 1: Acessar o app e iniciar cadastro como usuária
* **Descrição:** Entrar no aplicativo e iniciar o cadastro para migrar do cartão físico para o cartão virtual.
* **Sentimento do usuário:** *"Espero que seja mais rápido do que ir até um posto físico."*
* **Touchpoint:** `Área do Usuário (Home/Onboarding do App)`

### Etapa 2: Cadastrar dados pessoais, foto e vincular benefício estudantil
* **Descrição:** Inserir foto, nome, número de matrícula e tipo de benefício para gerar o cartão virtual.
* **Sentimento do usuário:** *"Se for reconhecido corretamente, não preciso mais andar com a carteirinha física."*
* **Touchpoint:** `Tela: Cadastro do Cartão Virtual`

### Etapa 3: Ativar validação por NFC ou QR Code Dinâmico
* **Descrição:** Configurar o método de validação preferido para embarque nos terminais e veículos.
* **Sentimento do usuário:** *"Quero uma forma rápida e que funcione mesmo sem internet."*
* **Touchpoint:** `Tela: Configuração de Validação (NFC/QR Code)`

### Etapa 4: Realizar recarga de créditos via Pix
* **Descrição:** Adicionar créditos ao benefício diretamente pelo celular, sem precisar de bilheteria.
* **Sentimento do usuário:** *"Ótimo não precisar mais enfrentar fila para recarregar."*
* **Touchpoint:** `Tela: Recarga de Créditos`

### Etapa 5: Validar embarque no ônibus (NFC/QR, inclusive offline)
* **Descrição:** Aproximar o celular do validador ou apresentar o QR Code para embarcar, mesmo sem sinal de internet.
* **Sentimento do usuário:** *"Preciso que funcione sempre, sem travar na catraca."*
* **Touchpoint:** `Componente: Tela de Embarque em Tempo Real`

### Etapa 6: Consultar histórico de viagens e saldo
* **Descrição:** Visualizar recargas, viagens realizadas e saldo atual para ter controle do uso.
* **Sentimento do usuário:** *"Bom saber exatamente quanto gastei e onde usei."*
* **Touchpoint:** `Tela: Histórico e Extrato`

### Etapa 7: Bloquear o cartão remotamente em caso de perda ou roubo
* **Descrição:** Bloquear o benefício imediatamente pelo app caso o celular seja perdido ou roubado.
* **Sentimento do usuário:** *"Alívio de saber que consigo agir na hora, sem depender de posto físico."*
* **Touchpoint:** `Componente: Bloqueio Remoto de Emergência`

---

## Jornada 4: Gestor Institucional (RH)
* **Persona:** Marcos, o coordenador de RH que gerencia o vale-transporte de dezenas de funcionários.
* **Objetivo:** Cadastrar, administrar e monitorar os benefícios de transporte da empresa pelo painel web do AccessFlow para reduzir custos e fraudes no MVP.

---

### Etapa 1: Acessar o painel administrativo e iniciar cadastro da empresa
* **Descrição:** Entrar na área de gestão institucional para configurar a empresa e seus benefícios.
* **Sentimento do usuário:** *"Preciso de um sistema único para não perder controle dos benefícios."*
* **Touchpoint:** `Área do Administrador (Home/Onboarding Institucional)`

### Etapa 2: Cadastrar e vincular funcionários aos benefícios
* **Descrição:** Inserir dados dos funcionários e vincular cada um ao tipo de benefício de transporte correspondente.
* **Sentimento do usuário:** *"Se o cadastro for simples, evito retrabalho e erros manuais."*
* **Touchpoint:** `Tela: Gestão de Usuários (CRUD)`

### Etapa 3: Definir regras de recarga e elegibilidade
* **Descrição:** Configurar valores, periodicidade e critérios de validação automática dos benefícios.
* **Sentimento do usuário:** *"Quero automatizar isso para não ter que aprovar tudo manualmente."*
* **Touchpoint:** `Tela: Administração de Benefícios`

### Etapa 4: Monitorar uso em tempo real pelo Dashboard
* **Descrição:** Acompanhar gráficos de fluxo de usuários, saldos médios e recargas realizadas.
* **Sentimento do usuário:** *"Preciso enxergar rápido se algo está fora do padrão."*
* **Touchpoint:** `Tela: Live Dashboard`

### Etapa 5: Emitir relatórios e logs de auditoria
* **Descrição:** Filtrar e exportar dados de recargas, saldos e viagens por data, perfil ou método de validação.
* **Sentimento do usuário:** *"Isso me dá segurança para prestar contas e identificar fraudes."*
* **Touchpoint:** `Tela: Relatórios e Auditoria`

### Etapa 6: Bloquear ou desbloquear credenciais remotamente
* **Descrição:** Suspender o acesso de um funcionário desligado ou reativar em caso de contestação.
* **Sentimento do usuário:** *"Preciso que a mudança tenha efeito imediato, sem depender de terceiros."*
* **Touchpoint:** `Componente: Gestão de Status (Bloqueio/Desbloqueio)`

### Etapa 7: Integrar o sistema com a folha de pagamento
* **Descrição:** Conectar o AccessFlow ao sistema de RH para sincronizar dados de admissão, desligamento e benefícios.
* **Sentimento do usuário:** *"Assim evito lançar a mesma informação em dois lugares diferentes."*
* **Touchpoint:** `Componente: Integração com Sistemas Externos (RH)`
