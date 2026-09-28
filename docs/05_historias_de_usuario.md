# ✍️ Histórias de Usuários (Requisitos Funcionais e BDD)

## 1. Baixar o app e iniciar o cadastro
* **Jornada/Passo:** Jornada 1, Cynthia (Passo J1-P1) | Fase 1
* **Narrativa:** Como Cynthia, a estudante que não pode perder a aula, eu quero baixar o app e iniciar o cadastro escolhendo o benefício estudantil, para começar rapidamente a trocar a carteirinha física pelo cartão virtual.
* **Descrição:** Onboarding curto, progressivo, com seleção de benefício (estudante/comum/VT). Salvamento no servidor para permitir retomar de onde parou.
* **Regras de Negócio:**
  * Nome obrigatório (2-60 char). E-mail/telefone com máscara/validador.
  * Senha min. 8 char.
  * Categoria e Termos de Uso (LGPD) são obrigatórios.

### Critérios de Aceitação (BDD)
**Cenário 1: Cadastro iniciado com sucesso**
**Dado** que estou na tela "Crie sua conta"
**Quando** preencho nome, contato e senha válidos e escolho a categoria "Estudante"
**E** aceito os termos e toco em "Continuar"
**Então** o sistema cria minha conta e abre o próximo passo do cadastro.

**Cenário 2: Falha de rede no salvamento**
**Dado** que preenchi os dados corretamente
**Quando** ocorre uma falha de conexão ao tocar em "Continuar"
**Então** vejo uma mensagem de erro e o botão "Tentar novamente"
**E** os dados preenchidos continuam na tela.

---

## 2. Enviar foto e vincular o benefício estudantil
* **Jornada/Passo:** Jornada 1, Cynthia (Passo J1-P2) | Fase 1
* **Narrativa:** Como Cynthia, eu quero enviar minha foto e vincular meu perfil à instituição de ensino, para gerar um cartão virtual oficial e válido no embarque.
* **Descrição:** Geração visual da credencial. Envio de selfie/upload. O sistema retorna o layout pronto e coloca em status de análise/ativo.
* **Regras de Negócio:**
  * Foto max 5MB (JPG/PNG/WEBP). Crop no front-end.
  * Matrícula obrigatória e Instituição selecionada em lista (combo-box).
  * Geração de ID universal único. Status "Em conferência" ou "Ativo" (MVP manual/mockado).

### Critérios de Aceitação (BDD)
**Cenário 1: Cartão gerado com sucesso**
**Dado** que estou na tela "Monte seu cartão virtual"
**Quando** envio uma foto válida, informo a matrícula e escolho a instituição
**E** toco em "Gerar cartão"
**Então** vejo o cartão virtual renderizado com foto, nome, matrícula, benefício e um ID único.

**Cenário 2: Foto acima do limite de peso**
**Dado** que estou enviando a foto do cartão
**Quando** escolho um arquivo acima de 5 MB
**Então** vejo um erro de validação explicando o limite
**E** os dados textuais informados permanecem preservados para reenvio.

---

## 3. Validar o embarque por NFC ou QR Code Dinâmico
* **Jornada/Passo:** Jornada 1, Cynthia / Jornada 2, Lucas (Passo J1-P4) | Fase 1
* **Narrativa:** Como usuário ativo (Cynthia/Lucas), eu quero aproximar o celular do validador (NFC) ou apresentar um QR Code dinâmico, para embarcar com segurança sem cartão plástico.
* **Descrição:** Núcleo do MVP. Alternância de interface entre HCE (aproximação Android) e QR Code Óptico.
* **Regras de Negócio:**
  * Requer cartão status "Ativo" e Saldo positivo.
  * QR Code roda algoritmo criptográfico TOTP (expira em máx 30 segs) para evitar prints e clonagem.
  * Vibração Haptic no sucesso. Feedback full-screen visual ("Liberado" / "Negado").

### Critérios de Aceitação (BDD)
**Cenário 1: Validação por NFC**
**Dado** que tenho um cartão "Ativo" em um aparelho Android compatível e saldo disponível
**Quando** aproximo o celular do validador da catraca
**Então** a catraca é liberada no leitor
**E** o app exibe a tela verde "Liberado" com feedback tátil de vibração.

**Cenário 2: Renovação automática do Token Óptico**
**Dado** que a tela do QR Code Dinâmico está aberta
**Quando** o tempo de validade (30 segundos) expira
**Então** o aplicativo gera imediatamente um novo QR Code atualizado
**E** a matriz anterior torna-se inválida para leitura na catraca.

**Cenário 3: Validação bloqueada por falta de credencial**
**Dado** que meu cartão está com status "Em conferência", "Bloqueado" ou com saldo insuficiente
**Quando** tento validar o embarque na catraca
**Então** vejo a tela vermelha "Negado" indicando o motivo específico
**E** a catraca não libera o giro.