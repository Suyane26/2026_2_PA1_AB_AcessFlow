# ✍️ Histórias de Usuários (Requisitos Funcionais e BDD)

## # 1. Cynthia — Validar o primeiro embarque por NFC

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 1 — MVP da Credencial Digital
- **Jornada de Usuário:** Cynthia — Cadastrar-se, ativar o cartão virtual e validar o primeiro embarque sem o cartão físico
- **Passo:** Validar o primeiro embarque por NFC

**## Geral**
- **Produto:** AccessFlow
- **Título:** Validar o primeiro embarque por NFC
- **Narrativa:** Como Cynthia, estudante que depende do ônibus todos os dias, eu quero validar meu embarque aproximando o celular na catraca, para confirmar que o cartão virtual realmente substitui o físico.
- **Prioridade:** Alta | **Tipo:** Feature | **Coluna:** Em trabalho

**## Detalhes**
**### Descrição Detalhada:** Esta história cobre o momento decisivo da jornada de Cynthia: a primeira validação real na catraca. O app deve emitir um sinal NFC (HCE) com um token de curta duração, exibir feedback visual e sonoro imediato de sucesso ou falha, e registrar a viagem no histórico em segundos.
**### Orientações de Tela:** Tela cheia com animação de "aguardando aproximação"; feedback verde + vibração em caso de sucesso; feedback vermelho + mensagem clara em caso de falha, com botão "tentar novamente" ou "usar QR Code".
**### Regras de Negócio:** Token NFC válido por poucos segundos e de uso único; se a leitura falhar 2 vezes, oferecer QR Code automaticamente como alternativa; registrar tentativas falhas para métricas de confiabilidade.

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Validação bem-sucedida por NFC

Dado que estou com o cartão virtual ativo

Quando aproximo o celular do leitor NFC da catraca

Então devo ver confirmação visual de sucesso em até 10 segundos

E a viagem deve aparecer no meu histórico imediatamente

Falha na leitura NFC

Dado que aproximei o celular do leitor

Quando a leitura falha

Então devo ver uma mensagem clara de erro

E devo ver a opção de usar QR Code como alternativa

**### Orientações para Implementação:** Usar HCE (Host Card Emulation) para simular o cartão via NFC; gerar token assinado no momento da aproximação, não antes; registrar evento de analytics: nfc_tentativa, nfc_sucesso, nfc_falha. Id do passo: 104

## # 2. Lucas — Validar embarque num ônibus lotado, sem sinal de internet

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 1 — MVP da Credencial Digital
- **Jornada de Usuário:** Lucas — Ativar o cartão virtual e confiar que a validação funciona mesmo sem internet
- **Passo:** Validar embarque num ônibus lotado, sem sinal de internet

**## Geral**
- **Produto:** AccessFlow
- **Título:** Validação offline em ônibus lotado
- **Narrativa:** Como Lucas, trabalhador que pega ônibus lotado, eu quero validar meu embarque mesmo sem internet, para não ficar dependente de sinal de celular no meio da viagem.
- **Prioridade:** Alta | **Tipo:** Feature | **Coluna:** Em trabalho

**## Detalhes**
**### Descrição Detalhada:** O app deve manter localmente um conjunto de tokens de validação pré-gerados e criptografados, renovados sempre que houver conexão, permitindo validação via NFC mesmo com o app totalmente offline. A sincronização com o backend deve ocorrer automaticamente assim que a conexão for restabelecida.
**### Orientações de Tela:** Indicador discreto de "modo offline ativo" no cartão virtual; tela de validação funciona normalmente, sem exigir internet; badge de "sincronizando" quando a conexão volta.
**### Regras de Negócio:** Manter no mínimo um lote de tokens offline válidos por até 48 horas sem conexão; ao voltar a conexão, sincronizar viagens validadas offline em segundo plano; bloquear geração de novos tokens offline se o saldo estiver zerado.

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Validação sem internet

Dado que meu celular está sem conexão com a internet

E eu tenho tokens offline válidos e saldo disponível

Quando aproximo o celular do leitor NFC da catraca

Então a validação deve ser concluída normalmente

E a viagem deve ficar marcada como "pendente de sincronização"

Sincronização após reconexão

Dado que tenho viagens validadas offline pendentes

Quando o celular recupera a conexão com a internet

Então as viagens devem sincronizar automaticamente com o backend

E o saldo exibido deve refletir o consumo real

**### Orientações para Implementação:** Armazenar tokens offline de forma criptografada no dispositivo; usar fila local (offline queue) para sincronização; registrar evento de analytics: validacao_offline, sincronizacao_concluida. Id do passo: 105

## # 3. Beatriz — Validar embarque por QR Code, sem NFC no celular

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 1 — MVP da Credencial Digital
- **Jornada de Usuário:** Beatriz — Usar o AccessFlow mesmo sem vínculo institucional e sem NFC
- **Passo:** Validar embarque por QR Code, já que o celular não tem NFC

**## Geral**
- **Produto:** AccessFlow
- **Título:** Validação por QR Code Dinâmico
- **Narrativa:** Como Beatriz, usuária avulsa sem NFC no celular, eu quero validar meu embarque apontando um QR Code, para conseguir usar o AccessFlow mesmo com um aparelho mais simples.
- **Prioridade:** Alta | **Tipo:** Feature | **Coluna:** Em trabalho

**## Detalhes**
**### Descrição Detalhada:** O app deve gerar um QR Code dinâmico, válido por poucos segundos, que o leitor da catraca escaneia para validar o embarque. Essa modalidade não depende de hardware NFC no celular do usuário, garantindo inclusão de aparelhos mais simples.
**### Orientações de Tela:** Botão "Validar por QR Code" visível mesmo quando o app detecta que o aparelho não tem NFC; QR Code em tela cheia com contador regressivo de validade; nova geração automática se expirar sem uso.
**### Regras de Negócio:** QR Code válido por no máximo 30 segundos; gerar novo código a cada tentativa; detectar automaticamente ausência de hardware NFC e priorizar QR Code na interface.

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Geração e uso do QR Code dentro da validade

Dado que estou na tela de validação de embarque

Quando toco em "Validar por QR Code"

Então um QR Code deve ser gerado com validade de até 30 segundos

E, ao ser escaneado pela catraca dentro desse tempo, a validação deve ser concluída

QR Code expirado

Dado que gerei um QR Code de validação

Quando o tempo de validade expira sem uso

Então o código deve ser invalidado automaticamente

E um novo código deve poder ser gerado com um toque

**### Orientações para Implementação:** Gerar o QR Code a partir de um token assinado no backend, nunca reaproveitar um código já usado; detectar hardware NFC via API do sistema operacional para priorizar a interface correta; registrar evento de analytics: qr_gerado, qr_validado, qr_expirado. Id do passo: 106

## # 4. Marcos — Importar a lista de alunos elegíveis do semestre

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 3 — Painel Web Institucional e Monetização
- **Jornada de Usuário:** Marcos — Usar o painel web para gerenciar as credenciais dos alunos em escala
- **Passo:** Importar a lista de alunos elegíveis do semestre

**## Geral**
- **Produto:** AccessFlow
- **Título:** Importação em lote de usuários elegíveis
- **Narrativa:** Como Marcos, coordenador de benefícios de uma instituição de ensino, eu quero importar centenas de alunos de uma vez via planilha, para não precisar cadastrar cada um manualmente.
- **Prioridade:** Alta | **Tipo:** Feature | **Coluna:** Análise

**## Detalhes**
**### Descrição Detalhada:** O painel deve permitir o upload de uma planilha (CSV/XLSX) com os dados mínimos de cada aluno (nome, matrícula, e-mail, tipo de benefício), validar o formato, sinalizar erros linha a linha e processar o cadastro em lote, dando origem a um convite automático para cada aluno ativar seu cartão virtual.
**### Orientações de Tela:** Botão "Importar usuários"; template de planilha para download; tela de revisão mostrando quantos registros são válidos e quantos têm erro, com detalhe por linha; confirmação final antes de processar.
**### Regras de Negócio:** Rejeitar linhas com e-mail ou matrícula duplicados dentro da própria planilha; permitir reprocessar apenas as linhas com erro após correção; disparar e-mail de convite automático para cada aluno importado com sucesso.

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Importação bem-sucedida

Dado que estou na tela "Importação de Usuários"

Quando envio uma planilha com todos os registros válidos

Então todos os alunos devem ser cadastrados automaticamente

E cada um deve receber um convite por e-mail para ativar o cartão virtual

Importação com linhas inválidas

Dado que envio uma planilha com algumas linhas com erro (matrícula duplicada, e-mail inválido)

Quando o sistema processa o arquivo

Então devo ver quais linhas falharam e por quê

E os registros válidos devem ser cadastrados normalmente, sem bloquear o restante

**### Orientações para Implementação:** Processar a importação de forma assíncrona (fila em background) para arquivos grandes; validar dados linha a linha antes de gravar; registrar evento de analytics: importacao_iniciada, importacao_concluida, linhas_com_erro. Id do passo: 107

## # 5. Ana — Configurar o crédito mensal automático de vale-transporte

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 3 — Painel Web Institucional e Monetização
- **Jornada de Usuário:** Ana — Configurar o crédito automático mensal e integrar ao sistema de RH
- **Passo:** Configurar o crédito mensal automático de vale-transporte

**## Geral**
- **Produto:** AccessFlow
- **Título:** Crédito automático mensal de benefício
- **Narrativa:** Como Ana, analista de RH, eu quero configurar o crédito mensal automático de vale-transporte por cargo, para eliminar o processo manual que se repete todo mês.
- **Prioridade:** Alta | **Tipo:** Feature | **Coluna:** Análise

**## Detalhes**
**### Descrição Detalhada:** O painel deve permitir definir regras de crédito automático (valor e data) associadas a cargos ou grupos de funcionários, processando o crédito recorrente sem intervenção manual todo mês, com notificação para o gestor confirmando a execução.
**### Orientações de Tela:** Tela "Crédito Automático" com lista de regras por cargo/grupo; campo de valor e data de crédito; toggle de ativar/pausar regra; histórico dos créditos já processados.
**### Regras de Negócio:** Processar o crédito automaticamente na data configurada, mesmo sem login do gestor; não permitir duas regras ativas conflitantes para o mesmo grupo; notificar o gestor em caso de falha no processamento (ex: cartão virtual não ativado).

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Execução do crédito automático na data configurada

Dado que configurei uma regra de crédito mensal para um grupo de funcionários

Quando chega a data configurada

Então o crédito deve ser processado automaticamente para todos os funcionários elegíveis

E devo receber uma confirmação de que o processamento foi concluído

Falha no crédito de um funcionário específico

Dado que o crédito automático está sendo processado

Quando um funcionário ainda não ativou o cartão virtual

Então o crédito dele deve ficar pendente, sem travar o processamento dos demais

E devo ver esse caso sinalizado no painel

**### Orientações para Implementação:** Usar job agendado (scheduler) para processar os créditos na data configurada; processar em lote com tratamento individual de falhas; registrar evento de analytics: credito_automatico_processado, credito_pendente. Id do passo: 108

## # 6. Roberto — Conferir o extrato de comissão sobre as recargas do período

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 3 — Painel Web Institucional e Monetização
- **Jornada de Usuário:** Roberto — Acompanhar a adoção do AccessFlow e validar o contrato de comissão
- **Passo:** Conferir o extrato de comissão sobre as recargas do período

**## Geral**
- **Produto:** AccessFlow
- **Título:** Extrato financeiro de comissão da operadora
- **Narrativa:** Como Roberto, gestor de operadora de transporte, eu quero ver o extrato de comissão gerado pelas recargas da minha frota, para validar se o modelo de receita compensa o contrato.
- **Prioridade:** Média | **Tipo:** Feature | **Coluna:** Backlog

**## Detalhes**
**### Descrição Detalhada:** O painel deve apresentar, por período, o total de recargas realizadas por usuários que validaram embarque na frota da operadora, o valor de comissão correspondente e a projeção com base na tendência do período anterior, permitindo exportação para conferência financeira.
**### Orientações de Tela:** Gráfico de comissão por período; tabela detalhável por linha/data; botão "Exportar extrato" (CSV/PDF); comparação com o período anterior.
**### Regras de Negócio:** Comissão calculada apenas sobre recargas de usuários com validações registradas na frota da operadora no período; valores exibidos em tempo real, com fechamento oficial mensal; extrato exportado deve bater com o relatório usado para faturamento.

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Consulta do extrato de comissão do período

Dado que estou no painel financeiro da operadora

Quando seleciono um período específico

Então devo ver o total de recargas associadas à minha frota e o valor de comissão correspondente

Exportação do extrato

Dado que estou visualizando o extrato de um período

Quando clico em "Exportar extrato"

Então devo receber um arquivo com os mesmos valores exibidos na tela, pronto para conferência financeira

**### Orientações para Implementação:** Calcular comissão em job assíncrono diário, com cache para consulta rápida no painel; garantir que o valor exportado seja idêntico ao exibido na tela (mesma fonte de dado); registrar evento de analytics: extrato_comissao_consultado, extrato_exportado. Id do passo: 109

## # 7. Fernanda — Auditar logs de segurança e tentativas de fraude

**## Passo de Jornada**
- **Fase do Roadmap Estratégico:** Fase 3 — Painel Web Institucional e Monetização
- **Jornada de Usuário:** Fernanda — Fiscalizar a conformidade do AccessFlow antes da aprovação ampla na cidade
- **Passo:** Auditar logs de segurança e tentativas de fraude

**## Geral**
- **Produto:** AccessFlow
- **Título:** Auditoria de segurança e conformidade
- **Narrativa:** Como Fernanda, representante de um consórcio de mobilidade urbana, eu quero auditar os logs de segurança do AccessFlow, para confirmar que o sistema é seguro o suficiente para operar em escala na cidade.
- **Prioridade:** Alta | **Tipo:** Feature | **Coluna:** Backlog

**## Detalhes**
**### Descrição Detalhada:** O painel deve oferecer uma visão consolidada de eventos de segurança: tentativas de validação inválida, bloqueios acionados, reemissões e qualquer padrão suspeito (ex: mesmo cartão validado em dois lugares distantes em curto intervalo), com filtros por período, operadora e tipo de evento.
**### Orientações de Tela:** Tela "Logs de Auditoria" com filtros (período, operadora, tipo de evento); lista de eventos com severidade sinalizada por cor; opção de exportar o relatório completo para documentação formal.
**### Regras de Negócio:** Sinalizar automaticamente padrões suspeitos (ex: validações geograficamente incompatíveis no mesmo intervalo de tempo) para revisão; reter os logs de auditoria por um período mínimo definido em contrato; acesso a esse painel restrito a perfis de auditoria/regulação.

**## BDD & Implementação**
**### Critérios de Aceitação (BDD)**

Consulta de logs por período

Dado que estou na tela "Logs de Auditoria"

Quando filtro por um período e uma operadora específicos

Então devo ver todos os eventos de segurança relevantes daquele recorte

Sinalização de padrão suspeito

Dado que o sistema identifica duas validações do mesmo cartão em locais incompatíveis num curto intervalo

Quando esse evento ocorre

Então ele deve aparecer destacado como "suspeito" na tela de auditoria

E deve ser possível abrir o detalhe do caso para investigação

**### Orientações para Implementação:** Implementar regra de detecção de anomalia geográfica/temporal como job assíncrono; manter trilha de auditoria imutável (append-only) para validade probatória; registrar evento de analytics: log_auditoria_consultado, evento_suspeito_sinalizado. Id do passo: 110

# 8. Cynthia — Cadastrar conta com perfil de estudante
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 1 — MVP da Credencial Digital   

2. Jornada de Usuário: Cynthia — Cadastrar-se, ativar o cartão virtual e validar o primeiro embarque sem o cartão físico   

3. Passo: Baixar o app e criar conta informando a matrícula da faculdade   

## Geral

Produto: AccessFlow   

Título: Cadastro de conta de estudante

Narrativa: Como Cynthia, estudante universitária, eu quero criar minha conta no aplicativo informando minha matrícula e e-mail institucional, para vincular meu perfil ao benefício estudantil.

Prioridade: Alta | Tipo: Feature | Coluna: Em trabalho

## Detalhes
### Descrição Detalhada: 

A tela de cadastro deve solicitar os dados básicos do estudante (nome completo, CPF, e-mail institucional, senha e número de matrícula), realizar a consulta de elegibilidade na base pré-carregada e encaminhar o usuário para a próxima etapa.

### Orientações de Tela: 

Formulário simples com campos validados em tempo real; 

Botão destacado de "Continuar"; 

Opção de suporte ou auxílio caso a matrícula não seja localizada.

### Regras de Negócio: 

1. O CPF e o e-mail devem ser únicos no sistema; 
2. A matrícula deve existir na lista de estudantes elegíveis enviada pela instituição de ensino; 
3. Em caso de divergência, bloquear o avanço e informar o canal de suporte da secretaria.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Cadastro com matrícula elegível

Dado que informo meus dados pessoais e uma matrícula válida e cadastrada pela instituição

Quando toco em "Continuar"

Então minha conta deve ser criada com sucesso

E devo ser direcionada para a etapa de foto e confirmação do cartão virtual

Matrícula não localizada

Dado que informo uma matrícula que não conste na base de elegíveis da instituição

Quando toco em "Continuar"

Então devo ver uma mensagem indicando que o vínculo não foi encontrado

E devo receber orientações para entrar em contato com a secretaria acadêmica

### Orientações para Implementação: 

Implementar validação de CPF e formato de e-mail no frontend; 

Integrar a verificação de matrícula ao endpoint de validação de elegibilidade; 

Registrar evento de analytics: cadastro_estudante_iniciado, cadastro_estudante_sucesso, cadastro_estudante_erro_matricula. Id do passo: 111

# 9. Cynthia — Visualizar e ativar cartão virtual com foto
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 1 — MVP da Credencial Digital   

2. Jornada de Usuário: Cynthia — Cadastrar-se, ativar o cartão virtual e validar o primeiro embarque sem o cartão físico   

3. Passo: Confirmar o vínculo e ativar o cartão virtual   

## Geral

Produto: AccessFlow   

Título: Exibição e ativação do cartão virtual

Narrativa: Como Cynthia, estudante com conta criada, eu quero cadastrar minha foto e visualizar meu cartão virtual ativo, para ter a certeza de que meu benefício está pronto para uso.

Prioridade: Alta | Tipo: Feature | Coluna: Em trabalho

## Detalhes
### Descrição Detalhada: 

A tela exibe o cartão virtual contendo nome do usuário, foto facial clara, ID/matrícula, instituição de ensino associada, tipo de benefício (Estudantil), status "Ativo" e saldo disponível.

### Orientações de Tela: 

Cartão visualmente idêntico a um documento de identificação digital; 

Botão para captura/upload de foto de perfil com guia de enquadramento facial; 

Selo de status em verde indicando "Ativo".

### Regras de Negócio: 

1. A foto deve passar por validação básica de presença facial; 
2. o cartão não pode ser ativado sem foto cadastrada; o status deve refletir a elegibilidade em tempo real com o backend.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Ativação com captura de foto válida

Dado que estou na etapa de ativação e envio uma foto facial nítida

Quando confirmo os dados do meu perfil

Então meu cartão virtual deve ser exibido com a foto, nome, tipo de benefício e status "Ativo"

Cartão inativo ou suspenso

Dado que meu cadastro consta como suspenso na instituição

Quando tento acessar a tela do cartão virtual

Então o cartão deve exibir o status "Inativo" em destaque de aviso

E o recurso de geração de código para validação deve ficar bloqueado

### Orientações para Implementação: 

Utilizar compressão de imagem antes do envio ao backend; 

Armazenar URL da imagem com token de autorização de leitura; 

Registrar evento de analytics: cartao_foto_enviada, cartao_virtual_ativado. Id do passo: 112

# 10. Lucas — Cadastro com vínculo de vale-transporte corporativo
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 1 — MVP da Credencial Digital   

Jornada de Usuário: Lucas — Ativar o cartão virtual e confiar que a validação funciona mesmo sem sinal de internet   

Passo: Criar conta com vínculo empresarial e ativar o cartão virtual   

## Geral

Produto: AccessFlow   

Título: Cadastro de conta corporativa (Vale-Transporte)

Narrativa: Como Lucas, funcionário CLT, eu quero me cadastrar usando meu ID funcional ou CPF para ativar meu cartão virtual de Vale-Transporte fornecido pela empresa.

Prioridade: Alta | Tipo: Feature | Coluna: Em trabalho

## Detalhes
### Descrição Detalhada: 

Permite ao trabalhador vincular seu perfil de usuário à empresa empregadora informando o CPF ou código funcional corporativo, carregando automaticamente o benefício de Vale-Transporte associado.

### Orientações de Tela: 

Tela de onboarding corporativo; 

Campo para busca da empresa parceira e digitação do ID funcional/CPF; 

Tela de confirmação com valor do benefício e nome da empresa.

### Regras de Negócio: 
1. O CPF informado deve bater com o lote enviado pelo RH da empresa parceira; 
2. Caso haja múltiplos vínculos ativos, permitir a alternância de perfis ou consolidar no mesmo app.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Vínculo corporativo localizado

Dado que digito meu CPF cadastrado previamente pelo RH da empresa

Quando confirmo o código de verificação recebido

Então o app deve vincular minha conta à empresa correspondente

E o cartão virtual corporativo deve ser ativado com o saldo de vale-transporte disponível

Vínculo corporativo pendente

Dado que o RH ainda não subiu meu lote de dados no sistema

Quando informo meu CPF

Então recebo uma notificação informando que a credencial corporativa está aguardando liberação do RH

### Orientações para Implementação: 

Endpoint de consulta de elegibilidade por CPF/CNPJ da empresa; 

Envio de SMS/e-mail para token 2FA de validação do titular; 

Registrar evento de analytics: cadastro_corporativo_sucesso, cadastro_corporativo_pendente. Id do passo: 113

# 11. Beatriz — Cadastro e ativação de cartão virtual avulso
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 1 — MVP da Credencial Digital   

Jornada de Usuário: Beatriz — Usar o AccessFlow mesmo sem vínculo institucional e sem NFC   

Passo: Criar conta como usuária avulsa, sem vínculo institucional   

## Geral

Produto: AccessFlow   

Título: Cadastro de perfil avulso sem vínculo institucional

Narrativa: Como Beatriz, usuária avulsa do transporte público, eu quero me cadastrar no app de forma simples sem precisar de vínculo com empresa ou escola, para utilizar o cartão virtual com recarga própria.

Prioridade: Média | Tipo: Feature | Coluna: Em trabalho

## Detalhes
### Descrição Detalhada: 

Fluxo simplificado de cadastro que exige apenas nome, CPF, e-mail e criação de senha para disponibilizar um cartão virtual na modalidade "Tarifa Inteira / Avulso".

### Orientações de Tela: 

Opção "Não possuo vínculo institucional / Uso Avulso" na tela inicial de cadastro; formulário enxuto de três campos; 

Confirmação imediata e redirecionamento para o cartão com saldo R$ 0,00.

### Regras de Negócio: 

1. Não exigir número de matrícula ou validação patronal; 
2. Vincular por padrão o perfil "Tarifa Comum / Avulso"; 
3. Permitir a inserção posterior de cupons ou solicitação de vínculo institucional.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Cadastro avulso concluído

Dado que escolho a opção de cadastro avulso sem instituição

Quando preencho nome, CPF e e-mail válidos

Então meu cartão virtual avulso deve ser gerado instantaneamente

E a interface deve sugerir a realização da primeira recarga

CPF já cadastrado em outra modalidade

Dado que informo um CPF que já possui conta ativa no AccessFlow

Quando tento concluir o cadastro avulso

Então devo ser orientada a realizar o login ou recuperar meu acesso existente

### Orientações para Implementação: 

Simplificar validações de backend no fluxo avulso;

Direcionar o usuário diretamente para a tela de primeira recarga após a conclusão; 

Registrar evento de analytics: cadastro_avulso_concluido. Id do passo: 114

# 12. Cynthia — Visualização do histórico de embarques no app
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 1 — MVP da Credencial Digital   

2. Jornada de Usuário: Cynthia — Cadastrar-se, ativar o cartão virtual e validar o primeiro embarque sem o cartão físico   

3. Passo: Confirmar no histórico que o embarque foi registrado

## Geral

Produto: AccessFlow   

Título: Exibição do histórico recente de viagens no app

Narrativa: Como Cynthia, usuária que acabou de passar na catraca, eu quero ver minha viagem atualizada imediatamente na tela inicial do app, para ter certeza de que o debito do embarque foi correto.

Prioridade: Média | Tipo: Feature | Coluna: Em trabalho

## Detalhes
### Descrição Detalhada: 

A tela inicial do aplicativo deve exibir um feed/card resumido mostrando as últimas viagens realizadas, incluindo linha/veículo, data, hora, valor debitado e método de validação utilizado (NFC ou QR Code).

### Orientações de Tela: 

Card "Última Atividade" na tela principal; 

Lista expansível com data/hora, linha do ônibus/metrô, modalidade e valor; 

Distintivo visual indicando "NFC" ou "QR Code".

### Regras de Negócio: 

1. Atualizar o histórico assim que a confirmação de validação for enviada pelo leitor; 
2. Caso a validação tenha sido offline, exibir a viagem com o status "Sincronizado recentemente" assim que a internet retornar.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Atualização de viagem validada online

Dado que acabei de passar na catraca via NFC com conexão ativa

Quando abro a tela inicial do aplicativo

Então devo ver o registro da viagem no topo da lista com hora, linha e valor debitado

Viagem sincronizada do modo offline

Dado que realizei um embarque em modo offline

Quando a conexão com a internet é restabelecida e o app sincroniza

Então a viagem deve aparecer no histórico acompanhada do horário exato em que ocorreu a validação offline

### Orientações para Implementação: 

Endpoint de listagem de transações com ordenação decrescente por timestamp; 

Suporte a cache local com Room/CoreData para exibição offline instantânea; 

Registrar evento de analytics: historico_viagem_visualizado. Id do passo: 115

# 13. Cynthia — Receber notificação automática de saldo baixo
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 2 — Recarga, Saldo e Segurança   

Jornada de Usuário: Cynthia — Recarregar o saldo pelo próprio app e acompanhar o extrato sem depender de ponto físico   

Passo: Receber o alerta de saldo baixo   

## Geral

Produto: AccessFlow

Título: Alerta e notificação push de saldo baixo

Narrativa: Como Cynthia, usuária do aplicativo, eu quero receber uma notificação automática quando meu saldo atingir um limite mínimo de passagens, para que eu possa recarregar antes de ir ao ponto de embarque.

Prioridade: Alta | Tipo: Feature | Coluna: Análise

## Detalhes
### Descrição Detalhada: 

O sistema deve monitorar o saldo remanescente do cartão virtual e disparar uma notificação push (e badge na tela principal) quando o valor for equivalente a 2 passagens ou menos (configurável pelo usuário).

### Orientações de Tela: 

Notificação push no sistema operacional ("Aviso: Seu saldo está baixo! Você possui apenas 1 passagem restante.");

Destaque em cor amarela/laranja no card de saldo do app.

### Regras de Negócio: 

1. Gatilho ativado após a conclusão de uma validação que rebaixe o saldo para um valor igual ou menor que o limite definido; 
2. Não disparar notificações duplicadas para o mesmo evento de saldo baixo até que ocorra uma nova recarga.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Disparo de notificação após viagem

Dado que meu saldo atual é de R$ 9,00 (equivalente a 2 passagens)

Quando realizo uma viagem que reduz o saldo para R$ 4,50 (1 passagem)

Então recebo uma notificação push alertando sobre o saldo baixo

E vejo o card de saldo destacado na cor de alerta ao abrir o app

Saldo restabelecido por recarga

Dado que estou com alerta de saldo baixo ativo

Quando efetuo uma recarga que eleva o saldo acima do limite mínimo

Então o alerta do card de saldo deve ser removido

E o gatilho de notificação deve ser rearmado para as próximas viagens

### Orientações para Implementação: 

Implementar worker de verificação pós-débito no backend; 

Integração com Firebase Cloud Messaging (FCM) / APNs; 

Registrar evento de analytics: alerta_saldo_baixo_disparado. Id do passo: 116

# 14. Cynthia — Realizar recarga instantânea de saldo via Pix
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 2 — Recarga, Saldo e Segurança   

Jornada de Usuário: Cynthia — Recarregar o saldo pelo próprio app e acompanhar o extrato sem depender de ponto físico

Passo: Recarregar via Pix pelo app   

## Geral

Produto: AccessFlow

Título: Recarga de saldo instantânea por Pix

Narrativa: Como Cynthia, estudante que precisa recarregar o saldo rapidamente, eu quero pagar a recarga via Pix dentro do app, para ter meus créditos liberados em poucos segundos.

Prioridade: Alta | Tipo: Feature | Coluna: Análise

## Detalhes
### Descrição Detalhada: 

Tela de seleção de valor de recarga com opções predefinidas ou valor customizado, geração de código "Pix Copia e Cola" e QR Code dinâmico do Pix, com confirmação e atualização do saldo no app via webhook em tempo real.

### Orientações de Tela: 

Botões com valores sugeridos (R$ 20, R$ 50, R$ 100) e campo customizado; 

Tela do Pix com botão destacado "Copiar Código Pix"; 

Indicador de contagem regressiva para expiração da chave Pix.

### Regras de Negócio: 
1. Valor mínimo de recarga de R$ 5,00; 
2. Chave Pix temporária válida por até 15 minutos; 
3. Atualização automática do saldo do cartão assim que a Payment Service Provider (PSP) notificar o pagamento via webhook.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Pagamento Pix com sucesso e crédito em tempo real

Dado que escolho o valor de R$ 20,00 e gero o código Pix no app

Quando realizo o pagamento no meu aplicativo bancário

Então o AccessFlow deve receber o webhook de confirmação

E exibir uma tela de sucesso adicionando R$ 20,00 ao saldo do meu cartão virtual em menos de 10 segundos

Chave Pix expirada sem pagamento

Dado que gerei uma cobrança Pix e não efetuei o pagamento dentro do prazo de 15 minutos

Quando o tempo limite expira

Então a cobrança deve ser cancelada no app

E devo ver um aviso para gerar um novo código caso ainda deseje recarregar

### Orientações para Implementação: 

Integração com gateway de pagamentos via API Pix (Webhooks / WebSockets no frontend para atualização sem refresh); 

Registrar evento de analytics: recarga_pix_gerada, recarga_pix_sucesso, recarga_pix_expirada. Id do passo: 117

# 15. Beatriz — Recarga via cartão de crédito ou débito
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 2 — Recarga, Saldo e Segurança   

2. Jornada de Usuário: Beatriz — Configurar notificações automáticas e entender seu padrão de uso pelo extrato   

3. Passo: Recarregar um valor pequeno via cartão de crédito   

## Geral

Produto: AccessFlow

Título: Recarga de saldo com cartão de crédito/débito

Narrativa: Como Beatriz, usuária avulsa do sistema, eu quero cadastrar meu cartão de crédito ou débito para realizar recargas rápidas no aplicativo sem precisar sair do ambiente do app.

Prioridade: Média | Tipo: Feature | Coluna: Análise

## Detalhes
### Descrição Detalhada: 

Permitir a inclusão de cartões de crédito/débito com armazenamento seguro de tokens (tokenização), seleção de bandeira, digitação de CVV para autorização e salvamento do cartão para compras futuras com um toque.

### Orientações de Tela: 

Formulário de checkout de cartão de crédito com mascaramento automático; 

Opção "Salvar cartão para futuras compras"; 

Botão de confirmação "Pagar R$ XX,XX".

### Regras de Negócio: 

1. Não armazenar dados sensíveis de cartão (PAN, CVV) no banco de dados da aplicação (usar tokenização PCI-DSS); 
2. Exigir confirmação de CVV ou 3D Secure para cada transação efetuada.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Recarga aprovada com cartão de crédito salvo

Dado que selecionei um cartão de crédito cadastrado anteriormente e digitei o CVV correto

Quando confirmo a compra do valor selecionado

Então a transação deve ser processada junto à adquirente

E o valor aprovado deve ser somado imediatamente ao saldo do cartão virtual

Transação recusada pela operadora

Dado que tento recarregar com um cartão sem limite ou recusado pelo banco

Quando o pagamento é processado

Então devo ver uma mensagem amigável informando a recusa do cartão

E o saldo do meu cartão virtual deve permanecer inalterado

### Orientações para Implementação: 

Integração com SDK/API do gateway de pagamento com suporte a Tokenização e 3D Secure 2.0; 

Registrar evento de analytics: recarga_cartao_sucesso, recarga_cartao_recusada. Id do passo: 118

# 16. Cynthia — Extrato detalhado com filtros de período
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 2 — Recarga, Saldo e Segurança   

2. Jornada de Usuário: Cynthia — Recarregar o saldo pelo próprio app e acompanhar o extrato sem depender de ponto físico   

3. Passo: Conferir o extrato de viagens da semana   

## Geral

Produto: AccessFlow

Título: Consulta de extrato detalhado com filtros

Narrativa: Como Cynthia, usuária do app, eu quero filtrar meu extrato de movimentações por períodos (semana, mês) e tipos (recargas, viagens), para entender meus hábitos e controlar meus gastos com transporte.

Prioridade: Média | Tipo: Feature | Coluna: Análise

## Detalhes
### Descrição Detalhada: 

Tela de Extrato Financeiro e Operacional detalhada com visão clara de Entradas (Recargas Pix/Cartão/VT) em verde e Saídas (Validações/Embarques) em vermelho, com seletores de período flexíveis.

### Orientações de Tela: 

Cabeçalho com saldo atual e totais de entradas/saídas do período selecionado; 

Abas de filtro "Tudo", "Viagens", "Recargas"; 

Seletor de intervalo de datas (Últimos 7 dias, Mês Atual, Personalizado).

### Regras de Negócio: 

1. Exibir dados históricos de até 12 meses; 
2. Detalhamento de cada item deve mostrar dados do estabelecimento/linha, ID da transação e método utilizado.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Filtragem por viagens nos últimos 7 dias

Dado que estou na tela de extrato e seleciono a aba "Viagens" e o período "Últimos 7 dias"

Quando o filtro é aplicado

Então a lista deve exibir unicamente os débitos relativos aos embarques efetuados na última semana

E o totalizador de saídas deve calcular a soma exata dos valores exibidos

Extrato sem movimentação no período

Dado que seleciono um intervalo de datas em que não realizei viagens nem recargas

Quando a consulta é realizada

Então a tela deve exibir um estado vazio informativo ("Nenhuma movimentação encontrada neste período")

### Orientações para Implementação: 

Paginação de resultados via API REST/GraphQL no backend; 

Otimização de queries com índices por usuario_id e data_transacao; 

Registrar evento de analytics: extrato_consultado, extrato_filtro_aplicado. Id do passo: 119

# 17. Lucas — Bloqueio remoto de segurança via Web
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 2 — Recarga, Saldo e Segurança   

2. Jornada de Usuário: Lucas — Perder o celular, bloquear o cartão virtual remotamente e conseguir uma reemissão digital   

3. Passo: Bloquear o cartão remotamente por outro dispositivo   

## Geral

Produto: AccessFlow   

Título: Bloqueio remoto imediato de credencial (Perda/Roubo)

Narrativa: Como Lucas, trabalhador que teve o celular roubado ou perdido, eu quero acessar o Portal Web do Usuário por outro aparelho e bloquear meu cartão virtual imediatamente, para impedir o uso indevido do meu saldo.

Prioridade: Alta | Tipo: Security | Coluna: Análise

## Detalhes
### Descrição Detalhada: 

Portal de autoatendimento web (mobile-friendly) para o usuário final que permite realizar login seguro, visualizar seus cartões ativos e acionar o bloqueio de emergência em caso de perda, roubo ou furto do smartphone.

### Orientações de Tela: 

Botão destacado em vermelho "Bloquear Cartão por Perda/Roubo"; 

Caixa de diálogo de confirmação exigindo reentrada de senha; 

Tela de confirmação do bloqueio efetuado com timestamp e protocolo.

### Regras de Negócio: 

1. O bloqueio deve revogar imediatamente os tokens de validação ativos no backend e invalidar a lista de tokens offline em segundo plano; 
2. A credencial deve passar para o status "Bloqueado por Segurança".

## BDD & Implementação
### Critérios de Aceitação (BDD)

Bloqueio remoto com confirmação de senha

Dado que acessei a conta web por outro dispositivo após perder o celular

Quando seleciono o cartão e confirmo a ação "Bloquear por Perda/Roubo" inserindo minha senha

Então o status do cartão virtual deve mudar para "Bloqueado" instantaneamente

E qualquer tentativa de validação na catraca com os tokens do aparelho antigo deve ser rejeitada

Validação tentada com cartão bloqueado

Dado que o cartão de um usuário foi bloqueado remotamente

Quando o dispositivo antigo (ou token antigo) tenta ser lido em uma catraca

Então a catraca deve negar o acesso e exibir sinal sonoro/visual de credencial bloqueada

### Orientações para Implementação: 

Invalidação imediata de sessões JWT/OAuth do usuário e revogação do certificado HCE associado ao aparelho; 

Envio de e-mail de alerta sobre o bloqueio realizado; registrar evento de analytics: cartao_bloqueado_remotamente. Id do passo: 120

# 18. Lucas — Reemissão digital instantânea da credencial
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 2 — Recarga, Saldo e Segurança   

Jornada de Usuário: Lucas — Perder o celular, bloquear o cartão virtual remotamente e conseguir uma reemissão digital   

Passo: Solicitar a reemissão digital do cartão virtual   

## Geral

Produto: AccessFlow   

Título: Reemissão digital de cartão virtual

Narrativa: Como Lucas, usuário que acabou de bloquear seu cartão após trocar de celular, eu quero solicitar a reemissão digital do meu cartão no novo aparelho, para recuperar meu saldo e benefícios sem ter que pagar taxa ou ir a um posto físico.

Prioridade: Alta | Tipo: Feature | Coluna: Análise

## Detalhes
### Descrição Detalhada: 

Fluxo dentro do aplicativo em um novo dispositivo que identifica a existência de um cartão bloqueado por perda/roubo e permite a transferência do saldo e do vínculo para o novo aparelho de forma 100% digital.

### Orientações de Tela: 

Tela de onboarding no novo celular detectando "Você possui uma credencial bloqueada"; 

Botão "Reemitir Cartão Digital"; 

Etapa de verificação de identidade via biometria/SMS/e-mail; 

Tela final com novo cartão ativo e saldo preservado.

### Regras de Negócio: 

1. Transferir integralmente o saldo remanescente e os benefícios ativos da credencial antiga para a nova;
2. Desvincular o ID do dispositivo (Hardware ID) anterior e registrar o novo aparelho.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Reemissão com sucesso no novo celular

Dado que realizei login no aplicativo num smartphone novo e possuo um cartão bloqueado

Quando confirmo a validação de segurança e solicito a reemissão

Então uma nova credencial digital deve ser gerada vinculada ao novo aparelho

E o saldo anterior total deve estar integralmente disponível no novo cartão

Tentativa de reemissão sem confirmação de segurança

Dado que inicio o processo de reemissão no novo aparelho

Quando erro a verificação de segurança (código SMS/e-mail incorreto)

Então a reemissão não deve ser concluída

E a credencial deve permanecer no status "Bloqueado"

### Orientações para Implementação: 

Endpoint de provisionamento de nova credencial vinculada ao novo device_id; 

Migração atômica de saldo no banco de dados; 

Registrar evento de analytics: cartao_reemitido_digitalmente. Id do passo: 121

# 19. Marcos — Visualizar Dashboard Institucional em tempo real
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   

Jornada de Usuário: Marcos — Usar o painel web para gerenciar as credenciais dos alunos em escala   

Passo: Acessar o dashboard institucional   

## Geral

Produto: AccessFlow   

Título: Dashboard Web de Gestão Institucional

Narrativa: Como Marcos, coordenador de ensino, eu quero visualizar um painel com métricas consolidada de ativação, uso e status das credenciais dos alunos da instituição, para acompanhar o nível de adesão da comunidade ao aplicativo.

Prioridade: Média | Tipo: Feature | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 

Visão geral administrativa exibindo KPIs principais: Total de alunos elegíveis, Cartões virtuais ativados, Alunos pendentes de ativação, Volume diário de embarques e Saldo médio distribuído.

### Orientações de Tela: 

Painel web com cards de métricas (KPIs) no topo; 

Gráficos de rosca para distribuição de status (Ativos, Inativos, Pendentes); 

Gráfico de linhas para evolução de embarques nos últimos 30 dias.

### Regras de Negócio: 

1. Os dados do dashboard devem ser filtráveis por campus, curso ou período; 
2. O acesso deve ser restrito a gestores autenticados com papéis de administração da instituição.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Acesso ao dashboard com dados atualizados

Dado que faço login no Painel Web com perfil de Coordenador Institucional

Quando a página inicial do dashboard carrega

Então vejo o total de alunos elegíveis cadastrados e o percentual exato que já ativou o cartão virtual

Filtro por campus/unidade

Dado que estou visualizando o dashboard geral

Quando seleciono o filtro "Campus Zona Sul"

Então todos os cards de KPI e gráficos devem recalcular e exibir apenas as informações relativas àquela unidade

### Orientações para Implementação: 

Consultas otimizadas com visões materializadas (Materialized Views) no banco de dados para agregar métricas; 

Atualização via cache redis de curto prazo; registrar evento de analytics: painel_dashboard_visualizado. Id do passo: 122

# 20. Marcos — Bloquear e gerenciar credencial individual de usuário
## Passo de Jornada

Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   

Jornada de Usuário: Marcos — Usar o painel web para gerenciar as credenciais dos alunos em escala   

Passo: Bloquear e encerrar a credencial de um aluno que trancou o curso   

## Geral

Produto: AccessFlow   

Título: Gestão individual de status de credencial de usuário (CRUD)

Narrativa: Como Marcos, coordenador de ensino, eu quero buscar um aluno pelo nome ou matrícula e alterar o status da sua credencial (ativar, suspender, encerrar), para garantir que apenas estudantes com curso ativo utilizem o benefício.

Prioridade: Alta | Tipo: Feature | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 
Tabela de gerenciamento de usuários no Painel Web com busca rápida por CPF, Nome ou Matrícula, detalhamento do perfil do aluno e modal de ação para alteração imediata do status da credencial.

### Orientações de Tela: 

Tabela com ordenação e busca instantânea; 

Coluna de status com tags coloridas (Verde = Ativo, Amarelo = Pendente, Vermelho = Bloqueado/Encerrado); 

Botão de ações com menu dropdown ("Editar", "Suspender Benefício", "Bloquear").

### Regras de Negócio: 

1. A alteração de status feita no painel deve refletir em tempo real no aplicativo do aluno; 
2. Em caso de encerramento do vínculo, revogar o passe e desativar o cartão virtual.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Bloqueio de credencial por desvinculação acadêmica

Dado que busco a matrícula de um aluno que trancou a faculdade

Quando altero seu status no painel de "Ativo" para "Encerrado" e confirmo a justificativa

Então a credencial do aluno deve mudar para "Encerrada" no painel

E o aplicativo mobile do aluno deve exibir o cartão inativo no próximo acesso

Reativação de credencial suspensa

Dado que um aluno regularizou suas pendências acadêmicas

Quando o gestor altera o status de "Suspenso" para "Ativo" no painel web

Então a credencial deve voltar ao status "Ativo" imediatamente habilitando o uso do cartão

### Orientações para Implementação: 

API RESTful para atualização parcial de recursos (PATCH /api/v1/admin/usuarios/{id}/status); 

Registro obrigatório de log de auditoria com ID do gestor que realizou a alteração; 

Registrar evento de analytics: painel_status_usuario_alterado. Id do passo: 123

# 21. Marcos — Exportar relatório de auditoria e uso institucional

## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   

2. Jornada de Usuário: Marcos — Usar o painel web para gerenciar as credenciais dos alunos em escala   

3. Passo: Exportar o relatório de auditoria para a diretoria   

## Geral

Produto: AccessFlow   

Título: Exportação de relatórios de auditoria e uso

Narrativa: Como Marcos, coordenador de ensino, eu quero exportar relatórios customizados com os dados de uso dos benefícios e emissões do semestre, para prestar contas do programa à diretoria da instituição.

Prioridade: Média | Tipo: Feature | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 

Módulo de relatórios no Painel Web com opções de filtros por intervalo de datas, tipo de curso/departamento, modalidade de validação e status de usuários, permitindo exportar em formatos padrão de mercado (PDF e CSV/XLSX).

### Orientações de Tela: 

Tela "Relatórios e Auditoria"; seletores de filtros; caixas de seleção de colunas desejadas; botões "Gerar Relatório", "Exportar para PDF" e "Exportar para Excel".

### Regras de Negócio: 

1. Relatórios extensos com mais de 5.000 linhas devem ser processados em segundo plano e disponibilizados via link de download enviado por e-mail ao gestor.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Exportação de relatório mensal em CSV

Dado que seleciono o período do mês passado e o formato CSV

Quando clico em "Exportar para Excel"

Então o sistema deve gerar e baixar um arquivo CSV contendo os dados detalhados de cada usuário e total de utilizações no período

Relatório grande processado de forma assíncrona

Dado que solicito um relatório referente a um histórico de 2 anos com mais de 50.000 registros

Quando solicito a exportação

Então devo ver um aviso de que o relatório está sendo gerado

E devo receber um e-mail com o link de download seguro assim que a geração for concluída

### Orientações para Implementação: 

Utilizar filas de processamento em background (RabbitMQ/SQS + Workers) para geração de planilhas e PDFs pesados; 

Armazenar temporariamente os relatórios gerados em bucket S3 com expiração em 48h; 

Registrar evento de analytics: relatorio_gerado, relatorio_download_efetuado. Id do passo: 124

# 22. Ana — Integrar painel institucional ao sistema de RH via API

## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   

2. Jornada de Usuário: Ana — Configurar o crédito automático mensal e integrar o AccessFlow ao sistema de RH   

3. Passo: Integrar o painel ao sistema de RH da empresa   

## Geral

Produto: AccessFlow   

Título: Integração via API/Webhooks com sistemas de RH / ERP

Narrativa: Como Ana, analista de RH, eu quero conectar a plataforma AccessFlow ao sistema de RH da empresa via API, para sincronizar admissões, demissões e alterações de vale-transporte automaticamente sem envio manual de arquivos.

Prioridade: Alta | Tipo: Enabler | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 

Disponibilizar uma API Web (REST/Webhooks) com suporte a tokens de integração (API Keys) permitindo que o software de RH/ERP da empresa envie comandos automáticos de criação, atualização e encerramento de colaboradores elegíveis.

### Orientações de Tela: 

Tela no Painel Web "Configurações > Integrações API"; 

Gerador de Chaves de API (API Keys); 

Documentação de endpoints acessível diretamente no painel; histórico de chamadas de API (logs).

### Regras de Negócio: 

1. A API deve suportar autenticação OAuth2 / API Key em HTTPS; 
2. Todas as requisições devem ser validadas contra esquemas estritos; 
3. Limites de requisições (rate limiting) configurados para proteção do servidor.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Admissão de funcionário sincronizada via API

Dado que o sistema de RH envia um payload JSON válido para o endpoint POST /api/v1/integrations/colaboradores

Quando a requisição é processada

Então o novo colaborador deve ser cadastrado como elegível ao vale-transporte no AccessFlow

E um convite automático de ativação deve ser disparado para o e-mail do colaborador

Demissão de funcionário via API

Dado que o sistema de RH envia uma notificação de desligamento via API

Quando a requisição é recebida

Então a credencial de vale-transporte do colaborador deve ser bloqueada/desativada no AccessFlow imediatamente

### Orientações para Implementação: 

Desenvolver especificação OpenAPI 3.0 (Swagger); 

Criar middleware de autenticação e validação de API Key; 

Registrar log de auditoria detalhado das chamadas externas; 

Registrar evento de analytics: api_rh_requisicao_sucesso, api_rh_requisicao_erro. Id do passo: 125

# 23. Ana — Fechar relatório financeiro mensal de vale-transporte

## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   

2. Jornada de Usuário: Ana — Configurar o crédito automático mensal e integrar o AccessFlow ao sistema de RH   

3. Passo: Fechar o relatório de custo do mês para o financeiro   

## Geral

Produto: AccessFlow   

Título: Fechamento e relatório financeiro de Vale-Transporte

Narrativa: Como Ana, analista de RH, eu quero exportar a demonstração detalhada dos custos mensais com Vale-Transporte por centro de custo/departamento, para enviar ao setor financeiro até o dia 5 do mês.

Prioridade: Média | Tipo: Feature | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 

Módulo de consolidação de faturamento e extrato corporativo que apresenta o total recarregado em contas funcionais, saldos não utilizados e memória de cálculo por centro de custo/departamento no período.

### Orientações de Tela: 

Tela "Fechamento Mensal VT"; resumo com valor total creditado, taxa de serviço e valor líquido; gráfico de gastos por departamento; botão "Fechar Mês e Exportar para Financeiro".

### Regras de Negócio: 

1. O relatório de fechamento mensal deve bloquear alterações em períodos já encerrados para garantir a consistência contábil; 

2. Os valores consolidados devem ser idênticos aos da nota fiscal/fatura emitida.

## BDD & Implementação

### Critérios de Aceitação (BDD)

Geração do fechamento mensal de custo

Dado que estou no painel e seleciono o mês de referência a ser encerrado

Quando clico em "Gerar Fechamento Financeiro"

Então o sistema deve exibir o detalhamento de custos por departamento e o valor consolidado final

E permitir o download da memória de cálculo em formato Excel e PDF

Visualização de mês já encerrado

Dado que um mês financeiro já foi encerrado pelo gestor

Quando tento acessar os dados desse período

Então a tela deve exibir os valores em modo somente leitura (read-only) com o selo de "Período Encerrado"

### Orientações para Implementação: 

Rotina de fechamento contábil e congelamento de registros históricos no banco de dados (snapshot financeiro); 

Geração de relatórios formatados em PDF/XLSX via biblioteca dedicada; 

Registrar evento de analytics: fechamento_financeiro_concluido. Id do passo: 126

# 24. Roberto — Acompanhar dashboard da operadora com volume de validações por linha

## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   


2. Jornada de Usuário: Roberto — Acompanhar a adoção do AccessFlow e validar o contrato de comissão   


3. Passo: Acessar o painel da operadora e ver o volume de validações por linha   


## Geral

Produto: AccessFlow

Título: Dashboard operacional por linhas e frota para operadoras

Narrativa: Como Roberto, gestor de operadora de transporte, eu quero acompanhar no painel em tempo real o volume de validações efetuadas pelos passageiros em cada linha e veículo da frota, para monitorar a operação e validar o desempenho da bilhetagem digital.

Prioridade: Média | Tipo: Feature | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 

Painel de controle para operadoras de transporte exibindo o volume de passageiros pagantes via AccessFlow, separando por linha de ônibus/metrô, horários de pico, modalidade (NFC vs. QR Code) e veículos operantes.

### Orientações de Tela: 

Tabela e gráficos de volume de embarques por linha de transporte; 

Mapa de calor dos horários de maior fluxo de validações;

Seletor de intervalo de tempo (Hoje, Últimos 7 dias, Mês).

### Regras de Negócio: 

1. O painel deve exibir apenas os dados dos veículos e linhas pertencentes à concessão daquela operadora específica; 
2. Os dados de validação online devem ser atualizados em intervalo curto (múltiplas vezes por hora).

## BDD & Implementação
### Critérios de Aceitação (BDD)

Visualização de embarques por linha em tempo real

Dado que estou autenticado no painel da operadora

Quando visito o dashboard de linhas operacionais

Então vejo o total de embarques validados pelo AccessFlow hoje por linha

E posso identificar qual linha possui maior volume de passageiros utilizando o cartão virtual

Filtro por modalidade de validação (NFC vs QR Code)

Dado que estou analisando os dados de uma linha específica

Quando aplico o filtro por modalidade de validação

Então o gráfico deve dividir as validações entre NFC (HCE) e QR Code Dinâmico

### Orientações para Implementação: 

Pipeline de ingestão de eventos de validação em tempo real utilizando streaming de dados; 

Agregadores por janela de tempo no banco analítico; 

Registrar evento de analytics: painel_operadora_linhas_consultado. Id do passo: 127

# 25. Fernanda — Visualizar relatórios regulatórios agregados de mobilidade
   
## Passo de Jornada

1. Fase do Roadmap Estratégico: Fase 3 — Painel Web Institucional e Monetização   


2. Jornada de Usuário: Fernanda — Usar o painel institucional para fiscalizar a conformidade do AccessFlow em escala   


3. Passo: Acessar relatórios agregados de todas as operadoras conectadas   


## Geral

Produto: AccessFlow   

Título: Relatórios regulatórios e visão consolidada de mobilidade urbana

Narrativa: Como Fernanda, representante do órgão público gestor de mobilidade, eu quero visualizar relatórios consolidados e anonimizados do fluxo de validações e integração no sistema de transporte da cidade, para fiscalizar a conformidade regulatória e subsidiar políticas públicas de mobilidade.

Prioridade: Média | Tipo: Feature | Coluna: Backlog

## Detalhes
### Descrição Detalhada: 

Módulo regulatório e de governança do Painel Web direcionado a órgãos reguladores e consórcios públicos, apresentando visão macro da utilização do sistema, índices de gratuidade/desconto estudantil e conformidade com os termos de permissão do serviço.

### Orientações de Tela: 

Painel de visão regulatória consolidada; 

Gráficos de uso por tipo de tarifa (Estudante, VT, Avulso, Gratuidade); 

Tabela com indicadores agregados por operadora parceira.

### Regras de Negócio: 

1. Todos os dados apresentados nesta visão devem ser anonimizados e estar em conformidade estrita com a LGPD (Lei Geral de Proteção de Dados); 
2. Não permitir a identificação pessoal de passageiros individuais nos relatórios públicos/regulatórios.

## BDD & Implementação
### Critérios de Aceitação (BDD)

Consulta de dados agregados regulatórios sem identificadores pessoais

Dado que estou no painel regulatório do órgão público

Quando gero o relatório consolidado mensal de viagens da cidade

Então devo ver os totais de validações divididos por categoria de benefício e por operadora

E nenhum dado pessoal identificável (nome, CPF, foto) de usuários finais deve estar presente no relatório

Exportação de dados para auditoria regulatória

Dado que solicito a exportação de dados de conformidade técnica para o conselho

Quando clico em "Exportar Relatório Regulatório PDF"

Então um documento formal assinado digitalmente pelo sistema deve ser gerado contendo os índices operacionais exigidos em contrato

### Orientações para Implementação: 

Aplicar técnicas de anonimização e agregação de dados no banco analítico de relatórios; 

Suporte a assinatura digital de relatórios PDF com certificado digital ICP-Brasil / PKI; 

Registrar evento de analytics: relatorio_regulatorio_gerado. Id do passo: 128
