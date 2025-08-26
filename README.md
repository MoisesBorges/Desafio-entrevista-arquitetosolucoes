## Desafio-entrevista-arquitetosolucoes
## Projeto de arquitetura escalável com monitoramento e observabilidade

## Sistema de Controle de Lançamentos e Consolidação Diária

## Descrição do Projeto
Este projeto tem como objetivo fornecer uma solução para o controle de lançamentos financeiros (débitos e créditos) e a geração de relatórios consolidados de saldo diário.  
A arquitetura foi desenhada com foco em escalabilidade, resiliência, segurança e facilidade de manutenção, aplicando boas práticas de desenvolvimento e arquitetura de software.

## Objetivos Principais

- Automatizar o registro e consulta de lançamentos financeiros
- Consolidar saldos por data e tipo de transação
- Expor dados financeiros via APIs REST
- Garantir segurança, escalabilidade e alta disponibilidade
- Facilitar integração com sistemas legados e novos canais

## Arquitetura da Solução

A solução foi estruturada com base em microsserviços para proporcionar desacoplamento, escalabilidade e resiliência. Cada serviço tem responsabilidade própria, permitindo evolução e manutenção independentes.

## Requisitos Funcionais
  
- RF01: Registrar lançamentos com data, valor, tipo e descrição
- RF02: Validar dados obrigatórios e tipos permitidos
- RF03: Consultar lançamentos por data ou intervalo
- RF04: Calcular saldo diário com base nos lançamentos
- RF05: Expor saldo consolidado via API
- RF06: Autenticar usuários via JWT
- RF07: Autorizar ações com base em perfis
- RF08: Registrar logs de acesso e ações sensíveis
- RF09: Expor métricas de uso e performance
- RF10: Gerar alertas em caso de falhas

## Requisitos Não Funcionais

•	RNF01: Tempo de resposta inferior a 500ms para consultas
•	RNF02: Disponibilidade mínima de 99,9%
•	RNF03: Escalabilidade horizontal dos serviços
•	RNF04: Criptografia de dados em trânsito (TLS)
•	RNF05: Proteção contra CSRF, XSS e brute force
•	RNF06: Logs estruturados por serviço
•	RNF07: Dashboards com métricas de latência e erros
•	RNF08: Código modular e testável
•	RNF09: Reprocessamento automático de eventos em caso de falha
•	RNF10: Suporte a múltiplos usuários simultâneos


### Componentes Principais

- **API Gateway**: Responsável por autenticação, autorização, roteamento e rate limiting.
- **Lançamentos Service**: Serviço responsável por criar, atualizar, consultar e excluir lançamentos financeiros. Publica eventos para o serviço de consolidação.
- **Consolidado Service**: Consome eventos de lançamentos, calcula o saldo diário consolidado e disponibiliza relatórios via API.
- **Banco de Dados**: Armazena os lançamentos e os saldos consolidados.
- **Cache (opcional)**: Redis utilizado para consultas rápidas de saldos consolidados.
- **Observabilidade e Logs**: Monitoramento e auditoria com Prometheus, Grafana e ELK Stack.

## Diagrama de Componentes
O diagrama apresenta a interação entre os serviços principais, banco de dados, cache, gateway e camada de observabilidade.

<img width="801" height="711" alt="Diagrama_componentes drawio" src="https://github.com/user-attachments/assets/0715ddb1-b202-401a-a764-ecf91d1a3ab3" />

## Diagrama 








## Tecnologias Utilizadas

| Componente        | Tecnologia            | Finalidade                                |
|-------------------|----------------------|------------------------------------------|
| Backend          | Node.js / Spring Boot | Desenvolvimento dos microsserviços      |
| API Gateway      | Kong / Nginx         | Roteamento, autenticação e limites      |
| Banco de Dados   | PostgreSQL / MySQL   | Persistência dos dados                  |
| Cache           | Redis                | Otimização de consultas                |
| Mensageria      | Kafka / RabbitMQ     | Comunicação assíncrona entre serviços  |
| Observabilidade | Prometheus / Grafana | Monitoramento de métricas             |
| Logs            | ELK Stack           | Centralização de registros e auditoria |
| Containerização | Docker + Compose    | Orquestração e empacotamento           |
