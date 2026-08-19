# Descrição da Ideia

Plataforma digital de mobilidade urbana, disponível em versões web e mobile, voltada para usuários de transporte público que utilizam cartões físicos como carteirinha de estudante, vale-transporte e bilhete único. Substitui os cartões de PVC e papel, permitindo recarga de créditos, consulta de saldo, uso do celular como meio de pagamento (NFC ou QR Code) e bloqueio remoto em caso de perda ou roubo. Centraliza em um único aplicativo todas as funcionalidades de recarga, consulta e validação, com gestão administrativa para empresas, instituições de ensino e operadoras de transporte. Não é carteira digital de pagamentos gerais, sistema de gestão de frotas, aplicativo de planejamento de rotas ou hardware de catraca — é a camada de software que integra benefícios de transporte ao dispositivo móvel do usuário.

## Matriz de Alinhamento do Produto: MobilidadeFlow (Ecossistema Web & Mobile)

### 1. É (Identidade e Posicionamento do Produto)
* Plataforma integrada de benefícios e pagamentos de transporte público com aplicativo mobile para usuários e painel web para gestores.
* Solução móvel baseada em NFC (HCE) e QR Code Dinâmico para validação rápida e segura nos terminais, ônibus, metrô e trens.
* Alternativa digital aos cartões físicos de transporte (carteirinha estudantil, vale-transporte, bilhete único) com recarga remota, consulta de saldo e bloqueio em caso de perda ou roubo.
* Sistema de gerenciamento centralizado na web para administração de benefícios por empresas, instituições de ensino e operadoras de transporte.
* Solução moderna, ecológica e inclusiva que reduz a dependência de cartões físicos, filas em bilheterias e custos de reemissão.

### 2. Não É (Delimitação de Escopo e Fronteiras)
* Não é uma carteira digital de pagamentos gerais (como PicPay, Mercado Pago ou Apple Pay) para compras em estabelecimentos.
* Não é um sistema de gestão de frotas ou logística voltado para empresas de transporte ou rastreamento de veículos.
* Não é um aplicativo de planejamento de rotas ou navegação (como Google Maps, Moovit ou Citymapper).
* Não é o hardware físico das catracas, validadores ou leitores (é a camada de software e API que se integra aos equipamentos existentes).
* Não é um sistema acadêmico completo (não gerencia notas, faltas, boletins ou ementas de disciplinas).

### 3. Faz (Funcionalidades e Entregáveis do Produto)

**No Aplicativo Mobile (Usuários Finais: Estudantes, Trabalhadores e Usuários do Transporte):**
* Permite recarga de créditos de vale-transporte, carteirinha estudantil e bilhete único diretamente pelo celular, via PIX, cartão de crédito ou débito.
* Exibe o cartão virtual do usuário com foto, nome, número de matrícula/ID, tipo de benefício (estudante, VT, comum), saldo atual e status em tempo real.
* Oferece dupla modalidade de validação: por aproximação via NFC ou leitura ótica de QR Code Dinâmico nos terminais e veículos.
* Permite ao usuário consultar histórico pessoal de recargas, saldos e viagens realizadas (locais, datas, horários e valores).
* Notifica o usuário sobre saldo baixo, liberações de benefícios, bloqueios de segurança ou pendências administrativas.
* Permite bloqueio remoto imediato em caso de perda ou roubo do celular, com reemissão digital sem necessidade de deslocamento a postos físicos.

**No Painel Web (Administradores: Empresas, Instituições de Ensino e Operadoras de Transporte):**
* Gerencia perfis e benefícios de usuários (CRUD): cadastra, vincula, ativa, suspende e bloqueia usuários e credenciais remotamente em tempo real.
* Administra benefícios de vale-transporte e carteirinha estudantil: define valores, periodicidade de recarga, regras de elegibilidade e validação automática.
* Monitora movimentação e uso em tempo real (Live Dashboard): exibe gráficos de fluxo de usuários, saldos médios, recargas realizadas e padrões de uso.
* Emite relatórios detalhados e logs de auditoria: filtra dados de recargas, saldos e viagens por data, perfil, benefício ou método de validação (NFC vs. QR Code).
* Gerencia integrações com sistemas existentes: conecta-se a folhas de pagamento (RH), sistemas acadêmicos (matrículas) e operadoras de transporte (bilhetagem eletrônica).

### 4. Não Faz (Fora do Escopo do Projeto)
* Não realiza pagamentos em estabelecimentos comerciais (comércio, serviços, aplicativos de delivery, etc.).
* Não substitui sistemas de gestão acadêmica ou de RH para lançamento de notas, faltas, cálculo de folha ou benefícios trabalhistas.
* Não gerencia frota de veículos, rotas ou motoristas de empresas de transporte.
* Não substitui a estrutura física das catracas, validadores ou sensores nos terminais e veículos.
* Não permite clonagem ou duplicação de cartões físicos de terceiros ou sistemas legados de bilhetagem.

### Resumo da Matriz de Alinhamento

| É | Não é |
|---|---|
| Plataforma de benefícios e pagamentos de transporte (App + Web). | Não é carteira digital de pagamentos gerais. |
| Solução de recarga e validação via NFC e QR Code Dinâmico. | Não é sistema de gestão de frotas ou logística. |
| Alternativa digital aos cartões físicos de transporte. | Não é aplicativo de planejamento de rotas. |
| Sistema de gestão centralizada para empresas, escolas e operadoras. | Não é hardware de catraca ou validador físico. |

| Faz | Não faz |
|---|---|
| Mobile: Recarga, cartão virtual, acesso por NFC/QR, histórico e bloqueio. | Não realiza pagamentos em estabelecimentos comerciais. |
| Web: Gestão de benefícios, regras, dashboard ao vivo e relatórios. | Não substitui sistemas acadêmicos ou de RH completos. |
| Gera tokens criptografados temporários de curta duração. | Não gerencia frota, rotas ou motoristas. |
| Permite bloqueio/desbloqueio remoto imediato via web. | Não substitui estrutura física das catracas e sensores. |
