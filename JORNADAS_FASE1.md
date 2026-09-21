# 🗺️ Jornadas dos Usuários — Fase 1: MVP da Credencial Digital

> **Cartão Virtual e Validação**

* **⏱️ Duração:** 6–8 semanas  
* **🎯 Foco estratégico:** Provar, com o menor esforço viável, que o smartphone substitui o cartão físico com total segurança, confiabilidade e velocidade — construindo a fundação técnica e de confiança para as fases seguintes.

> ℹ️ **Nota de Escopo:**  
> As jornadas abaixo cobrem as entregas exclusivas da **Fase 1**: cadastro simplificado, emissão de credencial virtual (foto, identificador único e tipo de benefício), validação dupla por aproximação (NFC) e leitura óptica (QR Code dinâmico), contingência por modo offline automático e tela de confirmação de embarque em tempo real.  
> 
> *A persona **Fernanda** (Gestora de RH / Instituição de Ensino) não possui jornada nesta etapa pois o painel web administrativo corporativo será entregue na **Fase 3** — o MVP é 100% centrado na experiência do passageiro final.*

---

## 🎓 Jornada 1: Beatriz (Estudante)

* **Persona:** Beatriz, a estudante que não pode perder a aula por causa da carteirinha  
* **Objetivo:** Substituir a carteirinha física pelo cartão virtual e comprovar que consegue realizar o embarque com rapidez e segurança utilizando exclusivamente o smartphone.

### Etapas da Jornada

#### 1. Baixar o app e iniciar o cadastro
* **Descrição:** Baixar o MobilidadeFlow e iniciar o fluxo de onboarding informando dados cadastrais básicos e selecionando a categoria de benefício estudantil.
* **Sentimento do usuário:** *"Espero que seja rápido — já estou testando algo novo em vez da minha carteirinha de sempre."*
* **Touchpoint:** `Tela: Onboarding / Cadastro`

#### 2. Enviar foto e vincular o benefício estudantil
* **Descrição:** Capturar selfie/enviar foto oficial para o cartão virtual e vincular o perfil à instituição de ensino correspondente.
* **Sentimento do usuário:** *"Preciso que pareça oficial, senão o cobrador ou a catraca não vão confiar."*
* **Touchpoint:** `Tela: Emissão do Cartão Virtual (Foto, ID e Benefício)`

#### 3. Visualizar o cartão virtual ativo
* **Descrição:** Visualizar na tela inicial (Home) a credencial ativa gerada com dados cadastrais, foto, matrícula, identificador e status operacional.
* **Sentimento do usuário:** *"Que bom, já não preciso mais carregar a carteirinha de papel."*
* **Touchpoint:** `Tela: Cartão Virtual (Home)`

#### 4. Validar o embarque por NFC ou QR Code
* **Descrição:** Aproximar o celular do validador (NFC) ou apontar o QR Code dinâmico para a câmera de leitura na catraca do coletivo.
* **Sentimento do usuário:** *"Momento da verdade — será que vai funcionar de primeira?"*
* **Touchpoint:** `Componente: Validação por NFC / QR Code Dinâmico (Catraca)`

#### 5. Confirmar o embarque na tela de status em tempo real
* **Descrição:** Receber feedback tátil e visual instantâneo de liberação da catraca com confirmação do embarque em tempo real.
* **Sentimento do usuário:** *"Funcionou! Consegui embarcar sem o cartão físico."*
* **Touchpoint:** `Tela: Embarque (Status em Tempo Real)`

#### 6. Validar em trecho sem conectividade
* **Descrição:** Executar o embarque com acionamento transparente do modo offline automático em áreas de sombra de cobertura de dados móveis.
* **Sentimento do usuário:** *"Alívio — nem precisei me preocupar com o sinal do celular."*
* **Touchpoint:** `Componente: Modo Offline Automático`

---

## 💼 Jornada 2: Marcos (Trabalhador CLT)

* **Persona:** Marcos, o trabalhador que não pode chegar atrasado por causa do vale-transporte  
* **Objetivo:** Substituir o cartão plástico de vale-transporte pelo aplicativo e confiar na validação em horário de pico sem fricção.

### Etapas da Jornada

#### 1. Cadastrar-se e vincular o benefício corporativo
* **Descrição:** Baixar o aplicativo, preencher os dados de identificação e autenticar o vínculo corporativo do vale-transporte disponibilizado pela empresa.
* **Sentimento do usuário:** *"Espero não precisar preencher um monte de coisa manual antes de conseguir usar."*
* **Touchpoint:** `Tela: Onboarding / Cadastro`

#### 2. Emitir o cartão virtual com foto e ID
* **Descrição:** Realizar o envio da foto de identificação e conferir o espelho digital do benefício emitido para uso imediato.
* **Sentimento do usuário:** *"Se está tudo certo aqui, não preciso mais andar com o cartão de plástico."*
* **Touchpoint:** `Tela: Emissão do Cartão Virtual (Foto, ID e Benefício)`

#### 3. Validar por NFC em horário de pico
* **Descrição:** Aproximar o dispositivo do sensor da catraca em horário de intenso fluxo de passageiros.
* **Sentimento do usuário:** *"Não posso travar a fila atrás de mim — precisa ser rápido."*
* **Touchpoint:** `Componente: Validação por NFC (Catraca)`

#### 4. Acompanhar a confirmação na tela de embarque
* **Descrição:** Checar a tela de confirmação imediata garantindo que a passagem foi debitada e validada sem inconsistências.
* **Sentimento do usuário:** *"Passou de primeira, que alívio."*
* **Touchpoint:** `Tela: Embarque (Status em Tempo Real)`

#### 5. Utilizar QR Code como contingência
* **Descrição:** Alternar rapidamente para a leitura óptica de QR Code dinâmico caso haja instabilidade no módulo NFC do dispositivo ou do validador.
* **Sentimento do usuário:** *"Bom saber que tem um plano B — não fico na mão na catraca."*
* **Touchpoint:** `Componente: Validação por QR Code Dinâmico`

#### 6. Validar o embarque em área sem cobertura de rede
* **Descrição:** Realizar a passagem pela catraca sem interrupção através da validação criptográfica offline local.
* **Sentimento do usuário:** *"Nem percebi que estava sem internet — funcionou igual."*
* **Touchpoint:** `Componente: Modo Offline Automático`
