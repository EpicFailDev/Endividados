# Endividados — plano inicial do produto

**Status:** planejamento, sem implementação de código  
**Data:** 2026-10-08

## Visão do produto

O Endividados será um organizador financeiro mobile-first, simples e rápido, para registrar, visualizar e editar despesas e rendas. Um casal ou grupo familiar poderá compartilhar um espaço financeiro: os lançamentos feitos nesse espaço ficam visíveis aos seus membros.

**Promessa inicial:** registrar um movimento financeiro sem fricção e manter as pessoas do espaço compartilhado a par, sem depender de planilhas ou mensagens.

## Decisões confirmadas

- O aplicativo não usará IA.
- O foco é lançar, visualizar e editar gastos, despesas e rendas.
- O produto deve priorizar uma experiência mobile rápida, simples e intuitiva.
- Os membros convidados compartilham os lançamentos feitos dentro do espaço financeiro compartilhado.
- A automação de build acordada é gerar um APK de teste em cada commit para a branch principal e criar um GitHub Release oficial somente quando uma versão for marcada.
- Ainda não iniciar implementação enquanto as ideias e regras do produto estão sendo consolidadas.

## Escopo proposto para a primeira versão

1. Criar um espaço financeiro compartilhado.
2. Convidar outra pessoa e permitir que ela aceite o convite.
3. Registrar manualmente despesas e rendas.
4. Consultar o histórico compartilhado e editar um lançamento.
5. Exibir um resumo dos valores registrados por período.

### Campos de lançamento a definir

A proposta inicial é incluir valor, tipo de movimento, data, categoria e descrição opcional. Ainda falta decidir quais campos serão obrigatórios; a prioridade é manter o registro rápido.

### Regras de compartilhamento a definir

- Regra base: o que for lançado dentro do espaço compartilhado fica visível para os membros desse espaço.
- Ainda é preciso definir como serão tratados registros pessoais fora do espaço compartilhado.
- Ainda é preciso definir se qualquer membro pode editar qualquer lançamento ou se a edição terá limites.

## Direção mobile e visual

O HTML criado no Google Stitch será usado como referência visual, não como implementação funcional. A direção é preservar uma interface mobile clara e simplificar a tela para priorizar:

- identidade do espaço compartilhado e seus membros;
- resumo das rendas e despesas registradas;
- ação principal para novo lançamento;
- lista de movimentos com autor visível e acesso simples à edição.

Metas, relatórios avançados, transferências e pagamento de boletos ficam fora do escopo inicial até serem priorizados. O “saldo em conta” não deve ser apresentado como saldo bancário real sem integração ou reconciliação com as contas.

## Direção técnica recomendada

A stack recomendada para avaliação e futura implementação é:

- TypeScript;
- aplicativo mobile em React Native com Expo;
- API em Node.js com Express;
- PostgreSQL;
- Prisma para acesso ao banco;
- Socket.IO para atualização dos lançamentos entre membros.

Essa é uma direção técnica planejada, ainda não implementada. O uso do Oracle Cloud Free Tier como hospedagem também precisa ser validado, incluindo backups, segurança e operação.

## Builds e distribuição Android

- Em cada push para a branch principal, GitHub Actions deverá acionar o build de um APK de teste e disponibilizá-lo como artefato para download.
- Um GitHub Release oficial será criado somente para uma versão marcada.
- Gerar um APK não instala o app automaticamente nos celulares; é um arquivo instalável para distribuição de teste.
- Tokens e credenciais de assinatura devem ficar em secrets, nunca no código ou no repositório.

Esta política está acordada; o workflow ainda não foi configurado.

## Próximas decisões de produto

1. Definir os passos de cadastro, criação do espaço e convite.
2. Definir os campos obrigatórios no lançamento e como editar movimentos.
3. Definir se haverá registros pessoais fora do espaço compartilhado.
4. Desenhar o fluxo mobile de início, novo lançamento e histórico.
5. Planejar arquitetura, autenticação, isolamento dos espaços, backups e implantação antes de programar.
