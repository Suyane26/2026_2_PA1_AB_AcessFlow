# 📱 Produto e Visão: AccessFlow

**Documentação do Projeto** | Equipe: Ismael, Salua, Suyana e Wesley

## 📖 Descrição do Produto
Eu quero transformar o celular no cartão de transporte. A ideia é construir um aplicativo mobile e um painel web que substituam os cartões físicos de PVC e papel, como a carteirinha estudantil, o vale-transporte e o bilhete único.

No aplicativo, o usuário terá um cartão virtual com foto, nome, matrícula ou ID e tipo de benefício. Poderá validar o embarque por aproximação (NFC) ou por QR Code dinâmico, inclusive sem internet, graças ao modo offline automático. Também poderá recarregar créditos por Pix, cartão de crédito ou débito, consultar saldo, extrato e histórico de viagens, receber alertas e bloquear o cartão remotamente em caso de perda ou roubo do celular.

No painel web, empresas, instituições de ensino e operadoras vão poder cadastrar usuários, definir regras de benefício e recarga, acompanhar o uso em tempo real, emitir relatórios de auditoria e integrar o sistema à folha de pagamento, aos sistemas acadêmicos e à bilhetagem eletrônica.

> **Nota Técnica:** A validação por NFC usa HCE (Host Card Emulation), voltada a Android. No iPhone, o embarque é feito pelo QR Code dinâmico.

---

## 🎯 Matriz: É, Não é, Faz e Não faz

### ✅ O que É
* Plataforma de benefícios e pagamentos de transporte público, com app mobile e painel web.
* Alternativa digital aos cartões físicos (carteirinha estudantil, vale-transporte e bilhete único).
* Credencial de embarque no celular, por NFC (HCE) ou QR Code dinâmico.
* Camada de software e API que se integra aos validadores e catracas existentes.
* Sistema de gestão centralizada de benefícios para empresas, instituições de ensino e operadoras.
* Experiência mobile-first que funciona mesmo sem internet (modo offline automático).

### ❌ O que Não É
* Carteira digital de pagamentos gerais (como PicPay, Mercado Pago ou Apple Pay).
* Sistema de gestão de frotas, rotas ou motoristas.
* Aplicativo de planejamento de rotas ou navegação (como Google Maps ou Moovit).
* Hardware de catraca, validador ou leitor.
* Sistema acadêmico ou de RH completo (não lança notas, faltas ou folha de pagamento).
* Ferramenta para clonar ou duplicar cartões físicos de terceiros.

### ⚙️ O que Faz
* Emite o cartão virtual com foto, nome, matrícula ou ID e tipo de benefício.
* Valida o embarque por aproximação (NFC) ou por QR Code dinâmico, inclusive offline.
* Gera tokens criptografados, temporários e de curta duração.
* Permite recarga por Pix, cartão de crédito ou débito.
* Mostra saldo, extrato e histórico de viagens, e envia notificações de saldo baixo e de status.
* Permite bloqueio remoto imediato e reemissão digital do cartão.
* Permite à empresa ou instituição cadastrar usuários, definir regras de benefício e bloquear ou desbloquear credenciais pelo painel web.
* Oferece dashboard em tempo real, relatórios e logs de auditoria, e integra com folha de pagamento, sistemas acadêmicos e bilhetagem.

### 🚫 O que Não Faz
* Não realiza pagamentos em comércio, serviços ou aplicativos de delivery.
* Não substitui sistemas de gestão acadêmica nem de RH.
* Não gerencia frota, rotas ou motoristas das operadoras.
* Não substitui catracas, validadores ou sensores dos terminais e veículos.
* Não define tarifas nem gratuidades legais: aplica as regras definidas por operadoras e instituições.
* Não substitui o atendimento presencial em casos que exijam documentação oficial.
* Não valida embarque em NFC no iPhone: nele, a validação é por QR Code dinâmico.

---

## 🔭 Visão do Produto
* **Para:** Estudantes, trabalhadores e usuários do transporte público, e para as instituições e empresas que gerenciam seus benefícios de transporte.
* **Que dores enfrentam:** Filas na catraca, cartões esquecidos ou não reconhecidos, saldo incerto na hora de embarcar e o risco de ficar sem acesso ao perder ou ter o cartão roubado, além de uma gestão manual e sem visibilidade dos benefícios.
* **O:** AccessFlow.
* **Que benefícios:** Transforma o celular na própria credencial de embarque, com validação instantânea por NFC ou QR Code dinâmico, mesmo offline, além de recarga, saldo em tempo real e bloqueio remoto em um toque.
* **É uma:** Plataforma mobile-first de mobilidade urbana, com app para o usuário final e painel web de gestão para instituições.
* **Diferente de:** Libercard e outras soluções de recarga, que ainda dependem do cartão físico na catraca.
* **O nosso produto:** Elimina o cartão físico de vez: o celular é o passe, continua funcionando sem internet e entrega a empresas, escolas e operadoras um painel único de controle.