# bank-api-v2
API bancária de estudo, padrão produção. Java 25, Spring Boot 4.1, Maven (use ./mvnw), PostgreSQL via Docker.

## Regras inegociáveis
- Nunca escrever segredos no código; configuração sensível vem de variáveis de ambiente.
- Toda mudança de regra de negócio vem com teste.
- Nunca editar uma migration já aplicada; criar uma nova.
- Valores monetários: BigDecimal, nunca double.
- Antes de mudanças grandes, apresentar plano e esperar aprovação.
- Toda operação que move dinheiro deve ser atômica (@Transactional) e usar lock, seja pessimista (SELECT ... FOR UPDATE) ou otimista (@Version).
- Lançamentos são imutáveis: nada de UPDATE ou DELETE em transações. Correções são feitas com estorno.